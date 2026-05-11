# Audit Checklist

Use this checklist after the first crosswalk exists and again after the first panel build.

## Identifier Audit

- Confirm the intended panel unit.
- Standardize tax IDs, filing IDs, and firm IDs before deduplication.
- Check for year-specific format changes, leading-zero issues, and mixed identifier systems.
- Define the rule for duplicate firm-year filings and document how ties are resolved.

## Crosswalk Audit

- State the empirical concept behind each harmonized variable.
- List the source accounts used in each regime.
- Distinguish directly observed accounts from residual constructions or proxies.
- Mark each regime-year as supported, weakly supported, or unsupported.

## Sign and Aggregation Audit

- Check returns, discounts, credits, contra-assets, accumulated depreciation, and final inventories.
- Confirm whether expense rows are stored as positive values, signed values, or mixed values.
- Remove or flag subtotal and informative rows unless they are intentionally part of the concept.

## Source-Anomaly Audit

- Flag impossible source cells relative to adjacent years or the firm's other accounts.
- Save exclusions in a durable output with a reason code.
- Do not silently overwrite filing anomalies.

## Comparability Audit

- Mark the years where the source regime changes.
- State whether each variable is fully comparable, partially comparable, or broken across those changes.
- Separate support problems from concept changes.

## Documentation Outputs

Produce or update:
- a regime timeline,
- a variable crosswalk,
- a support matrix,
- an audit log,
- a table of exclusions or unresolved anomalies.
