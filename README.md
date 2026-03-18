# AI Tools

A lightweight starter repository for new AI-assisted projects.

## What This Repo Provides

- A project `README` template for documenting scope, setup, workflows, and conventions
- An `AGENTS` template for defining how AI agents should operate in a codebase
- A reusable `SKILL` template for specialized agent workflows

## Structure

```text
.
├── logs
│   └── session-log.md
├── README.md
├── skills
│   ├── README.md
│   └── template
│       └── SKILL.md
└── templates
    ├── AGENTS.md
    ├── logs
    │   └── session-log.md
    └── README.md
```

## Suggested Usage

1. Copy [templates/README.md](/Users/pablo/github/ai-tools/templates/README.md) into a new project and replace the placeholders.
2. Copy [templates/AGENTS.md](/Users/pablo/github/ai-tools/templates/AGENTS.md) into the project root and tailor the operating rules to the repo.
3. Create `logs/session-log.md` using [templates/logs/session-log.md](/Users/pablo/github/ai-tools/templates/logs/session-log.md) and prepend a new entry for each work session.
4. Duplicate [skills/template/SKILL.md](/Users/pablo/github/ai-tools/skills/template/SKILL.md) when you need a repeatable workflow for a specific task or toolchain.

## Notes

These templates are intentionally minimal. They are meant to be edited heavily so each new project gets clear documentation, explicit agent behavior, and task-specific skills from the start.
