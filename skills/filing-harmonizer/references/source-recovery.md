# Source Recovery

Use this guide when the raw filing data do not come with a complete account catalog or when the available dictionary is too thin to support a reliable mapping.

## Objective

Recover the meaning of source variables and the relationship among filing fields well enough to build an auditable harmonized crosswalk.

## Priority Order

1. Official filing instructions.
2. Official blank forms in PDF or HTML.
3. Regulator or tax authority manuals and guidance pages.
4. Machine-readable catalogs or dictionaries.
5. Archived versions of the same materials for adjacent years.
6. Legacy scripts or prior builds.
7. Secondary descriptions only as a last resort.

## Procedure

1. Inventory what is missing.
   Record whether the missing object is an account label list, a layout dictionary, a filing guide, or a full regime description.

2. Search by regime, not just by year.
   Filing materials are often reused across multiple years. If the year-specific form is missing, search adjacent years with the same form family first.

3. Reconstruct the account hierarchy.
   Distinguish leaf accounts, subtotals, informative-only rows, and summary totals. Do not treat every numeric field as additive source material.

4. Record sign conventions directly from the form language.
   Flag rows labeled with explicit negative conventions such as `(-)`, contra-account language, credits, discounts, returns, or accumulated depreciation.

5. Compare alternative documents against the raw data.
   Confirm that the codes and labels found in PDFs or manuals actually appear in the source files. If they do not, document the mismatch instead of forcing the mapping.

6. Produce a regime note.
   For each regime, summarize:
   - source files covered,
   - documentation found,
   - anchor accounts used to identify the regime,
   - unresolved ambiguities,
   - likely implications for comparability.

## Common Failure Modes

- Assuming a subtotal is the right empirical concept.
- Treating informative rows as balance-sheet or income-statement accounts.
- Missing negative sign conventions embedded in the label text.
- Mapping adjacent-year forms together without checking whether labels changed meaning.
- Confusing tax-base concepts with book-income concepts.
