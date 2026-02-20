# Plan management

> **This file is the source of truth for plan management.** AI agents must follow these instructions when creating, moving, or modifying plans.

## Configuration

**Issue tracker:** none
<!-- Options: GitHub | GitLab | none -->
<!-- To activate: change to "GitHub" or "GitLab" and configure the repository -->

**Repository:** `user/repo-name`

## File naming format

```
TYPE-YYYY-MM-DD-NNNN-description.md
```

| Segment | Description | Example |
|---------|-------------|---------|
| `TYPE` | State: `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Date of transition to current state | `2026-01-15` |
| `NNNN` | Internal sequential ID, 4 digits zero-padded | `0001` |
| `description` | Short name in kebab-case | `user-auth-setup` |

### Internal ID (`NNNN`)

Project-specific incremental counter. To get the next one:

1. Find the highest `NNNN` across all subfolders (`backlog/`, `coding/`, `done/`)
2. Add 1

The ID is **permanent** — it does not change even if the plan's state or name changes.

> **Reserved:** ID `0000` is reserved for example/template files. The first real plan must use `0001`.

### Date rule

The date in the filename reflects the transition to the current state:

| State | Date in name = |
|-------|----------------|
| BACKLOG | Date the plan was created |
| CODING | Date work started |
| DONE | Date completed |

## Folder structure

```
workplan/
├── README.md          # This file (source of truth)
├── backlog/           # Pending plans
├── coding/            # Work in progress
├── done/              # Completed plans (archive)
└── draft/             # Drafts, ideas, and decisions (no state workflow)
```

## Standardized header

```markdown
# Plan: Descriptive title

**State:** Backlog | Coding | Done
**Backlog:** 2026-01-15
**Coding:** —
**Done:** —
**Domain:** general
**Issue:** —
```

**Header rules:**
- The state must match the filename prefix
- Dates record when each transition occurred (`—` if not applicable)
- **Issue** is `—` if the issue tracker is configured as "none"

## Standard template

### Required terminology

| Term | Usage | Example |
|------|-------|---------|
| **Phase** | Major implementation milestone | Phase 1: MVP, Phase 2: Improvements |
| **Step** | Concrete item in the progress checklist | `- [ ] Create SQL migration` |

### Section order

Header → Progress → Objective → Context → Implementation → Verification → Risks

Optional sections are **omitted**, not left empty.

### Template

```markdown
# Plan: Descriptive title

**State:** Backlog
**Backlog:** YYYY-MM-DD
**Coding:** —
**Done:** —
**Domain:** general
**Issue:** —

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
```

### Rules

1. **Progress always after the header**, never at the end
2. Steps grouped by phase (`### Phase N: Name`)
3. Each step must be concrete and verifiable (not generic)
4. Technical detail in Implementation, summary in Progress
5. Only "Phase" and "Step", never "Stage"
6. Optional sections are omitted, not left empty

## Workflow

### Create plan

1. Get the next sequential ID (`NNNN`)
2. Create file in `backlog/BACKLOG-YYYY-MM-DD-NNNN-description.md`

### Start work

1. Move from `backlog/` to `coding/CODING-YYYY-MM-DD-NNNN-description.md` (date = today, ID unchanged)
2. Update header: `State: Coding`, `Coding: YYYY-MM-DD`

### Complete

1. Move from `coding/` to `done/DONE-YYYY-MM-DD-NNNN-description.md` (date = today)
2. Update header: `State: Done`, `Done: YYYY-MM-DD`

### Return to backlog

1. Move from `coding/` to `backlog/BACKLOG-YYYY-MM-DD-NNNN-description.md`
2. Update header: `State: Backlog`

## Cross-references

Plans reference each other using the **internal ID** (`NNNN`), which is permanent:

```markdown
**Dependencies:** Plan 0001, Plan 0002

See plan 0003 for details.
```

**Rule:** never reference a plan by its full filename (it changes with each transition). Always use the internal ID.

## Get next ID

```bash
# Find the highest NNNN across all subfolders
ls workplan/{backlog,coding,done}/ | grep -oP '\d{4}' | sort -n | tail -1
# Add 1 to the result
```

## Drafts

Drafts are stored in `draft/` with the format `DRAFT-YYYY-MM-DD-description.md`. They do not follow the BACKLOG→CODING→DONE workflow and have no sequential ID. They serve as an idea bank: plan drafts, technical decisions, exploratory notes. When a draft matures enough, it is promoted to `backlog/` as a formal plan.
