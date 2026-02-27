# knowledge/ — Knowledge base

This folder contains the project's technical documentation. It is the **source of truth** that AI agents consult before making decisions.

## Purpose

- Document architecture decisions and their reasoning
- Keep technical guides up to date
- Prevent agents from repeating mistakes or making inconsistent decisions
- Preserve knowledge that doesn't fit in the code itself

## Structure

```
knowledge/
├── README.md           # This file
├── architecture/       # How the system is designed
│   └── AGENTS.md
├── development/        # How to work on the project
│   └── AGENTS.md
└── operations/         # How it's deployed and operated
    └── AGENTS.md
```

Each `AGENTS.md` provides context for AI agents about the folder's scope and when to consult it.

### architecture/

Architecture decisions, system structure, chosen patterns and their reasoning. Answers **"how is it designed and why"**.

Examples: folder structure, layer patterns, library decisions, component diagrams.

### development/

Day-to-day development guides. Answers **"how do I work on this project"**.

Examples: code conventions, testing guide, git workflow, local setup, linting.

### operations/

Everything related to getting code to production and keeping it running. Answers **"how is it deployed and operated"**.

Examples: CI/CD pipeline, environment configuration, monitoring, environment variables.

## When to add more folders

The three base folders cover most projects. If the project grows in a specific domain, add dedicated folders:

| Folder | When to add it |
|--------|----------------|
| `database/` | The project has its own database with migrations |
| `security/` | Auth rules, permissions, or compliance to document |
| `integrations/` | Multiple external APIs or third-party services |
| `api/` | Public API consumed by others |

**Rule:** don't create empty folders "just in case". Create them when there's at least one real document to put inside.

## Conventions

- Documents in Markdown, one topic per file
- Keep updated when architecture changes
- Reference from `AGENTS.md` in the "Detailed specifications" section

## Difference from plan folders

| | `knowledge/` | `backlog/`, `coding/`, `done/`, `draft/` |
|---|-----------|-------------|
| **Contains** | Permanent documentation | Work plans with lifecycle |
| **Changes** | When architecture evolves | Constantly (backlog → coding → done) |
| **Format** | Free-form | Standardized template with frontmatter |
| **Purpose** | Understand the system | Manage what needs to be done |
