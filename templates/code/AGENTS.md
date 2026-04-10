# AGENTS.md

## Code Subtree Context

- Scope: `code/`
- Purpose: scripts that prepare data, run estimations, and build outputs
- Main entry point: `code/00_master.R`
- Primary rule: follow the repository root `AGENTS.md`, then apply these narrower code-specific instructions

## Code Responsibilities

- Keep scripts in `code/` single-purpose and easy to run in sequence.
- Prefer explicit script order over hidden side effects.
- Treat shared helpers as reusable utilities, not one-off snippets.
- Keep script names stable and descriptive.

## Execution Order

- `code/00_master.R` should orchestrate the project.
- `code/01_utils.R` should hold shared helpers and defaults.
- `code/02_clean.R` should read raw inputs and produce analysis-ready data.
- `code/03_build.R` should produce summary objects, figures, and tables.

## Local Editing Rules

- Do not write outputs back into `code/` unless the file is itself a script or helper.
- Keep code changes localized to the smallest script that owns the behavior.
- If a change affects the pipeline order, update the master script and the documentation together.
- When a script needs special setup, document it near the top of that script.

## Validation

- Prefer running the narrowest script or check that exercises the changed code path.
- Confirm outputs land in `data/analysis/`, `output/`, or the expected downstream folder.
- If validation is skipped, note the reason in `logs/session-log.md` or the relevant task note.
