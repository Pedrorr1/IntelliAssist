# Checklists - Definition of Ready (DoR) e Definition of Done (DoD)

## Índice
- [Definition of Ready (DoR)](#definition-of-ready-dor)
- [Definition of Done (DoD)](#definition-of-done-dod)
- [Checklist de Code Review](#checklist-de-code-review)
- [Checklist de Release](#checklist-de-release)

---

## Definition of Ready (DoR)

O DoR define os critérios que uma User Story deve atender **antes** de entrar em uma Sprint.

### Checklist - User Story está pronta quando:

#### 📋 Clareza e Detalhamento
- [ ] História escrita no formato: "Como [persona], quero [ação], para [objetivo]"
- [ ] Descrição clara e compreensível por todos os membros do time
- [ ] Contexto de negócio explicado
- [ ] Valor para o usuário está claro

#### ✅ Critérios de Aceitação
- [ ] Critérios de aceitação estão definidos e testáveis
- [ ] Cenários de sucesso documentados
- [ ] Cenários de erro/exceção documentados
- [ ] Validações de dados especificadas
- [ ] Comportamentos esperados descritos

#### 🎨 Design e UX
- [ ] Protótipos ou mockups disponíveis (quando aplicável)
- [ ] Fluxo de usuário definido
- [ ] Especificações de UI/UX documentadas
- [ ] Aprovação do designer (quando necessário)

#### 🔧 Requisitos Técnicos
- [ ] Dependências técnicas identificadas
- [ ] Integrações necessárias mapeadas
- [ ] Impacto em outros sistemas avaliado
- [ ] Requisitos de performance definidos (quando aplicável)
- [ ] Requisitos de segurança identificados

#### 📊 Estimativa
- [ ] Story Points estimados pelo time
- [ ] Complexidade técnica avaliada
- [ ] História é pequena o suficiente (máx 13 pontos)
- [ ] Se >13 pontos, história foi quebrada em menores

#### 🧪 Testabilidade
- [ ] Casos de teste podem ser escritos
- [ ] Ambiente de teste disponível
- [ ] Dados de teste identificados
- [ ] Critérios de aceitação são verificáveis

#### 🔗 Dependências
- [ ] Dependências de outras histórias mapeadas
- [ ] Bloqueadores identificados e resolvidos
- [ ] APIs/serviços externos documentados
- [ ] Permissões e acessos necessários garantidos

#### 👥 Aprovações
- [ ] Product Owner revisou e aprovou
- [ ] Time de desenvolvimento fez perguntas e esclareceu dúvidas
- [ ] Sem dúvidas pendentes significativas

---

## Definition of Done (DoD)

O DoD define os critérios que uma User Story deve atender para ser considerada **completa**.

### Checklist - User Story está concluída quando:

#### 💻 Desenvolvimento
- [ ] Código implementado conforme critérios de aceitação
- [ ] Código segue padrões de codificação do time
- [ ] Código está comentado adequadamente
- [ ] Não há código comentado/morto no commit
- [ ] Variáveis e funções com nomes significativos
- [ ] Complexidade ciclomática aceitável (< 10)

#### 🧪 Testes
- [ ] Testes unitários escritos e passando
- [ ] Cobertura de código ≥ 80% nas novas funcionalidades
- [ ] Testes de integração implementados (quando aplicável)
- [ ] Testes E2E para fluxos críticos (quando aplicável)
- [ ] Todos os testes da CI/CD passando
- [ ] Testes manuais realizados
- [ ] Cenários de erro testados

#### 🔍 Code Review
- [ ] Pull Request criado com descrição clara
- [ ] Código revisado por pelo menos 1 desenvolvedor
- [ ] Comentários do code review resolvidos
- [ ] Aprovação do revisor obtida
- [ ] Conflicts resolvidos
- [ ] Build da CI/CD passou

#### 📝 Documentação
- [ ] README atualizado (se necessário)
- [ ] Documentação da API atualizada (Swagger/OpenAPI)
- [ ] Comentários em código complexo
- [ ] CHANGELOG atualizado
- [ ] Documentação técnica criada (se aplicável)

#### 🎨 UI/UX (quando aplicável)
- [ ] Interface implementada conforme design
- [ ] Responsividade testada (mobile, tablet, desktop)
- [ ] Acessibilidade verificada (contraste, navegação por teclado)
- [ ] Feedback visual para ações do usuário
- [ ] Estados de loading/erro implementados
- [ ] Validações de formulário funcionando

#### 🔒 Segurança
- [ ] Inputs sanitizados e validados
- [ ] Autenticação/autorização implementada
- [ ] Dados sensíveis não expostos em logs
- [ ] Vulnerabilidades conhecidas verificadas
- [ ] CORS configurado adequadamente
- [ ] Rate limiting implementado (quando necessário)

#### 🚀 Deploy
- [ ] Código mergeado na branch develop
- [ ] Deploy realizado no ambiente de staging
- [ ] Smoke tests realizados em staging
- [ ] Migrations de banco aplicadas (se houver)
- [ ] Variáveis de ambiente configuradas

#### ✅ Aceitação
- [ ] Todos os critérios de aceitação atendidos
- [ ] Demo realizada para o PO
- [ ] Product Owner aprovou a entrega
- [ ] Funcionalidade testada em staging pelo PO
- [ ] Sem bugs críticos pendentes

#### 📊 Performance (quando aplicável)
- [ ] Requisitos de performance atendidos
- [ ] Queries otimizadas
- [ ] Sem memory leaks identificados
- [ ] Tempo de resposta dentro do aceitável (< 3s)

#### 🐛 Bugs
- [ ] Nenhum bug crítico ou blocker aberto
- [ ] Bugs menores documentados como novas histórias
- [ ] Logs de erro tratados adequadamente

---

## Checklist de Code Review

### Para o Autor do PR

#### Antes de Criar o PR
- [ ] Código testado localmente
- [ ] Todos os testes passando
- [ ] Código formatado (black, prettier)
- [ ] Linter sem erros (ruff, eslint)
- [ ] Commits com mensagens significativas
- [ ] Branch atualizada com develop/main
- [ ] Removidos console.logs, debuggers, comentários desnecessários

#### Ao Criar o PR
- [ ] Título descritivo e claro
- [ ] Descrição explicando o que foi feito
- [ ] Referência à issue/task (ex: "Closes #123")
- [ ] Screenshots/GIFs (para mudanças visuais)
- [ ] Checklist de teste preenchido
- [ ] Reviewers atribuídos
- [ ] Labels apropriadas adicionadas

#### Template de Descrição do PR
```markdown
## Descrição
[Descreva o que foi implementado]

## Tipo de Mudança
- [ ] Bug fix
- [ ] Nova feature
- [ ] Breaking change
- [ ] Refatoração
- [ ] Documentação

## Issues Relacionadas
Closes #[número]

## Como Testar
1. [Passo 1]
2. [Passo 2]
3. [Resultado esperado]

## Screenshots
[Se aplicável]

## Checklist
- [ ] Testes passando
- [ ] Documentação atualizada
- [ ] Code review solicitado
```

---

### Para o Revisor

#### Aspectos Gerais
- [ ] Código resolve o problema proposto?
- [ ] Solução está de acordo com a arquitetura?
- [ ] Código é legível e autoexplicativo?
- [ ] Nomes de variáveis/funções são claros?

#### Funcionalidade
- [ ] Lógica está correta?
- [ ] Casos de erro são tratados?
- [ ] Edge cases foram considerados?
- [ ] Performance é aceitável?

#### Segurança
- [ ] Inputs são validados?
- [ ] Não há exposição de dados sensíveis?
- [ ] Autenticação/autorização adequada?
- [ ] SQL injection prevenido?

#### Testes
- [ ] Cobertura de testes adequada?
- [ ] Testes são significativos?
- [ ] Casos de erro testados?

#### Código
- [ ] Não há duplicação desnecessária?
- [ ] Funções são pequenas e focadas?
- [ ] Comentários explicam o "porquê", não o "o quê"?
- [ ] Sem código morto/comentado?

#### Feedback
- [ ] Comentários construtivos e respeitosos
- [ ] Sugestões de melhoria quando possível
- [ ] Elogios aos pontos positivos

---

## Checklist de Release

### Preparação (1 semana antes)

#### Código
- [ ] Todos os PRs da sprint mergeados
- [ ] Branch de release criada (release/v1.x.x)
- [ ] Version bump realizado (package.json, __version__)
- [ ] CHANGELOG atualizado com todas as mudanças

#### Testes
- [ ] Todos os testes automatizados passando
- [ ] Testes de regressão executados
- [ ] Testes de performance realizados
- [ ] Testes de segurança executados (OWASP ZAP)
- [ ] Testes exploratórios realizados

#### Documentação
- [ ] README atualizado
- [ ] Documentação da API atualizada
- [ ] Guias de usuário atualizados
- [ ] Release notes escritas
- [ ] Migration guide (se necessário)

### Deploy (dia do release)

#### Pré-Deploy
- [ ] Backup do banco de dados realizado
- [ ] Rollback plan documentado
- [ ] Monitoramento configurado
- [ ] Alertas configurados
- [ ] Stakeholders notificados

#### Deploy
- [ ] Migrations aplicadas
- [ ] Deploy em produção realizado
- [ ] Health checks passando
- [ ] Smoke tests executados
- [ ] Monitoramento ativo

#### Pós-Deploy
- [ ] Funcionalidades críticas testadas
- [ ] Métricas monitoradas (15min, 1h, 24h)
- [ ] Logs verificados
- [ ] Performance monitorada
- [ ] Usuários notificados (release notes)
- [ ] Tag criada no Git (v1.x.x)

### Validação (24h após release)

- [ ] Sem erros críticos reportados
- [ ] Performance dentro do esperado
- [ ] Métricas de uso normais
- [ ] Feedback de usuários coletado
- [ ] Incidentes documentados (se houver)

---

## Critérios de Aceitação - Templates

### Template Genérico
```gherkin
Dado [contexto inicial]
Quando [ação do usuário]
Então [resultado esperado]
E [validação adicional]
```

### Exemplo - Login
```gherkin
Dado que estou na página de login
Quando preencho email válido e senha correta
E clico em "Entrar"
Então sou redirecionado para o dashboard
E vejo uma mensagem de boas-vindas
E meu token de autenticação é salvo
```

### Exemplo - Chat
```gherkin
Dado que estou autenticado
E estou na página de chat
Quando envio uma mensagem "Olá"
Então a mensagem aparece na interface
E vejo um indicador de "digitando..."
E recebo uma resposta da IA em até 3 segundos
E a resposta é exibida corretamente
```

---

## Níveis de Severidade de Bugs

| Severidade | Descrição | Ação | Exemplo |
|------------|-----------|------|---------|
| 🔴 **Crítico** | Sistema inoperante | Corrigir imediatamente | Aplicação não inicia |
| 🟠 **Alto** | Funcionalidade principal quebrada | Corrigir na sprint atual | Login não funciona |
| 🟡 **Médio** | Funcionalidade secundária com problema | Corrigir próxima sprint | Busca com resultados incorretos |
| 🟢 **Baixo** | Problema cosmético/menor | Backlog | Alinhamento visual incorreto |

---

*Última atualização: Sprint 3 - 09/04/2025*