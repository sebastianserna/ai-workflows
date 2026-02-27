# Rules: backlog/

> Pending plans waiting to be worked on.

## What goes here

- Plans that are defined and ready to start (or waiting for prioritization)
- New plans enter here after creation

## Naming

```
BACKLOG-YYYY-MM-DD-author_description.md
```

The date reflects when the plan was created.

## Key rules

- Each plan must have YAML frontmatter with `state: "backlog"` (see `workplan/README.md` for format)
- Fill in `author` (username) and other relevant frontmatter fields
- To start work: move to `coding/`, rename prefix to `CODING`, update date and frontmatter
- Plans can also be returned here from `coding/` if paused
- See `workplan/README.md` for full reference

## Examples

### Minimal example

```markdown
---
plan: "User authentication setup"
state: "backlog"
author: "sebastianserna"
author_model: "claude-opus-4"
assignee: ""
assignee_model: ""
issue: ""
backlog: "2026-01-15"
coding: ""
done: ""
tags: "enhancement"
---

# User authentication setup

## Progress

### Phase 1: MVP
- [ ] Create database migration for users table
- [ ] Implement JWT token generation and validation
- [ ] Add login and registration API endpoints
- [ ] Create authentication middleware

## Objective

Implement user authentication for the application using JWT tokens. All API endpoints need to verify user identity before any user-facing feature can be deployed.

## Implementation

### Phase 1: MVP

Create a `users` table with `id`, `email`, `password_hash`, `created_at`. Use bcrypt for password hashing and jsonwebtoken for JWT. The middleware will extract the token from the Authorization header and attach the user to `req.user`.
```

### Complete example

```markdown
---
plan: "User authentication setup"
state: "backlog"
author: "sebastianserna"
author_model: "claude-opus-4"
assignee: ""
assignee_model: ""
issue: "https://github.com/user/repo/issues/60"
backlog: "2026-01-15"
coding: ""
done: ""
tags: "enhancement, auth"
---

# User authentication setup

## Progress

### Phase 1: MVP
- [ ] Create database migration for users table
- [ ] Implement JWT token generation and validation
- [ ] Add login and registration API endpoints
- [ ] Create authentication middleware

### Phase 2: Improvements
- [ ] Add password reset flow
- [ ] Implement rate limiting on auth endpoints

## Objective

Implement user authentication for the application using JWT tokens. This is required before any user-facing feature can be deployed, as all API endpoints need to verify user identity.

## Context

The application currently has no authentication. The database is PostgreSQL and the API is built with Express. The frontend expects a Bearer token in the Authorization header.

## Implementation

### Phase 1: MVP

Create a `users` table with `id`, `email`, `password_hash`, `created_at`. Use bcrypt for password hashing and jsonwebtoken for JWT. The middleware will extract the token from the Authorization header and attach the user to `req.user`.

### Phase 2: Improvements

Add a `password_reset_tokens` table. Implement a `/forgot-password` endpoint that sends a reset link and a `/reset-password` endpoint that validates the token and updates the password.

## Verification

- [ ] Registration creates a user and returns a valid JWT
- [ ] Login with correct credentials returns a JWT
- [ ] Login with wrong credentials returns 401
- [ ] Protected endpoints reject requests without a valid token
- [ ] Password reset flow sends email and allows password change

## Risks

- JWT secret must be stored in environment variables, never committed
- Rate limiting is critical to prevent brute-force attacks on login
```

## See also

- `coding/README.md` — Rules for plans in progress
- `done/README.md` — Rules for completed plans
- `draft/README.md` — Rules for drafts and ideas
