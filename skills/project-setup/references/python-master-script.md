# Python Master Script Pattern

Use this reference when setting up or reorganizing a Python analytical repo. Also read `script-structure.md` first for the general script standards.

The master script should be an empirical control panel: imports, configuration, paths, run switches, stable file locations, and execution order should be visible without chasing hidden routing layers. Child modules or scripts should assume the master has configured the run and should focus on one analytical task.

## Template

```python
"""Set up and run the analysis pipeline."""

from pathlib import Path

from scripts.clean_data import clean_data
from scripts.build_analysis_data import build_analysis_data
from scripts.main_results import run_main_results
from scripts.robustness_checks import run_robustness_checks
from scripts.export_outputs import export_outputs


# Project switches
REBUILD_DATA = True
RUN_MAIN_RESULTS = True
RUN_ROBUSTNESS = True
EXPORT_OUTPUTS = True

# Directory paths
PATH_REPO = Path(__file__).resolve().parent
PATH_DATA_RAW = Path("[absolute/path/to/raw/data]")
PATH_DATA_ANALYSIS = PATH_REPO / "data" / "analysis"
PATH_CODE = PATH_REPO / "scripts"
PATH_OUTPUT = PATH_REPO / "output"
PATH_LOGS = PATH_REPO / "logs"

# Stable file locations
FILE_PANEL = PATH_DATA_ANALYSIS / "panel.parquet"
FILE_ANALYSIS = PATH_DATA_ANALYSIS / "analysis.parquet"


def main() -> None:
    """Run the pipeline in visible order."""
    if REBUILD_DATA:
        clean_data(
            path_data_raw=PATH_DATA_RAW,
            file_panel=FILE_PANEL,
        )
        build_analysis_data(
            file_panel=FILE_PANEL,
            file_analysis=FILE_ANALYSIS,
        )

    if RUN_MAIN_RESULTS:
        run_main_results(
            file_analysis=FILE_ANALYSIS,
            path_output=PATH_OUTPUT,
        )

    if RUN_ROBUSTNESS:
        run_robustness_checks(
            file_analysis=FILE_ANALYSIS,
            path_output=PATH_OUTPUT,
        )

    if EXPORT_OUTPUTS:
        export_outputs(path_output=PATH_OUTPUT)


if __name__ == "__main__":
    main()
```

## Adaptation Rules

- Use `main.py`, `run_all.py`, or the repo's existing top-level entry point.
- Keep imports, configuration, paths, run switches, stable file locations, and execution order directly visible in the master script.
- Prefer direct function calls in execution order over a custom routing function or dynamic script discovery.
- Use `pathlib.Path` for paths unless the repo already follows another consistent pattern.
- Define raw-data paths plainly. If raw data live outside the repo, record the location expectation in `README.md` and `AGENTS.md`.
- Do not add fallback path discovery, environment probing, or config-file machinery unless the repo already uses it or the task explicitly requires it.
- Keep child modules focused on one step: source import, data cleaning, variable construction, estimation, validation, or output export.
- Pass paths and stable file locations into child functions, or import them from one small local config module if that is already the repo pattern. Do not let every child module rediscover the repo root.
- Do not repeat package imports that only support setup, routine folder creation, or run-routing logic in every child module.
- Keep local empirical choices near the code that uses them, such as sample restrictions, year windows, classifications, model formulas, or output-specific formatting.
- Keep input existence checks in the child module that consumes the file, for example checking `file_analysis.exists()` before reading it.
- Document in `README.md` and `AGENTS.md` whether child modules should be run through the master or interactively only after the master setup has been loaded.
