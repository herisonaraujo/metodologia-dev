# Stack Tecnologica

## Visao Geral

Stack otimizada para produtividade, manutencao e performance em producao.

```
┌────────────────────────────────────────────────────────────────────────┐
│                              STACK                                      │
├──────────────┬──────────────┬──────────────┬──────────────┬────────────┤
│   FRONTEND   │   BACKEND    │   DATABASE   │    INFRA     │    AI      │
├──────────────┼──────────────┼──────────────┼──────────────┼────────────┤
│   Next.js    │   NestJS     │  PostgreSQL  │   Docker     │  OpenAI    │
│   React      │   Node.js    │  Redis       │   VPS        │  Claude    │
│   TypeScript │   TypeScript │  Prisma      │   Cloudflare │  Agents    │
│   Tailwind   │   GraphQL    │  MongoDB     │   Nginx      │  Embeddings│
└──────────────┴──────────────┴──────────────┴──────────────┴────────────┘
```

---

## Frontend

### Core

| Tecnologia | Versao | Uso |
|------------|--------|-----|
| Next.js | 14+ | Framework React com SSR/SSG |
| React | 18+ | Biblioteca UI |
| TypeScript | 5+ | Type safety |
| Tailwind CSS | 3+ | Styling utility-first |

### Bibliotecas Complementares

```json
{
  "dependencies": {
    "next": "^14.0.0",
    "react": "^18.2.0",
    "tailwindcss": "^3.4.0",
    "framer-motion": "^11.0.0",
    "lucide-react": "^0.300.0",
    "date-fns": "^3.0.0",
    "zod": "^3.22.0",
    "react-hook-form": "^7.50.0",
    "@tanstack/react-query": "^5.0.0"
  }
}
```

### Estrutura de Componentes

```
components/
├── ui/                    # Primitivos
│   ├── Button.tsx
│   ├── Input.tsx
│   ├── Card.tsx
│   └── Modal.tsx
│
├── forms/                 # Formularios complexos
│   ├── LoginForm.tsx
│   └── ContactForm.tsx
│
└── layouts/               # Estruturas de pagina
    ├── Header.tsx
    ├── Footer.tsx
    └── Sidebar.tsx
```

---

## Backend

### Core

| Tecnologia | Versao | Uso |
|------------|--------|-----|
| NestJS | 10+ | Framework backend estruturado |
| Node.js | 20 LTS | Runtime |
| TypeScript | 5+ | Type safety |
| Prisma | 5+ | ORM type-safe |

### Dependencias Principais

```json
{
  "dependencies": {
    "@nestjs/core": "^10.0.0",
    "@nestjs/platform-express": "^10.0.0",
    "@nestjs/jwt": "^10.2.0",
    "@nestjs/passport": "^10.0.0",
    "@prisma/client": "^5.0.0",
    "bcrypt": "^5.1.0",
    "class-validator": "^0.14.0",
    "class-transformer": "^0.5.0"
  }
}
```

### Modulos Padrao

```typescript
// Estrutura de modulo NestJS
@Module({
  imports: [
    PrismaModule,
    JwtModule.register({
      secret: process.env.JWT_SECRET,
      signOptions: { expiresIn: '7d' },
    }),
  ],
  controllers: [AuthController],
  providers: [AuthService],
  exports: [AuthService],
})
export class AuthModule {}
```

---

## Database

### PostgreSQL (Principal)

Banco relacional para dados estruturados e transacionais.

```sql
-- Exemplo de schema
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) UNIQUE NOT NULL,
  name VARCHAR(255) NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_users_email ON users(email);
```

### Redis (Cache)

Cache de sessoes, filas e dados temporarios.

```typescript
// Uso com cache
@Injectable()
export class CacheService {
  constructor(private redis: Redis) {}

  async get<T>(key: string): Promise<T | null> {
    const data = await this.redis.get(key);
    return data ? JSON.parse(data) : null;
  }

  async set(key: string, value: any, ttl: number): Promise<void> {
    await this.redis.setex(key, ttl, JSON.stringify(value));
  }
}
```

### Prisma ORM

Schema type-safe com migrations automaticas.

```prisma
// schema.prisma
model User {
  id        String   @id @default(uuid())
  email     String   @unique
  name      String
  posts     Post[]
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}

model Post {
  id        String   @id @default(uuid())
  title     String
  content   String?
  author    User     @relation(fields: [authorId], references: [id])
  authorId  String
  createdAt DateTime @default(now())
}
```

---

## Infraestrutura

### Docker

Containerizacao para deploy consistente.

```dockerfile
# Dockerfile (Backend)
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM node:20-alpine AS runner
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
EXPOSE 3000
CMD ["node", "dist/main.js"]
```

### Docker Compose

Orquestracao de servicos.

```yaml
# docker-compose.yml
version: '3.8'

services:
  api:
    build: ./backend
    ports:
      - "3000:3000"
    environment:
      - DATABASE_URL=postgresql://user:pass@db:5432/app
    depends_on:
      - db
      - redis

  db:
    image: postgres:15-alpine
    volumes:
      - postgres_data:/var/lib/postgresql/data
    environment:
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=pass
      - POSTGRES_DB=app

  redis:
    image: redis:7-alpine
    volumes:
      - redis_data:/data

volumes:
  postgres_data:
  redis_data:
```

### Cloudflare

CDN, DNS e protecao.

- SSL/TLS automatico
- DDoS protection
- Cache de assets
- DNS management
- Email routing

---

## Integracoes AI

### OpenAI

```typescript
import OpenAI from 'openai';

const openai = new OpenAI({
  apiKey: process.env.OPENAI_API_KEY,
});

async function generateText(prompt: string): Promise<string> {
  const response = await openai.chat.completions.create({
    model: 'gpt-4',
    messages: [{ role: 'user', content: prompt }],
  });

  return response.choices[0].message.content;
}
```

### Claude API

```typescript
import Anthropic from '@anthropic-ai/sdk';

const anthropic = new Anthropic({
  apiKey: process.env.CLAUDE_API_KEY,
});

async function analyze(content: string): Promise<string> {
  const response = await anthropic.messages.create({
    model: 'claude-3-opus-20240229',
    max_tokens: 1024,
    messages: [{ role: 'user', content }],
  });

  return response.content[0].text;
}
```

---

## Pagamentos

### PIX Integration

```typescript
interface PixPayment {
  txid: string;
  valor: {
    original: string;
  };
  chave: string;
  infoAdicionais?: Array<{
    nome: string;
    valor: string;
  }>;
}

async function createPixCharge(amount: number): Promise<PixPayment> {
  // Integracao com API do banco
  const response = await bankApi.post('/pix/cob', {
    valor: { original: amount.toFixed(2) },
    chave: process.env.PIX_KEY,
  });

  return response.data;
}
```

---

## Ferramentas de Desenvolvimento

| Categoria | Ferramenta |
|-----------|------------|
| Editor | VS Code |
| Version Control | Git |
| Package Manager | pnpm |
| Linting | ESLint |
| Formatting | Prettier |
| Testing | Jest, Vitest |
| API Testing | Insomnia, Bruno |
| Database | DBeaver, pgAdmin |
| Design | Figma |
| Diagramas | PlantUML |
