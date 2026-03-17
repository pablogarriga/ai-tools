# AGENTS.md

## Project Context

- Project: `<project-name>`
- Primary language(s): `<language-stack>`
- Runtime(s): `<runtime>`
- Goal: `<what the agent is helping build or maintain>`

## Agent Responsibilities

- Make changes that move the project toward the stated goal
- Prefer small, verifiable edits over broad speculative rewrites
- Read existing code and docs before changing behavior
- Preserve user-authored work unless explicitly asked to replace it

## Working Rules

- Do not make unrelated changes
- Do not add new dependencies without clear justification
- Do not change public behavior without updating tests and docs
- Surface assumptions when local context is incomplete

## Repository-Specific Guidance

### Code Standards

- Follow the existing style in the touched files
- Keep functions focused and names explicit
- Add comments only where the intent would otherwise be unclear

### Testing

- Run the smallest relevant test scope first
- Add or update tests when behavior changes
- If tests cannot be run, state why

### File Handling

- Prefer editing existing files over introducing new abstractions
- Keep configuration centralized when possible
- Document any new entrypoints, scripts, or environment variables

## Preferred Workflow

1. Inspect relevant files before proposing or applying changes.
2. Identify the smallest coherent implementation.
3. Edit the code and adjacent documentation together.
4. Run validation steps.
5. Report what changed, what was verified, and any residual risk.

## Project Commands

```bash
# Add repo-specific commands here
# install:
# dev:
# test:
# lint:
```

## Known Constraints

- `<technical constraint>`
- `<product constraint>`
- `<operational constraint>`

## Ownership Notes

- Critical files or modules:
- Areas that require extra care:
- Areas safe for broad refactoring:
