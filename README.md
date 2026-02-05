# Guyton-Klinger-Withdrawals Database Documentation

## Overview
The **Guyton-Klinger-Withdrawals** database is a specialized financial engine designed to automate a retirement withdrawal strategy. It implements the "Guardrail" decision rules (Guyton-Klinger) to dynamically adjust spending based on portfolio performance and inflation (CPI). 

The system tracks daily account balances, calculates moving averages, monitors inflation, and generates a specific "Paycheck" amount and funding source (Cash vs. Asset Sale) for every processing period.

## Mermaid Data Flow Visualization

[![](https://mermaid.ink/img/pako:eNp9Vm1PIjEQ_itNE_2EnAgeyodLeNMjikcCanJwIWW3LI1LS7pdBI3__abd7e52QYjZdF77zNOZiZ_YEz7FLRxIslmhSW_GEfzOztAT6KNEiuJFYu7vFJWchPOxiKVHIzSdYatDqW6G_yVR-vdKF_PuaABunccx-oEGfBkSxQRHPaLIgWuH8LcInO8YJ9xjkHTAI8VUrEMOM7c9T8Rc6Qh7ROdoQnZkEVI02W_oQciQyDeqIGCshPeGEtEFQ7k_46XCBzygkcENobkASST10UgKj_qxLBU_Hs2fNxGVSjMQR5tceiQKMriubd_vkND4wXFIeExCUAAP1HXsktDrivXGuGohBkqp1oiIKTqSDF7hRC262AWJqC4lO080ZS78iXm5DO1TvF5QGTkOwLqaWuodiy4lRe8auqGI6FR_GQ8crIl9JKSa6s9ShEy4obrovM7jPiRa3YXifXr_YI8nqLDspQ9bFPs8YJyW33NIIuh2w_z9w_PGB2bKD6510IKOT9qSlpDOvvdNoO0UGwjy8-HrDwnjqVsB8gGcl_lQbNvbYLp9nx_Spo3wBO0tlSQogRkrSVRyA1WvTK18Sd5JaNQ02J9g9E-sNrEyi8Eez9EL-3CI7O88Gk7NF3bCC4ug1dmHKaLYDP01YeCmv6gdwuSg35PhY2lqtD4ZGn06UqdDSwEyrLi-H1DUFZxTL1kwvLCz0MXFL2eEc6tZU8ZuGv2YIRvo3JitqCRQz05uTBdRYjIzYnEWIVi7BZPdUgaT5rBQ7MqwRk3OcVtBYS_LbDZaI0cXVUtP2uAFvMmU5ARmHifsxZpcu-14e4Ep85vkE_flnMT5csjA56nL42uLTyNKDoWnKDvYlAf2DISl1o5nYrCSBW9mLctqpO8JyQsDDzNXx5OaGclbx8yUCdEzhivwTwDzcUvJmFbwmkrQgog_dcQMqxVdw0JswdGnSxKHaoZn_AvCNoT_FWJtI6WIgxVuLUkYgRQbxnqMwILIXWAQqezqecCtWt2kwK1PvAPp6rJav2o2ajX4u7m5vmpU8B63bpvV23qz_rPWbNabjUb99quCP8yll9Wb5vXXf0g_zPs?type=png)](https://mermaid.live/edit#pako:eNp9Vm1PIjEQ_itNE_2EnAgeyodLeNMjikcCanJwIWW3LI1LS7pdBI3__abd7e52QYjZdF77zNOZiZ_YEz7FLRxIslmhSW_GEfzOztAT6KNEiuJFYu7vFJWchPOxiKVHIzSdYatDqW6G_yVR-vdKF_PuaABunccx-oEGfBkSxQRHPaLIgWuH8LcInO8YJ9xjkHTAI8VUrEMOM7c9T8Rc6Qh7ROdoQnZkEVI02W_oQciQyDeqIGCshPeGEtEFQ7k_46XCBzygkcENobkASST10UgKj_qxLBU_Hs2fNxGVSjMQR5tceiQKMriubd_vkND4wXFIeExCUAAP1HXsktDrivXGuGohBkqp1oiIKTqSDF7hRC262AWJqC4lO080ZS78iXm5DO1TvF5QGTkOwLqaWuodiy4lRe8auqGI6FR_GQ8crIl9JKSa6s9ShEy4obrovM7jPiRa3YXifXr_YI8nqLDspQ9bFPs8YJyW33NIIuh2w_z9w_PGB2bKD6510IKOT9qSlpDOvvdNoO0UGwjy8-HrDwnjqVsB8gGcl_lQbNvbYLp9nx_Spo3wBO0tlSQogRkrSVRyA1WvTK18Sd5JaNQ02J9g9E-sNrEyi8Eez9EL-3CI7O88Gk7NF3bCC4ug1dmHKaLYDP01YeCmv6gdwuSg35PhY2lqtD4ZGn06UqdDSwEyrLi-H1DUFZxTL1kwvLCz0MXFL2eEc6tZU8ZuGv2YIRvo3JitqCRQz05uTBdRYjIzYnEWIVi7BZPdUgaT5rBQ7MqwRk3OcVtBYS_LbDZaI0cXVUtP2uAFvMmU5ARmHifsxZpcu-14e4Ep85vkE_flnMT5csjA56nL42uLTyNKDoWnKDvYlAf2DISl1o5nYrCSBW9mLctqpO8JyQsDDzNXx5OaGclbx8yUCdEzhivwTwDzcUvJmFbwmkrQgog_dcQMqxVdw0JswdGnSxKHaoZn_AvCNoT_FWJtI6WIgxVuLUkYgRQbxnqMwILIXWAQqezqecCtWt2kwK1PvAPp6rJav2o2ajX4u7m5vmpU8B63bpvV23qz_rPWbNabjUb99quCP8yll9Wb5vXXf0g_zPs)

## Core Logic & Data Flow
The database operates on a daily or periodic update cycle orchestrated by the master procedure `usp_GKUpdate`. 


1.  **Ingest:** Market data (Closing Prices), Account Balances, and Inflation numbers (CPI) are updated.
2.  **Aggregate:** Balances are summed by Tax Bucket (Taxable, Tax-Free, Deferred).
3.  **Calculate:** The `GKCashFlow` engine calculates the daily "Paycheck" by applying inflation adjustments and checking against Upper/Lower spending guardrails.
4.  **Decide:** The system determines the *Source* of the funds (Cash vs. Assets) based on the portfolio's 2-week moving average.

---

## Schema Summary

### 1. The Calculation Engine (Primary Tables)

| Table Name | Description | Key Columns |
| :--- | :--- | :--- |
| **`GKCashFlow`** | **The Master Ledger.** Records the daily state of the strategy, including total assets, calculated inflation rates, spending limits (Upper/Lower guardrails), and the final "Paycheck" amount. | `Date`, `Total_Assets`, `Inflated_Withdrawal_Amount`, `GK_Upper/Lower_Amount`, `Paycheck`, `Paycheck_Source` |
| **`GKYearOverYearStats`** | Stores aggregated statistical performance data for annual reporting and analysis. | `Year`, `Taxable_Percent`, `Spent`, `CPI_U` |
| **`CompositePortfolio`** | Tracks the calculated daily value of the investment portfolio based on weighted symbol performance. Used to trigger guardrails. | `ID`, `TaxType`, `Closing`, `CompositePrice` |

### 2. Core Data & Inputs

| Table Name | Description | Key Columns |
| :--- | :--- | :--- |
| **`Balances`** | Historical ledger of all account balances. Supports versioning by tracking multiple updates per sequence/date. | `ID`, `Name`, `Balance`, `LastUpdate` |
| **`CPILatestNumbers`** | Stores scraped CPI (Consumer Price Index) reports to calculate daily inflation rates. | `ReportMonth`, `NSA_Monthly_Change`, `SA_Monthly_Change` |
| **`ClosingPrices`** | Records daily market closing prices for symbols tracked in the portfolio. | `Closing`, `Symbol`, `Price` |
| **`Portfolio`** | Defines the target asset allocation weights for specific symbols within tax buckets. | `Symbol`, `TaxType`, `Percent`, `Active` |
| **`Accounts`** | Metadata mapping account names to Tax Types (Taxable, Roth, etc.) and Categories. | `Name`, `TaxType`, `Category` |

### 3. Reference Data

| Table Name | Description |
| :--- | :--- |
| **`FederalTaxRates`** | Stores historical and current federal tax brackets/rates by filing status. |
| **`FederalStandardDeductions`** | Stores standard deduction amounts by tax year and filing status. |

---

## Stored Procedures & Orchestration

### Master Orchestrator
#### `usp_GKUpdate`
* **Role:** The single entry point for daily updates.
* **Parameters:** `@Date` (Defaults to `GETDATE()`).
* **Execution Chain:**
    1.  `usp_GKUpdateTaxableBalancesByDate`: Aggregates raw balances into the Cash Flow table.
    2.  `usp_GKUpdateCPIU`: Fetches latest CPI, calculates daily inflation, and updates Cash Flow.
    3.  `usp_GKCalculationUpdate`: Runs the core Guyton-Klinger math (Guardrails & Paycheck).

### Calculation Procedures
#### `usp_GKCalculationUpdate`
* **Purpose:** The "Brain" of the system.
* **Logic:**
    * **Jan 1st Reset:** If run on Jan 1, it resets the Upper (+20%) and Lower (-20%) spending guardrails based on current portfolio value.
    * **Inflation Adjustment:** Adjusts the previous withdrawal amount by the calculated CPI-U.
    * **Guardrail Check:** If the adjusted withdrawal exceeds the Upper/Lower limits, it applies a "Pay Cut" (-10%) or "Pay Raise" (+10%).
    * **Paycheck Gen:** Calculates the final `Paycheck` amount and stamps the `Paycheck_Source` (from `usp_GetWithdrawalStrategy`).

#### `usp_GKUpdateCPIU`
* **Purpose:** Converts raw monthly CPI strings (e.g., "0.2%") into daily inflation factors.
* **Logic:**
    * Parses the latest `SA_Monthly_Change` from `CPILatestNumbers`.
    * Calculates a daily inflation rate based on days in the month.
    * Applies this rate to the `Inflated_Withdrawal_Percent` in `GKCashFlow`.

#### `usp_GetWithdrawalStrategy`
* **Purpose:** Determines *where* the money comes from.
* **Logic:** Checks the 2-Week Moving Average of the portfolio (via `vw_CompositePortfolio_MovingAverage`).
    * **> 90%:** Sell Assets.
    * **< 80%:** Use Cash.
    * **80-90%:** Linear sliding scale (mixed Cash/Assets).

### Utility & Reporting
* **`usp_Alert_CompositePortfolioUpdate`**: Checks if the Moving Average crossed a 10% threshold and sends an HTML email via Database Mail.
* **`usp_GetBalanceUpdateHistogram_Pivot`**: Generates a heatmap (Day of Week vs. Hour) of data entry frequency for auditing.
* **`usp_AddManualBalance`**: Helper to insert balances for accounts that cannot be automated (e.g., specific Voya 401k).

---

## Key Views

* **`vw_CompositePortfolio_MovingAverage`**: The "Speedometer" of the system. Calculates the 2-week moving average vs. the all-time high to determine the withdrawal strategy.
* **`vw_AccountBalancesByTaxTypeAndCategory`**: Summarizes net worth by tax bucket (Taxable, Tax-Free, Deferred, Cash), excluding non-investment assets like 529s or operational cash.

## Configuration Notes
* **Database Mail:** The alerting system requires a profile named `'MyMailProfile'`.
* **Hardcoded IDs:** Some procedures (e.g., `usp_AddManualBalance`) contain hardcoded `SequenceID`s specific to the owner's data.
* **SQL Version:** Script sets `COMPATIBILITY_LEVEL = 150` (SQL Server 2019).

## License

This project is licensed under the [GPL-3.0 License](LICENSE.txt).