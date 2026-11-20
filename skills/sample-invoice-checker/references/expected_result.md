# Expected result for the synthetic sample

- Input rows: 4
- Unique invoices: 3
- Duplicate invoice ID: TEST-001 (two occurrences)
- Raw sum: 370.00 USD
- Excluded duplicate amount: 120.00 USD
- Payable total: 250.00 USD
- Validation problems: None

The duplicate row is a planted condition. Correct handling identifies it and excludes the repeated 120.00 USD from the payable total.
