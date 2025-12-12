<div align="center">

<br>

# ⚙️ Metodologia de Desenvolvimento

<br>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0a192f,100:1a365d&height=120&section=header&text=&fontSize=0" width="100%"/>

<br>

### Arquitetura • Processo • Entrega

<br>

<p align="center">
  <a href="#arquitetura">
    <img src="https://img.shields.io/badge/ARQUITETURA-0a192f?style=for-the-badge&logoColor=white" alt="Arquitetura"/>
  </a>
  <a href="#processo">
    <img src="https://img.shields.io/badge/PROCESSO-1a365d?style=for-the-badge&logoColor=white" alt="Processo"/>
  </a>
  <a href="#stack">
    <img src="https://img.shields.io/badge/STACK-d4af37?style=for-the-badge&logoColor=black" alt="Stack"/>
  </a>
  <a href="#projetos">
    <img src="https://img.shields.io/badge/PROJETOS-00875f?style=for-the-badge&logoColor=white" alt="Projetos"/>
  </a>
</p>

<br>

<table>
<tr>
<td>

```
 Problema identificado
        ↓
 Arquitetura desenhada
        ↓
 Codigo em producao
```

</td>
</tr>
</table>

<br>

<p>
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript"/>
  <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black" alt="React"/>
  <img src="https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=next.js&logoColor=white" alt="Next.js"/>
  <img src="https://img.shields.io/badge/NestJS-E0234E?style=flat-square&logo=nestjs&logoColor=white" alt="NestJS"/>
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white" alt="Docker"/>
  <img src="https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white" alt="Cloudflare"/>
</p>

<br>

---

</div>

<br>

## 🏛️ Arquitetura

<a name="arquitetura"></a>

> O desenho precede o codigo. Sempre.

Cada projeto comeca com a definicao clara das camadas, responsabilidades e fluxos de dados. Isso elimina retrabalho e garante escalabilidade desde o dia zero.

<br>

<div align="center">
  <img src="./architecture/01-arquitetura.svg" alt="Arquitetura do Sistema" width="720"/>
</div>

<br>

<table>
<thead>
<tr>
<th width="25%">Camada</th>
<th width="35%">Responsabilidade</th>
<th width="40%">Tecnologias</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Cliente</strong></td>
<td>Interface, UX, Responsividade</td>
<td><code>Next.js</code> <code>React</code> <code>Tailwind</code></td>
</tr>
<tr>
<td><strong>Servidor</strong></td>
<td>Logica de Negocio, APIs, Auth</td>
<td><code>NestJS</code> <code>Node.js</code> <code>TypeScript</code></td>
</tr>
<tr>
<td><strong>Dados</strong></td>
<td>Persistencia, Cache, Queries</td>
<td><code>PostgreSQL</code> <code>Redis</code> <code>Prisma</code></td>
</tr>
<tr>
<td><strong>Infra</strong></td>
<td>Deploy, Seguranca, CDN</td>
<td><code>Docker</code> <code>VPS</code> <code>Cloudflare</code></td>
</tr>
</tbody>
</table>

<br>

---

<br>

## 🚀 Processo

<a name="processo"></a>

> Ciclo continuo orientado a producao.

Cada iteracao resulta em software funcionando. Nao existe "quase pronto". Existe no ar ou nao existe.

<br>

<div align="center">
  <img src="./architecture/02-ciclo-entrega.svg" alt="Ciclo de Entrega" width="600"/>
</div>

<br>

<div align="center">

| Design | Build | Test | Deploy | Monitor |
|:------:|:-----:|:----:|:------:|:-------:|
| Wireframes | Codigo | Unitarios | Container | Logs |
| Prototipos | Review | Integracao | Producao | Metricas |
| UI/UX | Refactor | E2E | SSL/CDN | Alertas |

</div>

<br>

### Diferencial na Abordagem

<div align="center">
  <img src="./architecture/03-comparacao.svg" alt="Comparacao" width="650"/>
</div>

<br>

<table>
<tr>
<td width="50%">

**Consultoria Tradicional**
```
Semana 1   → Diagnostico
Semana 2   → Proposta
Semana 3   → Revisao
Semana 4   → Contrato
Semana 5-12→ "Desenvolvimento"
Semana 13+ → Ajustes infinitos
```

</td>
<td width="50%">

**Entrega Direta**
```
Semana 1 → Sistema no ar
Semana 2 → Usuarios testando
Semana 3 → Ajustes em producao
Semana 4 → Segunda feature

✓ Problema resolvido
```

</td>
</tr>
</table>

<br>

---

<br>

## 🛠️ Stack

<a name="stack"></a>

> Type-safe de ponta a ponta.

Stack moderna otimizada para produtividade, manutencao e performance em escala.

<br>

<div align="center">
  <img src="./architecture/04-stack.svg" alt="Stack Tecnologica" width="720"/>
</div>

<br>

<table>
<tr>
<td align="center" width="25%">
<br>
<img src="https://skillicons.dev/icons?i=react,nextjs,ts,tailwind" /><br><br>
<strong>Frontend</strong><br>
<sub>React • Next.js • TypeScript • Tailwind</sub>
<br><br>
</td>
<td align="center" width="25%">
<br>
<img src="https://skillicons.dev/icons?i=nodejs,nestjs,express,graphql" /><br><br>
<strong>Backend</strong><br>
<sub>Node.js • NestJS • Express • GraphQL</sub>
<br><br>
</td>
<td align="center" width="25%">
<br>
<img src="https://skillicons.dev/icons?i=postgres,mongodb,redis,prisma" /><br><br>
<strong>Database</strong><br>
<sub>PostgreSQL • MongoDB • Redis • Prisma</sub>
<br><br>
</td>
<td align="center" width="25%">
<br>
<img src="https://skillicons.dev/icons?i=docker,aws,cloudflare,nginx" /><br><br>
<strong>Infra</strong><br>
<sub>Docker • AWS • Cloudflare • Nginx</sub>
<br><br>
</td>
</tr>
</table>

<br>

### Integracoes Especializadas

<div align="center">

| <img src="https://img.shields.io/badge/AI-000?style=flat-square"/> AI & LLMs | <img src="https://img.shields.io/badge/PAY-000?style=flat-square"/> Pagamentos | <img src="https://img.shields.io/badge/COM-000?style=flat-square"/> Comunicacao |
|:---:|:---:|:---:|
| OpenAI API | PIX Integration | WhatsApp API |
| Claude API | Banking APIs | Email Transacional |
| AI Agents | Payment Gateways | SMS Gateway |

</div>

<br>

---

<br>

## 📦 Entrega

> Nao entrego codigo. Entrego solucao funcionando.

<br>

<div align="center">
  <img src="./architecture/06-entrega.svg" alt="Entrega Completa" width="650"/>
</div>

<br>

<div align="center">

```
┌─────────────────┬─────────────────┬─────────────────┬─────────────────┐
│     CODIGO      │      INFRA      │    OPERACAO     │      DOCS       │
├─────────────────┼─────────────────┼─────────────────┼─────────────────┤
│ ✓ Frontend      │ ✓ Servidor VPS  │ ✓ Dominio       │ ✓ README        │
│ ✓ Backend       │ ✓ Docker        │ ✓ Email Corp.   │ ✓ API Docs      │
│ ✓ Database      │ ✓ SSL/HTTPS     │ ✓ Backups       │ ✓ Deploy Guide  │
│ ✓ Testes        │ ✓ CDN           │ ✓ Monitor 24/7  │ ✓ Arquitetura   │
└─────────────────┴─────────────────┴─────────────────┴─────────────────┘
```

</div>

<br>

### Fluxo Completo

<div align="center">
  <img src="./architecture/07-fluxo-entrega-real.svg" alt="Fluxo de Entrega Real" width="800"/>
</div>

<br>

---

<br>

## 🏆 Projetos

<a name="projetos"></a>

> Cases reais. Sistemas ativos. Usuarios de verdade.

<br>

<div align="center">
  <img src="./architecture/05-projetos.svg" alt="Projetos em Producao" width="650"/>
</div>

<br>

<table>
<thead>
<tr>
<th>Projeto</th>
<th>Tipo</th>
<th>Destaques</th>
<th>Status</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="https://prophetique.com.br"><strong>prophetique.com.br</strong></a></td>
<td>Consultoria Tech</td>
<td><code>SEO 100/100</code> <code>Performance</code></td>
<td><a href="https://prophetique.com.br" target="_blank"><img src="https://img.shields.io/badge/●_Visitar-Online-00875f?style=flat-square&labelColor=0a192f"/></a></td>
</tr>
<tr>
<td><a href="https://bemficamarchado.com"><strong>bemficamarchado.com</strong></a></td>
<td>Export Internacional</td>
<td><code>8 idiomas</code> <code>RTL</code> <code>Multi-moeda</code></td>
<td><a href="https://bemficamarchado.com" target="_blank"><img src="https://img.shields.io/badge/●_Visitar-Online-00875f?style=flat-square&labelColor=0a192f"/></a></td>
</tr>
<tr>
<td><a href="https://reflorestamentobrasil.com.br"><strong>reflorestamentobrasil.com.br</strong></a></td>
<td>E-commerce Ambiental</td>
<td><code>WhatsApp API</code> <code>Orcamentos</code></td>
<td><a href="https://reflorestamentobrasil.com.br" target="_blank"><img src="https://img.shields.io/badge/●_Visitar-Online-00875f?style=flat-square&labelColor=0a192f"/></a></td>
</tr>
<tr>
<td><strong>Enterprise Systems</strong></td>
<td>Fintech & ERP</td>
<td><code>PIX</code> <code>Banking</code> <code>Microservices</code></td>
<td><img src="https://img.shields.io/badge/●-Privado-1a365d?style=flat-square&labelColor=0a192f"/></td>
</tr>
</tbody>
</table>

<br>

### Tempo Medio de Entrega

<div align="center">

| Tipo | Prazo | O que inclui |
|:-----|:-----:|:-------------|
| **Landing Page** | 1 semana | Design, codigo, deploy, dominio, SSL |
| **Sistema Web** | 2-4 semanas | Full-stack, auth, API, infra completa |
| **E-commerce** | 3-5 semanas | Catalogo, carrinho, pagamento, admin |
| **SaaS MVP** | 4-6 semanas | Multi-tenant, billing, dashboard |

</div>

<br>

---

<br>

## 📂 Estrutura

```
metodologia-dev/
│
├── README.md                 # Visao geral da metodologia
├── LICENSE                   # MIT License
│
├── architecture/             # Diagramas de arquitetura
│   ├── 01-arquitetura.svg
│   ├── 02-ciclo-entrega.svg
│   ├── 03-comparacao.svg
│   ├── 04-stack.svg
│   ├── 05-projetos.svg
│   ├── 06-entrega.svg
│   └── 07-fluxo-entrega-real.svg
│
├── docs/                     # Documentacao tecnica
│   ├── ARCHITECTURE.md       # Principios e patterns
│   ├── STACK.md              # Detalhamento da stack
│   └── DEPLOYMENT.md         # Guia de deploy
│
└── templates/                # Templates reutilizaveis
    ├── project-structure.md  # Estrutura padrao de projeto
    └── api-documentation.md  # Template de API docs
```

<br>

---

<br>

<div align="center">

## 🤝 Contato

<br>

**Herison da Costa Araujo**

Full-Stack Developer

<br>

<a href="https://herisonaraujo.github.io">
  <img src="https://img.shields.io/badge/Portfolio-herisonaraujo.github.io-d4af37?style=for-the-badge&labelColor=0a192f" alt="Portfolio"/>
</a>

<br><br>

<a href="https://linkedin.com/in/herison-araujo">
  <img src="https://img.shields.io/badge/LinkedIn-herison--araujo-0077b5?style=for-the-badge&logo=linkedin&labelColor=0a192f" alt="LinkedIn"/>
</a>
&nbsp;
<a href="https://github.com/herisonaraujo">
  <img src="https://img.shields.io/badge/GitHub-herisonaraujo-ffffff?style=for-the-badge&logo=github&labelColor=0a192f" alt="GitHub"/>
</a>

<br><br>

<a href="mailto:herison@prophetique.com.br">
  <img src="https://img.shields.io/badge/Email-herison%40prophetique.com.br-d4af37?style=flat-square" alt="Email"/>
</a>
&nbsp;&nbsp;
<a href="https://wa.me/5532999735469">
  <img src="https://img.shields.io/badge/WhatsApp-(32)%2099973--5469-25D366?style=flat-square&logo=whatsapp&logoColor=white" alt="WhatsApp"/>
</a>

<br><br>

---

<br>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1a365d,100:0a192f&height=100&section=footer" width="100%"/>

<br>

*"Arquitetura primeiro, codigo depois. Excelencia em cada entrega."*

<br>

</div>
