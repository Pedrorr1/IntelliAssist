# Documentação - IntelliAssist

## Hub Central de Documentação

Este é o ponto de partida para toda a documentação do projeto IntelliAssist.

---

## 📚 Documentação do Projeto

### Planejamento e Gestão

- **[Product Backlog](./BACKLOG_PRODUTO.md)**
  - Épicos e user stories
  - Priorização de features
  - Critérios de aceitação

- **[Cronograma](./CRONOGRAMA.md)**
  - Timeline do projeto
  - Milestones principais
  - Alocação de recursos

- **[Sprints](./SPRINTS.md)**
  - Detalhamento de cada sprint
  - Entregas e métricas
  - Retrospectivas

- **[Definition of Ready/Done](./CHECKLISTS_DOR_DOD.md)**
  - Checklist de DoR (Definition of Ready)
  - Checklist de DoD (Definition of Done)
  - Critérios de qualidade

---

## 🛠️ Documentação Técnica

### Desenvolvimento

- **[Tecnologias Utilizadas](./TECNOLOGIAS.md)**
  - Stack completo (frontend/backend)
  - Bibliotecas e frameworks
  - Ferramentas de desenvolvimento

- **[Estrutura do Projeto](./ESTRUTURA_PROJETO.md)**
  - Organização de diretórios
  - Padrões de código
  - Arquitetura da aplicação

- **[Como Executar](./COMO_EXECUTAR.md)**
  - Instalação e configuração
  - Comandos úteis
  - Troubleshooting

---

## 👥 Equipe e Processos

- **[Equipe](./EQUIPE.md)**
  - Membros do time
  - Papéis e responsabilidades
  - Matriz de habilidades

- **[DoR e DoD por Sprint](./SPRINTS_DOR_DOD.md)**
  - Definition of Ready específica
  - Definition of Done específica
  - Critérios por tipo de tarefa

---

## 📖 Documentação do Usuário

- **[Manual do Usuário](./MANUAL_USUARIO.md)**
  - Como usar o IntelliAssist
  - Funcionalidades principais
  - Perguntas frequentes (FAQ)

---

## 📋 Guias e Padrões

### Padrões de Desenvolvimento

**Commits:**
```
<tipo>(#issue): descrição curta

Tipos: feat, fix, docs, style, refactor, test, chore
Exemplo: feat(#123): implementação do chat com IA
```

**Branches:**
```
feature/AB-123-descricao
fix/AB-456-descricao
```

**Pull Requests:**
- Título descritivo
- Descrição do que foi feito
- Como testar
- Screenshots (se aplicável)
- Link para issue relacionada

---

## 🔗 Links Úteis

### Repositório
- [GitHub Repository](https://github.com/seu-usuario/intelliassist)
- [Issues](https://github.com/seu-usuario/intelliassist/issues)
- [Pull Requests](https://github.com/seu-usuario/intelliassist/pulls)

### Ferramentas
- [Jira Board](https://seu-projeto.atlassian.net)
- [Figma Designs](https://figma.com/file/...)
- [API Documentation](http://localhost:8000/docs)

### Ambientes
- **Desenvolvimento:** http://localhost:3000
- **Staging:** https://staging.intelliassist.com
- **Produção:** https://intelliassist.com

---

## 📊 Métricas e Qualidade

### Cobertura de Testes
- Backend: 80%+
- Frontend: 75%+

### Performance
- Tempo de resposta API: < 200ms (média)
- First Contentful Paint: < 1.5s
- Time to Interactive: < 3s

### Qualidade de Código
- SonarQube Quality Gate: Passed
- Bugs críticos: 0
- Code smells: < 10

---

## 🆘 Suporte e Contato

**Encontrou um bug?**
- Abra uma [issue no GitHub](https://github.com/seu-usuario/intelliassist/issues)
- Use o template de bug report

**Tem uma sugestão?**
- Abra uma [issue](https://github.com/seu-usuario/intelliassist/issues) com o template de feature request
- Participe das discussões

**Contato Direto:**
- 📧 Email: contato@intelliassist.com
- 💬 Slack: #intelliassist-dev
- 📱 WhatsApp: (12) 98765-4321

---

## 📝 Convenções de Documentação

### Formato
- Todos os documentos em **Markdown (.md)**
- Idioma: **Português (BR)**
- Encoding: **UTF-8**

### Estrutura
```markdown
# Título Principal

## Seção

### Subseção

**Negrito** para destaque
*Itálico* para ênfase
`código inline`
```

### Atualizações
- Sempre atualizar data no rodapé
- Manter histórico de mudanças quando relevante
- Revisar docs a cada sprint

---

## 🔄 Ciclo de Vida da Documentação

1. **Criação:** Durante o desenvolvimento da feature
2. **Revisão:** No code review do PR
3. **Publicação:** Ao mergear na branch main
4. **Manutenção:** Atualização contínua
5. **Arquivamento:** Quando feature é deprecada

---

## 📚 Glossário

**API:** Application Programming Interface  
**CI/CD:** Continuous Integration / Continuous Deployment  
**DoD:** Definition of Done  
**DoR:** Definition of Ready  
**JWT:** JSON Web Token  
**ORM:** Object-Relational Mapping  
**PR:** Pull Request  
**REST:** Representational State Transfer  
**SPA:** Single Page Application  
**UX/UI:** User Experience / User Interface  

---

## 📅 Última Atualização

**Data:** 27 de outubro de 2025  
**Versão da Documentação:** 1.0  
**Mantido por:** Equipe IntelliAssist