# Stata Master Do-File Pattern

Use this reference when setting up or reorganizing a Stata repo. Also read `script-structure.md` first for the general script standards.

The goal is a readable master do-file that makes the full analysis order explicit while keeping project-specific setup out of child do-files.

## Structure

A good master do-file should have:
- a short header with title, purpose, author, and date
- setup commands that make reruns clean
- project-level switches for optional steps
- path globals grouped in one place
- stable file-location globals grouped near the path globals when the repo uses them
- a log file in `logs/`
- required package checks
- ordered calls to child do-files
- optional cleanup of intermediate files

Child do-files should not repeat the project setup layer. They should assume the master has already defined paths, switches, package availability, and stable file globals. Their job is to clean sources, construct variables, estimate results, validate outputs, or export tables and figures.

## Template

```stata
* Title: [Project title]
* Descr.: Sets up environment and runs the analysis pipeline
* Auth.: [Name]
* Date: [YYYY-MM-DD]

* Setup
    clear all
    set more off
    cap log close
    cap program drop _all
    cap macro drop _all

    * Project switches
    glo cleanup_intermediates 0
    glo rebuild_data 1

* Directory paths
    if "`c(username)'"=="[username_1]" {
        glo path_repo          "[absolute/path/to/repo]"
        glo path_data_raw      "[absolute/path/to/raw/data]"
        glo path_data_analysis "${path_repo}/data/analysis"
        glo path_code          "${path_repo}/code"
        glo path_output        "${path_repo}/output"
    }

    if "`c(username)'"=="[username_2]" {
        glo path_repo          "[absolute/path/to/repo]"
        glo path_data_raw      "[absolute/path/to/raw/data]"
        glo path_data_analysis "${path_repo}/data/analysis"
        glo path_code          "${path_repo}/code"
        glo path_output        "${path_repo}/output"
    }

    log using "${path_repo}/logs/01_master.log", replace text

* Required packages
    foreach pkg in ftools gtools estout coefplot binscatter {
        capture which `pkg'
        if _rc {
            ssc install `pkg', replace
        }
    }

* Run do-files

    * Data preparation
    if ${rebuild_data} == 1 {
        do "${path_code}/02_clean_data.do"
        do "${path_code}/03_build_analysis_data.do"
    }

    * Estimation and result export
    do "${path_code}/04_main_results.do"
    do "${path_code}/05_robustness_checks.do"
    do "${path_code}/06_export_tables_figures.do"

* Cleanup
    if ${cleanup_intermediates} == 1 {
        foreach file in intermediate_file_1.dta intermediate_file_2.dta {
            capture erase "${path_data_analysis}/`file'"
        }
    }

    log close
```

## Adaptation Rules

- Keep the path block near the top. Add user-specific path blocks when collaborators need different raw-data or repo locations.
- Use globals for stable project paths, switches, and file locations. Avoid scattering absolute paths across child do-files.
- Keep run switches as direct global assignments near the top.
- Number child do-files in execution order when the repo already follows that pattern, for example `01_master.do`, `02_clean_data.do`, `03_build_analysis_data.do`.
- Keep child do-files single-purpose: data cleaning, construction of analysis files, main estimates, robustness checks, output export.
- Do not put `clear all`, `set more off`, `version`, fallback path globals, package installation, or routine `capture mkdir` calls in every child do-file.
- Keep local empirical choices in the child do-file section that uses them, such as sample restrictions, year windows, classifications, or model definitions.
- Keep file existence checks in the child do-file that consumes the file, for example confirming a required constructed dataset exists before `use`.
- Use comments to name workflow stages, not to narrate obvious commands.
- Avoid hidden routing layers. Let the master do-file show the execution order directly.
- Only install packages that are actually used by the repo.
- Do not create routine output folders throughout the pipeline. If the repo needs setup-time folder creation, keep it in the master or document it as a provisioning step.
- Do not silently delete intermediate files. Put cleanup behind an explicit switch.
- Document in `README.md` and `AGENTS.md` whether child do-files should be run through the master or interactively only after the master setup has been loaded.
- If raw data live outside the repo, record that in `README.md` and `AGENTS.md`.
