# AGENTS.md

Guide for AI agents working on this project.

<!-- Language: define here the language for agent responses and for code -->

## Stack

<!-- Define the project's technology stack here. Example:
- Framework:
- UI:
- Backend/DB:
- Language:
-->

## Setup and commands

<!-- Essential project commands. Example:
```bash
npm install        # Install dependencies
npm run dev        # Development server
npm run build      # Production build
npm run lint       # Linter
npm run test       # Tests
```
-->

<!-- Required environment variables:
- List here the variables required in `.env`
-->

## Project structure

<!-- Describe the main folder structure of the project. Example:
```
src/
docs/
tests/
workplans/
```
-->

## Code conventions

- Indentation: 2 spaces
- Code in English, documentation and comments in English

<!-- Add more team conventions. Example:
- Naming: camelCase for variables, PascalCase for components
- Strict TypeScript
-->

## Plan management (workplans/)

The `workplans/` folder manages the lifecycle of project tasks.

**Folders:**
- `backlog/` — Pending plans, prioritized and ready to work on
- `coding/` — Plans in active progress
- `done/` — Completed plans (historical archive)
- `draft/` — Drafts, ideas, and decisions
- `knowledge/` — Knowledge base (architecture, development, operations)

**Workflow:** `(draft/) -> backlog/ -> coding/ -> done/`

**File naming format:** `TYPE-YYYY-MM-DD-author_description.md`
- TYPE: `BACKLOG`, `CODING`, `DONE`, `DRAFT`
- author: Username of the plan creator (GitHub, GitLab, Bitbucket, etc.)
- `_` separates author from description

All states share the same YAML frontmatter structure (uniform fields across draft, backlog, coding, done).

The `knowledge/` subfolder contains the project's technical documentation — the source of truth for understanding how the system works. Agents should consult `workplans/knowledge/` before making decisions that affect existing architecture or patterns. See `workplans/knowledge/README.md` for details.

See `workplans/README.md` for the complete template and detailed rules.

## Auth and roles

<!-- Define the authentication and roles system. Example:
- Auth provider:
- Role hierarchy:
- Composable/function for permission checks:
-->

## Git workflow

- Main branch: `main` (PRs required)
- Branches: `feature/`, `fix/`, `hotfix/`, `refactor/`, `chore/`, `docs/` + description in English
- Commits: Conventional Commits in English (`feat:`, `fix:`, `docs:`, etc.)
- PRs: title in English (Conventional Commits), description/body in English
- Issues: title and description in English
- **Do not include** `Co-Authored-By` from AI agents in commits
- **Do not include** the "Generated with Claude Code" link in commit messages or PRs

<!-- Add more Git workflow rules if needed -->

## Testing

<!-- Define the testing strategy. Example:
- Test framework:
- What must have tests:
- File pattern: `*.test.ts` or `*.spec.ts`
-->

## Protected zones (DO NOT modify)

<!-- List files or folders that agents must NOT modify. Example:
| File | Reason |
|------|--------|
| `.env` | Never commit |
| `migrations/` (applied) | Create a new one instead |
-->

## Known gotchas

<!-- Document known issues or common pitfalls. Example:
- Bug X: description and workaround
- Limitation Y: context and temporary solution
-->

## Detailed specifications

<!-- List links to reference documents in workplans/knowledge/. Example:
| Document | Content |
|----------|---------|
| [workplans/knowledge/architecture/...](workplans/knowledge/architecture/...) | System architecture |
| [workplans/knowledge/database/...](workplans/knowledge/database/...) | DB schema and conventions |
-->
