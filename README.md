# Synthetic EPO skill for Git import testing

All names, invoices and amounts in this repository are invented test data. No API keys, external tools or client material are required.

## Import in the EPO app

1. Open Skill Registry, then Import from Git, then Connect a Git repo.
2. Name: EPO Sample Skills. Repository URL: https://github.com/gitty-hash/samplerepo.git
3. Default branch: qa. Path pattern: skills/*
4. Connect the repo. If the source dropdown does not update, refresh the page and reopen Import from Git.
5. Select qa, then skills/sample-invoice-checker, then Import. Keep the skill key sample-invoice-checker and leave the version label empty.
6. Wait for the import job to succeed. Open the produced version and inspect Files, Evals and the recorded branch/commit.

Expected QA result: version 0.1.0, 5 skill files, one eval for out/invoice_report.md. main and qa initially contain the same commit; importing that same commit/path again is intentionally rejected as a duplicate.

Select dev to import version 0.2.0 of the same skill. The dev version adds vendor subtotals. Compare the two versions and verify the different commits and file hashes.

The CSV inside the skill is a sample input. A later execution test needs an assigned dataset version; Git skill import alone does not register a dataset or execute the skill. Skill execution and judging in the current EPO prototype are simulated.

Git import requires this repository to be accessible from the API process. Private-repository credential setup is separate from the skill package.
