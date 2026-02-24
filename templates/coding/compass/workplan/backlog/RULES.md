# Rules: backlog/

> Pending plans waiting to be worked on.

## What goes here

- Plans that are defined and ready to start (or waiting for prioritization)
- New plans enter here after creation

## Naming

**With issue tracker (GitHub / GitLab):**

```
BACKLOG-YYYY-MM-DD-iNNNN-description.md
```

**Without issue tracker:**

```
BACKLOG-YYYY-MM-DD-description.md
```

The date reflects when the plan was created.

## Key rules

- Each plan must have YAML frontmatter with `state: "backlog"` (see `workplan/README.md` for format)
- **If an issue tracker is configured**, create the issue first (`gh issue create`, `glab issue create`, etc.) and use the issue number in the filename (`iNNNN`)
- To start work: move to `coding/`, rename prefix to `CODING`, update date and frontmatter
- Plans can also be returned here from `coding/` if paused
- See `workplan/README.md` for full reference

## See also

- `coding/RULES.md` — Rules for plans in progress
- `done/RULES.md` — Rules for completed plans
- `draft/RULES.md` — Rules for drafts and ideas
