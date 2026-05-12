# Script Structure Pattern

Use this reference when creating or reorganizing scripts in analytical repos, regardless of language. The goal is code that is easy to inspect interactively, easy to run from a master script, and clear about the empirical object being constructed.

## General Standards

- Keep code linear and readable.
- Prefer direct data-construction code over extra abstraction layers.
- Keep helper functions lightweight and near the top of the script when they are only relevant to that script.
- Do not introduce a helper merely to avoid a few repeated lines if it hides a substantive operation.
- Introduce relevant code blocks with a short comment explaining what the block is doing.
- Keep child scripts single-purpose and easy to rerun after the master setup has established packages, paths, switches, and shared file locations.
- Do not duplicate project setup, fallback path logic, package loading, routine folder creation, or run routing across child scripts.
- Avoid hidden execution-routing layers when the same sequence can be written directly in the master script.
- Use spaces, not tabs, with 4 spaces per indentation level.
- Prefer staged transformations with explicitly named intermediate objects over deeply nested pipelines.

## Master Script Standards

Treat master scripts as empirical control panels. Package loading, folder paths, sample or country switches, and execution order should be visible in the master script.

- Make the master script the default place for environment setup, package loading, stable paths, run switches, stable file locations, logging setup, and ordered calls to child scripts.
- Keep run switches as direct assignments near the top.
- Keep workspace cleanup simple and visible.
- Preserve only the control objects needed by the run.
- Define folder paths directly in the master script.
- Do not add fallback path discovery, override-preserving switch logic, or hidden routing layers unless the task explicitly requires that flexibility.
- Source or run child scripts in visible execution order.
- If the master script calls all child scripts directly, keep project-level run switches in the master and put only genuinely script-local switches in child scripts.
- Do not replace visible path objects with a bundled `paths` list unless the existing workflow already uses that pattern consistently.

## Analysis Script Standards

Write analysis scripts as direct empirical construction scripts:
- load inputs
- define the sample, years, countries, or other target scope
- construct variables or outputs
- write generated files

Child scripts should focus on the empirical or analytical task. Keep local choices such as samples, years, countries, classifications, model definitions, and output-specific formatting near the block that uses them. Keep input existence checks in the child script that consumes the file. These checks verify the empirical pipeline; they are not setup boilerplate.

Prefer explicit repeated construction blocks over generic helpers when the helper would hide a substantive choice, such as the weighting variable, sample restriction, classification, grouping variable, or identifying comparison.

Preserve source-standard classifications in analysis outputs unless the specification explicitly redefines the empirical object. Do not round analysis outputs by default; keep full precision in CSVs and apply rounding in figure/table scripts.

Put final-stage display choices, such as regrouping regions or formatting labels, in figure/table scripts rather than upstream analysis scripts.

## Object Naming

Use stable prefixes when they fit the language and existing repo style:
- `path_` for directory paths
- `data_` for datasets
- `fun_` for helper functions
- `out_` for exported or final output objects

When a shared family repeats across related variables or outputs, put the repeated family first when useful for readability and searchability:
- `path_project`, `path_code`
- `data_raw`, `data_clean`
- `industry_6digits`, `industry_4digits`
- `out_concentration_revenue`, `out_concentration_wagebill`
