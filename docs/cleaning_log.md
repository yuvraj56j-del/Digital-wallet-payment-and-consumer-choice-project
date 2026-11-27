# Cleaning Log (Week 3)

Every cleaning decision is recorded here with its reason. The raw file `data/raw/digital_payment_transactions_dirty.xlsx` is never changed; all fixes are made on a copy (`df_clean`) saved to `data/processed/digital_payment_transactions_cleaned.csv`.

| # | Column(s) | Problem found | Rows affected | Treatment | Reason | Member |
|---|---|---|---|---|---|---|
| 1 | transaction_id | Same ID appears twice with different details | 35 extra (70 rows) | Kept both rows; added flag `id_repeated` | They are not exact copies, so deleting could remove real transactions | 2 |
| 2 | merchant_category, payment_channel, customer_segment, region, transaction_status | Blank values | 169, 241, 270, 205, 108 | Filled with "Unknown" | Each column is under 1.5% blank; filling keeps the row and its other values | 2 |
| 3 | merchant_category, payment_channel, customer_segment, region, transaction_status, day_of_week | Case, spacing and spelling variants (e.g. `Groceris`, `successfull`) | 1,707 cells (205, 323, 286, 229, 354 and 310 respectively) | Stripped spaces, made capitalisation consistent, mapped typos with a dictionary | Variants of one label must be grouped together or counts are wrong | 3 |
| 4 | currency | `kes`, `KES ` and `Ksh` variants; 6 USD rows; 14 blanks | 20 variants fixed; 6 USD rows flagged; 14 blanks | Variants standardised to `KES`; USD rows flagged with `non_kes` and not converted; blanks left blank | USD amounts must not be added to KES totals, there is no exchange rate in the data, and a blank currency should not be guessed | 3 |
| 5 | amount | Text entries: `1,2OO` (8) and `unknown` (6) | 14 | `1,2OO` changed to 1200; `unknown` left blank | `1,2OO` is an obvious typo (comma and letter O); `unknown` has no value to recover | 4 |
| 6 | amount | Negative (15) and zero (7) amounts | 22 | Flagged `amount_invalid`; excluded from value analysis; not deleted | Not valid payments, but deleting rows would reduce the dataset | 4 |
| 7 | amount | Extreme values: five of 999,999,999 and 8 above 100,000 | 8 | Flagged `is_outlier` (rule: above 100,000 KES); not deleted | Placeholder-like values distort the mean; flag instead of deleting | 4 |
| 8 | timestamp | 22 invalid values and 62 blanks | 84 | Converted to datetime; invalid values become blank (NaT); added `month`, `hour`, `weekday` | Dates cannot be guessed; rows are kept for non-time analysis | 4 |
| 9 | day_of_week | Spelling variants and 144 blanks | 310 spelling variants corrected; 144 blanks rebuilt (0 weekday mismatches found against valid timestamps) | Rebuilt from the timestamp where the timestamp is valid | The timestamp is the more reliable source | 4 |
| 10 | all columns | Row count after cleaning | 18,000 before and after | No rows dropped | Keeps the dataset above the 15,000 row minimum | 5 |

## Validation
- Raw rows x columns: 18,000 x 10. Processed rows x columns: 18,000 x 17 (the extra columns are the flags and date parts).
- `meets_size()` result: True. Processed file: `data/processed/digital_payment_transactions_cleaned.csv`.
- Before/after summary: see section 9 of `notebooks/03_cleaning_analysis.ipynb`.
