# 🛍️ E-Commerce Customer Returns — Behavior Analysis

<p align="left">
  <img src="https://img.shields.io/badge/Status-Complete-2E7D32?style=flat-square" alt="status"/>
  <img src="https://img.shields.io/badge/Python-3.11-1E2761?style=flat-square&logo=python&logoColor=white" alt="python"/>
  <img src="https://img.shields.io/badge/Pandas-2.x-8A9BF0?style=flat-square&logo=pandas&logoColor=white" alt="pandas"/>
  <img src="https://img.shields.io/badge/Tableau-Dashboard-E97627?style=flat-square&logo=tableau&logoColor=white" alt="tableau"/>
  <img src="https://img.shields.io/badge/License-MIT-black?style=flat-square" alt="license"/>
</p>

> **A statistically validated, business-ready analysis of why 1 in 5 e-commerce orders gets returned — and what to do about it.**

---

## 📌 Executive Summary

| Metric | Value |
|---|---|
| Orders analyzed | **19,940** (cleaned from 20,000 raw rows) |
| Overall return rate | **19.58%** (95% CI: 19.03% – 20.14%) |
| Estimated revenue tied up in returns | **$1,070,492** |
| Strongest driver identified | **Delivery delay** (Cramér's V = 0.249) |
| Highest-risk single scenario | **Beauty category × 5+ days late → 56.5% return rate** |

Returns in this dataset are **not random** — they concentrate in specific, identifiable combinations of product category, delivery performance, and customer history. Every pattern reported is backed by a significance test **and** an effect size, so recommendations are built on what's statistically *and* practically meaningful, not just what's detectable at scale.

---

## 🗂️ Repository Structure

```
Capstone_Project_Retail_Returns/
│
├── data/
│   └── ecommerce_returns.csv              # Raw source dataset (20,000 rows)
│
├── notebooks/
│   └── merged_capstone_notebook.ipynb     # End-to-end notebook: DQ → Cleaning → EDA → Stats
│
├── reports/
│   ├── Data_Quality_Report_B2.pdf         # Data quality assessment & cleaning log
│   └── EDA_Report.pdf                     # Exploratory & statistical analysis (business report)
│
├── dashboard/
│   └── (Tableau workbook / published dashboard link)
│
└── README.md
```

---

## 🧭 Project Workflow

This project follows a four-stage analytical pipeline, moving from raw data to boardroom-ready recommendations:

```
  1. DATA QUALITY            2. CLEANING              3. EDA & STATISTICS         4. RECOMMENDATIONS
  ──────────────────         ──────────────           ─────────────────────       ────────────────────
  • Missing values     →     • Standardize      →     • Univariate profiling →    • Priority-ranked
  • Duplicates                 categories              • Bivariate testing          business actions
  • Invalid ranges           • Impute missing         • Multivariate analysis     • Revenue-at-risk
  • Outlier detection          values                 • Effect-size ranking         quantification
                              • Resolve logical
                                conflicts
```

---

## 🔍 Key Findings

### Top Drivers of Return Behavior (ranked by effect size)

| Rank | Driver | Statistical Test | Effect Size | Verdict |
|---|---|---|---|---|
| 1 | **Delivery Delay** | Chi-square = 1235.95, p < 0.00001 | Cramér's V = **0.249** | 🔴 Act on first |
| 2 | **Product Category** | Chi-square = 421.72, p < 0.00001 | Cramér's V = **0.144** | 🔴 Act on first |
| 3 | Shipping Method | Chi-square = 86.19, p < 0.00001 | Cramér's V = 0.065 | 🟡 Secondary |
| 4 | Price Band | Chi-square = 40.36, p < 0.00001 | Cramér's V = 0.042 | 🟡 Secondary |
| 5 | Payment Method | Chi-square = 16.64, p = 0.0052 | Cramér's V = 0.024 | 🟢 Monitor |
| 6 | Customer Gender | — | Cramér's V = 0.021 | ⚪ De-prioritize |
| 7 | Customer Age Group | Chi-square = 0.11, p = 0.998 | Cramér's V = 0.000 | ⚪ De-prioritize |

**Continuous predictors:**
- **Past Return Rate** — point-biserial r = 0.138 → strongest numeric predictor; the "once a returner, often a returner" pattern holds.
- **Customer Rating** — Cohen's d = -0.550 (medium effect) → usable as an early-warning signal.
- **Discount Percent** — Cohen's d = 0.068 (negligible) → *not* a meaningful driver despite statistical significance.

### Return Rate by Delivery Delay

```
On-time/Early   ████░░░░░░░░░░░░░░░░  12.1%
1-2 days late   ███████░░░░░░░░░░░░░  20.0%
3-5 days late   ██████████████░░░░░░  39.5%
5+ days late    ████████████████░░░░  46.5%
```

### Revenue at Risk by Category (Pareto)

```
Electronics    ███████████████████████████████████  $585,295
Fashion        █████████████                         $206,803
Home & Living  ████████                              $125,891
Sports         ████                                  $68,020
Beauty         ███                                    $54,488
Groceries      █                                      $16,277
Books          █                                      $13,718
```
> Electronics does **not** have the highest return *rate*, but its high average order value makes it the largest absolute revenue risk — over half of the ~$1.07M total.

---

## ✅ Business Recommendations (Priority Order)

| Priority | Recommendation | Backed By |
|---|---|---|
| **1** | Set a hard SLA alert at 3-day delay; trigger proactive customer outreach before a return is filed | Delivery delay = strongest driver (Cramér's V 0.249) |
| **2** | Category-specific fixes — sizing tools for Fashion, tightened QA for Electronics — rather than a blanket returns policy | Category effect (Cramér's V 0.144) + return-reason breakdown |
| **3** | Operationalize a 4-factor pre-shipment risk score (history + delay + category + payment) — separates a 59.8% vs. 12.6% risk tier | Multivariate risk segmentation |
| **4** | Pilot partial-prepayment for high-risk Cash-on-Delivery orders | COD return rate significantly above average |
| **De-prioritize** | Discount depth, customer age, and gender — statistically detectable but practically negligible | Effect-size ranking (Section 7 of EDA Report) |

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Data Processing | Python, Pandas, NumPy |
| Statistical Testing | SciPy (Chi-square, Welch's t-test, Mann-Whitney U, point-biserial, logistic regression) |
| Visualization | Matplotlib, Seaborn |
| Dashboard | Tableau |
| Environment | Jupyter Notebook |

---

## 📁 File Guide

| File | Description |
|---|---|
| `ecommerce_returns.csv` | Raw dataset — 20,000 orders, 16 fields |
| `merged_capstone_notebook.ipynb` | Full pipeline: data quality checks, cleaning, EDA, and statistical validation |
| `Data_Quality_Report_B2.pdf` | Documents every data quality issue found and how it was resolved (duplicates, standardization, imputation, outliers) |
| `EDA_Report.pdf` | Business-facing report — univariate/bivariate/multivariate analysis, effect sizes, and prioritized recommendations |

---

## 📈 Methodology Notes

- Every relationship reported is validated with **both** a significance test and an effect size — Chi-square + Cramér's V for categorical pairs, Welch's t-test + Cohen's d for continuous-vs-binary comparisons, and point-biserial correlation for continuous predictors.
- At n = 19,940, even trivial differences can be statistically significant — effect sizes are what separate *detectable* from *worth acting on* throughout this analysis.
- `order_value`, `price_band`, `delivery_delay_bucket`, and `age_group` are engineered/bucketed fields, not present in the raw source file — defined to align with the Tableau dashboard's existing categories.

---

## 👤 Author

Prepared as part of a data analytics capstone project on e-commerce customer returns behavior.

<p align="left">
  <img src="https://img.shields.io/badge/Made%20with-Python%20%26%20Statistics-4B2E83?style=flat-square" alt="made-with"/>
</p>
