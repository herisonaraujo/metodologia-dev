# Template: Estrutura de Projeto

## Full-Stack Application

```
project-name/
│
├── frontend/                      # Aplicacao Next.js
│   ├── src/
│   │   ├── app/                   # App Router
│   │   │   ├── (auth)/           # Rotas autenticadas
│   │   │   ├── (public)/         # Rotas publicas
│   │   │   ├── api/              # API Routes
│   │   │   ├── layout.tsx
│   │   │   └── page.tsx
│   │   │
│   │   ├── components/
│   │   │   ├── ui/               # Componentes base
│   │   │   ├── forms/            # Formularios
│   │   │   └── layouts/          # Layouts
│   │   │
│   │   ├── lib/                  # Utilitarios
│   │   ├── hooks/                # Custom hooks
│   │   ├── services/             # API calls
│   │   ├── types/                # TypeScript types
│   │   └── styles/               # Estilos globais
│   │
│   ├── public/                   # Assets estaticos
│   ├── next.config.js
│   ├── tailwind.config.js
│   ├── tsconfig.json
│   └── package.json
│
├── backend/                       # Aplicacao NestJS
│   ├── src/
│   │   ├── modules/
│   │   │   ├── auth/             # Autenticacao
│   │   │   ├── users/            # Usuarios
│   │   │   └── [domain]/         # Dominios de negocio
│   │   │
│   │   ├── common/
│   │   │   ├── decorators/
│   │   │   ├── guards/
│   │   │   ├── interceptors/
│   │   │   └── filters/
│   │   │
│   │   ├── config/               # Configuracoes
│   │   ├── database/             # Prisma
│   │   │   ├── schema.prisma
│   │   │   └── migrations/
│   │   │
│   │   ├── app.module.ts
│   │   └── main.ts
│   │
│   ├── test/                     # Testes E2E
│   ├── tsconfig.json
│   └── package.json
│
├── docker/                        # Docker configs
│   ├── frontend/
│   │   └── Dockerfile
│   └── backend/
│       └── Dockerfile
│
├── docs/                          # Documentacao
│   ├── ARCHITECTURE.md
│   ├── API.md
│   └── DEPLOYMENT.md
│
├── scripts/                       # Scripts utilitarios
│   ├── deploy.sh
│   ├── backup.sh
│   └── setup.sh
│
├── .github/                       # GitHub configs
│   └── workflows/
│       └── ci.yml
│
├── docker-compose.yml            # Development
├── docker-compose.prod.yml       # Production
├── .env.example
├── .gitignore
├── README.md
└── LICENSE
```

---

## Arquivos de Configuracao

### .gitignore

```gitignore
# Dependencies
node_modules/
.pnpm-store/

# Build
dist/
.next/
out/

# Environment
.env
.env.local
.env.*.local

# IDE
.vscode/
.idea/
*.swp

# Logs
*.log
npm-debug.log*

# OS
.DS_Store
Thumbs.db

# Testing
coverage/

# Prisma
prisma/*.db
prisma/*.db-journal
```

### .env.example

```env
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/dbname

# Redis
REDIS_URL=redis://localhost:6379

# JWT
JWT_SECRET=your-secret-key
JWT_EXPIRES_IN=7d

# Frontend
NEXT_PUBLIC_API_URL=http://localhost:3000/api

# Email
SMTP_HOST=smtp.example.com
SMTP_PORT=587
SMTP_USER=user@example.com
SMTP_PASS=password

# External APIs
OPENAI_API_KEY=sk-...
```

### tsconfig.json (Frontend)

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "bundler",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true,
    "plugins": [{ "name": "next" }],
    "paths": {
      "@/*": ["./src/*"]
    }
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", ".next/types/**/*.ts"],
  "exclude": ["node_modules"]
}
```

---

## Scripts Package.json

### Frontend

```json
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint",
    "type-check": "tsc --noEmit"
  }
}
```

### Backend

```json
{
  "scripts": {
    "dev": "nest start --watch",
    "build": "nest build",
    "start": "node dist/main",
    "start:prod": "node dist/main",
    "lint": "eslint \"{src,test}/**/*.ts\"",
    "test": "jest",
    "test:e2e": "jest --config ./test/jest-e2e.json",
    "db:migrate": "prisma migrate dev",
    "db:push": "prisma db push",
    "db:studio": "prisma studio"
  }
}
```

---

## GitHub Actions CI

```yaml
# .github/workflows/ci.yml
name: CI

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  frontend:
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: frontend

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
          cache-dependency-path: frontend/package-lock.json

      - name: Install dependencies
        run: npm ci

      - name: Type check
        run: npm run type-check

      - name: Lint
        run: npm run lint

      - name: Build
        run: npm run build

  backend:
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: backend

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
          cache-dependency-path: backend/package-lock.json

      - name: Install dependencies
        run: npm ci

      - name: Lint
        run: npm run lint

      - name: Test
        run: npm run test

      - name: Build
        run: npm run build
```

---

## Inicializacao Rapida

```bash
# Clone o template
git clone https://github.com/username/project-template.git my-project
cd my-project

# Setup ambiente
cp .env.example .env

# Instalar dependencias
cd frontend && npm install
cd ../backend && npm install

# Iniciar banco
docker-compose up -d db redis

# Rodar migrations
cd backend && npm run db:migrate

# Iniciar desenvolvimento
# Terminal 1
cd frontend && npm run dev

# Terminal 2
cd backend && npm run dev
```
