# Arquitetura de Software

## Principios de Design

### 1. Separacao de Responsabilidades

Cada camada do sistema possui responsabilidades bem definidas:

```
┌─────────────────────────────────────────────────────────────┐
│                      PRESENTATION                            │
│              UI Components, Pages, Layouts                   │
├─────────────────────────────────────────────────────────────┤
│                      APPLICATION                             │
│            Controllers, Use Cases, DTOs                      │
├─────────────────────────────────────────────────────────────┤
│                        DOMAIN                                │
│           Entities, Business Rules, Interfaces               │
├─────────────────────────────────────────────────────────────┤
│                     INFRASTRUCTURE                           │
│         Database, External APIs, File System                 │
└─────────────────────────────────────────────────────────────┘
```

### 2. Type Safety

TypeScript em toda a stack garante:

- Erros capturados em tempo de compilacao
- Autocomplete e documentacao inline
- Refatoracao segura
- Contratos claros entre camadas

### 3. API First

APIs sao desenhadas antes da implementacao:

```typescript
// Contrato definido primeiro
interface CreateUserDTO {
  email: string;
  name: string;
  password: string;
}

interface UserResponse {
  id: string;
  email: string;
  name: string;
  createdAt: Date;
}

// Implementacao segue o contrato
async createUser(dto: CreateUserDTO): Promise<UserResponse>
```

---

## Estrutura de Projeto Padrao

### Frontend (Next.js)

```
src/
├── app/                    # App Router (Next.js 14+)
│   ├── (auth)/            # Grupo de rotas autenticadas
│   ├── (public)/          # Rotas publicas
│   ├── api/               # API Routes
│   └── layout.tsx         # Layout raiz
│
├── components/
│   ├── ui/                # Componentes base (Button, Input, etc)
│   ├── forms/             # Formularios
│   └── layouts/           # Layouts reutilizaveis
│
├── lib/                   # Utilitarios e configuracoes
├── hooks/                 # Custom hooks
├── services/              # Chamadas a APIs
├── types/                 # TypeScript types
└── styles/                # Estilos globais
```

### Backend (NestJS)

```
src/
├── modules/
│   ├── auth/              # Autenticacao
│   │   ├── auth.controller.ts
│   │   ├── auth.service.ts
│   │   ├── auth.module.ts
│   │   └── dto/
│   │
│   ├── users/             # Usuarios
│   └── [domain]/          # Outros dominios
│
├── common/
│   ├── decorators/        # Decorators customizados
│   ├── guards/            # Auth guards
│   ├── interceptors/      # Interceptors
│   └── filters/           # Exception filters
│
├── config/                # Configuracoes
├── database/              # Prisma schema, migrations
└── main.ts                # Entry point
```

---

## Padroes de Comunicacao

### REST API

```
GET    /api/v1/users          # Listar
GET    /api/v1/users/:id      # Buscar por ID
POST   /api/v1/users          # Criar
PATCH  /api/v1/users/:id      # Atualizar parcial
DELETE /api/v1/users/:id      # Remover
```

### Respostas Padronizadas

```typescript
// Sucesso
{
  "success": true,
  "data": { ... },
  "meta": {
    "page": 1,
    "limit": 20,
    "total": 150
  }
}

// Erro
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Email invalido",
    "details": [...]
  }
}
```

---

## Seguranca

### Autenticacao

- JWT com refresh tokens
- Cookies HTTP-only para web
- Rate limiting por IP e usuario

### Validacao

- Input validation em todas as rotas
- Sanitizacao de dados
- Prepared statements (Prisma)

### Headers

```
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
Strict-Transport-Security: max-age=31536000
Content-Security-Policy: default-src 'self'
```

---

## Performance

### Frontend

- Server-side rendering (SSR)
- Static generation (SSG) onde possivel
- Image optimization (next/image)
- Code splitting automatico
- Lazy loading de componentes

### Backend

- Connection pooling (Prisma)
- Redis para cache de sessoes
- Query optimization
- Compression (gzip)

### Infraestrutura

- CDN (Cloudflare)
- Cache de assets (1 ano)
- HTTP/2
- Brotli compression
