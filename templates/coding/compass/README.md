# Project Name

Brief description of the project.

## Requirements

<!-- List system requirements: Node.js, Python, Docker, etc. -->

## Installation

```bash
# Clone the repository
git clone <repo-url>
cd <project-name>

# Install dependencies
# npm install / pip install / etc.

# Set up environment variables
cp .env.example .env
```

## Development

```bash
# Start development server
# npm run dev / python manage.py runserver / etc.
```

## Project structure

```
AGENTS.md               # Instructions for AI agents
CLAUDE.md               # Claude Code configuration
README.md               # This file
wisdom/                 # Knowledge base (architecture, guides)
workplan/               # Work plan management
├── backlog/            #   Pending plans
├── coding/             #   In progress
├── done/               #   Completed
└── draft/              #   Drafts and ideas
```

## Working with AI agents

This project is set up to work with AI agents like Claude Code:

- **AGENTS.md** — Complete guide for agents to understand the project
- **CLAUDE.md** — Entry point that loads automatically when starting Claude Code
- **wisdom/** — Technical documentation that agents consult for decision-making
- **workplan/** — Task management system that agents can read and update
