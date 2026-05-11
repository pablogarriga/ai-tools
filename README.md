# AI Tools

A lightweight starter repository for new AI-assisted projects.

## What This Repo Provides

- A project `README` template for documenting scope, setup, workflows, and conventions
- A personal root `AGENTS` template for defining machine-level or account-level working preferences
- A repository root `AGENTS` template for defining how AI agents should operate in a codebase
- A nested `AGENTS` template for subdirectories that need narrower instructions than the repo root
- A `project-setup` skill for organizing a repository around its analytical workflow without copying auxiliary template folders verbatim
- A `filing-harmonizer` skill for building or auditing comparable filing-based panels across years and regimes

## Structure

```text
.
├── README.md
├── skills
│   ├── README.md
│   ├── filing-harmonizer
│   │   ├── agents
│   │   │   └── openai.yaml
│   │   ├── references
│   │   │   ├── audit-checklist.md
│   │   │   ├── diagnostics.md
│   │   │   └── source-recovery.md
│   │   └── SKILL.md
│   ├── project-setup
│   │   ├── agents
│   │   │   └── openai.yaml
│   │   ├── references
│   │   │   ├── r-master-script.md
│   │   │   ├── script-structure.md
│   │   │   └── stata-master-dofile.md
│   │   └── SKILL.md
└── templates
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
5. Create `logs/session-log.md` in a target project using [templates/logs/session-log.md](/Users/pablo/github/ai-tools/templates/logs/session-log.md) and prepend a new entry for each work session.
6. Use [skills/project-setup/SKILL.md](/Users/pablo/github/ai-tools/skills/project-setup/SKILL.md) when you want Codex to structure a repo around its folder layout, analytical pipeline, README, AGENTS.md, and logs.
7. Use [skills/filing-harmonizer/SKILL.md](/Users/pablo/github/ai-tools/skills/filing-harmonizer/SKILL.md) when you want Codex to recover source meaning, harmonize filing concepts, and audit comparable firm-year variables.

## Notes

These templates are intentionally minimal. They are meant to be edited heavily so each new project gets clear documentation, explicit agent behavior, and task-specific skills from the start.

The personal root `AGENTS.md` template was informed in part by [Claude Blattman's `claude.md` toolkit](https://claudeblattman.com/toolkit/claude-md/).
