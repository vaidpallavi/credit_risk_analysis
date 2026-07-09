# Quantitative Credit Scoring & Cost-Optimized Underwriting System

## Overview
This repository contains an automated credit score underwriting pipeline designed around modern transactional data. Moving beyond lagging, traditional credit bureau metrics, this engine utilizes real-time bank ledger insights—such as recurring debit bounce flags, variable cash flow buffers, and transaction risk profiles—to predict structural consumer defaults.

The business purpose is to establish an automated underwriting decision model that balances potential default write-offs against missed customer conversion interest margins.

---

## Performance Matrix & Model Benchmarks

A challenger model framework was evaluated using a stratified 20% validation split. The models achieved the following out-of-sample performance:

| Engine Variant | Validation ROC-AUC | Regulatory Gini Index | Operational Deployment Status |
| :--- | :---: | :---: | :--- |
| **XGBoost Classifier** | **0.9037** | **0.8073** | **Production Champion** |
| Random Forest | 0.9017 | 0.8035 | Core Challenger |
| Logistic Regression | 0.8600 | 0.7201 | Baseline Interpretation |

*Note: The Gini Index ($2 \times \text{AUC} - 1$) is the core standard used by internal risk compliance teams and external bank regulators to evaluate model separation stability.*

---

## Core Infrastructure Engineering

### Class Equalization Engine (SMOTE)
Consumer defaults represent a natural minority class within standard loan books (15.51% default rate in this portfolio). To prevent model bias toward majority approvals, the training partition was synthetically equalized using a SMOTE framework. This rebalancing process is kept strictly post-split to preserve data integrity and prevent validation leakage.

### Balance Sheet Loss Optimization Matrix
Instead of standard statistical evaluations that rely on a generic 50% probability boundary, this pipeline maps underwriting choices directly to financial results using an explicit banking loss optimization formula:
* **False Negative Cost ($5,000):** Misclassifying a high-risk applicant as safe, resulting in unpaid debt principal.
* **False Positive Cost ($500):** Turning down a creditworthy customer, resulting in lost interest margin.

The system tests multiple threshold options to find the exact configuration that minimizes overall credit risk and financial loss.

---

## Analytical & Visual Data Portfolio Assets
*(Running the notebook updates and outputs these diagnostic files to your root repository directory)*
* `modern_risk_drivers.png`: Focus boxplots highlighting transactional anomalies across risk groups.
* `fintech_feature_importance.png`: Feature weight ranking showing the top 10 indicators driving credit risk.
* `roc_curve_comparison.png`: Evaluation chart tracking true positive and false positive rates.
* `risk_correlation_heatmap.png`: Matrix mapping inner linear correlations against the primary default flag.
* `bounce_risk_rate.png`: Step-chart showing default progression scaling directly against account bounce counts.
* `credit_score_distribution.png`: Density profiles verifying clean portfolio separation across risk cutoffs.
* `salary_vs_risk.png`: Log-scaled income distribution plot showing structural salary ranges across risk tiers.