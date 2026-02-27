# Workplans

> **This file is the source of truth for plan management.** AI agents must follow these instructions when creating, moving, or modifying plans.

## What is a plan

A plan is a structured Markdown file that works like an issue in a project tracker. It has a defined state (`draft` → `backlog` → `coding` → `done`), YAML frontmatter with metadata, and a body that guides an AI agent through the execution of its tasks. Each plan lives in the folder that matches its current state.

```
workplans/
├── README.md          # This file (source of truth)
├── backlog/           # Pending plans
├── coding/            # Work in progress
├── done/              # Completed plans (archive)
├── draft/             # Drafts, ideas, and decisions
└── knowledge/         # Knowledge base (architecture, development, operations)
```

## File naming format

```
TYPE-YYYY-MM-DD-author_description.md
```

| Segment | Description | Example |
|---------|-------------|---------|
| `TYPE` | State: `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Date of transition to current state | `2026-01-15` |
| `author` | Username of the plan creator on the version control platform (GitHub, GitLab, Bitbucket, etc.) | `sebastianserna` |
| `_` | Underscore separator between author and description | `_` |
| `description` | Short name in kebab-case | `user-auth-setup` |

### Author identifier

The username of the creator on the version control platform (GitHub, GitLab, Bitbucket, etc.) serves as the plan's author identifier:

- The underscore `_` separates the author from the description, avoiding ambiguity with usernames that contain hyphens
- The author is **permanent** — it does not change when the plan moves between states
- Uniqueness is guaranteed by the combination of date + author + description
- Provides immediate visibility of who created each plan when listing files: `ls *sebastianserna*`
- **Multiple authors:** the filename always uses the **creator** (one person). If multiple people co-author the plan, the frontmatter `author` field lists them comma-separated (e.g., `"sebastianserna, juanperez"`), but the filename only includes the creator

### Date rule

The date in the filename reflects the transition to the current state:

| State | Date in name = |
|-------|----------------|
| BACKLOG | Date the plan was created |
| CODING | Date work started |
| DONE | Date completed |
| DRAFT | Date the draft was created |

## YAML Frontmatter

Every plan file must start with a YAML frontmatter block on **line 1** (no blank lines before the opening `---`). GitHub renders this as a metadata table.

**All states use the same frontmatter structure** (like an issue in Jira or Linear — same fields, only values change):

```yaml
---
plan: "Descriptive title"
state: "backlog"
author: ""
author_model: ""
assignee: ""
assignee_model: ""
issue: ""
backlog: "2026-01-15"
coding: ""
done: ""
tags: ""
---
```

**Frontmatter fields:**

| Field | Description | Values |
|-------|-------------|--------|
| `plan` | Short descriptive title | Free text |
| `state` | Current state (must match filename prefix) | `backlog`, `coding`, `done`, `draft` |
| `author` | Username(s) of the plan creator(s) (from version control platform) | `"sebastianserna"`, `"sebastianserna, juanperez"`, `""` |
| `author_model` | AI model(s) that created the plan | `"claude-opus-4"`, `"claude-opus-4, claude-sonnet-4"`, `""` |
| `assignee` | Username of the person implementing | `"sebastianserna"`, `""` |
| `assignee_model` | AI model(s) that executed the plan | `"claude-sonnet-4"`, `""` |
| `issue` | URL to the linked issue (any tracker) | `"https://github.com/user/repo/issues/60"`, `""` |
| `backlog` | Date the plan was created | `"2026-01-15"`, `""` |
| `coding` | Date work started | `"2026-01-20"`, `""` |
| `done` | Date completed | `"2026-02-01"`, `""` |
| `tags` | Labels for categorization (like issue tracker labels) | `"enhancement"`, `"bug, api"`, `""` |

**Frontmatter rules:**
- The first `---` must be exactly on line 1 with no blank lines before it
- The `state` value must match the filename prefix (lowercase)
- **All fields are present in every state** — empty (`""`) if not yet applicable
- Promoting a draft to backlog only requires updating `state` and `backlog` date — no structural change
- `issue` is a full URL to any issue tracker (GitHub, Linear, Jira, etc.) — leave empty if no issue is linked
- All multi-value fields (`author`, `author_model`, `assignee_model`, `tags`) use comma-separated strings: `"claude-opus-4, claude-sonnet-4"`, `"enhancement, api"`
- The first value in `author` is the creator and must match the author in the filename
- Date fields record when each transition occurred (`""` if not yet reached)

## Standard template

### Required terminology

| Term | Usage | Example |
|------|-------|---------|
| **Phase** | Major implementation milestone | Phase 1: MVP, Phase 2: Improvements |
| **Step** | Concrete item in the progress checklist | `- [ ] Create SQL migration` |

### Section order

Frontmatter → H1 title → Progress → Objective → Context → Implementation → Verification → Risks → Comments

Optional sections are **omitted**, not left empty.

### Template

```markdown
---
plan: "Descriptive title"
state: "backlog"
author: ""
author_model: ""
assignee: ""
assignee_model: ""
issue: ""
backlog: "YYYY-MM-DD"
coding: ""
done: ""
tags: ""
---

# Descriptive title

## Progress

### Phase 1: MVP
- [ ] Concrete, verifiable step
- [ ] Another step

### Phase 2: Improvements *(if applicable)*
- [ ] Concrete, verifiable step

## Objective

What you want to achieve and why (1-3 paragraphs).

## Context *(optional)*

Current state, prerequisites.

## Implementation

### Phase 1: MVP

Technical detail of the implementation.

### Phase 2: Improvements *(optional)*

## Verification *(optional)*

Steps to validate the plan was completed correctly.

## Risks *(optional)*

Only for complex plans.

## Comments *(optional)*

### YYYY-MM-DD — author
Comment text: decisions, blockers, status updates, context changes.
```

### Rules

1. **H1 title after the frontmatter** — must match the `plan` field value
2. **Progress always after the H1**, never at the end
3. Steps grouped by phase (`### Phase N: Name`)
4. Each step must be concrete and verifiable (not generic)
5. Technical detail in Implementation, summary in Progress
6. Only "Phase" and "Step", never "Stage"
7. Optional sections are omitted, not left empty
8. **Comments** are always the last section, in chronological order (oldest first)

## Workflow

### Create plan

1. Create file in `backlog/BACKLOG-YYYY-MM-DD-author_description.md` (e.g., `BACKLOG-2026-01-15-sebastianserna_user-auth-setup.md`)
2. Fill in the frontmatter fields (`author`, `backlog` date, `tags`, etc.)
3. *(Optional)* Create an issue in your tracker and add the URL to the `issue` field

### Start work

1. Move from `backlog/` to `coding/CODING-YYYY-MM-DD-author_description.md` (date = today, author unchanged)
2. Update frontmatter: `state: "coding"`, `coding: "YYYY-MM-DD"`

### Complete

1. Move from `coding/` to `done/DONE-YYYY-MM-DD-author_description.md` (date = today)
2. Update frontmatter: `state: "done"`, `done: "YYYY-MM-DD"`

### Return to backlog

1. Move from `coding/` to `backlog/BACKLOG-YYYY-MM-DD-author_description.md`
2. Update frontmatter: `state: "backlog"`, `coding: ""`

## Cross-references

Reference plans by their descriptive name, which is permanent across state transitions:

```markdown
**Dependencies:** user-auth-setup, api-rate-limiting
```

If plans have linked issues, you can also reference them by issue number for auto-linking:

```markdown
**Dependencies:** #1, #2

See #3 for details.
```

**Rule:** never reference a plan by its full filename (it changes with each transition).

## Drafts

Drafts are stored in `draft/` with the format `DRAFT-YYYY-MM-DD-author_description.md`. They use the same frontmatter structure as all other states. They serve as an idea bank: plan drafts, technical decisions, exploratory notes. When a draft matures enough, it is promoted to `backlog/` as a formal plan — only the `state` and `backlog` date need to be updated.
