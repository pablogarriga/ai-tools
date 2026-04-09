# AGENTS.md

## Project Context

- Project: `<project-name>`
- Workflow: single-source research pipeline
- Primary language(s): `<R / Python / Stata / mixed>`
- Main entry point: `code/00_master.R`
- Goal: `<what the agent is helping build, clean, estimate, or maintain>`

## Repository Map

- `code/` owns data preparation, estimation, and figure/table construction.
- `data/raw/` owns original inputs and should remain as close as possible to the source files.
- `data/analysis/` owns cleaned and intermediate datasets reused across steps.
- `output/` owns rebuildable analytical products, including figures and tables.
- `logs/` owns workflow memory such as session notes, todo lists, lessons, handoffs, and verification records.
- `skills/` stores optional repo-local skills for recurring agent tasks.

## Working Rule

Treat the repository as an empirical workflow:

1. raw inputs enter through `data/raw/`
2. cleaned or harmonized data are written to `data/analysis/`
3. scripts in `code/` construct variables, estimate specifications, and generate figures/tables
4. final outputs are written to `output/`
5. progress, decisions, and checks are recorded in `logs/`

## Agent Priorities

- Optimize for reproducibility and clarity over speed.
- Prefer small, verifiable edits over broad speculative rewrites.
- Read the existing code and documentation before changing behavior.
- Preserve user-authored work unless explicitly asked to replace it.
- Keep the repository understandable for a human collaborator working without AI support.

## Communication Style

- Write like an empirical economist, not like a software engineer.
- Use familiar research language: `harmonize`, `construct`, `reweight`, `benchmark`, `specification`, `sensitivity check`, `replication`, `figure`, and `table`.
- Describe work in terms of data preparation, variable construction, estimation, and result comparison.
- Avoid developer jargon when a simpler empirical term exists. Prefer `reorganize the weighting pipeline` over `refactor`, and `country-specific preparation do-file` over `country wrapper`.
- Be precise about what changes in the empirical object, what identifying assumption is being used, and what the robustness comparison is testing.

## Execution Conventions

- Use `code/00_master.R` as the default entry point unless the task clearly targets one isolated script.
- Keep shared helper functions in `code/01_utils.R`.
- Keep data cleaning and harmonization logic in `code/02_clean.R`.
- Keep final dataset construction, summary outputs, and figure/table inputs in `code/03_build.R`.
- Do not overwrite raw source files in `data/raw/`.
- Do not treat `output/` as source data.
- Keep project documentation in `README.md` and workflow instructions in `AGENTS.md`.
- Record significant session progress in `logs/session-log.md`. Add other files under `logs/` only when they clearly support the workflow.

## R Conventions

- Assume R is usually run interactively in `RStudio` or from `VSCode` attached to a live R session.
- Prefer a master-script-first structure for analysis projects, with child scripts sourced in order.
- Keep the master script focused on session setup, paths, package loading, and execution order.
- Put reusable helper functions and plotting defaults in `code/01_utils.R` or another sourced utilities script.
- Keep child scripts single-purpose, sectioned, and easy to run incrementally.
- Use top-of-script switches for optional outputs, revisions, expensive steps, or local-data branches during interactive work.
- Prefer readable, staged transformations with explicitly named intermediate objects over deeply nested pipelines.
- Keep script-specific helper functions local unless they are reused across scripts.
- Use consistent object prefixes to signal purpose, such as `fun_` for functions, `data_` for datasets, `tab_` for tables, `fig_` for figures, and `out_` for final or exported outputs.
- Treat validation tables and diagnostic summaries as part of the workflow, not as afterthoughts.
- Default to tidyverse-style data manipulation and `ggplot2` plotting unless the task clearly calls for another approach.
- If performance matters, use `data.table` selectively for heavy wrangling while preserving the same staged and readable structure.

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
