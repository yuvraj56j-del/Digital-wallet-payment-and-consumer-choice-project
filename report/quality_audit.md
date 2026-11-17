# Quality Audit (Week 2)

**Source of the counts:** `notebooks/02_exploration.ipynb`. The raw data has not been changed; all counts describe the data **before cleaning** and will be compared with the cleaned data in Week 3.

## Audit table (notebook section 10)

| Issue | Column(s) | Count | Note | Notebook section |
|---|---|---|---|---|
| Missing values | all columns except transaction_id | 1,330 | Blank cells in 1,300 rows; highest in customer_segment (270) and payment_channel (241) | 5 |
| Repeated IDs | transaction_id | 35 | Same ID, different details | 6 |
| Fully duplicated rows | all | 0 | None found | 6 |
| Text in numeric column | amount | 14 | `1,2OO` (8) and `unknown` (6) | 7 |
| Negative amounts | amount | 15 | Not valid for a payment | 7 |
| Zero amounts | amount | 7 | Questionable | 7 |
| Extreme amounts (999,999,999) | amount | 5 | Placeholder-like values | 7 |
| Invalid timestamps | timestamp | 22 | `2025-19-45` (9), `31/13/2025 25:61` (7), `not recorded` (6) | 9 |
| Inconsistent category labels | 7 categorical columns | 53 | Extra labels from case and spacing variants (labels, not rows; typos not counted) | 8 |
| Non-KES currency labels | currency | 13 | USD (6) and `Ksh` (7) | 8 |

## Supporting detail

**Blank cells by column (section 5)**

| Column | Blank cells | Percent |
|---|---|---|
| customer_segment | 270 | 1.50% |
| payment_channel | 241 | 1.34% |
| region | 205 | 1.14% |
| merchant_category | 169 | 0.94% |
| day_of_week | 144 | 0.80% |
| amount | 117 | 0.65% |
| transaction_status | 108 | 0.60% |
| timestamp | 62 | 0.34% |
| currency | 14 | 0.08% |
| transaction_id | 0 | 0.00% |

**Amount statistics (section 7):** median KES 1,007.71; mean KES 281,806.05 (pulled up by five values of 999,999,999). Largest values: 153,522.57; 162,956.02; 180,000.00 and five of 999,999,999.

**Labels per categorical column (section 8)**

| Column | Labels in file | After strip and lowercase |
|---|---|---|
| merchant_category | 32 | 21 |
| payment_channel | 24 | 13 |
| customer_segment | 21 | 13 |
| region | 25 | 15 |
| transaction_status | 13 | 9 |
| day_of_week | 28 | 21 |
| currency | 5 | 3 |

Labels still outnumber the intended categories after stripping and lowercasing, because of typos such as `Groceris`, `successfull` and `Fryday`. These need a mapping in Week 3.

**Date range of the valid timestamps (section 9):** 2025-01-01 00:31:22 to 2025-12-31 23:45:05; 62 timestamps are blank.
