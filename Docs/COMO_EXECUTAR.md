# Como Executar o Projeto - IntelliAssist

## Índice
1. [Pré-requisitos](#pré-requisitos)
2. [Instalação Rápida com Docker](#instalação-rápida-com-docker)
3. [Instalação Manual](#instalação-manual)
4. [Configuração](#configuração)
5. [Executando o Projeto](#executando-o-projeto)
6. [Testes](#testes)
7. [Troubleshooting](#troubleshooting)

---

## Pré-requisitos

### Software Necessário

- **Node.js** 18.x ou superior ([Download](https://nodejs.org/))
- **Python** 3.11 ou superior ([Download](https://www.python.org/))
- **PostgreSQL** 15 ou superior ([Download](https://www.postgresql.org/download/))
- **Redis** 7.0 ou superior ([Download](https://redis.io/download/))
- **Git** ([Download](https://git-scm.com/downloads))

**Opcional (recomendado):**
- **Docker** e **Docker Compose** ([Download](https://www.docker.com/))

### Verificando Instalações

```bash
# Verificar Node.js
node --version  # Deve ser v18.x.x ou superior

# Verificar Python
python --version  # Deve ser 3.11.x ou superior

# Verificar PostgreSQL
psql --version  # Deve ser 15.x ou superior

# Verificar Redis
redis-cli --version  # Deve ser 7.x.x ou superior

# Verificar Git
git --version
```

---

## Instalação Rápida com Docker

### Passo 1: Clone o Repositório

```bash
git clone https://github.com/seu-usuario/intelliassist.git
cd intelliassist
```

### Passo 2: Configure as Variáveis de Ambiente

```bash
# Copie os arquivos de exemplo
cp backend/.env.example backend/.env
cp frontend/.env.example frontend/.env

# Edite os arquivos .env com suas configurações
# Veja a seção "Configuração" para detalhes
```

### Passo 3: Execute com Docker Compose

```bash
# Inicia todos os serviços (frontend, backend, PostgreSQL, Redis)
docker-compose up -d

# Aguarde alguns segundos para os serviços iniciarem
# Verifique os logs se necessário
docker-compose logs -f
```

### Passo 4: Execute as Migrations

```bash
# Aplica as migrations do banco de dados
docker-compose exec backend alembic upgrade head
```

### Passo 5: Acesse a Aplicação

- **Frontend:** http://localhost:3000
- **Backend API:** http://localhost:8000
- **Documentação da API:** http://localhost:8000/docs

**Credenciais de teste:**
- Email: `demo@intelliassist.com`
- Senha: `Demo123!`

---

## Instalação Manual

### Passo 1: Clone o Repositório

```bash
git clone https://github.com/seu-usuario/intelliassist.git
cd intelliassist
```

### Passo 2: Configure o Backend

```bash
cd backend

# Crie e ative um ambiente virtual
python -m venv venv

# No Windows
venv\Scripts\activate

# No Linux/Mac
source venv/bin/activate

# Instale as dependências
pip install -r requirements.txt

# Copie o arquivo de configuração
cp .env.example .env
```

### Passo 3: Configure o Banco de Dados

```bash
# Entre no PostgreSQL
psql -U postgres

# Crie o banco de dados
CREATE DATABASE intelliassist;
CREATE USER intelliassist_user WITH PASSWORD 'sua_senha_aqui';
GRANT ALL PRIVILEGES ON DATABASE intelliassist TO intelliassist_user;
\q

# Execute as migrations
alembic upgrade head

# (Opcional) Carregue dados de exemplo
python scripts/seed_data.py
```

### Passo 4: Inicie o Redis

```bash
# Em um novo terminal, inicie o Redis
redis-server

# Ou se instalado como serviço
sudo systemctl start redis
```

### Passo 5: Configure o Frontend

```bash
# Em um novo terminal, vá para a pasta frontend
cd frontend

# Instale as dependências
npm install

# Copie o arquivo de configuração
cp .env.example .env
```

### Passo 6: Execute a Aplicação

```bash
# Terminal 1 - Backend
cd backend
source venv/bin/activate  # ou venv\Scripts\activate no Windows
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000

# Terminal 2 - Celery Worker (tarefas assíncronas)
cd backend
source venv/bin/activate
celery -A app.workers.celery_app worker --loglevel=info

# Terminal 3 - Frontend
cd frontend
npm run dev
```

### Passo 7: Acesse a Aplicação

- **Frontend:** http://localhost:3000
- **Backend API:** http://localhost:8000
- **Documentação da API:** http://localhost:8000/docs

---

## Configuração

### Backend (.env)

```bash
# ======================
# Database Configuration
# ======================
DATABASE_URL=postgresql://intelliassist_user:sua_senha_aqui@localhost:5432/intelliassist
REDIS_URL=redis://localhost:6379/0

# ======================
# Security
# ======================
SECRET_KEY=sua-chave-secreta-super-segura-aqui-min-32-chars
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=1440

# ======================
# OpenAI Configuration
# ======================
OPENAI_API_KEY=sk-sua-chave-openai-aqui
OPENAI_MODEL=gpt-4
OPENAI_MAX_TOKENS=2000
OPENAI_TEMPERATURE=0.7

# ======================
# Email Configuration (SendGrid)
# ======================
SENDGRID_API_KEY=SG.sua-chave-sendgrid-aqui
FROM_EMAIL=noreply@intelliassist.com
FROM_NAME=IntelliAssist

# ======================
# AWS Configuration (Opcional)
# ======================
AWS_ACCESS_KEY_ID=sua-access-key
AWS_SECRET_ACCESS_KEY=sua-secret-key
AWS_REGION=us-east-1
S3_BUCKET_NAME=intelliassist-uploads

# ======================
# Monitoring (Opcional)
# ======================
SENTRY_DSN=https://sua-dsn-sentry-aqui
ENVIRONMENT=development

# ======================
# Application Settings
# ======================
DEBUG=True
CORS_ORIGINS=http://localhost:3000,http://localhost:5173
MAX_UPLOAD_SIZE=5242880  # 5MB em bytes
RATE_LIMIT=100  # Requisições por minuto
```

### Frontend (.env)

```bash
# API Configuration
VITE_API_URL=http://localhost:8000/api/v1
VITE_WS_URL=ws://localhost:8000/ws

# Monitoring (Opcional)
VITE_SENTRY_DSN=https://sua-dsn-sentry-aqui
VITE_ENVIRONMENT=development

# Feature Flags
VITE_ENABLE_ANALYTICS=false
VITE_ENABLE_CHAT_EXPORT=true
```

### Como Obter as Chaves de API

**OpenAI API Key:**
1. Acesse [platform.openai.com](https://platform.openai.com)
2. Faça login ou crie uma conta
3. Vá em "API Keys" no menu
4. Clique em "Create new secret key"
5. Copie a chave (ela só será exibida uma vez!)

**SendGrid API Key:**
1. Acesse [sendgrid.com](https://sendgrid.com)
2. Crie uma conta gratuita (100 emails/dia)
3. Vá em Settings > API Keys
4. Crie uma nova API Key com permissões de "Mail Send"

---

## Executando o Projeto

### Modo Desenvolvimento

```bash
# Método 1: Docker Compose (recomendado)
docker-compose up

# Método 2: Manual (3 terminais)
# Terminal 1 - Backend
cd backend && uvicorn app.main:app --reload

# Terminal 2 - Celery
cd backend && celery -A app.workers.celery_app worker -l info

# Terminal 3 - Frontend
cd frontend && npm run dev
```

### Modo Produção

```bash
# Build do frontend
cd frontend
npm run build

# O backend serve os arquivos estáticos do frontend
cd backend
gunicorn app.main:app -w 4 -k uvicorn.workers.UvicornWorker -b 0.0.0.0:8000
```

### Comandos Úteis

```bash
# Criar nova migration
cd backend
alembic revision --autogenerate -m "descrição da mudança"

# Aplicar migrations
alembic upgrade head

# Reverter última migration
alembic downgrade -1

# Limpar banco de dados
alembic downgrade base
alembic upgrade head

# Formatar código Python
black app/
ruff check app/ --fix

# Formatar código TypeScript
cd frontend
npm run lint
npm run format

# Ver logs do Docker
docker-compose logs -f [service_name]

# Reiniciar um serviço específico
docker-compose restart backend
```

---

## Testes

### Backend

```bash
cd backend

# Executar todos os testes
pytest

# Testes com cobertura
pytest --cov=app --cov-report=html

# Testes específicos
pytest tests/unit/test_auth.py

# Testes com output verbose
pytest -v

# Ver relatório de cobertura
open htmlcov/index.html  # Mac/Linux
start htmlcov/index.html  # Windows
```

### Frontend

```bash
cd frontend

# Testes unitários
npm run test

# Testes com cobertura
npm run test:coverage

# Testes E2E
npm run test:e2e

# Testes E2E no modo interativo
npm run test:e2e:ui
```

### Testes de Integração

```bash
# Com Docker Compose
docker-compose -f docker-compose.test.yml up --abort-on-container-exit

# Manual
cd backend
pytest tests/integration/
```

---

## Troubleshooting

### Problemas Comuns

#### 1. Erro de Conexão com o Banco de Dados

```
sqlalchemy.exc.OperationalError: could not connect to server
```

**Solução:**
```bash
# Verifique se o PostgreSQL está rodando
sudo systemctl status postgresql  # Linux
brew services list  # Mac

# Verifique as credenciais no .env
# Teste a conexão manualmente
psql -h localhost -U intelliassist_user -d intelliassist
```

#### 2. Erro com Redis

```
redis.exceptions.ConnectionError: Error connecting to Redis
```

**Solução:**
```bash
# Inicie o Redis
redis-server

# Ou como serviço
sudo systemctl start redis

# Verifique se está rodando
redis-cli ping  # Deve retornar "PONG"
```

#### 3. Erro de Importação no Python

```
ModuleNotFoundError: No module named 'fastapi'
```

**Solução:**
```bash
# Certifique-se de estar no ambiente virtual
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate  # Windows

# Reinstale as dependências
pip install -r requirements.txt
```

#### 4. Erro de Porta em Uso

```
Error: listen EADDRINUSE: address already in use :::3000
```

**Solução:**
```bash
# Linux/Mac - Encontre e mate o processo
lsof -ti:3000 | xargs kill -9

# Windows - Encontre e mate o processo
netstat -ano | findstr :3000
taskkill /PID <PID> /F

# Ou use outra porta
npm run dev -- --port 3001
```

#### 5. Erro com Migrations

```
alembic.util.exc.CommandError: Can't locate revision identified by 'xyz'
```

**Solução:**
```bash
# Resete o banco (CUIDADO: apaga todos os dados!)
alembic downgrade base
alembic upgrade head

# Ou force a versão atual
alembic stamp head
```

#### 6. Erro OpenAI API

```
openai.error.AuthenticationError: Incorrect API key provided
```

**Solução:**
- Verifique se a chave está correta no `.env`
- Confirme que tem créditos na conta OpenAI
- Teste a chave: https://platform.openai.com/api-keys

---

### Logs e Debug

```bash
# Backend - Aumentar nível de log
# No .env
LOG_LEVEL=DEBUG

# Frontend - Ver requisições
# No browser DevTools > Network

# Docker - Ver logs de um serviço
docker-compose logs -f backend

# PostgreSQL - Ver queries lentas
# No postgresql.conf
log_min_duration_statement = 1000  # Log queries > 1s
```

---

### Limpeza e Reset

```bash
# Parar todos os containers
docker-compose down

# Remover volumes (APAGA DADOS!)
docker-compose down -v

# Limpar cache do npm
cd frontend
rm -rf node_modules package-lock.json
npm install

# Limpar cache do pip
cd backend
pip cache purge
pip install -r requirements.txt --force-reinstall
```

---

## Próximos Passos

Após configurar o ambiente:

1. ✅ Leia a [Documentação](./DOCUMENTATION.md)
2. ✅ Confira a [Estrutura do Projeto](./PROJECT_STRUCTURE.md)
3. ✅ Veja o [Manual do Usuário](./MANUAL_USUARIO.md)
4. ✅ Consulte as [Tecnologias](./TECHNOLOGIES.md)

---

## Suporte

Encontrou algum problema? 

- 📧 Email: suporte@intelliassist.com
- 💬 Slack: #intelliassist-dev
- 🐛 Issues: [GitHub Issues](https://github.com/seu-usuario/intelliassist/issues)