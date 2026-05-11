---
name: filing-harmonizer
description: Build or audit a comparable firm-year panel from tax forms, balance sheets, regulatory filings, or related administrative accounts across multiple years and filing regimes. Use when Codex needs to recover source meaning from catalogs or filing guides, detect regime changes, harmonize source accounts into empirical variables, assess comparability across years, document departures from source logic, or run sanity checks on aggregate panel series.
---

# Filing Harmonizer

## Overview

Construct comparable firm-year variables from filing-based source data without assuming that layouts, account meanings, identifiers, or empirical concepts stay fixed over time. Separate source recovery, regime detection, harmonization, comparability assessment, and diagnostics.

## Required Inputs

- Raw source files or a clear inventory of where they live.
- The target panel unit, usually firm-year.
- The target harmonized variables or empirical concepts.

## Optional Inputs

- Source catalogs, dictionaries, or codebooks.
- Filing instructions, PDF forms, regulator guidance, or tax authority manuals.
- A legacy script or prior build to use as a baseline.
- Known regime breaks, identifier rules, or country-specific accounting notes.

## Workflow

1. Inspect the source before proposing mappings.
   Identify file families, year coverage, record unit, identifier fields, account fields, and whether the source is already long or still in wide filing layout.

2. Build a regime map.
   Group years into filing regimes based on layout shape, anchor account codes, recurring labels, source documentation, and known institutional changes. Treat regime detection as an empirical object, not a housekeeping detail.

3. Recover source meaning when catalogs are incomplete.
   If catalogs or dictionaries are missing, reconstruct account meaning from filing PDFs, official instructions, regulator manuals, tax authority guides, and archived dictionaries. Prefer primary sources. Record unresolved ambiguities explicitly instead of guessing. See [references/source-recovery.md](./references/source-recovery.md).

4. Define harmonized variables conceptually before coding them.
   For each target variable, state what the empirical concept is, what source accounts feed it, whether signs need adjustment, and whether the result is fully comparable, partially comparable, or not comparable across regimes.

5. Stage the raw data into a long firm-account table.
   Preserve year, firm identifiers, filing identifiers, regime markers, account code, account label, raw value, and source file metadata. Keep staging separate from harmonization so mappings can be revised without re-importing the raw archives.

6. Map source accounts into harmonized variables by regime.
   Use regime-specific crosswalks rather than one universal mapping. Keep country-specific rules explicit. Pay special attention to inventories, contra-asset accounts, depreciation, tax credits, informative-only rows, and subtotal lines.

7. Audit identifiers, duplicates, and support.
   Standardize identifiers, define the deduplication rule, and build a support matrix showing which variables are supported, weakly supported, or unsupported in each regime-year. See [references/audit-checklist.md](./references/audit-checklist.md).

8. Run aggregate diagnostics after the panel exists.
   Check time series of firm counts and aggregate totals for sales, materials, wage bill, capital, and other core variables. Inspect structural breaks at known regime changes and review key ratios that should be interpretable over time. See [references/diagnostics.md](./references/diagnostics.md).

9. Document every substantive deviation from source logic.
   Keep an audit log of mapping choices, sign decisions, exclusions, weak-support years, and changes relative to any baseline build. Save durable diagnostics outputs so later reviews can reproduce the judgment.

## Parallel Regime Analysis

Use regime-level delegation only when the user explicitly allows subagents or parallel agent work.

When delegation is allowed and there are multiple materially different regimes:
- Split work by regime or form family, not by single year.
- Give each subagent ownership of one regime note or crosswalk artifact.
- Use separate subagents for source-document recovery or post-build diagnostics only when those tasks are meaningfully independent.
- Keep final integration with the main agent so one place owns the merged crosswalk, comparability judgment, and final panel outputs.

Do not delegate when:
- there is only one regime,
- the task is only extending a solved regime by a few years, or
- the subagents would need to edit the same files.

## Output Expectations

Return or update the following objects as appropriate:
- a source inventory and regime timeline,
- a harmonized variable crosswalk,
- a support or comparability matrix by regime-year,
- an audit log of substantive choices and exclusions,
- the staged long account-level data or the final panel build,
- aggregate diagnostics tables or plots,
- a short statement of what remains uncertain.

## References

- [references/source-recovery.md](./references/source-recovery.md)
- [references/audit-checklist.md](./references/audit-checklist.md)
- [references/diagnostics.md](./references/diagnostics.md)
