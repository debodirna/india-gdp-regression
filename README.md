# Predicting India's Quarterly Real GDP Growth with Simple & Multiple OLS Regressions

**Project Student:** Debodirna Ghosh
** Project Mentor:** Suchismita Banerjee

## Project Overview
This project evaluates whether three high-frequency monthly economic indicators can estimate current-quarter Indian Real GDP growth (2011-12 base) ahead of the official MoSPI release and outperform a naive persistence benchmark.

* **Target Variable:** Quarterly Real GDP YoY Growth (%), Q1 FY2012-13 to Q2 FY2025-26 (`qtr_gdp_mrkt_prc_rn.csv`)
* **Monthly Indicators (converted to quarterly averages & YoY growth):**
  1. **IIP General Index** (Base 2011-12, MoSPI)
  2. **Merchandise Exports in USD** (Oil + Non-Oil, RBI DBIE)
  3. **Non-Food Bank Credit** of Scheduled Commercial Banks (RBI DBIE)

## Methodology & Sample Split
* **Training Period:** Q1 FY2012-13 to Q4 FY2019-20 (32 quarters)
* **Test Period:** Q1 FY2022-23 to Q2 FY2025-26 (14 quarters, excluding COVID-19 outlier years FY2020-21 and FY2021-22)
* **Naive Benchmark:** $\hat{y}_t = y_{t-1}$ (this quarter's growth = last quarter's growth)

## Out-of-Sample Test Results (FY2022-23 to Q2 FY2025-26)

| Model | MAE (pp) | RMSE (pp) | Beats Naive Benchmark? |
| :--- | :---: | :---: | :---: |
| **Naive Benchmark (Last Qtr Growth)** | 2.1077 | 3.3717 | Baseline |
| **Single OLS: IIP General Index** | **1.2462** | **1.5309** | **Yes (Best Model)** |
| **Multiple OLS: All 3 Indicators** | 1.2627 | 1.6002 | **Yes** |
| **Single OLS: Merchandise Exports** | 1.7859 | 2.4773 | **Yes** |
| **Single OLS: Non-Food Bank Credit** | 1.7935 | 2.4833 | **Yes** |

## Repository Structure
* `GDP_analysis.ipynb` — Main Python notebook containing data cleaning, quarterly aggregation, `statsmodels` OLS regressions, error evaluation, and plots.
* `Master_quarterly_cleaned_v2.xlsx` — Aligned quarterly dataset (Q1 FY2012-13 to Q2 FY2025-26).
