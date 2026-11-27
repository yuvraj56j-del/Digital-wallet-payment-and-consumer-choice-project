# Digital-wallet-payment-and-consumer-choice-project
Analyze a dataset on AI generated digital wallet transactions dataset of Kenya to understand what customers spend on, how they spend, where and when they pay, and where payments fail. The aim is to recommend ways to improve the wallet experience.

# Project 06: Digital Wallet Transactions and Consumer Habits

DSA 1080A Programming for Data Science | Future Data Lab group project
**Group:** 06 | **Repository:** https://github.com/yuvraj56j-del/Digital-wallet-payment-and-consumer-choice-project.git

## Project overview
We analysed 2025 digital wallet transactions in Kenya to understand what customers spend on, how, where and when they pay, and where payments fail. The work uses Python, Pandas and Matplotlib only.

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

Team Members
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
| Nduta | Project Proposal | proposal.md / proposal document |
| Godwinnfrey | Data Source Documentation | DATA_SOURCE.md |
| Ishmail | Schema Documentation | SCHEMA.md (review and verify column descriptions) |
| Morris | Notebook Updates and Evidence | Notebook changes and project screenshots |

## Project Progress for WEEK 2

| Week | Focus | Deliverables | Status |
|---|---|---|---|
| 1 | Problem definition, data acquisition, GitHub setup | Proposal, objectives and research questions, dataset source notes, `01_week1_intro.ipynb`, dataset schema | Done |
| 2 | Inspect, validate and profile the dataset | `02_exploration.ipynb`, data dictionary, quality audit table | Done |
| 3 | Cleaning and first analysis | | In progress |

## Week 2: Data Inspection and Quality Audit

**What we did**
- Loaded the raw dataset with Pandas and inspected it using `head()`, `tail()`, `shape`, `info()`, `dtypes` and `describe()`.
- Wrote reusable functions (`validate_columns()`, `summarize_missingness()`, `find_invalid_categories()`) to check the data.
- Built a data dictionary covering all 10 columns (type, meaning, valid values, expected missing values).
- Built a quality audit table listing each problem, how many rows it affects and how we plan to fix it.
- The source data was not changed in Week 2. Cleaning starts in Week 3.

**Key findings**
- The raw file has 18,000 rows and 10 columns, which meets the minimum requirement, and it has no fully duplicated rows.
- There are 1,330 missing cells across 1,300 rows (7.2% of rows).
- `amount` is stored as text and contains values like `unknown`, negatives, zeros and extreme values.
- 1,733 values in the category columns have spelling or casing errors.
- 22 timestamps cannot be read and 62 are missing.
- 35 transaction IDs appear more than once on different transactions.

**Files**
- Notebook: https://github.com/yuvraj56j-del/Digital-wallet-payment-and-consumer-choice-project/blob/main/notebook/02_exploration.ipynb
- Data dictionary: https://github.com/yuvraj56j-del/Digital-wallet-payment-and-consumer-choice-project/blob/main/docs/data_dictionary.md
- Quality audit: `report/quality_audit.csv`



