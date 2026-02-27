# Changelog

All notable changes to the **compass** template will be documented in this file.

This project uses [Semantic Versioning](https://semver.org/):
- **MAJOR** — Incompatible structural changes (files renamed/removed, frontmatter schema changes)
- **MINOR** — New files, sections, or features added (backwards compatible)
- **PATCH** — Content fixes, typos, wording improvements

## [2.0.0] - 2026-02-26

### Breaking changes
- **Filename format**: `TYPE-YYYY-MM-DD-author_description.md` — author (username) replaces `iNNNN` as identifier, underscore `_` separates author from description
- **Frontmatter schema**: uniform structure across all states (draft, backlog, coding, done)
  - Added: `author`, `author_model`, `assignee`, `assignee_model`, `tags`, date fields for drafts
  - Changed: `issue` now holds a URL (any tracker) instead of `iNNNN`
  - Removed: `domain` (replaced by `tags`)
- **Template files renamed**: `*-example-template.md` → `*-author_example-template.md`

## [1.0.0] - 2026-02-24

Initial stable release.

### Structure
- Project root: README.md, AGENTS.md, CLAUDE.md
- wisdom/: architecture, development, operations
- workplan/: backlog, coding, done, draft (with YAML frontmatter)
- i18n/: 10 language translations
