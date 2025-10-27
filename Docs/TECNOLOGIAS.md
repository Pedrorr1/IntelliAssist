# Tecnologias Utilizadas - IntelliAssist

## Stack Tecnológico

### Frontend
![React](https://img.shields.io/badge/React-18.2.0-blue?logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue?logo=typescript)
![Tailwind](https://img.shields.io/badge/TailwindCSS-3.3-blue?logo=tailwindcss)
![Vite](https://img.shields.io/badge/Vite-4.3-purple?logo=vite)

**Principais bibliotecas:**
- **React Router DOM** (6.11): Roteamento de páginas
- **Axios** (1.4): Cliente HTTP para chamadas de API
- **React Query** (4.29): Gerenciamento de estado e cache
- **React Hook Form** (7.44): Formulários com validação
- **Zod** (3.21): Validação de schemas TypeScript-first
- **Zustand** (4.3): Estado global leve
- **Socket.io Client** (4.6): WebSocket para chat real-time
- **Recharts** (2.6): Gráficos e visualizações
- **date-fns** (2.30): Manipulação de datas
- **React Hot Toast** (2.4): Notificações toast

**Ferramentas de desenvolvimento:**
- ESLint + Prettier: Linting e formatação
- Vitest: Testes unitários
- Cypress: Testes E2E
- Storybook: Documentação de componentes

---

### Backend
![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-0.109-green?logo=fastapi)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue?logo=postgresql)
![Redis](https://img.shields.io/badge/Redis-7.2-red?logo=redis)

**Framework e bibliotecas principais:**
- **FastAPI** (0.109): Framework web assíncrono
- **SQLAlchemy** (2.0): ORM para banco de dados
- **Alembic** (1.13): Migrations de banco de dados
- **Pydantic** (2.5): Validação de dados e serialização
- **python-jose** (3.3): JWT tokens
- **passlib** (1.7): Hash de senhas com bcrypt
- **python-multipart** (0.0.6): Upload de arquivos
- **aiohttp** (3.9): Cliente HTTP assíncrono
- **celery** (5.3): Tarefas assíncronas em background
- **redis-py** (5.0): Cliente Redis para cache
- **openai** (1.12): SDK oficial OpenAI
- **langchain** (0.1): Framework para aplicações com LLMs

**Infraestrutura e DevOps:**
- **uvicorn** (0.27): ASGI server
- **gunicorn** (21.2): WSGI server para produção
- **pytest** (8.0): Framework de testes
- **pytest-asyncio** (0.23): Testes assíncronos
- **pytest-cov** (4.1): Cobertura de código
- **black** (24.1): Formatador de código
- **ruff** (0.2): Linter rápido

---

### Banco de Dados

**PostgreSQL 15**
- Banco principal para dados estruturados
- Schemas: public, auth, chat, automation, analytics
- Índices otimizados para queries frequentes
- Triggers para auditoria automática

**Redis 7.2**
- Cache de sessões de usuário (TTL: 24h)
- Cache de respostas frequentes da IA (TTL: 1h)
- Rate limiting
- Filas do Celery para tarefas assíncronas

**Estrutura do Banco:**
```sql
-- Principais tabelas
users (id, email, name, password_hash, created_at, updated_at)
conversations (id, user_id, title, created_at, updated_at)
messages (id, conversation_id, role, content, tokens, created_at)
reminders (id, user_id, title, scheduled_at, status, created_at)
automations (id, user_id, name, workflow_json, enabled, created_at)
```

---

### Inteligência Artificial

**OpenAI GPT-4**
- Modelo principal para conversação
- Configuração: temperature=0.7, max_tokens=2000
- Context window: 8k tokens
- Custo médio: $0.03 por 1k tokens (input) + $0.06 por 1k tokens (output)

**LangChain**
- Chain management para contexto
- Memory para manter histórico de conversa
- Embeddings para busca semântica

**Vector Database (Pinecone)**
- Armazenamento de embeddings
- Busca semântica em conversas antigas
- Índice: 1536 dimensões (OpenAI ada-002)

---

### DevOps e Infraestrutura

**Controle de Versão:**
- **Git** com GitHub
- Branch strategy: GitHub Flow
- Commit convention: Conventional Commits

**CI/CD:**
- **GitHub Actions**
  - Workflow de testes automáticos em cada PR
  - Deploy automático para staging (branch develop)
  - Deploy manual para produção (branch main)
  - Build e push de Docker images
  - Análise de código com SonarCloud

**Containerização:**
- **Docker** (24.0): Containerização de aplicações
- **Docker Compose**: Orquestração local de containers
- Imagens otimizadas (multi-stage builds)
- Health checks configurados

**Cloud Provider:**
- **AWS (Amazon Web Services)**
  - EC2: Servidores de aplicação
  - RDS: PostgreSQL gerenciado
  - ElastiCache: Redis gerenciado
  - S3: Armazenamento de arquivos (fotos de perfil)
  - CloudFront: CDN para assets estáticos
  - Route 53: DNS
  - Certificate Manager: Certificados SSL/TLS

**Monitoramento:**
- **Sentry**: Error tracking e performance monitoring
- **CloudWatch**: Logs e métricas da AWS
- **Grafana**: Dashboards de métricas
- **Prometheus**: Coleta de métricas

**Segurança:**
- **HTTPS/TLS** obrigatório em todas as conexões
- **Secrets Manager** da AWS para credenciais
- **OWASP ZAP**: Testes de segurança automatizados
- Rate limiting em todos os endpoints
- CORS configurado adequadamente

---

### Ferramentas de Desenvolvimento

**IDEs:**
- Visual Studio Code (recomendado)
- PyCharm Professional (opcional para backend)

**Ferramentas de Colaboração:**
- **GitHub**: Repositório e code review
- **Jira**: Gestão de backlog e sprints
- **Figma**: Design e prototipagem
- **Slack**: Comunicação do time
- **Notion**: Documentação e wikis
- **Postman**: Testes de API

**Qualidade de Código:**
- **SonarQube**: Análise de código estático
- **CodeCov**: Cobertura de testes
- **Dependabot**: Atualização de dependências
- **Pre-commit hooks**: Validações antes de commit

---

## Arquitetura da Aplicação

### Visão Geral
```
┌─────────────┐
│   Cliente   │ (React SPA)
└──────┬──────┘
       │ HTTPS
       ↓
┌─────────────────┐
│  Load Balancer  │ (AWS ALB)
└────────┬────────┘
         │
    ┌────┴────┐
    ↓         ↓
┌────────┐ ┌────────┐
│ API 1  │ │ API 2  │ (FastAPI)
└───┬────┘ └───┬────┘
    │          │
    └────┬─────┘
         ↓
    ┌─────────┐
    │ Redis   │ (Cache/Queue)
    └─────────┘
         │
         ↓
    ┌─────────────┐
    │ PostgreSQL  │ (Database)
    └─────────────┘
         │
         ↓
    ┌─────────────┐
    │   Celery    │ (Workers)
    └─────────────┘
         │
         ↓
    ┌─────────────┐
    │ OpenAI API  │ (IA)
    └─────────────┘
```

### Padrões de Projeto

**Backend:**
- **Repository Pattern**: Abstração da camada de dados
- **Dependency Injection**: FastAPI dependencies
- **Service Layer**: Lógica de negócio isolada
- **DTO Pattern**: Pydantic models para transferência de dados

**Frontend:**
- **Component Composition**: Componentes reutilizáveis
- **Custom Hooks**: Lógica compartilhada
- **Container/Presentational**: Separação de lógica e UI
- **Error Boundaries**: Tratamento de erros em componentes

---

## Estrutura de Diretórios

### Frontend
```
frontend/
├── public/
│   └── assets/
├── src/
│   ├── components/       # Componentes reutilizáveis
│   │   ├── ui/          # Componentes de UI básicos
│   │   ├── forms/       # Componentes de formulário
│   │   └── layout/      # Layouts da aplicação
│   ├── pages/           # Páginas da aplicação
│   │   ├── auth/        # Páginas de autenticação
│   │   ├── chat/        # Páginas de chat
│   │   └── dashboard/   # Dashboard
│   ├── hooks/           # Custom React hooks
│   ├── services/        # Serviços de API
│   ├── store/           # Estado global (Zustand)
│   ├── utils/           # Funções utilitárias
│   ├── types/           # TypeScript types
│   ├── constants/       # Constantes da aplicação
│   └── App.tsx          # Componente raiz
├── tests/
│   ├── unit/
│   └── e2e/
└── package.json
```

### Backend
```
backend/
├── alembic/             # Migrations de banco
│   └── versions/
├── app/
│   ├── api/             # Endpoints da API
│   │   ├── v1/
│   │   │   ├── auth.py
│   │   │   ├── chat.py
│   │   │   ├── users.py
│   │   │   └── automation.py
│   │   └── deps.py      # Dependencies
│   ├── core/            # Configurações core
│   │   ├── config.py
│   │   └── security.py
│   ├── db/              # Database
│   │   ├── base.py
│   │   └── session.py
│   ├── models/          # SQLAlchemy models
│   ├── schemas/         # Pydantic schemas
│   ├── services/        # Lógica de negócio
│   ├── repositories/    # Acesso a dados
│   ├── workers/         # Celery tasks
│   └── main.py          # Entry point
├── tests/
│   ├── unit/
│   ├── integration/
│   └── conftest.py
└── requirements.txt
```

---

## Variáveis de Ambiente

### Backend (.env)
```bash
# Database
DATABASE_URL=postgresql://user:pass@localhost:5432/intelliassist
REDIS_URL=redis://localhost:6379/0

# Security
SECRET_KEY=your-secret-key-here
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=1440

# OpenAI
OPENAI_API_KEY=sk-...
OPENAI_MODEL=gpt-4

# Email
SENDGRID_API_KEY=SG...
FROM_EMAIL=noreply@intelliassist.com

# AWS
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_KEY=...
AWS_REGION=us-east-1
S3_BUCKET_NAME=intelliassist-uploads

# Monitoring
SENTRY_DSN=https://...
```

### Frontend (.env)
```bash
VITE_API_URL=http://localhost:8000/api/v1
VITE_WS_URL=ws://localhost:8000/ws
VITE_SENTRY_DSN=https://...
```

---

## Performance e Otimizações

**Frontend:**
- Code splitting por rotas
- Lazy loading de componentes pesados
- Memoização com React.memo e useMemo
- Debouncing em buscas e inputs
- Service Worker para PWA

**Backend:**
- Connection pooling (10-20 conexões)
- Query optimization com índices
- Cache de queries frequentes (Redis)
- Async/await para operações I/O
- Pagination em listagens

**API OpenAI:**
- Streaming de respostas para melhor UX
- Cache de prompts similares
- Rate limiting por usuário
- Fallback para respostas pré-definidas

---

## Requisitos do Sistema

### Para Desenvolvimento

**Software necessário:**
- Node.js 18+ e npm/yarn
- Python 3.11+
- PostgreSQL 15+
- Redis 7+
- Docker e Docker Compose (opcional)
- Git

**Hardware mínimo:**
- 8GB RAM
- 20GB espaço em disco
- Processador dual-core

### Para Produção

**Servidor:**
- 4GB RAM mínimo (recomendado 8GB)
- 2 vCPUs (recomendado 4)
- 50GB SSD
- Largura de banda: 100 Mbps

---

## Links Úteis

- [Documentação FastAPI](https://fastapi.tiangolo.com/)
- [Documentação React](https://react.dev/)
- [Documentação OpenAI](https://platform.openai.com/docs)
- [Documentação PostgreSQL](https://www.postgresql.org/docs/)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [GitHub Flow](https://guides.github.com/introduction/flow/)