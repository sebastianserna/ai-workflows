# Plan management

> **This file is the source of truth for plan management.** AI agents must follow these instructions when creating, moving, or modifying plans.

## Configuration

**Issue tracker:** none
<!-- Options: GitHub | GitLab | none -->
<!-- To activate: change to "GitHub" or "GitLab" and configure the repository -->

**Repository:** `user/repo-name`

## File naming format

The format depends on whether an issue tracker is configured:

**With issue tracker (GitHub / GitLab):**

```
TYPE-YYYY-MM-DD-iNNNN-description.md
```

**Without issue tracker (none):**

```
TYPE-YYYY-MM-DD-description.md
```

| Segment | Description | Example |
|---------|-------------|---------|
| `TYPE` | State: `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Date of transition to current state | `2026-01-15` |
| `iNNNN` | Issue number, 4 digits zero-padded with `i` prefix (only with tracker) | `i0060` |
| `description` | Short name in kebab-case | `user-auth-setup` |

### Issue identifier (`iNNNN`)

When an issue tracker is configured (GitHub or GitLab), each plan **must** have a corresponding issue. The issue number becomes the plan's unique identifier:

- The `i` prefix distinguishes the issue number from other numeric segments
- Zero-padded to 4 digits: issue #7 → `i0007`, issue #123 → `i0123`
- The identifier is **permanent** — it does not change when the plan moves between states
- GitHub/GitLab guarantees atomic uniqueness, eliminating collision risks in collaborative environments

**When the issue tracker is "none"**, plans have no identifier segment. The filename is simply `TYPE-YYYY-MM-DD-description.md`.

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
- When tracker is active, **Issue** links to the issue: `[#60](https://github.com/user/repo/issues/60)`

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

**With issue tracker:**

1. Create the issue first: `gh issue create` (GitHub) or `glab issue create` (GitLab)
2. Note the issue number (e.g., #60)
3. Create file in `backlog/BACKLOG-YYYY-MM-DD-iNNNN-description.md` (e.g., `BACKLOG-2026-01-15-i0060-user-auth-setup.md`)
4. Fill in the `Issue` header field with the link

**Without issue tracker:**

1. Create file in `backlog/BACKLOG-YYYY-MM-DD-description.md`

### Start work

1. Move from `backlog/` to `coding/CODING-YYYY-MM-DD-...-description.md` (date = today, identifier unchanged)
2. Update header: `State: Coding`, `Coding: YYYY-MM-DD`

### Complete

1. Move from `coding/` to `done/DONE-YYYY-MM-DD-...-description.md` (date = today)
2. Update header: `State: Done`, `Done: YYYY-MM-DD`

### Return to backlog

1. Move from `coding/` to `backlog/BACKLOG-YYYY-MM-DD-...-description.md`
2. Update header: `State: Backlog`

## Cross-references

**With issue tracker:** plans reference each other using the issue number with `#N`, which is permanent and enables auto-linking:

```markdown
**Dependencies:** #1, #2

See #3 for details.
```

**Without issue tracker:** reference plans by their descriptive name:

```markdown
**Dependencies:** user-auth-setup, api-rate-limiting
```

**Rule:** never reference a plan by its full filename (it changes with each transition).

## Drafts

Drafts are stored in `draft/` with the format `DRAFT-YYYY-MM-DD-description.md`. They do not follow the BACKLOG→CODING→DONE workflow and have no issue identifier. They serve as an idea bank: plan drafts, technical decisions, exploratory notes. When a draft matures enough, it is promoted to `backlog/` as a formal plan.
