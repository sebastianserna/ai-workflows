# Rules: draft/

> Drafts are an idea bank: plan drafts, technical decisions, exploratory notes.

## What goes here

- Early-stage ideas that are not yet ready for backlog
- Technical decision records
- Exploratory notes and research

## Naming

```
DRAFT-YYYY-MM-DD-author_description.md
```

## Key rules

- Each draft must have YAML frontmatter with `state: "draft"` (see `workplans/README.md` for format)
- Drafts use the same frontmatter structure as all other states
- Drafts do **not** follow the BACKLOG → CODING → DONE workflow
- When a draft matures, promote it to `backlog/` — only update `state` and `backlog` date
- See `workplans/README.md` for full reference

## Examples

### Minimal example

```markdown
---
plan: "API rate limiting strategy"
state: "draft"
author: "sebastianserna"
author_model: ""
assignee: ""
assignee_model: ""
issue: ""
backlog: ""
coding: ""
done: ""
tags: "architecture"
---

# API rate limiting strategy

## Context

The API currently has no rate limiting. After deploying authentication, we observed automated login attempts from multiple IPs. We need a strategy before opening the API to external consumers.

## Options considered

### Option A: Express middleware (express-rate-limit)
- Pros: simple setup, no external dependencies
- Cons: per-instance only, not suitable for multi-instance deployments

### Option B: Redis-based (rate-limiter-flexible)
- Pros: shared across instances, supports sliding window
- Cons: requires Redis infrastructure

## Decision

Leaning towards Option B since we already use Redis for sessions. To be promoted to `backlog/` once limits per endpoint are defined.
```

### Complete example

```markdown
---
plan: "API rate limiting strategy"
state: "draft"
author: "sebastianserna"
author_model: ""
assignee: ""
assignee_model: ""
issue: ""
backlog: ""
coding: ""
done: ""
tags: "architecture, api"
---

# API rate limiting strategy

## Context

The API currently has no rate limiting. After the authentication system was deployed, we observed automated login attempts from multiple IPs. We need a rate limiting strategy before opening the API to external consumers.

## Options considered

### Option A: Express middleware (express-rate-limit)
- Pros: simple setup, in-memory by default, no external dependencies
- Cons: per-instance only, resets on restart, not suitable for multi-instance deployments

### Option B: Redis-based (rate-limiter-flexible)
- Pros: shared across instances, persistent, supports sliding window
- Cons: requires Redis infrastructure, additional operational complexity

### Option C: API Gateway (cloud provider)
- Pros: no code changes, managed service, includes DDoS protection
- Cons: vendor lock-in, less granular control, higher cost

## Decision

When the draft matures, it is promoted to `backlog/` as a formal plan.

## Comments

### 2026-01-25 — sebastianserna
Initial draft after observing automated login attempts. Leaning towards Option B since we already use Redis for sessions.

### 2026-01-28 — juanperez
Confirmed Redis is available in all environments. Option B is viable. Need to define limits per endpoint.
```

## See also

- `backlog/README.md` — Rules for pending plans
- `coding/README.md` — Rules for plans in progress
- `done/README.md` — Rules for completed plans
