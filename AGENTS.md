# AGENTS.md

Instructions for AI agents working with this repository.

## What is this repo?

A collection of reusable templates and workflows for AI-assisted projects. Templates are organized by domain inside `templates/`.

## How to find templates

1. Read `README.md` at the repo root — it contains the full **template catalog** organized by category
2. Each category has its own folder under `templates/` with a README listing available templates
3. Each template is a self-contained folder with its own README explaining purpose and usage

### Quick reference

```
templates/
├── coding/       # Code generation, repo setup, dev workflows
├── images/       # Image generation, editing, style transfer
├── video/        # Video generation, editing, motion
├── audio/        # Audio generation, music, speech, sound design
├── 3d/           # 3D modeling, texturing, scene generation
├── writing/      # Creative writing, copywriting, documentation
└── other/        # Miscellaneous and experimental
```

## How to use a template

1. Browse the catalog in `README.md` or the `templates/` directory
2. Open the template's folder and read its `README.md` for instructions
3. Copy the template files into the target project
4. Adapt the content to fit the project's needs

## i18n

- All templates are written in **English** by default
- Some templates include an `i18n/` subfolder with translations
- If a user requests a specific language, check for `i18n/` inside the template before translating manually

## Git workflow

- Main branch: `main` (protected, PRs required)
- Branch naming: `feature/`, `fix/`, `hotfix/`, `refactor/`, `chore/`, `docs/` + description in English
- Commits: Conventional Commits in English (`feat:`, `fix:`, `docs:`, `chore:`, `refactor:`, `style:`, `test:`, `ci:`, `perf:`, `build:`)
- PRs: title in English (Conventional Commits format), description/body in Spanish
- Issues: title and description in Spanish
- Do **not** include `Co-Authored-By` from AI agents in commits
- Do **not** include "Generated with Claude Code" links in commit messages or PRs

## Guidelines for agents

- Do **not** modify templates in this repo unless explicitly asked — they are meant to be copied, not edited in place
- When recommending a template, link to its README so the user can review it first
- If no template fits the user's need, suggest creating a new one following `CONTRIBUTING.md`
