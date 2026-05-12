---
name: project-setup
description: Structure new or lightly organized repositories around a clear analytical workflow. Use when a user wants to initialize or reorganize a repo's folder structure, code pipeline, README.md, AGENTS.md, or logs for empirical research, data analysis, writing projects, or mixed analytical work. Also use when a user wants to apply conventions from a starter repo without blindly copying template folders or unrelated auxiliary files.
---

# Project Setup

## Overview

Shape the repository around the work it is meant to produce. Treat documentation as support for the workflow, not as the main deliverable. Start by reconstructing the empirical or analytical pipeline from the files that already exist, then make the smallest structural changes that make the pipeline easier to inspect, rerun, and maintain.

## Workflow

1. Inspect the repository before editing anything.
   Look for raw data folders, processed data, code, output tables, figures, manuscripts, slides, logs, and project notes. Check `git status` so existing work is not overwritten or moved accidentally.

2. Infer the project object and pipeline.
   Identify, as far as the repo allows:
   - the question, dataset, or product the repo is organized around
   - the main inputs and outputs
   - the order in which data are prepared, variables are constructed, estimates are produced, and results are exported
   - the scripts or documents that act as entry points
   - any unclear or missing steps in the workflow

3. Design the folder structure around the pipeline.
   Prefer a simple structure that separates inputs, code, outputs, writing, and project records. A typical analytical repo may use:
   - `data/raw/` for source data that should not be modified manually
   - `data/processed/` or `data/derived/` for constructed analysis files
   - `code/`, `scripts/`, or language-specific folders for reproducible code
   - `output/`, `results/`, `figures/`, or `tables/` for generated objects
   - `writing/`, `paper/`, `slides/`, or `docs/` for narrative outputs
   - `logs/session-log.md` for dated work records

   Use the names already present in the repo when they are coherent. Do not rename or move large sets of files unless the user asked for a reorganization and the move is low risk.

4. Get the code pipeline right.
   Prefer a readable top-level orchestration path over scattered one-off scripts. When appropriate, create or update an entry-point script such as `run_all.*`, `main.*`, or a root-level README section that records execution order. Make the sequence explicit:
   - setup and paths
   - data import or cleaning
   - variable construction
   - estimation, analysis, or transformation
   - result export
   - manuscript, deck, or report build steps

   Do not invent commands that are not supported by the repo. If execution is uncertain, document the uncertainty plainly and leave a short verification note.

   Treat the master script or master do-file as the visible control panel for the pipeline. It should own package loading, environment setup, stable paths, run switches, stable file locations, and execution order. Child scripts should assume that setup has already happened and should focus on one analytical task, such as importing a source, constructing variables, estimating results, validating outputs, or exporting tables and figures.

   Do not make every child script a mini-master. Avoid repeated setup blocks, fallback path definitions, package loading, routine folder creation, and hidden run-routing in child scripts unless the repo explicitly needs standalone execution. Keep local empirical choices, such as samples, year windows, classifications, or model definitions, near the code that uses them. Keep input existence checks in the child script that consumes the input, because those checks protect the empirical pipeline rather than configure it.

   Before creating or revising scripts, read `references/script-structure.md` and apply the parts that fit the repo's language and workflow.

   For Stata repos, read `references/stata-master-dofile.md` before creating or revising a master do-file. Use it as a pattern for `01_master.do` or the repo's equivalent top-level pipeline script.

   For R repos, read `references/r-master-script.md` before creating or revising a master script. Use it as a pattern for `01_master.R`, `run_all.R`, or the repo's equivalent top-level pipeline script.

   For Python repos, read `references/python-master-script.md` before creating or revising a master script. Use it as a pattern for `main.py`, `run_all.py`, or the repo's equivalent top-level pipeline script.

   If the repo has multiple valid pipeline layers, such as raw-data construction plus downstream analysis, deck, or reporting workflows, do not force them into one master script. Make the primary pipeline and secondary pipelines explicit, document how they hand off, and keep each layer's entry point readable.

5. Add or update only the default support files that belong.
   Default support files:
   - root `README.md`
   - root `AGENTS.md`
   - `logs/session-log.md`

6. Adapt every file to the actual repo.
   Replace placeholders with project-specific content:
   - project purpose or empirical object
   - directory map
   - pipeline order and entry points
   - important data and output locations
   - run commands, if known
   - validation expectations
   - open questions or missing setup details

7. Preserve existing work.
   If `README.md`, `AGENTS.md`, `logs/`, code folders, or output folders already exist, update them carefully instead of overwriting them wholesale. Do not remove user-authored content without a clear reason. Ask before broad file moves, destructive cleanup, or hard-to-reverse restructuring.

8. Validate the result.
   Check that:
   - the folder structure reflects the actual pipeline
   - README.md instructions match the files and commands that exist
   - AGENTS.md gives repo-specific guidance
   - no unwanted scaffolding was added
   - `git status` shows only intended additions, edits, or moves

## File Guidance

### `README.md`

Write a concise project README that makes the workflow inspectable. Include:
- what the repo is for
- the main inputs and outputs
- the directory structure
- the pipeline order
- whether child scripts should be run through the master script or only after loading master setup
- how to rerun the work, if known
- setup gaps or unresolved questions

### `AGENTS.md`

Write repo-specific instructions for future agents. Include:
- project context
- how the pipeline is organized
- what belongs in the master script versus child scripts
- where raw data, constructed data, code, results, writing, and logs live
- rules for preserving user work
- how to validate analytical changes
- naming, style, or language conventions visible in the repo

### `logs/session-log.md`

Create one reverse-chronological session log when no log exists. Prepend the newest entry first. Use `YYYY-MM-DD HH:MM` headings and concise bullets that record what changed, what was checked, and what remains unresolved.

## Starter Repos

When the user references another repo as a model, treat it as a source of conventions. Borrow structure, naming, and documentation patterns only when they fit the current repo's workflow.

## Output Expectations

After setup or reorganization, report:
- which folders or files were added, updated, or moved
- how the pipeline is now organized
- which conventions from any starter repo were adopted
- which things were intentionally not copied or created
- what validation was performed
- what remains uncertain or needs user judgment
