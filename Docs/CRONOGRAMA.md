# Cronograma do Projeto - IntelliAssist

## Visão Geral
**Período Total:** 4 meses (Março a Junho de 2025)  
**Metodologia:** Scrum com Sprints de 2 semanas  
**Total de Sprints:** 8

---

## Linha do Tempo

```
Março 2025          Abril 2025          Maio 2025           Junho 2025
├─Sprint 1──┤      ├─Sprint 3──┤      ├─Sprint 5──┤      ├─Sprint 7──┤
├─Sprint 2──┤      ├─Sprint 4──┤      ├─Sprint 6──┤      ├─Sprint 8──┤
```

---

## Cronograma Detalhado

### Sprint 1 (04/03 - 17/03/2025)
**Objetivo:** Setup inicial e fundamentos de autenticação

**Entregas Principais:**
- Configuração do ambiente de desenvolvimento
- Estrutura inicial do projeto (frontend + backend)
- Sistema básico de cadastro e login
- Configuração do banco de dados
- CI/CD pipeline inicial

**Marcos:**
-  Repositório configurado
-  Ambientes de dev/staging criados

---

### Sprint 2 (18/03 - 31/03/2025)
**Objetivo:** Completar sistema de autenticação

**Entregas Principais:**
- Recuperação de senha
- Validação de email
- Gerenciamento de sessões
- Testes unitários de autenticação
- Documentação de API

**Marcos:**
-  MVP de autenticação funcional

---

### Sprint 3 (01/04 - 14/04/2025)
**Objetivo:** Interface de chat básica

**Entregas Principais:**
- UI/UX do chat
- Integração com API de IA
- Sistema de mensagens em tempo real
- Armazenamento de conversas
- Tratamento de erros

**Marcos:**
-  Primeira versão do chat operacional

---

### Sprint 4 (15/04 - 28/04/2025)
**Objetivo:** Melhorias no chat e contexto

**Entregas Principais:**
- Sistema de manutenção de contexto
- Histórico de conversas
- Busca em conversas antigas
- Otimização de performance
- Testes de integração

**Marcos:**
-  Chat com contexto inteligente
-  **Review Sprint 1** (Apresentação para stakeholders)

---

### Sprint 5 (29/04 - 12/05/2025)
**Objetivo:** Automação de tarefas - Fase 1

**Entregas Principais:**
- Criação de lembretes via chat
- Sistema de notificações
- Gerenciamento de tarefas
- Integração com calendário
- API de webhooks

**Marcos:**
-  Funcionalidades de produtividade ativas

---

### Sprint 6 (13/05 - 26/05/2025)
**Objetivo:** Automação de tarefas - Fase 2

**Entregas Principais:**
- Agendamento de automações
- Templates de tarefas recorrentes
- Sistema de workflows
- Configurações de usuário avançadas
- Testes end-to-end

**Marcos:**
-  Sistema de automação completo
-  **Review Sprint 2** (Apresentação para stakeholders)

---

### Sprint 7 (27/05 - 09/06/2025)
**Objetivo:** Dashboard e Analytics

**Entregas Principais:**
- Painel de controle do usuário
- Gráficos de uso e estatísticas
- Relatórios de produtividade
- Exportação de dados
- Página de administração

**Marcos:**
-  Dashboard funcional com métricas

---

### Sprint 8 (10/06 - 23/06/2025)
**Objetivo:** Refinamento e preparação para lançamento

**Entregas Principais:**
- Correção de bugs críticos
- Otimização de performance
- Melhorias de UX baseadas em feedback
- Documentação final completa
- Testes de carga e segurança
- Preparação para deploy em produção

**Marcos:**
-  Produto pronto para lançamento
-  **Apresentação Final** (24/06/2025)

---

## Milestones Principais

| Data | Milestone | Status |
|------|-----------|--------|
| 17/03/2025 | Sistema de autenticação completo | Concluído |
| 14/04/2025 | Chat inteligente funcional | Concluído |
| 28/04/2025 | Review Sprint 1 com stakeholders | Em andamento |
| 26/05/2025 | Sistema de automação completo | Planejado |
| 09/06/2025 | Dashboard e analytics prontos | Planejado |
| 23/06/2025 | Produto final entregue | Planejado |

---

## Recursos e Alocação

### Time Core
- **Product Owner:** 1 pessoa (20h/semana)
- **Scrum Master:** 1 pessoa (10h/semana)
- **Desenvolvedores:** 4 pessoas (40h/semana cada)
- **Designer UX/UI:** 1 pessoa (20h/semana)
- **QA Engineer:** 1 pessoa (30h/semana)

### Infraestrutura
- Ambiente de desenvolvimento: AWS Free Tier
- Ambiente de staging: Digital Ocean
- Produção: AWS (a definir custos)
- Ferramentas: GitHub, Jira, Figma, Slack

---

## Riscos e Mitigações

| Risco | Probabilidade | Impacto | Mitigação |
|-------|---------------|---------|-----------|
| Atraso na integração de IA | Média | Alto | Buffer de 1 sprint, API alternativa preparada |
| Mudanças de requisitos | Alta | Médio | Backlog refinado semanalmente |
| Problemas de performance | Baixa | Alto | Testes de carga desde Sprint 3 |
| Indisponibilidade de membros | Média | Médio | Documentação contínua, pair programming |

---

## Cerimônias Scrum

**Daily Standup:** Segunda a Sexta, 9h30 (15 min)  
**Sprint Planning:** Primeira Segunda-feira da Sprint (2h)  
**Sprint Review:** Última Sexta-feira da Sprint (1h)  
**Sprint Retrospective:** Última Sexta-feira da Sprint (1h)  
**Backlog Refinement:** Quarta-feira (1h)