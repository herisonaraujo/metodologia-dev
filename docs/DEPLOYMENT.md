# Guia de Deploy

## Visao Geral

Processo de deploy estruturado para garantir entregas consistentes em producao.

```
LOCAL → BUILD → TEST → STAGING → PRODUCTION
```

---

## Ambiente de Producao

### Infraestrutura Base

```
┌─────────────────────────────────────────────────────────────────────────┐
│                            CLOUDFLARE                                    │
│                   (DNS, SSL, CDN, DDoS Protection)                       │
├─────────────────────────────────────────────────────────────────────────┤
│                              NGINX                                       │
│                        (Reverse Proxy)                                   │
├──────────────────────────────┬──────────────────────────────────────────┤
│        FRONTEND              │              BACKEND                      │
│     (Docker Container)       │          (Docker Container)               │
│        Next.js               │             NestJS                        │
│        Port 3001             │             Port 3000                     │
├──────────────────────────────┴──────────────────────────────────────────┤
│                           DATABASES                                      │
│              PostgreSQL (5432) │ Redis (6379)                            │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Servidor VPS

### Requisitos Minimos

| Recurso | Especificacao |
|---------|---------------|
| vCPU | 2 cores |
| RAM | 4 GB |
| Storage | 80 GB SSD |
| OS | Ubuntu 22.04 LTS |
| Rede | 1 Gbps |

### Setup Inicial

```bash
# Atualizar sistema
sudo apt update && sudo apt upgrade -y

# Instalar dependencias
sudo apt install -y curl git nginx certbot python3-certbot-nginx

# Instalar Docker
curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker $USER

# Instalar Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

---

## Nginx Configuration

### Site Configuration

```nginx
# /etc/nginx/sites-available/app.conf

upstream frontend {
    server 127.0.0.1:3001;
}

upstream backend {
    server 127.0.0.1:3000;
}

server {
    listen 80;
    server_name example.com www.example.com;
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl http2;
    server_name example.com www.example.com;

    ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;

    # Security headers
    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header X-XSS-Protection "1; mode=block" always;

    # Frontend
    location / {
        proxy_pass http://frontend;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }

    # API
    location /api {
        proxy_pass http://backend;
        proxy_http_version 1.1;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    # Static files cache
    location ~* \.(js|css|png|jpg|jpeg|gif|ico|svg|woff|woff2)$ {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }
}
```

---

## Docker Compose Production

```yaml
# docker-compose.prod.yml
version: '3.8'

services:
  frontend:
    build:
      context: ./frontend
      dockerfile: Dockerfile.prod
    restart: always
    ports:
      - "127.0.0.1:3001:3000"
    environment:
      - NODE_ENV=production
      - NEXT_PUBLIC_API_URL=https://example.com/api
    depends_on:
      - backend

  backend:
    build:
      context: ./backend
      dockerfile: Dockerfile.prod
    restart: always
    ports:
      - "127.0.0.1:3000:3000"
    environment:
      - NODE_ENV=production
      - DATABASE_URL=postgresql://user:pass@db:5432/app?schema=public
      - REDIS_URL=redis://redis:6379
      - JWT_SECRET=${JWT_SECRET}
    depends_on:
      - db
      - redis

  db:
    image: postgres:15-alpine
    restart: always
    volumes:
      - postgres_data:/var/lib/postgresql/data
      - ./backups:/backups
    environment:
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=pass
      - POSTGRES_DB=app

  redis:
    image: redis:7-alpine
    restart: always
    volumes:
      - redis_data:/data
    command: redis-server --appendonly yes

volumes:
  postgres_data:
  redis_data:
```

---

## Deploy Script

```bash
#!/bin/bash
# deploy.sh

set -e

echo "=== Iniciando deploy ==="

# Variaveis
PROJECT_DIR="/var/www/app"
BACKUP_DIR="/var/backups/app"

# Criar backup do banco
echo ">>> Criando backup..."
docker exec app_db_1 pg_dump -U user app > "$BACKUP_DIR/backup_$(date +%Y%m%d_%H%M%S).sql"

# Pull das alteracoes
echo ">>> Atualizando codigo..."
cd $PROJECT_DIR
git pull origin main

# Build e restart
echo ">>> Rebuilding containers..."
docker-compose -f docker-compose.prod.yml build --no-cache
docker-compose -f docker-compose.prod.yml up -d

# Migrations
echo ">>> Executando migrations..."
docker exec app_backend_1 npx prisma migrate deploy

# Limpeza
echo ">>> Limpando imagens antigas..."
docker image prune -f

# Health check
echo ">>> Verificando saude..."
sleep 5
curl -f http://localhost:3000/api/health || exit 1

echo "=== Deploy concluido com sucesso ==="
```

---

## SSL com Certbot

```bash
# Gerar certificado
sudo certbot --nginx -d example.com -d www.example.com

# Renovacao automatica (cron)
echo "0 0 1 * * certbot renew --quiet" | sudo tee -a /etc/crontab
```

---

## Cloudflare Setup

### DNS Records

| Type | Name | Content | Proxy |
|------|------|---------|-------|
| A | @ | SERVER_IP | Proxied |
| A | www | SERVER_IP | Proxied |
| CNAME | api | @ | Proxied |

### SSL/TLS Settings

- Mode: Full (strict)
- Always Use HTTPS: On
- Minimum TLS Version: 1.2

### Page Rules

```
*example.com/*
├── Cache Level: Cache Everything
├── Edge Cache TTL: 1 month
└── Browser Cache TTL: 1 year

example.com/api/*
├── Cache Level: Bypass
└── Security Level: High
```

---

## Backup Automatico

```bash
#!/bin/bash
# backup.sh

BACKUP_DIR="/var/backups/app"
RETENTION_DAYS=30

# Backup banco
docker exec app_db_1 pg_dump -U user app | gzip > "$BACKUP_DIR/db_$(date +%Y%m%d).sql.gz"

# Backup arquivos
tar -czf "$BACKUP_DIR/files_$(date +%Y%m%d).tar.gz" /var/www/app/uploads

# Limpar backups antigos
find $BACKUP_DIR -name "*.gz" -mtime +$RETENTION_DAYS -delete

# Enviar para storage externo (opcional)
# rclone copy $BACKUP_DIR remote:backups/
```

### Cron Schedule

```bash
# /etc/crontab
0 3 * * * root /var/www/app/scripts/backup.sh
```

---

## Monitoramento

### Health Check Endpoint

```typescript
// backend/src/health/health.controller.ts
@Controller('health')
export class HealthController {
  constructor(private prisma: PrismaService) {}

  @Get()
  async check() {
    const dbHealthy = await this.checkDatabase();

    return {
      status: dbHealthy ? 'healthy' : 'unhealthy',
      timestamp: new Date().toISOString(),
      services: {
        database: dbHealthy,
        cache: await this.checkRedis(),
      },
    };
  }

  private async checkDatabase(): Promise<boolean> {
    try {
      await this.prisma.$queryRaw`SELECT 1`;
      return true;
    } catch {
      return false;
    }
  }
}
```

### Uptime Monitoring

- Endpoint: `https://example.com/api/health`
- Intervalo: 1 minuto
- Alerta: Slack/Email

---

## Rollback

```bash
#!/bin/bash
# rollback.sh

# Reverter para commit anterior
cd /var/www/app
git reset --hard HEAD~1

# Rebuild
docker-compose -f docker-compose.prod.yml build
docker-compose -f docker-compose.prod.yml up -d

# Restaurar backup do banco (se necessario)
# cat /var/backups/app/backup_YYYYMMDD.sql | docker exec -i app_db_1 psql -U user app
```

---

## Checklist Pre-Deploy

```
[ ] Testes passando localmente
[ ] Variaveis de ambiente configuradas
[ ] Migrations testadas em staging
[ ] Backup do banco criado
[ ] DNS propagado (se novo dominio)
[ ] SSL certificado valido
[ ] Health check respondendo
[ ] Logs sem erros criticos
```
