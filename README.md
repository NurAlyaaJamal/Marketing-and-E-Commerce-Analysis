# Marketing-and-E-Commerce-Analysis

**Understanding customer behaviour through EDA, funnel analysis, A/B testing, customer segmentation and revenue analytics.**

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-SQLite-003B57?logo=sqlite&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## Project Overview

This project analyses a multi-table marketing and e-commerce dataset to understand how customers browse, click, add to cart and purchase, how marketing campaigns perform, and what drives revenue. It combines **SQL (SQLite)** for joins, aggregations, window functions, CTEs and RFM scoring with **Python** for statistical testing, modelling and visualisation.

> ⚠️ **Note:** The dataset is entirely **synthetic**. The findings demonstrate analytical techniques and should not be treated as evidence of real e-commerce business performance.

## Objectives

- Validate data quality and relationships across five related tables
- Analyse the conversion funnel (view → click → cart → purchase)
- Evaluate marketing campaign effectiveness and traffic sources
- Run and interpret an A/B test (conversion, uplift, significance, adjusted effect)
- Analyse revenue, discounts, refunds and revenue concentration
- Segment customers by profile and RFM (Recency, Frequency, Monetary)
- Examine trends, seasonality and product performance
- Translate results into business recommendations and state analytical limitations

## Dataset

Source: [Marketing and E-Commerce Analytics Dataset (Kaggle)](https://www.kaggle.com/datasets/geethasagarbonthu/marketing-and-e-commerce-analytics-dataset)

| Table | Rows | Description |
|---|---|---|
| `customers` | 100,000 | Customer profile: signup date, country, age, gender, loyalty tier, acquisition channel |
| `products` | 2,000 | Category, brand, base price, launch date, premium flag |
| `campaigns` | 50 | Channel, objective, dates, target segment, expected uplift |
| `events` | 2,000,000 | Interaction events: view, click, cart, purchase, device, traffic source, experiment group |
| `transactions` | 103,127 | Purchases: quantity, discount, gross revenue, refund flag |

## Analysis Workflow

1. **Load & validate**: structure, data types, missing values, duplicates, key integrity
2. **Clean & engineer features**: dates, standardised labels, campaign exposure, seasonality flags, age groups, price bands
3. **SQL database**: cleaned tables copied into in-memory SQLite; revenue rebuilt as gross, refunded and net
4. **Customer & product profile**
5. **Conversion funnel** (overall and by segment)
6. **Campaign effectiveness** (exposure, channel, expected vs observed)
7. **A/B testing**: sample-ratio check, balance check, two-proportion z-tests, confidence intervals, segment effects, logistic regression with cluster-robust errors, revenue per 1,000 events
8. **Statistical tests**: chi-square with Cramér's V, Mann-Whitney U, Kruskal-Wallis, Benjamini-Hochberg FDR adjustment
9. **Revenue & transactions**: discounts, refunds, Pareto concentration
10. **Customer segmentation & RFM**
11. **Trends & seasonality**
12. **Product performance**
13. **Business findings, recommendations & conclusion**

## Key Findings

| Area | Result |
|---|---|
| **Scale** | 2,000,000 events, 103,127 orders, 64,035 buyers (64.0% of customers) |
| **Net revenue** | $8,630,269 · AOV $95.89 · refund rate 2.94% of orders |
| **Funnel** | Overall purchase rate 5.16%; steepest drop is add-to-cart → purchase |
| **Traffic source** | Email converts at 8.89% vs Organic at 2.09% |
| **A/B test** | Control 4.74% · Variant_A 5.24% · **Variant_B 6.30%** (+1.56 pp, +33% relative; adjusted OR 1.36) |
| **Revenue per 1,000 events** | $5,202 (Variant_B) vs $3,997 (Control) |
| **Seasonality** | Nov–Dec purchase rate 6.38% vs 4.91% rest of year (+30%); weekends +0.51 pp |
| **Discounts** | Cost $385,250 (4.2% of list value); no association with basket size |
| **Customers** | Loyalty tier is the main differentiator ($76.58 to $111.35 revenue per customer); age, gender, country and acquisition channel show no detectable difference |
| **RFM** | Champions: 10.9% of buyers, 22.9% of revenue; at-risk + lapsing-loyal: 14.1% of buyers, 19.7% of revenue |
| **Products** | Electronics brings 41% of revenue; top 20% of products = 44% of revenue; category conversion is nearly identical |

## Business Recommendations

1. **Prioritise Variant_B**, then confirm with a customer-level (not event-level) split and check its running cost.
2. **Run a proper campaign holdout** within each paid channel to separate campaign effect from channel effect.
3. **Plan for November–December**: align stock, budget and campaign calendar to the holiday peak.
4. **Test the discount policy**: run a controlled test on the deepest discounts (20%).
5. **Target by behaviour, not demographics**: win back at-risk buyers and protect Champions.
6. **Fix tracking gaps**: missing revenue (about 10% of orders), non-unique `session_id`, inconsistent traffic-source labels, campaign dates that don't match exposure.

## Limitations

- Data is synthetic
- Event-level (not customer-level) experiment assignment, so spill-over between groups can't be ruled out
- Campaign exposure is fully confounded with traffic source
- No cost data, so ROAS and discount ROI can't be calculated
- Funnel is built from event counts, not individual user journeys
- About 10% of transactions have no revenue value (excluded, not imputed)

## Tech Stack

- **Languages:** Python, SQL (SQLite)
- **Data:** pandas, NumPy
- **Visualisation:** Matplotlib, Seaborn
- **Statistics:** SciPy, Statsmodels

> 💾 The `events` table has 2 million rows (roughly 800 MB in memory), so make sure you have enough RAM. The notebook also runs on Kaggle with the dataset attached.

## 👩‍💻 Author

**Nur Alyaa binti Jamal**
Industrial Statistics graduate, Universiti Utara Malaysia | Aspiring Data Analyst / BI Analyst

- GitHub: [@your-username](https://github.com/NurAlyaaJamal)
- LinkedIn: [your-linkedin](https://www.linkedin.com/in/nur-alyaa-jamal13/)

---

⭐ If you found this project useful, feel free to star the repository!
