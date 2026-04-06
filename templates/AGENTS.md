# AGENTS.md

## Project Context

- Project: `<project-name>`
- Workflow: single-source research pipeline
- Primary language(s): `<R / Python / Stata / mixed>`
- Main entry point: `code/00_master.R`
- Goal: `<what the agent is helping build, clean, estimate, or maintain>`

## Repository Map

- `code/` owns transformation logic.
- `data/raw/` owns original inputs and should remain as close as possible to the source files.
- `data/analysis/` owns cleaned and intermediate datasets reused across steps.
- `output/` owns rebuildable analytical products, including figures and tables.
- `logs/` owns workflow memory such as session notes, todo lists, lessons, handoffs, and verification records.
- `skills/` stores optional repo-local skills for recurring agent tasks.

## Working Rule

Treat the repository as a pipeline:

1. raw inputs enter through `data/raw/`
2. cleaned or staged data are written to `data/analysis/`
3. scripts in `code/` produce analytical outputs
4. final figures and tables are written to `output/fig_tab/`
5. work progress and decisions are recorded in `logs/`

## Agent Priorities

- Optimize for reproducibility and clarity over speed.
- Prefer small, verifiable edits over broad speculative rewrites.
- Read the existing code and documentation before changing behavior.
- Preserve user-authored work unless explicitly asked to replace it.
- Keep the repository understandable for a human collaborator working without AI support.

## Execution Conventions

- Use `code/00_master.R` as the default entry point unless the task clearly targets one isolated script.
- Keep shared helper functions in `code/01_utils.R`.
- Keep cleaning and harmonization logic in `code/02_clean.R`.
- Keep final dataset construction, summary outputs, and figure/table inputs in `code/03_build.R`.
- Do not overwrite raw source files in `data/raw/`.
- Do not treat `output/` as source data.
- Keep project documentation in `README.md` and workflow instructions in `AGENTS.md`.
- Record significant session progress in `logs/session-log.md`. Add other files under `logs/` only when they clearly support the workflow.

## Editing Rules

- Do not make unrelated changes.
- Do not add new dependencies without clear justification.
- Update nearby documentation when workflow, file structure, or public behavior changes.
- Keep functions focused and names explicit.
- Add comments only where the intent would otherwise be unclear.
- Use spaces, not tabs, for indentation.
- Indentation should increase in steps of 4 spaces per nesting level: 4 for the first level, 8 for the second, 12 for the third, and so on.
- Preserve existing formatting only in generated or third-party material that should not be hand-reformatted.

## Validation

- Run the smallest relevant validation step first.
- Confirm that outputs land in the expected folders.
- If a task changes behavior, update or add the relevant checks.
- If validation cannot be run, state why and identify the residual risk.

## Minimal Structure Rule

When adding or modifying files, preserve this separation:

- inputs in `data/`
- transformation logic in `code/`
- rebuildable products in `output/`
- workflow memory in `logs/`

## Known Constraints

- `<data access constraint>`
- `<runtime constraint>`
- `<operational constraint>`
