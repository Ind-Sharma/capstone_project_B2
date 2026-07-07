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



Prepared as part of a data analytics capstone project on e-commerce customer returns behavior.

<p align="left">
  <img src="https://img.shields.io/badge/Made%20with-Python%20%26%20Statistics-4B2E83?style=flat-square" alt="made-with"/>
</p>
