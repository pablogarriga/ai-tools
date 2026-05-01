# AGENTS.md

## Who I Am

I use AI as a working partner across `[research / writing / coding / analysis / operations / other]`.

I am comfortable working with `[technical tools / non-technical workflows / mixed environments]` and expect agents to be competent, direct, and efficient. I do not need hand-holding, but I do want clear reasoning when tradeoffs matter or when a change has risk.

## My Work and How I Use AI

- `[primary use case 1]`
- `[primary use case 2]`
- `[primary use case 3]`
- `[primary use case 4]`
- `[primary use case 5]`

Default to being a strong generalist. Match the response style to the task instead of forcing a coding-only workflow onto everything.

## My Skill Level

Use this as calibration for explanation depth, tooling choices, and how much implementation scaffolding to provide.

- `[tool / language / domain 1]`: `[beginner / intermediate / expert]`
- `[tool / language / domain 2]`: `[beginner / intermediate / expert]`
- `[tool / language / domain 3]`: `[beginner / intermediate / expert]`
- `[tool / language / domain 4]`: `[beginner / intermediate / expert]`
- `[tool / language / domain 5]`: `[beginner / intermediate / expert]`

## How I Prefer to Work

- Be concise by default. Expand only when the complexity of the task warrants it.
- Explain reasoning when it changes a recommendation, a design decision, or a risky action.
- Prefer making progress over prolonged theorizing.
- Ask before broad, destructive, or hard-to-reverse changes.
- Preserve my work and intent, even when the current state is imperfect.
- When something is ambiguous, resolve what you can from the environment before asking me.
- Avoid unrelated edits.
- Validate the thing you changed, and if direct validation is not possible, state the residual risk.

## Communication and Decision Rules

- Start by orienting yourself before editing anything.
- Read the relevant files first and infer the local pattern before proposing a new one.
- Some directories or files may be system-managed, cached, generated, or sensitive, so treat them accordingly.
- If a task has a dominant professional context, write in that idiom instead of default software-engineering language.
- Describe work in the vocabulary that best matches the task, such as analysis, operations, editing, data preparation, estimation, debugging, or document revision.
- Avoid jargon when a simpler term exists.
- Be specific about what you changed, what you checked, and what remains uncertain.
- Report tradeoffs plainly. Do not soften important risks with vague language.
- When there is a smallest viable edit that solves the problem, prefer it over a broad rewrite.
- If a task touches multiple possible approaches, pick one, explain why briefly, and proceed unless the decision is genuinely high impact.

## Task-Specific Conventions

Apply the following conventions only when they fit the task. These are conditional defaults, not global rules.

### Empirical and Analytical Work

- Write like an empirical researcher rather than like a software engineer.
- Describe work in terms of data preparation, variable construction, estimation, result comparison, and robustness checks.
- Be precise about what changes in the empirical object, what identifying assumption is being used, and what the comparison is testing.
- Be explicit about provenance, restrictions, transformations, and validation.

### Script Structure Standards

- Keep code linear and readable.
- Prefer direct data-construction code over unnecessary abstraction layers.
- Use explicit section headers to mark the main landmarks in a file.
- Introduce relevant code blocks with a short explanatory comment describing what the block is doing.
- Prefer a readable top-level orchestration script that makes package loading, directory paths, and execution order easy to inspect.
- Keep child scripts single-purpose and easy to rerun independently.
- Keep helper functions lightweight and near the top of the script when they are only relevant to that script.

### Coding Style Conventions

- Make scripts understandable for a human collaborator working without AI support.
- Use spaces, not tabs, for indentation.
- Indentation should increase in steps of 4 spaces per nesting level: 4 for the first level, 8 for the second, 12 for the third, and so on.
- Prefer readable sequential transformations with explicitly named intermediate objects over deeply nested pipelines.
- When a shared family repeats across related variables or outputs, put the repeated family first when that improves readability and searchability. Example: `sales`, `sales_log`, `sales_adj`.

## How to Use This Template

- Fill in the placeholders with your own work profile, tool calibration, and preferences.
- Keep this file at the personal or machine level as your default instruction layer.
- Add repo-level `AGENTS.md` files for project-specific rules.
- Add narrower subtree-level `AGENTS.md` files only when a subdirectory needs tighter instructions than the repo root.
