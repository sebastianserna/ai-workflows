# Rules: done/

> Completed plans — archive and reference.

## What goes here

- Plans that have been fully implemented and verified
- This folder serves as a historical record

## Naming

```
DONE-YYYY-MM-DD-author_description.md
```

The date reflects when the plan was completed.

## Key rules

- Each plan must have YAML frontmatter with `state: "done"` (see `workplans/README.md` for format)
- All progress checkboxes should be checked
- Completed plans should generally not be modified
- See `workplans/README.md` for full reference

## Examples

### Minimal example

```markdown
---
plan: "User authentication setup"
state: "done"
author: "sebastianserna"
author_model: "claude-opus-4"
assignee: "sebastianserna"
assignee_model: "claude-sonnet-4"
issue: ""
backlog: "2026-01-15"
coding: "2026-01-20"
done: "2026-02-01"
tags: "enhancement"
---

# User authentication setup

## Progress

### Phase 1: MVP
- [x] Create database migration for users table
- [x] Implement JWT token generation and validation
- [x] Add login and registration API endpoints
- [x] Create authentication middleware

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
state: "done"
author: "sebastianserna"
author_model: "claude-opus-4"
assignee: "sebastianserna"
assignee_model: "claude-sonnet-4"
issue: "https://github.com/user/repo/issues/60"
backlog: "2026-01-15"
coding: "2026-01-20"
done: "2026-02-01"
tags: "enhancement, auth"
---

# User authentication setup

## Progress

### Phase 1: MVP
- [x] Create database migration for users table
- [x] Implement JWT token generation and validation
- [x] Add login and registration API endpoints
- [x] Create authentication middleware

### Phase 2: Improvements
- [x] Add password reset flow
- [x] Implement rate limiting on auth endpoints

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

- [x] Registration creates a user and returns a valid JWT
- [x] Login with correct credentials returns a JWT
- [x] Login with wrong credentials returns 401
- [x] Protected endpoints reject requests without a valid token
- [x] Password reset flow sends email and allows password change

## Comments

### 2026-01-20 — sebastianserna
Started implementation. Migration and JWT utils are done. Moving on to API endpoints.

### 2026-01-21 — sebastianserna
Decided to use refresh tokens instead of long-lived JWTs. Access token expires in 15 minutes, refresh token in 7 days.

### 2026-02-01 — sebastianserna
All phases complete. Rate limiting set to 5 attempts per minute per IP. PR merged.
```

## See also

- `backlog/README.md` — Rules for pending plans
- `coding/README.md` — Rules for plans in progress
- `draft/README.md` — Rules for drafts and ideas
