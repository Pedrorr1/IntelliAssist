# Estrutura do Projeto - IntelliAssist

## Visão Geral

O IntelliAssist segue uma arquitetura simples de três camadas:
- **Frontend:** React + TypeScript
- **Backend:** Python + FastAPI  
- **Banco de Dados:** PostgreSQL + Redis

---

## Estrutura de Diretórios

```
intelliassist/
│
├── backend/                    # Backend (Python/FastAPI)
│   ├── app/
│   │   ├── api/               # Endpoints da API
│   │   ├── models/            # Models do banco de dados
│   │   ├── schemas/           # Validação de dados (Pydantic)
│   │   ├── services/          # Lógica de negócio
│   │   └── main.py            # Aplicação principal
│   ├── tests/                 # Testes
│   ├── requirements.txt       # Dependências
│   └── .env                   # Variáveis de ambiente
│
├── frontend/                   # Frontend (React/TypeScript)
│   ├── src/
│   │   ├── components/        # Componentes React
│   │   ├── pages/             # Páginas da aplicação
│   │   ├── services/          # Chamadas para API
│   │   ├── hooks/             # Custom hooks
│   │   └── App.tsx            # Componente principal
│   ├── package.json           # Dependências
│   └── .env                   # Variáveis de ambiente
│
├── Docs/                       # Documentação
│   ├── PRODUCT_BACKLOG.md
│   ├── SPRINTS.md
│   ├── TIMELINE.md
│   ├── TEAM.md
│   └── ...
│
├── docker-compose.yml          # Orquestração de containers
├── .gitignore
└── README.md
```

---

## Backend - Organização

### API (`app/api/`)
Endpoints REST organizados por recurso:
- `auth.py` - Login, registro, recuperação de senha
- `users.py` - Gerenciamento de usuários
- `chat.py` - Chat com IA
- `automation.py` - Lembretes e automações

### Models (`app/models/`)
Tabelas do banco de dados:
- `user.py` - Usuários
- `conversation.py` - Conversas
- `message.py` - Mensagens
- `reminder.py` - Lembretes

### Services (`app/services/`)
Lógica de negócio:
- `auth_service.py` - Autenticação e tokens
- `chat_service.py` - Integração com OpenAI
- `email_service.py` - Envio de emails

---

## Frontend - Organização

### Components (`src/components/`)
```
components/
├── ui/              # Botões, inputs, cards
├── forms/           # Formulários (login, cadastro)
├── layout/          # Header, sidebar, footer
└── chat/            # Interface de chat
```

### Pages (`src/pages/`)
```
pages/
├── auth/            # Login, cadastro
├── chat/            # Chat com IA
├── dashboard/       # Dashboard do usuário
└── profile/         # Perfil do usuário
```

### Services (`src/services/`)
Chamadas para o backend:
- `auth.service.ts` - Autenticação
- `chat.service.ts` - Chat
- `user.service.ts` - Usuários

---

## Fluxo de Dados

### Exemplo: Login de Usuário

```
1. Usuário preenche formulário → LoginForm.tsx
2. Valida dados → React Hook Form
3. Envia para API → auth.service.ts
4. Backend processa → auth_service.py
5. Retorna token JWT
6. Frontend salva token → localStorage
7. Redireciona para /chat
```

### Exemplo: Enviar Mensagem no Chat

```
1. Usuário digita mensagem → ChatInterface.tsx
2. Envia para API → chat.service.ts
3. Backend processa → chat_service.py
4. Chama OpenAI API
5. Retorna resposta da IA
6. Frontend exibe mensagem → MessageBubble.tsx
```

---

## Convenções de Código

### Backend (Python)
- **Classes:** `PascalCase` (ex: `UserService`)
- **Funções:** `snake_case` (ex: `create_user`)
- **Arquivos:** `snake_case.py` (ex: `auth_service.py`)

### Frontend (TypeScript)
- **Componentes:** `PascalCase` (ex: `LoginForm.tsx`)
- **Funções:** `camelCase` (ex: `handleSubmit`)
- **Arquivos:** `PascalCase.tsx` (ex: `LoginPage.tsx`)

### Banco de Dados
- **Tabelas:** plural, snake_case (ex: `users`, `messages`)
- **Colunas:** snake_case (ex: `created_at`, `user_id`)

---

## Principais Tecnologias

| Camada | Tecnologia | Propósito |
|--------|-----------|-----------|
| Frontend | React 18 | Interface de usuário |
| Frontend | TypeScript | Tipagem estática |
| Frontend | Tailwind CSS | Estilização |
| Backend | FastAPI | Framework web |
| Backend | SQLAlchemy | ORM |
| Backend | OpenAI API | Inteligência artificial |
| Banco | PostgreSQL | Banco principal |
| Banco | Redis | Cache e filas |
| DevOps | Docker | Containerização |
| DevOps | GitHub Actions | CI/CD |

---

## Comandos Úteis

### Backend
```bash
# Instalar dependências
pip install -r requirements.txt

# Rodar aplicação
uvicorn app.main:app --reload

# Rodar testes
pytest

# Criar migration
alembic revision --autogenerate -m "descrição"
```

### Frontend
```bash
# Instalar dependências
npm install

# Rodar aplicação
npm run dev

# Rodar testes
npm test

# Build para produção
npm run build
```

### Docker
```bash
# Subir todos os serviços
docker-compose up -d

# Ver logs
docker-compose logs -f

# Parar serviços
docker-compose down
```

---

## Arquitetura Simplificada

```
┌─────────────┐
│   Browser   │ (React)
└──────┬──────┘
       │ HTTP/WebSocket
       ↓
┌─────────────┐
│   FastAPI   │ (Backend)
└──────┬──────┘
       │
   ┌───┴───┐
   ↓       ↓
┌──────┐ ┌────────┐
│Redis │ │Postgres│
└──────┘ └────────┘
   │
   ↓
┌──────────┐
│OpenAI API│
└──────────┘
```