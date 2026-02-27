# AGENTS.md

Guia para agentes de IA que trabalham neste projeto.

<!-- Idioma: defina aqui o idioma para respostas do agente e para o código -->

## Stack

<!-- Defina o stack tecnológico do projeto aqui. Exemplo:
- Framework:
- UI:
- Backend/DB:
- Linguagem:
-->

## Setup e comandos

<!-- Comandos essenciais do projeto. Exemplo:
```bash
npm install        # Instalar dependências
npm run dev        # Servidor de desenvolvimento
npm run build      # Build de produção
npm run lint       # Linter
npm run test       # Testes
```
-->

<!-- Variáveis de ambiente necessárias:
- Liste aqui as variáveis necessárias no `.env`
-->

## Estrutura do projeto

<!-- Descreva a estrutura principal de pastas do projeto. Exemplo:
```
src/
docs/
tests/
wisdom/
workplan/
```
-->

## Convenções de código

- Indentação: 2 espaços
- Código em inglês, documentação e comentários em português

<!-- Adicionar mais convenções da equipe. Exemplo:
- Nomenclatura: camelCase para variáveis, PascalCase para componentes
- TypeScript estrito
-->

## Base de conhecimento (wisdom/)

A pasta `wisdom/` contém a documentação técnica do projeto. É a fonte da verdade para entender como o sistema funciona.

Estrutura base:
- `wisdom/architecture/` — Como o sistema é projetado (decisões, padrões, estrutura)
- `wisdom/development/` — Como trabalhar no projeto (convenções, testes, workflows)
- `wisdom/operations/` — Como é feito o deploy e a operação (CI/CD, ambientes, monitoramento)

Pastas adicionais (`database/`, `security/`, `integrations/`) podem ser criadas quando o projeto precisar. Veja `wisdom/README.md` para os critérios.

Os agentes devem consultar `wisdom/` antes de tomar decisões que afetem a arquitetura ou padrões existentes.

## Gestão de planos (workplan/)

A pasta `workplan/` gerencia o ciclo de vida das tarefas do projeto.

**Pastas:**
- `backlog/` — Planos pendentes, priorizados e prontos para trabalhar
- `coding/` — Planos em andamento
- `done/` — Planos concluídos (arquivo histórico)
- `draft/` — Rascunhos, ideias e decisões de arquitetura (sem workflow ou identificador)

**Workflow:** `(draft/) -> backlog/ -> coding/ -> done/`

**Formato de nomes de arquivo:**
- Com issue tracker: `TYPE-YYYY-MM-DD-iNNNN-description.md`
- Sem issue tracker: `TYPE-YYYY-MM-DD-description.md`
- TYPE: `BACKLOG`, `CODING`, `DONE`
- iNNNN: número da issue do GitHub/GitLab (quando o tracker está configurado)

Veja `workplan/README.md` para o template completo e regras detalhadas.

## Autenticação e papéis

<!-- Defina o sistema de autenticação e papéis. Exemplo:
- Provedor de auth:
- Hierarquia de papéis:
- Composable/função para verificação de permissões:
-->

## Workflow Git

- Branch principal: `main` (PRs obrigatórios)
- Branches: `feature/`, `fix/`, `hotfix/`, `refactor/`, `chore/`, `docs/` + descrição em inglês
- Commits: Conventional Commits em inglês (`feat:`, `fix:`, `docs:`, etc.)
- PRs: título em inglês (Conventional Commits), descrição/body em português
- Issues: título e descrição em português
- **Não incluir** `Co-Authored-By` de agentes de IA nos commits
- **Não incluir** o link "Generated with Claude Code" em mensagens de commit ou PRs

<!-- Adicionar mais regras de workflow Git se necessário -->

## Testes

<!-- Defina a estratégia de testes. Exemplo:
- Framework de testes:
- O que deve ter testes:
- Padrão de arquivos: `*.test.ts` ou `*.spec.ts`
-->

## Zonas protegidas (NÃO modificar)

<!-- Liste arquivos ou pastas que os agentes NÃO devem modificar. Exemplo:
| Arquivo | Motivo |
|---------|--------|
| `.env` | Nunca fazer commit |
| `migrations/` (aplicadas) | Criar uma nova em vez de alterar |
-->

## Problemas conhecidos

<!-- Documente problemas conhecidos ou armadilhas comuns. Exemplo:
- Bug X: descrição e solução alternativa
- Limitação Y: contexto e solução temporária
-->

## Especificações detalhadas

<!-- Liste links para documentos de referência em wisdom/. Exemplo:
| Documento | Conteúdo |
|-----------|----------|
| [wisdom/architecture/...](wisdom/architecture/...) | Arquitetura do sistema |
| [wisdom/database/...](wisdom/database/...) | Schema do DB e convenções |
-->
