# Digital-wallet-payment-and-consumer-choice-project
Analyze a dataset on AI generated digital wallet transactions dataset of Kenya to understand what customers spend on, how they spend, where and when they pay, and where payments fail. The aim is to recommend ways to improve the wallet experience.

# Project 06: Digital Wallet Transactions and Consumer Habits

DSA 1080A Programming for Data Science | Future Data Lab group project
**Group:** 06 | **Repository:** https://github.com/yuvraj56j-del/Digital-wallet-payment-and-consumer-choice-project.git

## Project overview
We analysed a synthetic 2025 digital wallet transactions dataset of Kenya to understand what customers spend on, how, where and when they pay, and where payments fail. The work uses Python, Pandas and Matplotlib only.

**Specific objectives**
1. Identify the spending categories, customer segments and regions that account for most transaction value.
2. Describe how transaction volume and value change over time (month, weekday, hour).
3. Compare payment channels and regions by failure, pending and reversal rates.

**Research questions**
1. Which merchant categories account for the largest share of total spending in KES?
2. Which customer segments have the highest median transaction value?
3. Which regions record the most transactions, and which have the highest average value?
4. How do total monthly transaction value and transaction count change across 2025?
5. Which weekday and which hour of the day are the busiest?
6. Which payment channels have the highest failure rate?
7. Do failed or reversed transactions differ in amount from successful ones?

**Team Members**
| No. | Full Name | Student ID |
| --- | --- | --- |
| 1. | Yuvraj Rajankumar Thorat | 202604918 |
| 2. | Godwinfrey Mwema Gathiru | 202609294 |
| 3. | Nduta Gathigi | 202616126 |
| 4. | Morris Muhia | 202618102 |
| 5. | Ismail Hassan | 202606767 |
| 6. | Jediel Njagi Wambura | 2026014700 |


## Team Member Responsibilities for WEEK ONE

| Member Name | Responsibility | Deliverable |
|------------|---------------|-------------|
| Yuvraj | Project Documentation | README.md |
| Nduta | Project Proposal | report/Group06_Proposal.pdf |
| Godwinfrey | Data Source Documentation | data/DATA_SOURCE.md |
| Ismail | Schema Documentation | docs/dataset_schema.md (reviewed and verified column descriptions) |
| Morris | Notebook Updates and Evidence | Notebook changes and project screenshots |

## Project Progress

| Week | Focus | Deliverables | Status |
|---|---|---|---|
| 1 | Problem definition, data acquisition, GitHub setup | Proposal, objectives and research questions, dataset source notes, `01_foundations.ipynb`, dataset schema | Done |
| 2 | Inspect, validate and profile the dataset | `02_exploration.ipynb`, data dictionary, quality audit table | Done |
| 3 | Cleaning and first analysis | | In progress |

## Week 2 Roles and Contributions

| Member | Role | Week 2 task | Brief item | Files |
|---|---|---|---|---|
| `<Name 1>` | Project lead | Wrote the five initial observations with evidence, updated the README and progress table, checked that everyone committed | 6 | `README.md`, observations section of `notebooks/02_exploration.ipynb` |
| `<Name 2>` | Data lead | Built and checked the data dictionary for all 10 columns (type, meaning, categories, expected missing values) | 3 | `data/DATA_DICTIONARY.md` |
| `<Yuvraj Rajankumar Thorat>` | Loading and first-look lead | Loaded the data from a relative path and ran `head(10)`, `tail(5)`, `shape`, `info()`, `dtypes` and `describe(include="all")` | 1, 2 | `notebooks/02_exploration.ipynb` (sections 1-2) |
| `<Name 4>` | Validation lead | Wrote the reusable functions (`validate_columns()`, `summarize_missingness()`) and ran the checks for nulls, duplicates, invalid amounts, categories and date parsing without changing the source data | 4, 5 | `notebooks/02_exploration.ipynb` (sections 3-4) |
| `<Name 5>` | Audit lead | Wrote the quality audit table and the three potential data-quality issues with evidence | 4, 6 | `report/quality_audit.csv`, issues section of `notebooks/02_exploration.ipynb` |

*Jediel joined the group at the start of Week 3, so he has no Week 1 or Week 2 tasks.*

## Data Inspection and Quality Audit

**What we did**
- Loaded the raw dataset with Pandas and inspected it using `head()`, `tail()`, `shape`, `info()`, `dtypes` and `describe()`.
- Wrote reusable functions (`validate_columns()`, `summarize_missingness()`, `find_invalid_categories()`) to check the data.
- Built a data dictionary covering all 10 columns (type, meaning, valid values, expected missing values).
- Built a quality audit table listing each problem, how many rows it affects and how we plan to fix it.
- The source data was not changed in Week 2. Cleaning starts in Week 3.

### What we learned about the data
- **Size:** the file holds 18,000 transactions across 10 columns, which is above the project minimum of 15,000 rows and 10 columns.
- **Data types:** nine columns are stored as plain text. `amount` shows as `object` because 14 of its entries are not real numbers, and `timestamp` is text instead of a proper date.
- **Missing values:** every column except `transaction_id` has some blanks, adding up to 1,330 empty cells. The most affected columns are `customer_segment` (1.50%) and `payment_channel` (1.34%).
- **Amount distribution:** the typical (median) amount is about KES 1,008, yet the average is about KES 281,806. Five placeholder-sized entries of 999,999,999 are responsible for the gap.
- **Early patterns (before cleaning):** Mobile Wallet is the most common channel (33.3% of rows), Nairobi the most common region (30.8%), and 90.1% of transactions are marked Successful. These shares may shift slightly once spelling variants are merged.

### Problems we need to fix
1. **Messy category labels:** `merchant_category` contains 32 different labels, although only 13 categories are intended. The extras are differences in capitalisation, spacing and spelling. Left as they are, they would split real categories into several smaller groups.
2. **Unusable amounts:** 14 text entries, 15 negative values, 7 zeros and the five 999,999,999 entries would throw off totals and averages.
3. **Time and ID problems:** 22 timestamps cannot be read as dates, and 35 transaction IDs are repeated across transactions with different details. This weakens any time-based analysis and means IDs cannot be treated as unique.

**Where to find the evidence**
- Notebook: https://github.com/yuvraj56j-del/Digital-wallet-payment-and-consumer-choice-project/blob/main/notebooks/02_exploration.ipynb
- Data dictionary: https://github.com/yuvraj56j-del/Digital-wallet-payment-and-consumer-choice-project/blob/main/docs/data_dictionary.md
- Quality audit: https://github.com/yuvraj56j-del/Digital-wallet-payment-and-consumer-choice-project/blob/main/docs/quality_audit.md



