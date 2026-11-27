# Data Dictionary
**Dataset:** `data/raw/digital_payment_transactions_dirty.xlsx` | 18,000 rows x 10 columns | Period: 2025 | Currency: KES
**Source of the counts:** `notebooks/02_exploration.ipynb` (section 3 for this table, section 5 for the blank counts). The raw file has not been changed.
- **Stored type** is what Pandas reads from the raw file.
- **Intended type** is what we will convert the column to in Week 3.
- **Missing in raw file** is the number (and percentage) of blank cells out of 18,000 rows.

| Column | Stored type | Intended type | Meaning | Units / valid categories | Expected missing values | Missing in raw file |
|---|---|---|---|---|---|---|
| transaction_id | str | text (ID) | Transaction reference | `TXN2025` + 7 digits (14 characters); should be unique | None | 0 (0.00%) |
| timestamp | str | datetime | Date and time of the payment | `YYYY-MM-DD HH:MM:SS`, in 2025 | None | 62 (0.34%) |
| merchant_category | str | category | What the payment was for | 13: Groceries, Food & Dining, Transport, Shopping, Utilities, Entertainment, Fuel, Healthcare, Education, Cash Transfer, Subscriptions, Government Services, Travel | None | 169 (0.94%) |
| amount | object | float | Transaction value | KES, expected above zero | None | 117 (0.65%) |
| currency | str | category | Currency of the amount | KES | None | 14 (0.08%) |
| payment_channel | str | category | How the payment was made | 6: Mobile Wallet, QR Payment, USSD, In-App Payment, NFC / Contactless, Web Checkout | None | 241 (1.34%) |
| customer_segment | str | category | Type of customer | 7: Salaried Employee, Student, Self-Employed, Small Business Owner, Gig Worker, Retired, Other | Few | 270 (1.50%) |
| region | str | category | Region of the transaction | 10: Nairobi, Mombasa, Kisumu, Nakuru, Kiambu, Eldoret, Machakos, Nyeri, Kakamega, Other | Few | 205 (1.14%) |
| transaction_status | str | category | Outcome of the payment | 4: Successful, Failed, Pending, Reversed | None | 108 (0.60%) |
| day_of_week | str | category | Weekday of the payment | Monday to Sunday | None (can be rebuilt from timestamp) | 144 (0.80%) |

**Expected missing values:** "None" means the field should always be filled, so any blank is a data-quality issue. "Few" means a small number of blanks is plausible (the customer may not give the information).

## Notes
- `amount` is stored as `object` (mixed) because 14 entries are text (`1,2OO` and `unknown`), so it cannot yet be treated as a number.
- `timestamp` is stored as text. 22 non-blank values are not valid dates (see the quality audit).
- Each categorical column has more labels in the file than the intended number, because of case, spacing and spelling variants (see the quality audit).
- Total blank cells: 1,330, spread over 1,300 rows.
