<div align="center">

# Metodologia de Desenvolvimento

### Arquitetura, Processo e Entrega de Software

<br>

[![Stack](https://img.shields.io/badge/Stack-Full--Stack-0a192f?style=for-the-badge&labelColor=1a365d)](https://github.com/herisonaraujo)
[![TypeScript](https://img.shields.io/badge/TypeScript-100%25-d4af37?style=for-the-badge&labelColor=0a192f)](https://www.typescriptlang.org/)
[![Deploy](https://img.shields.io/badge/Deploy-Production-00875f?style=for-the-badge&labelColor=0a192f)](https://github.com/herisonaraujo)

<br>

**Documentacao completa da metodologia de desenvolvimento utilizada em projetos de software.**

[Arquitetura](#arquitetura) • [Processo](#processo-de-entrega) • [Stack](#stack-tecnologica) • [Projetos](#projetos-em-producao) • [Contato](#contato)

<br>

---

</div>

## Visao Geral

Este repositorio documenta a metodologia de desenvolvimento aplicada em projetos de software corporativo. O objetivo e garantir entregas consistentes, documentadas e em producao.

```
Problema identificado → Arquitetura desenhada → Codigo em producao
```

<br>

## Arquitetura

O desenho da arquitetura precede qualquer linha de codigo. Isso garante clareza nas decisoes tecnicas e alinhamento com os requisitos de negocio.

<br>

<div align="center">

### Arquitetura Base

<img src="./architecture/01-arquitetura.svg" alt="Arquitetura do Projeto" width="700">

</div>

<br>

### Camadas do Sistema

| Camada | Responsabilidade | Tecnologias |
|--------|------------------|-------------|
| **Cliente** | Interface do usuario, experiencia, responsividade | Next.js, React, Tailwind CSS |
| **Servidor** | Logica de negocio, autenticacao, APIs | NestJS, Node.js, TypeScript |
| **Dados** | Persistencia, cache, queries otimizadas | PostgreSQL, Redis, Prisma ORM |
| **Infraestrutura** | Hospedagem, seguranca, performance | Docker, VPS, Cloudflare, SSL |

<br>

---

<br>

## Processo de Entrega

O ciclo de entrega e continuo e orientado a producao. Cada iteracao resulta em software funcionando.

<br>

<div align="center">

### Ciclo de Entrega

<img src="./architecture/02-ciclo-entrega.svg" alt="Ciclo de Entrega" width="600">

</div>

<br>

### Fases do Ciclo

```
┌─────────────────────────────────────────────────────────────────────────┐
│                                                                         │
│   DESIGN        BUILD         TEST          DEPLOY        MONITOR      │
│   ──────        ─────         ────          ──────        ───────      │
│   Wireframes    Codigo        Unitarios     Build         Logs         │
│   Prototipos    Review        Integracao    Container     Metricas     │
│   UI/UX         Refactor      E2E           Producao      Alertas      │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Stack Tecnologica

Stack moderna, type-safe e otimizada para produtividade e manutencao.

<br>

<div align="center">

### Stack Completa

<img src="./architecture/04-stack.svg" alt="Stack Tecnologica" width="700">

</div>

<br>

### Detalhamento

<table>
<tr>
<td width="25%" valign="top">

**Frontend**
- React.js
- Next.js 14+
- TypeScript
- Tailwind CSS
- Framer Motion

</td>
<td width="25%" valign="top">

**Backend**
- Node.js
- NestJS
- Express
- GraphQL
- REST APIs

</td>
<td width="25%" valign="top">

**Database**
- PostgreSQL
- MongoDB
- Redis
- Prisma ORM
- Drizzle

</td>
<td width="25%" valign="top">

**Infra**
- Docker
- AWS / VPS
- Cloudflare
- CI/CD
- Nginx

</td>
</tr>
</table>

<br>

### Integracoes Especializadas

| Categoria | Tecnologias |
|-----------|-------------|
| **AI & LLMs** | OpenAI API, Claude API, AI Agents, Embeddings |
| **Pagamentos** | PIX, Banking APIs, Payment Gateways |
| **Comunicacao** | WhatsApp API, Email Transacional, SMS |
| **Analytics** | Google Analytics, Eventos customizados |

<br>

---

<br>

## Entrega Completa

Nao entrego apenas codigo. Entrego solucao funcionando em producao.

<br>

<div align="center">

### O Que Esta Incluido

<img src="./architecture/06-entrega.svg" alt="Entrega Completa" width="650">

</div>

<br>

### Checklist de Entrega

```
CODIGO                    INFRAESTRUTURA           OPERACAO
──────                    ──────────────           ────────
[x] Frontend              [x] Servidor VPS         [x] Dominio configurado
[x] Backend               [x] Docker containers    [x] Email corporativo
[x] Banco de dados        [x] SSL/HTTPS            [x] Backups automaticos
[x] Testes                [x] CDN Cloudflare       [x] Monitoramento 24/7

DOCUMENTACAO
────────────
[x] README tecnico
[x] API documentation
[x] Deploy guide
[x] Diagrama de arquitetura
```

<br>

---

<br>

## Fluxo de Entrega Real

Do briefing ate o sistema online, com todas as conexoes explicitas.

<br>

<div align="center">

### Fluxo Completo

<img src="./architecture/07-fluxo-entrega-real.svg" alt="Fluxo de Entrega Real" width="800">

</div>

<br>

### Tempo Medio de Entrega

| Tipo de Projeto | Prazo | Inclui |
|-----------------|-------|--------|
| Landing Page | 1 semana | Design, codigo, deploy, dominio |
| Sistema Web | 2-4 semanas | Full-stack, auth, API, infra |
| E-commerce | 3-5 semanas | Catalogo, carrinho, pagamento, admin |
| SaaS MVP | 4-6 semanas | Multi-tenant, billing, dashboard |

<br>

---

<br>

## Projetos em Producao

Cases reais com sistemas ativos e usuarios.

<br>

<div align="center">

<img src="./architecture/05-projetos.svg" alt="Projetos em Producao" width="650">

</div>

<br>

### Portfolio Ativo

| Projeto | Tipo | Destaques | Status |
|---------|------|-----------|--------|
| [prophetique.com.br](https://prophetique.com.br) | Consultoria Tech | SEO 100/100, Performance otimizada | [![Online](https://img.shields.io/badge/-Online-00875f?style=flat-square)]() |
| [bemficamarchado.com](https://bemficamarchado.com) | Exportacao Internacional | 8 idiomas, RTL, Multi-moeda | [![Online](https://img.shields.io/badge/-Online-00875f?style=flat-square)]() |
| [reflorestamentobrasil.com.br](https://reflorestamentobrasil.com.br) | E-commerce Ambiental | WhatsApp API, Sistema de orcamentos | [![Online](https://img.shields.io/badge/-Online-00875f?style=flat-square)]() |
| Enterprise Systems | Fintech & ERP | PIX, Banking, Microservices | [![Privado](https://img.shields.io/badge/-Privado-1a365d?style=flat-square)]() |

<br>

---

<br>

## Abordagem

<div align="center">

### Consultoria Tradicional vs Entrega Direta

<img src="./architecture/03-comparacao.svg" alt="Comparacao de Abordagem" width="650">

</div>

<br>

```
CONSULTORIA TRADICIONAL              ENTREGA DIRETA
───────────────────────              ──────────────

Semana 1: Diagnostico                Semana 1: Sistema no ar
Semana 2: Proposta                   Semana 2: Usuarios testando
Semana 3: Revisao                    Semana 3: Ajustes em producao
Semana 4: Contrato                   Semana 4: Segunda feature pronta
Semana 5-12: Desenvolvimento
Semana 13+: Ajustes infinitos        Problema resolvido.
```

<br>

---

<br>

## Estrutura do Repositorio

```
metodologia-dev/
│
├── README.md                 # Este documento
├── LICENSE
│
├── architecture/             # Diagramas de arquitetura
│   ├── 01-arquitetura.svg
│   ├── 02-ciclo-entrega.svg
│   ├── 03-comparacao.svg
│   ├── 04-stack.svg
│   ├── 05-projetos.svg
│   ├── 06-entrega.svg
│   ├── 07-fluxo-entrega-real.svg
│   └── *.puml                # Fontes PlantUML
│
├── docs/                     # Documentacao detalhada
│   ├── ARCHITECTURE.md
│   ├── STACK.md
│   └── DEPLOYMENT.md
│
└── templates/                # Templates reutilizaveis
    ├── project-structure.md
    └── api-documentation.md
```

<br>

---

<br>

## Contato

<div align="center">

<br>

**Herison da Costa Araujo**

Full-Stack Developer

<br>

[![Portfolio](https://img.shields.io/badge/Portfolio-herisonaraujo.github.io-d4af37?style=for-the-badge&labelColor=0a192f)](https://herisonaraujo.github.io)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-herison--araujo-0077b5?style=for-the-badge&logo=linkedin&labelColor=0a192f)](https://linkedin.com/in/herison-araujo)

[![GitHub](https://img.shields.io/badge/GitHub-herisonaraujo-ffffff?style=for-the-badge&logo=github&labelColor=0a192f)](https://github.com/herisonaraujo)

<br>

[![Email](https://img.shields.io/badge/Email-herison%40prophetique.com.br-d4af37?style=flat-square)](mailto:herison@prophetique.com.br)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-(32)%2099973--5469-25D366?style=flat-square)](https://wa.me/5532999735469)

<br>

---

<br>

*"Arquitetura primeiro, codigo depois. Excelencia em cada entrega."*

<br>

</div>
