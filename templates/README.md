# <Project Name>

Short description of the project, the question it answers, and why it exists.

## Project Overview

- Research question or core problem:
- Main data source:
- Main outputs:
- Current project status:

## Repository Structure

This project is organized as a single-source research pipeline. Raw data enter through `data/raw`, are cleaned into `data/analysis`, are processed by scripts in `code/`, generate final exhibits in `output/fig_tab`, and are documented operationally in `logs/`.

```text
project-name/
├── .editorconfig
├── README.md
├── AGENTS.md
├── skills/
│   ├── README.md
│   └── template/
│       └── SKILL.md
├── code/
│   ├── 00_master.R
│   ├── 01_utils.R
│   ├── 02_clean.R
│   └── 03_build.R
├── data/
│   ├── raw/
│   └── analysis/
├── output/
│   └── fig_tab/
└── logs/
    └── session-log.md
```

## Folder and File Roles

- `.editorconfig`: lightweight editor-level defaults for indentation, line endings, and trailing whitespace.
- `README.md`: human-facing documentation for the project. It explains the research question, data source, workflow, structure, and run instructions.
- `AGENTS.md`: AI-facing workflow instructions. It defines conventions, guardrails, logging rules, and how agents should operate in the repository.
- `skills/`: optional reusable instructions for recurring AI-supported tasks. This supports the workflow but is not part of the analytical pipeline itself.
- `code/`: the execution layer of the project.
- `code/00_master.R`: the main entry point. It orchestrates the project in the intended order.
- `code/01_utils.R`: shared helper functions used across scripts.
- `code/02_clean.R`: reads the raw source files, cleans and harmonizes variables, applies restrictions, and writes reusable analysis-ready datasets.
- `code/03_build.R`: builds final analytical outputs from the cleaned data, including summary measures and inputs for figures or tables.
- `data/raw/`: original source files. This folder should stay as close as possible to the source data.
- `data/analysis/`: intermediate or cleaned datasets created from `data/raw/` and reused downstream.
- `output/`: generated results that can be rebuilt from code.
- `output/fig_tab/`: final figures and tables for papers, slides, or notes.
- `logs/`: workflow memory, including session notes, todo lists, handoffs, lessons, and validation records. At minimum, keep a reverse-chronological `logs/session-log.md`.

## Design Rule

- `data/` stores inputs and reusable intermediate datasets.
- `code/` transforms those datasets.
- `output/` stores rebuildable products.
- `logs/` stores the operational memory of the project.

## Typical Workflow

1. Place original source files in `data/raw/`.
2. Run `code/00_master.R` to execute the project in the intended order.
3. Let the cleaning stage write reusable datasets to `data/analysis/`.
4. Let the build stage write final outputs to `output/fig_tab/` or other output folders as needed.

## How to Run

From R:

```r
source("code/00_master.R")
```

From the shell:

```bash
Rscript code/00_master.R
```

If the project does not use R, replace these commands with the actual entry point while preserving the same folder logic.

## Working Conventions

- Keep the repository structure simple and readable.
- Prefer one clear master script over many ad hoc entry points.
- Keep raw data separate from cleaned data and from rebuildable outputs.
- Document significant session progress in `logs/session-log.md`.
- Update this file and `AGENTS.md` when the workflow or structure changes materially.
- Keep `.editorconfig` aligned with any explicitly documented formatting rules.

## Conventions

- Naming conventions: use lower case for file and folder names.
- Naming conventions: use `-` as a space when two words are needed, for example `dom-rep`.
- Naming conventions: use `_` to separate concepts within a file name, for example `dom-rep_2024.png`.

## Open Questions

- Unknown or risky area 1
- Unknown or risky area 2
