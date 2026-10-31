# Dataset Schema

**File:** `digital_payment_transactions_dirty.xlsx` 
**Size:** 18,000 rows x 10 columns (verified in `notebooks/01_foundations.ipynb` with `df.shape`)
**Period:** 2025 | **Currency:** Kenyan shillings (KES)

| # | Column | Type (intended) | Meaning | Expected values / units |
|---|---|---|---|---|
| 1 | transaction_id | text (ID) | Transaction reference | Format `TXN2025xxxxxx` |
| 2 | timestamp | datetime | Date and time of the payment | `YYYY-MM-DD HH:MM:SS`, in 2025 |
| 3 | merchant_category | categorical | What the payment was for | Groceries, Food & Dining, Transport, Shopping, Utilities, Entertainment, Fuel, Healthcare, Education, Cash Transfer, Subscriptions, Government Services, Travel |
| 4 | amount | numeric (float) | Transaction value | KES, expected > 0 |
| 5 | currency | categorical | Currency of the amount | KES |
| 6 | payment_channel | categorical | How the payment was made | Mobile Wallet, QR Payment, USSD, In-App Payment, NFC / Contactless, Web Checkout |
| 7 | customer_segment | categorical | Type of customer | Salaried Employee, Student, Self-Employed, Small Business Owner, Gig Worker, Retired, Other |
| 8 | region | categorical | Region of the transaction | Nairobi, Mombasa, Kisumu, Nakuru, Kiambu, Eldoret, Machakos, Nyeri, Kakamega, Other |
| 9 | transaction_status | categorical | Outcome of the payment | Successful, Failed, Pending, Reversed |
| 10 | day_of_week | categorical | Weekday of the payment | Monday to Sunday |
