# AI Tools

A lightweight starter repository for new AI-assisted projects.

## What This Repo Provides

- A project `README` template for documenting scope, setup, workflows, and conventions
- An `AGENTS` template for defining how AI agents should operate in a codebase
- A starter `.editorconfig` for spaces-only, 4-space indentation and basic text-file defaults
- A reusable `SKILL` template for specialized agent workflows
- A `repo-setup` skill for bootstrapping a new repo from these conventions without copying auxiliary template folders verbatim

## Structure

```text
.
├── .editorconfig
├── logs
│   └── session-log.md
├── README.md
├── skills
│   ├── README.md
│   ├── repo-setup
│   │   ├── agents
│   │   │   └── openai.yaml
│   │   └── SKILL.md
│   └── template
│       └── SKILL.md
└── templates
    ├── .editorconfig
    ├── AGENTS.md
    ├── logs
    │   └── session-log.md
    └── README.md
```

## Suggested Usage

1. Copy [templates/README.md](/Users/pablo/github/ai-tools/templates/README.md) into a new project and replace the placeholders.
2. Copy [templates/AGENTS.md](/Users/pablo/github/ai-tools/templates/AGENTS.md) into the project root and tailor the operating rules to the repo.
3. Copy [templates/.editorconfig](/Users/pablo/github/ai-tools/templates/.editorconfig) into the project root if you want the indentation and basic text-file conventions enforced by editors.
4. Create `logs/session-log.md` using [templates/logs/session-log.md](/Users/pablo/github/ai-tools/templates/logs/session-log.md) and prepend a new entry for each work session.
5. Duplicate [skills/template/SKILL.md](/Users/pablo/github/ai-tools/skills/template/SKILL.md) when you need a repeatable workflow for a specific task or toolchain.
6. Use [skills/repo-setup/SKILL.md](/Users/pablo/github/ai-tools/skills/repo-setup/SKILL.md) when you want Codex to initialize a new repo from this starter structure and adapt it to the target codebase.

## Notes

These templates are intentionally minimal. They are meant to be edited heavily so each new project gets clear documentation, explicit agent behavior, and task-specific skills from the start.

The `.editorconfig` is meant to complement, not replace, language-specific formatters when a project already has stronger tooling.
