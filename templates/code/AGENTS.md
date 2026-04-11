# AGENTS.md

## Code Subtree Context

- Scope: `code/`
- Purpose: scripts that prepare data, run estimations, and build outputs
- Main entry point: `code/00_master.R`
- Primary rule: follow the repository root `AGENTS.md`, then apply these narrower code-specific instructions

## Goal

Write pipeline scripts that are:

- easy to run end to end from `code/00_master.R`
- easy to run partially during interactive editing in RStudio
- easy to modify by toggling small, independent sections

## Script Structure Standards

For active pipeline scripts in `code/`:

1. Keep one clear orchestration entry point used by the master script.
2. Keep reusable helpers in named functions near the top. Use `01_utils.R` for very general utilities, but feel free to define script-specific helpers in the same file if they are only relevant there.
3. If interactive iteration is expected, provide a manual-run block with switches.
4. For scripts designed for manual editing, prefer inline procedural code over nested helper functions. Put all logic for a section directly in its `if` block so it is easy to find and modify without jumping between function definitions.
5. Avoid extra abstraction layers for single-purpose scripts; keep the data flow linear and visible.
6. Use explicit section headers with the style `# Section ----`.

Preferred section pattern for interactively edited scripts:

- `# Setup ----` for colors, themes, and simple utilities
- `# Code switches ----` for all booleans, defaulting to `FALSE`
- `# Setup process ----` for loading data, guarded by `if (isTRUE(setup))`
- `# Figure 1 ----`, `# Figure 2 ----`, etc. for complete chunks guarded by `if (isTRUE(run_fig_*))`
- `# Pipeline entry point ----` for the canonical `run_*()` function used by the master script

## Manual-Run Conventions

- Add top-level booleans for switches, starting with `setup <- FALSE` and per-chunk switches such as `run_fig_* <- FALSE`.
- Place all code switches together near the top in a dedicated `# Code switches ----` section.
- Guard the setup block with `if (isTRUE(setup)) { ... }`.
- Guard each chunk, figure, or table block with `if (isTRUE(run_fig_*)) { ... }`.
- Put the complete logic for each chunk inline within its `if` block.
- Print written output paths when chunks complete, for example `cat("Written:", output_path, "\n")`.
- For the pipeline entry point, duplicate the logic inline and generate all outputs without expecting switches.

## Function Naming Conventions

- Keep helper functions minimal when they are shared across chunks.
- Use `*_setup(...)` for context loaders only if needed and documented.
- Do not use `chunk_*` functions or `run_*_chunks()` orchestrators for manually edited scripts.
- Use `run_<stage>(paths = get_project_paths())` as the canonical master-script entry point.

## Compatibility Requirements

- Do not break the master pipeline contract.
- Keep `run_<stage>(paths = get_project_paths())` available for each stage script.
- Do not require manual switches for master execution paths.
- Avoid duplicate execution paths that accidentally rerun earlier stages.

## Safety and Reproducibility

- Use saved local inputs unless a task explicitly requests new downloads.
- Keep path handling rooted in project helpers, for example `get_project_paths()`.
- Preserve canonical output names unless explicitly asked to change them.
- Keep dependencies lightweight and consistent with existing project usage.

## Validation Expectations for Code Changes

After changing scripts in `code/`:

- run `Rscript code/00_master.R --stage=<stage>` for the touched stage, at minimum
- if orchestration changes were made, run `Rscript code/00_master.R`
- confirm expected writes in `data/analysis/`, `output/`, and `output/fig_tab/` as appropriate
