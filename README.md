# AI Tools

A lightweight starter repository for new AI-assisted projects.

## What This Repo Provides

- A project `README` template for documenting scope, setup, workflows, and conventions
- A personal root `AGENTS` template for defining machine-level or account-level working preferences
- A repository root `AGENTS` template for defining how AI agents should operate in a codebase
- A nested `AGENTS` template for subdirectories that need narrower instructions than the repo root
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
    ├── code
    │   └── AGENTS.md
    ├── logs
    │   └── session-log.md
    ├── personal
    │   └── AGENTS.md
    └── README.md
```

## Instruction Layers

- `templates/personal/AGENTS.md`: personal root instructions you set once per machine or account.
- `templates/AGENTS.md`: repo-level instructions that define how agents should operate in a specific project.
- `templates/code/AGENTS.md`: narrower instructions for a subtree that needs rules beyond the repo root.

## Suggested Usage

1. Copy [templates/personal/AGENTS.md](/Users/pablo/github/ai-tools/templates/personal/AGENTS.md) into your machine-level or account-level agent instruction location and replace the placeholders with your own working preferences.
2. Copy [templates/README.md](/Users/pablo/github/ai-tools/templates/README.md) into a new project and replace the placeholders.
3. Copy [templates/AGENTS.md](/Users/pablo/github/ai-tools/templates/AGENTS.md) into the project root and tailor the operating rules to the repo.
4. Copy [templates/code/AGENTS.md](/Users/pablo/github/ai-tools/templates/code/AGENTS.md) into a nested `code/` folder when that subtree needs its own instructions.
5. Copy [templates/.editorconfig](/Users/pablo/github/ai-tools/templates/.editorconfig) into the project root if you want the indentation and basic text-file conventions enforced by editors.
6. Create `logs/session-log.md` using [templates/logs/session-log.md](/Users/pablo/github/ai-tools/templates/logs/session-log.md) and prepend a new entry for each work session.
7. Duplicate [skills/template/SKILL.md](/Users/pablo/github/ai-tools/skills/template/SKILL.md) when you need a repeatable workflow for a specific task or toolchain.
8. Use [skills/repo-setup/SKILL.md](/Users/pablo/github/ai-tools/skills/repo-setup/SKILL.md) when you want Codex to initialize a new repo from this starter structure and adapt it to the target codebase.

## Notes

These templates are intentionally minimal. They are meant to be edited heavily so each new project gets clear documentation, explicit agent behavior, and task-specific skills from the start.

The `.editorconfig` is meant to complement, not replace, language-specific formatters when a project already has stronger tooling.

The personal root `AGENTS.md` template was informed in part by [Claude Blattman's `claude.md` toolkit](https://claudeblattman.com/toolkit/claude-md/).
