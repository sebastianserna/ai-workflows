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
wisdom/
workplan/
```
-->

## Code conventions

<!-- Define team conventions. Example:
- Indentation: 2 spaces
- Naming: camelCase for variables, PascalCase for components
- Strict TypeScript
- Code in English, documentation in English
-->

## Knowledge base (wisdom/)

The `wisdom/` folder contains the project's technical documentation. It is the source of truth for understanding how the system works.

Base structure:
- `wisdom/architecture/` — How the system is designed (decisions, patterns, structure)
- `wisdom/development/` — How to work on the project (conventions, testing, workflows)
- `wisdom/operations/` — How it's deployed and operated (CI/CD, environments, monitoring)

Additional folders (`database/`, `security/`, `integrations/`) can be added when the project requires them. See `wisdom/README.md` for criteria.

Agents should consult `wisdom/` before making decisions that affect existing architecture or patterns.

## Plan management (workplan/)

The `workplan/` folder manages the lifecycle of project tasks.

**Folders:**
- `backlog/` — Pending plans, prioritized and ready to work on
- `coding/` — Plans in active progress
- `done/` — Completed plans (historical archive)
- `draft/` — Drafts, ideas, and architecture decisions (no workflow or ID)

**Workflow:** `backlog/ -> coding/ -> done/`

**File naming format:** `TYPE-YYYY-MM-DD-NNNN-description.md`
- TYPE: `BACKLOG`, `CODING`, `DONE`
- NNNN: Permanent sequential ID (does not change when moving between folders)

See `workplan/README.md` for the complete template and detailed rules.

## Auth and roles

<!-- Define the authentication and roles system. Example:
- Auth provider:
- Role hierarchy:
- Composable/function for permission checks:
-->

## Git workflow

<!-- Define the Git workflow. Example:
- Main branch: `main`
- Branches: `feature/`, `fix/`, `hotfix/`, `docs/` + description
- Commits: Conventional Commits (`feat:`, `fix:`, `docs:`, etc.)
- PRs required for merging to main
-->

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

<!-- List links to reference documents in wisdom/. Example:
| Document | Content |
|----------|---------|
| [wisdom/architecture/...](wisdom/architecture/...) | System architecture |
| [wisdom/database/...](wisdom/database/...) | DB schema and conventions |
-->
