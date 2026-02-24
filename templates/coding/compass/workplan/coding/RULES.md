# Rules: coding/

> Plans actively being worked on.

## What goes here

- Plans currently in progress
- Only plans that are being actively implemented

## Naming

**With issue tracker (GitHub / GitLab):**

```
CODING-YYYY-MM-DD-iNNNN-description.md
```

**Without issue tracker:**

```
CODING-YYYY-MM-DD-description.md
```

The date reflects when work started.

## Key rules

- Each plan must have YAML frontmatter with `state: "coding"` (see `workplan/README.md` for format)
- Update progress checkboxes as steps are completed
- When done: move to `done/`, rename prefix to `DONE`, update date and frontmatter
- To pause: move back to `backlog/`, rename prefix to `BACKLOG`, update frontmatter
- See `workplan/README.md` for full reference

## See also

- `backlog/RULES.md` — Rules for pending plans
- `done/RULES.md` — Rules for completed plans
- `draft/RULES.md` — Rules for drafts and ideas
