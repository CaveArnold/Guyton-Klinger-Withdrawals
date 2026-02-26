# Guyton-Klinger Withdrawals Database Documentation

**Database Name:** `[Guyton-Klinger-Withdrawals]`

**Developer:** Cave Arnold

**AI Assistant:** Gemini

**Script Date:** February 21, 2026


## Overview
This database implements a financial withdrawal strategy based on the Guyton-Klinger decision rules. It manages account balances, tracks portfolio performance against moving averages, calculates inflation adjustments (CPI-U), and enforces capital preservation and prosperity guardrails to determine safe withdrawal rates.

## Mermaid Data Flow Visualization

[![](https://mermaid.ink/img/pako:eNqVWN1u2zYUfhVCRYsUSBzbsZdEWzskcZsFSZsgThpkdRFQEmVrkUWVpOK4Te92sQ0DuqHAhu1mV90z7Hn2Atsj7JAUKdmRnC43kQ7P-fjx_FJ-6_g0II7rDBlOR-ikN0gQ_N2_j3okjBKC-mIaE66lfow5BzmaEA-FURy790gr7IZkmQtGL4l7r9nqrm96-evKJArEyG2n15_P2QfGPAzDTb9jzUPPb7aDO81TRn2z_0bYJZsWoE3Wg7X2nQA0E4bAGumGXWu_7rVCXGmvEXjmaUedEe-iTzPmE45eDpx___jxJylDPSwwyhcGzittJf_65HVGEp8sSeX3fyKcpo0hETwXNyL6hcdWHy9t-T7NEoG2cYwTie5N0Qm-RifTlDwcOA9d1wXvF7h-HPmXFh0NnJEQKXdXV29vsDpwYP0wJQk6Jj5lwcApcLYP-orah-_kY2NIrzSfnaO9lVO0l4QxFhFN1AHreYBpicJkMml4MZdgq34arQIE4WIlycYeYbwxEuNFjJ5hdkmE3E8T-x5ykdLXDZ-ONTWtgHZiyqNkiI5YBP6q51bglShyA7mIyRnBsRiFjCbCUCmJCkJ7yRWcb0wgfEeUiZDGEV1AqIQx57TJLPrCwO0loEEOsGeoycBHShhjjzIsKJsqFE2yT_0Ix5AxfsYiMUXPj17UU7TgJYKV2IsYbsXRcGQ9h9Vb4bQjknCZWDgJ0EEUEtiTZ0zm_mJqGnXOcQV4LSOSBLeqWSaFhznRpfzrt__89R7tZlNBk5X9GHKLsJWzSIwChic45lZ9psCLJwu7B5ZcVs3FCfZi0yk-fCwWkF6YAVLVmFf_S_Ba4NGGeQdvvAJ3BN6sOhSp0YTHA1Vmz3WV1VnootE1Y23LwhpDm9g7NAmjoTG14gqzksdn3LODYz_TbeXiSTKU0wYc9Pfvv0n3lxZRvrgE9c9IAIVOfRJkTBX7nOMOmT-Cw6vMfAloGU8vdvdP0wB8YroGF4TNKEoYSVrOlVm4OacBJxuZOXDo0TKUZnl72rM7bg2HjAxlUGwn5_Vbyk1kPOfwQXRquozpxVvBN5nuN4vhdvcLtJJfy17ZzTCD9I4gux-g4yxexLAvvUaGUwtKRFEdZjE_OufQoa840OBQZsSPZK3_H3_3BRa3nK2Eeodzeo7kawT15N_lVjpOIcMFMXjGGcSu6NzX0GdENhOZcISFlI1lYKs3qM1wyNfZ2v9BydABHUZ-XfHLIPHR05hOTHUVEs2sB4GalktETZmqct3d1w60QOcEs8MrwuR_tVTXIKyvTHOwLlpQ6vLv_KR3mzcI6zrDggZ6TFLYDFrSxQGeQtFqH_5cyEu9AC09ufZJjJ4SElQ0BjC5UC61qQRpa9htT6U7lL2KSW0WSZS5jFSvn2gqXVeqGuvJTzT_CpLcmOeNRoooOGv8iRDHOLk0EPIZfHgXeRukqsl5mIk0E3l2__JRdu4XEc9gDr_RPeoB2kpwPJXFORMTtelSXhM6cj2IhkehD3E99OGWXui_iN6Y-6m6ws3sMm9QYiq_ZKR-MXJlwPMPGnttXll5fLN1tHdjB69el9dZudT34bCE38hBq1dKl0lrOzs-k7mbo9J7hhNgfTM_RbVycdkqq56bb7L8wnNrzZ6zPDKL8QZvWqM88dCjR49nxtkCFXvmytXd_QWLusEkRXUDS936SkGwXzpwsgpOZYk6_GnKCRMQjKK7GCcAVYtiaecvuW2g5nAxQ-9X4RQSC2fOaeabglNncSGN4hipUccRnF7afnkzY6WfZygc4Sl4DC6yD-DaO46qD1RBpORTCH-V2L7OuyvXybXK2Vp4zXR5rTSXp3VqMyKtVCjYyBdduxT9uROaNm0W7TmK1lvPzLTYirwy7bNmSbbCElPd1co0DS9lodpVIS84zi1ILlVySaRKLlks3gC6YAU8SJ1lZ8iiwHEFy8iyMyZwXZGvzlupP3DEiIyhvbvwGJAQZ7GQ30PvwCzFydeUjo0lo9lw5LghfOfAW6aStRdhOWKsCrRXwnbkzxSO-1lnTWE47lvn2nFba63GZmujs76x3m2vNbvt7rIzddxus9Fstjc63U6n2W222s3Ou2Xnjdq22dhsN9vdVnO91emuNTc7YEGCCNrIM_3LlPqB6t1_V-AKSQ?type=png)](https://mermaid.live/edit#pako:eNqVWN1u2zYUfhVCRYsUSBzbsZdEWzskcZsFSZsgThpkdRFQEmVrkUWVpOK4Te92sQ0DuqHAhu1mV90z7Hn2Atsj7JAUKdmRnC43kQ7P-fjx_FJ-6_g0II7rDBlOR-ikN0gQ_N2_j3okjBKC-mIaE66lfow5BzmaEA-FURy790gr7IZkmQtGL4l7r9nqrm96-evKJArEyG2n15_P2QfGPAzDTb9jzUPPb7aDO81TRn2z_0bYJZsWoE3Wg7X2nQA0E4bAGumGXWu_7rVCXGmvEXjmaUedEe-iTzPmE45eDpx___jxJylDPSwwyhcGzittJf_65HVGEp8sSeX3fyKcpo0hETwXNyL6hcdWHy9t-T7NEoG2cYwTie5N0Qm-RifTlDwcOA9d1wXvF7h-HPmXFh0NnJEQKXdXV29vsDpwYP0wJQk6Jj5lwcApcLYP-orah-_kY2NIrzSfnaO9lVO0l4QxFhFN1AHreYBpicJkMml4MZdgq34arQIE4WIlycYeYbwxEuNFjJ5hdkmE3E8T-x5ykdLXDZ-ONTWtgHZiyqNkiI5YBP6q51bglShyA7mIyRnBsRiFjCbCUCmJCkJ7yRWcb0wgfEeUiZDGEV1AqIQx57TJLPrCwO0loEEOsGeoycBHShhjjzIsKJsqFE2yT_0Ix5AxfsYiMUXPj17UU7TgJYKV2IsYbsXRcGQ9h9Vb4bQjknCZWDgJ0EEUEtiTZ0zm_mJqGnXOcQV4LSOSBLeqWSaFhznRpfzrt__89R7tZlNBk5X9GHKLsJWzSIwChic45lZ9psCLJwu7B5ZcVs3FCfZi0yk-fCwWkF6YAVLVmFf_S_Ba4NGGeQdvvAJ3BN6sOhSp0YTHA1Vmz3WV1VnootE1Y23LwhpDm9g7NAmjoTG14gqzksdn3LODYz_TbeXiSTKU0wYc9Pfvv0n3lxZRvrgE9c9IAIVOfRJkTBX7nOMOmT-Cw6vMfAloGU8vdvdP0wB8YroGF4TNKEoYSVrOlVm4OacBJxuZOXDo0TKUZnl72rM7bg2HjAxlUGwn5_Vbyk1kPOfwQXRquozpxVvBN5nuN4vhdvcLtJJfy17ZzTCD9I4gux-g4yxexLAvvUaGUwtKRFEdZjE_OufQoa840OBQZsSPZK3_H3_3BRa3nK2Eeodzeo7kawT15N_lVjpOIcMFMXjGGcSu6NzX0GdENhOZcISFlI1lYKs3qM1wyNfZ2v9BydABHUZ-XfHLIPHR05hOTHUVEs2sB4GalktETZmqct3d1w60QOcEs8MrwuR_tVTXIKyvTHOwLlpQ6vLv_KR3mzcI6zrDggZ6TFLYDFrSxQGeQtFqH_5cyEu9AC09ufZJjJ4SElQ0BjC5UC61qQRpa9htT6U7lL2KSW0WSZS5jFSvn2gqXVeqGuvJTzT_CpLcmOeNRoooOGv8iRDHOLk0EPIZfHgXeRukqsl5mIk0E3l2__JRdu4XEc9gDr_RPeoB2kpwPJXFORMTtelSXhM6cj2IhkehD3E99OGWXui_iN6Y-6m6ws3sMm9QYiq_ZKR-MXJlwPMPGnttXll5fLN1tHdjB69el9dZudT34bCE38hBq1dKl0lrOzs-k7mbo9J7hhNgfTM_RbVycdkqq56bb7L8wnNrzZ6zPDKL8QZvWqM88dCjR49nxtkCFXvmytXd_QWLusEkRXUDS936SkGwXzpwsgpOZYk6_GnKCRMQjKK7GCcAVYtiaecvuW2g5nAxQ-9X4RQSC2fOaeabglNncSGN4hipUccRnF7afnkzY6WfZygc4Sl4DC6yD-DaO46qD1RBpORTCH-V2L7OuyvXybXK2Vp4zXR5rTSXp3VqMyKtVCjYyBdduxT9uROaNm0W7TmK1lvPzLTYirwy7bNmSbbCElPd1co0DS9lodpVIS84zi1ILlVySaRKLlks3gC6YAU8SJ1lZ8iiwHEFy8iyMyZwXZGvzlupP3DEiIyhvbvwGJAQZ7GQ30PvwCzFydeUjo0lo9lw5LghfOfAW6aStRdhOWKsCrRXwnbkzxSO-1lnTWE47lvn2nFba63GZmujs76x3m2vNbvt7rIzddxus9Fstjc63U6n2W222s3Ou2Xnjdq22dhsN9vdVnO91emuNTc7YEGCCNrIM_3LlPqB6t1_V-AKSQ)

## 1. Core Tables
The database utilizes the following tables to store financial data, configuration, and calculation results:

* **`Balances`**: Stores raw balance entries for accounts, including error logging and timestamps.
* **`Accounts`**: Configuration table defining account metadata such as Name, TaxType, and Category.
* **`GKCashFlow`**: The central logic table storing daily cash flow calculations, inflation adjustments, and Guyton-Klinger guardrail metrics (Upper/Lower limits, Pay Raises/Cuts).
* **`GKCashFlowYTD`**: Summary table for Year-To-Date aggregations of assets, income, spending, and net worth.
* **`GKYearOverYearStats`**: Stores longitudinal statistical data to track performance across years, including `Sequence_of_Returns`.
* **`CompositePortfolio`**: Stores calculated composite prices grouped by TaxType and Closing Date.
* **`Portfolio`**: Defines asset allocation, including Symbols, Names, Tax Types, and active Percentages.
* **`ClosingPrices`**: Stores historical closing prices for individual symbols.
* **`CPILatestNumbers`**: Stores the latest Consumer Price Index (CPI) reports (Seasonally and Non-Seasonally Adjusted).
* **`FederalTaxRates`** & **`FederalStandardDeductions`**: Lookup tables for federal tax logic based on filing status.

## 2. Views
Views are used to abstract complex filtering logic and moving average calculations.

### `vw_MostRecentBalances`
* **Description**: Returns the most recent valid balance for each account.
* **Error Handling**: Implements logical error handling by filtering out rows where the `[Error]` column is populated or the `[Balance]` is zero/negative.
* **Logic**: Uses `ROW_NUMBER()` to find the last "Good" record, preventing temporary scraping failures from breaking downstream dashboards.

### `vw_AccountBalancesByTaxTypeAndCategory`
* **Description**: Aggregates account balances by Tax Type and Category.
* **Logic**: Filters out specific categories (529, Liability, Operational-Cash) and non-account types. Handles NULLs for defensive coding.

### `vw_CompositePortfolio_MovingAverage`
* **Description**: Calculates a 14-day (2-week) moving average for the Composite Portfolio.
* **Logic**: Determines the percentage of the current price relative to historical maximums per TaxType. Uses `NULLIF` to prevent divide-by-zero exceptions.

## 3. Stored Procedures
The procedures are categorized by their role in the system: Orchestration, Calculation, Data Update, and Reporting.

### Master Orchestrator
* **`usp_GKUpdate`**: The master orchestration procedure for the daily update process. It executes child procedures in dependency order:
    1.  Update Balances (`usp_GKUpdateTaxableBalancesByDate`)
    2.  Update CPI Data (`usp_GKUpdateCPIU`)
    3.  Run Core Calculations (`usp_GKCalculationUpdate`)
    4.  Update Statistics (`usp_GKUpdateStats` & `usp_GKUpdateStatsMean`)
    5.  Update Weekly/Monthly Paycheck sums (`usp_GKWeeklyMonthlyPaycheck`)
    6.  Update YTD Summaries (`usp_GKCashFlowYTDSums`, `usp_GKCashFlowYTDLast`, `usp_GKCashFlowYTDNetWorth`)

### Core Logic & Strategy
* **`usp_GKCalculationUpdate`**: Performs the Guyton-Klinger capital preservation and prosperity rule calculations. It determines guardrail limits based on inflation-adjusted withdrawals and applies pay raises/cuts.
* **`usp_GetWithdrawalStrategy`**: Calculates a dynamic withdrawal strategy using a 2-week moving average.
    * **> 90% Valuation**: "100% from sale of assets."
    * **< 80% Valuation**: "100% from cash."
    * **80% - 90%**: Linear interpolation (sliding scale) between assets and cash.
* **`usp_GKUpdateCPIU`**: Fetches latest CPI-U data and calculates daily inflation adjustments. Includes backtracking logic to find the last valid CPI number if the current date's data is missing.

### Data Ingestion & Updates
* **`usp_AddManualBalance`**: Inserts a manual balance entry (specifically for Voya 401(k)) to address missing data gaps. Enforces a "One Entry Per Day" business rule.
* **`usp_CalculateCompositePrices`**: Calculates weighted composite prices for active portfolio symbols using `Sum(Price * (PortfolioPercent / 100))`.
* **`usp_Alert_CompositePortfolioUpdate`**: Checks if the 2-Week Moving Average Percent has crossed a 10% threshold and sends an HTML email alert via Database Mail.

### Reporting & Excel Extracts
These procedures are designed specifically to feed Excel data connections:
* **`usp_BalanceHistogramExcelTable`**: Generates a histogram of balance updates grouped by hour of day and day of week.
* **`usp_GetPortfolioExcelTable`**: Retrieves active portfolio data, converting integer percentages to decimal scale (0.0 - 1.0).
* **`usp_GKGetCashFlowByYearExcelTable`**: Retrieves detailed cash flow and calculation data for a specific year.
* **`usp_GKStatsExcelTable`**: Retrieves Year-Over-Year stats with custom sorting (Chronological, then 'Goal', then 'Mean').
* **`usp_RankingsExcelTable`**: Generates a ranked list of account updates with a date range footer.

## 4. Error Handling Strategy
* **Transactions**: `SET XACT_ABORT ON` is used in key procedures to ensure immediate rollback on severe errors.
* **Try/Catch**: Procedures utilize `BEGIN TRY...BEGIN CATCH` blocks to capture error severity and state, re-raising them to the calling application.
* **Defensive Views**: Views filter out specific error codes logged during scraping to prevent "poison" data from breaking reports.

## License

This project is licensed under the [GPL-3.0 License](LICENSE.txt).