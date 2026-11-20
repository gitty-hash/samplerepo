---
name: sample-invoice-checker
title: Sample Invoice Checker
description: Synthetic skill that finds duplicate invoice IDs and calculates a payable total for a small invented invoice file.
version: 0.2.0
invocation: /sample-invoice-checker
tools: [file_read, file_write]
---
# Sample Invoice Checker

This skill is a synthetic Git import and pre-run demonstration.

## Inputs
- Read input/invoices.csv from the assigned dataset.
- For a standalone manual example, use [the sample invoices](examples/invoices.csv).
- CSV fields: invoice_id, vendor, amount_usd.

## Method
- Read rows in their original order and validate that amounts are numeric and nonnegative.
- Treat invoice_id as the duplicate key. Count the first occurrence once and exclude later occurrences with that ID.
- If a repeated ID has conflicting vendor or amount values, report the conflict for human review rather than silently choosing a new value.
- List duplicate IDs, excluded amounts and the total payable for unique invoice IDs.
- Group the unique invoices by vendor and report each vendor subtotal.
- Write the report using [the report template](templates/invoice_report.md).
- Compare the manual example with [the expected result](references/expected_result.md).

## Done when
- Create `out/invoice_report.md` containing the input count, unique invoice count, duplicate IDs, excluded amount, payable total and any validation problems.
- For the provided sample, report 4 input rows, 3 unique invoices, duplicate TEST-001, 120.00 USD excluded, and 250.00 USD payable.

- Include vendor subtotals: Demo Vendor A 120.00 USD and Demo Vendor B 130.00 USD for the sample.

## Standards
- All inputs are synthetic. Preserve invoice identifiers exactly.
- Show USD amounts to two decimal places.
- Do not invent invoices or silently ignore validation errors.
- Do not contact external services or request credentials.
