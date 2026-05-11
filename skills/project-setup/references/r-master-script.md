# R Master Script Pattern

Use this reference when setting up or reorganizing an R repo. Also read `script-structure.md` first for the general script standards.

The master script should be an empirical control panel: package loading, paths, switches, and execution order should be visible without chasing hidden routing layers.

## Template

```r
# Title: [Project title]
# Descr.: Sets up environment and runs the analysis pipeline
# Auth.: [Name]
# Date: [YYYY-MM-DD]

# Setup ----

rm(list = ls())

library(here)
library(readr)
library(dplyr)
library(tidyr)
library(purrr)

# Project switches ----

rebuild_data <- TRUE
run_main_results <- TRUE
run_robustness <- TRUE
export_outputs <- TRUE

# Directory paths ----

path_repo <- here::here()
path_data_raw <- "[absolute/path/to/raw/data]"
path_data_analysis <- file.path(path_repo, "data", "analysis")
path_code <- file.path(path_repo, "code")
path_output <- file.path(path_repo, "output")
path_logs <- file.path(path_repo, "logs")

# Run scripts ----

# Data preparation
if (rebuild_data) {
    source(file.path(path_code, "02_clean_data.R"))
    source(file.path(path_code, "03_build_analysis_data.R"))
}

# Estimation and result export
if (run_main_results) {
    source(file.path(path_code, "04_main_results.R"))
}

if (run_robustness) {
    source(file.path(path_code, "05_robustness_checks.R"))
}

if (export_outputs) {
    source(file.path(path_code, "06_export_tables_figures.R"))
}
```

## Adaptation Rules

- Use section headers with `# Section ----`.
- Keep package loading, paths, switches, and execution order directly visible.
- Prefer direct `source(file.path(...))` calls in execution order over a custom routing function.
- Define raw-data paths plainly. If raw data live outside the repo, record the location expectation in `README.md` and `AGENTS.md`.
- Use `here::here()` only for the repo root when that fits the existing workflow. Do not add extra path-discovery machinery by default.
- Keep child scripts easy to run interactively in RStudio.
- Put child-script run switches in the child scripts when the master sources all children directly.
- Use objects such as `data_*`, `out_*`, and `fun_*` when consistent with the repo's style.
