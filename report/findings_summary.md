# Findings Summary: Digital Wallet Transactions and Consumer Habits

**Data:** 18,000 synthetic digital wallet transactions from Kenya, 2025 (cleaned). The charts use successful payments with a valid KES amount that are not flagged as outliers (16,381 rows). Figures are in `visuals/` and the code is in `notebooks/04_visualization.ipynb`.

## Conclusions

1. **Spend is concentrated in a few categories, and payment size explains why.** Shopping (21.6%) and Travel (15.0%) together take 36.6% of spend, and the top four categories take 56.2%. Travel has only 423 payments but a median of KES 7,034, while Transport has 2,080 payments with a median of KES 276 and just 2.3% of spend (Figures 4 and 5).

2. **Activity is concentrated in Nairobi and Mombasa but is otherwise steady.** Nairobi accounts for 31.6% of transactions, and Nairobi and Mombasa together for 45.8%. Each region's share of spend closely follows its share of transactions (for example Nakuru 9.1% of transactions and 10.0% of spend), and monthly activity stays flat: 1,265 to 1,429 transactions and KES 2.32 to 2.82 million per month, with no clear seasonal pattern (Figures 1 and 3).

3. **Typical payments are small, and failures are rare and similar across channels.** The median payment is KES 1,011 while the mean is KES 1,971, and 73.1% of payments are under KES 2,000 (Figure 2). The overall failure rate is 3.45%, and by channel it ranges only from 3.05% (QR Payment) to 3.91% (In-App Payment), as found in Week 3, Question 6.

## Recommendations

1. **Focus merchant partnerships, offers and reliability checks on Shopping and Travel.** They hold 36.6% of spend, and each Travel payment is large (median KES 7,034), so a failed or delayed Travel payment costs more than one in a low-value category. For high-frequency, low-value categories such as Groceries, Food & Dining and Transport, aim for convenience and repeat use instead.

2. **Track failure rates every month by payment channel, starting with In-App Payment (3.91% against 3.45% overall).** The current gaps are under one percentage point and rest on 70 to 209 failed payments per channel, so they may be chance. A monthly check would show whether any channel moves clearly above the average before money is spent redesigning it.

## Limitations
The dataset is synthetic (AI-generated and approved by the lecturer), so the patterns reflect how it was generated and not real customers. It covers one year only. Invalid and flagged extreme amounts are excluded, and the share charts show percentages, not absolute amounts.
