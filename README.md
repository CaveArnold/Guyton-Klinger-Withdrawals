# Guyton-Klinger Withdrawals Database Documentation

**Database Name:** `[Guyton-Klinger-Withdrawals]`
**Developer:** Cave Arnold
**AI Assistant:** Gemini
**Script Date:** February 10, 2026

## Overview
This database implements a financial withdrawal strategy based on the Guyton-Klinger decision rules. It manages account balances, tracks portfolio performance against moving averages, calculates inflation adjustments (CPI-U), and enforces capital preservation and prosperity guardrails to determine safe withdrawal rates.

## Mermaid Data Flow Visualization

[![](https://mermaid.ink/img/pako:eNqVV91u2zYUfhVCRYsUiJ3YjmNHWzskcZsFyZYgTlpkdRFQEmWrkUWVpOK4Te92sQ0DuqHAhu1mV90z7Hn2Atsj7FAUKcmRnC43Ec8fP37nh_Rby6UesWxrzHA8QaeDUYTg7_59NCB-EBE0FPOQcCV1Q8w5yNGMOMgPwtC-R1p-1yerXDB6Sex7661ub8vJlo1Z4ImJ3Y6vP1vw97S77_tb7oZx9x13ve3d6R4z6ur9-36XbJkAbdLzOu07A9BEaAAd0vW7xr_ntHxc6a8i8MRRRD0nzsWQJswlHL0YWf_-8eNPUoYGWGCUKUbWS-Ul_4bkdUIil6xI4_d_IhzHzTERPBM3A_q5w9Yer2y7Lk0igXZwiCMZ3ZmjU3yNTucxeTiyHtq2Dezncd0wcC9NdDSyJkLE3F5bu73B2sgC_VFMInRCXMq8kZXH2TkcptA-fCc_m2N6pfDsHu83ztB-5IdYBDRKD1iPA1wLEGazWdMJuQy25sbBGoQgXDSiZOoQxpsTMV2G6CvMLomQ-ylg30MtUvq66dKpgqYM0G5IeRCN0TELgK96bHm8AkSuQ9YhIZF3K_kyhoM5UZn_9dt__nqP9pK5oFHjIAQohDWeB2LiMTzDITfmpXrIv0zYffDkkuSLU-yEurA-fMwVSClKgdLkZcXyApjyHNrUa-DiJZDhOWVzyKm2hM_DNCtfq6TUeSiOFcXGtyiscTymTPg0DOgujfxgrF2NuMKtwHiJnl0cuomqwosn0VgOJyDo799_k_QXlChTrkC5MOJBXVCXeAlLa2OBuCPmTuDwDIPpC4iW8Phi7-As9oATXWRcEFYylGEkaDmGyuEWSANMJjMLwaGlZSq1emc-MDtuj8eMjGVSTOPz-i3lJjKfC_FBdKbC5a277b1KuJiSSCwPt3eQRyvwWmRlL8EMyjuA6n6ATpJwGcKhZI2M5yYoEXl3aGV2dM6hoa84wODQZsQNOGz8f_geCixukZ0K1Q7n9BzJZQD95N5FK53GUOGC6HiaDGI0qvZV6OckGE-ELDjCfMqmMrHVG9RWONRrufd_SGXokI4Dt675ZZL45GlIZ7q7colCNoBEzYstkk7JqnbdO1AEmkDnBLOjK8Lk_1RVNyAMV3o4GIqWtLr8Oz8d3MYNwrrJsGSAnpAYNoORdHGI59C0isOfc3lhFqCVJ9cuCdFTQryKwQAuFymlppSgbDW6nbmkI_VPc1JbRTLKQkWmy090ldQVusYw-YnuX0KRa_ds0EgRBbKmnxjiBEeXOoT8Bg7vAm-SVHVzHiUiTkRW3b98lJP7WcATHAZv1Ix6gLYjHM5lc5Zykm66kvWEytwAsuFQmENcXfnwqMvtnwVv9HMmvfFLuyw6FJDKh6-0z69cmfDs_Xsc4sBDjcbjm-3j_Rtz6yqlfPpI1dCFkxJ-I29ZpSk8PIxv-e7MNy_eY_mdAytlUbyG0KNHj0t3zBITg6VSu3ewRKm6PspbDlCqeVRgxrxW4YAVmIqSlIOzmBMmgKS85TUJANVEMbCzRebrpZdjfrHdr4qTS0w4fU596aTh0rPY8IIOQ5TePxzB6aXvFzclL_VdgnCM58AYvC0foMNgGlQfqAJIgVOYdFVis1ykK7PJrIpVlLOmR29WteUnWJ1ZSaSMcgOT-XyUFrK_cEI9O7XSnCOfh_XI9NyrqCs902pUcj4VkKpRU4SpcaUe6QzJ5TnGBYXEUiWXQKrkEsWiXM0rKYSxZK3Cb-3As2zBErJqTQm8FOTSeiuNR5aYkClMVhs-PeLjJBTyp8g7cItx9A2lU-3JaDKeWLYPPzFglaQlOQiwnO5GymC0EbYrf1FadqfXT4NY9lvr2rIbnX632ep3Nzub67321lavs7FqzS17s9_s9dobG93N9dZmt7fRfrdqvUn3bTXbrW6_1QGPXm-r1--23_0HmI87_A?type=png)](https://mermaid.live/edit#pako:eNqVV91u2zYUfhVCRYsUiJ3YjmNHWzskcZsFyZYgTlpkdRFQEmWrkUWVpOK4Te92sQ0DuqHAhu1mV90z7Hn2Atsj7FAUKcmRnC43Ec8fP37nh_Rby6UesWxrzHA8QaeDUYTg7_59NCB-EBE0FPOQcCV1Q8w5yNGMOMgPwtC-R1p-1yerXDB6Sex7661ub8vJlo1Z4ImJ3Y6vP1vw97S77_tb7oZx9x13ve3d6R4z6ur9-36XbJkAbdLzOu07A9BEaAAd0vW7xr_ntHxc6a8i8MRRRD0nzsWQJswlHL0YWf_-8eNPUoYGWGCUKUbWS-Ul_4bkdUIil6xI4_d_IhzHzTERPBM3A_q5w9Yer2y7Lk0igXZwiCMZ3ZmjU3yNTucxeTiyHtq2Dezncd0wcC9NdDSyJkLE3F5bu73B2sgC_VFMInRCXMq8kZXH2TkcptA-fCc_m2N6pfDsHu83ztB-5IdYBDRKD1iPA1wLEGazWdMJuQy25sbBGoQgXDSiZOoQxpsTMV2G6CvMLomQ-ylg30MtUvq66dKpgqYM0G5IeRCN0TELgK96bHm8AkSuQ9YhIZF3K_kyhoM5UZn_9dt__nqP9pK5oFHjIAQohDWeB2LiMTzDITfmpXrIv0zYffDkkuSLU-yEurA-fMwVSClKgdLkZcXyApjyHNrUa-DiJZDhOWVzyKm2hM_DNCtfq6TUeSiOFcXGtyiscTymTPg0DOgujfxgrF2NuMKtwHiJnl0cuomqwosn0VgOJyDo799_k_QXlChTrkC5MOJBXVCXeAlLa2OBuCPmTuDwDIPpC4iW8Phi7-As9oATXWRcEFYylGEkaDmGyuEWSANMJjMLwaGlZSq1emc-MDtuj8eMjGVSTOPz-i3lJjKfC_FBdKbC5a277b1KuJiSSCwPt3eQRyvwWmRlL8EMyjuA6n6ATpJwGcKhZI2M5yYoEXl3aGV2dM6hoa84wODQZsQNOGz8f_geCixukZ0K1Q7n9BzJZQD95N5FK53GUOGC6HiaDGI0qvZV6OckGE-ELDjCfMqmMrHVG9RWONRrufd_SGXokI4Dt675ZZL45GlIZ7q7colCNoBEzYstkk7JqnbdO1AEmkDnBLOjK8Lk_1RVNyAMV3o4GIqWtLr8Oz8d3MYNwrrJsGSAnpAYNoORdHGI59C0isOfc3lhFqCVJ9cuCdFTQryKwQAuFymlppSgbDW6nbmkI_VPc1JbRTLKQkWmy090ldQVusYw-YnuX0KRa_ds0EgRBbKmnxjiBEeXOoT8Bg7vAm-SVHVzHiUiTkRW3b98lJP7WcATHAZv1Ix6gLYjHM5lc5Zykm66kvWEytwAsuFQmENcXfnwqMvtnwVv9HMmvfFLuyw6FJDKh6-0z69cmfDs_Xsc4sBDjcbjm-3j_Rtz6yqlfPpI1dCFkxJ-I29ZpSk8PIxv-e7MNy_eY_mdAytlUbyG0KNHj0t3zBITg6VSu3ewRKm6PspbDlCqeVRgxrxW4YAVmIqSlIOzmBMmgKS85TUJANVEMbCzRebrpZdjfrHdr4qTS0w4fU596aTh0rPY8IIOQ5TePxzB6aXvFzclL_VdgnCM58AYvC0foMNgGlQfqAJIgVOYdFVis1ykK7PJrIpVlLOmR29WteUnWJ1ZSaSMcgOT-XyUFrK_cEI9O7XSnCOfh_XI9NyrqCs902pUcj4VkKpRU4SpcaUe6QzJ5TnGBYXEUiWXQKrkEsWiXM0rKYSxZK3Cb-3As2zBErJqTQm8FOTSeiuNR5aYkClMVhs-PeLjJBTyp8g7cItx9A2lU-3JaDKeWLYPPzFglaQlOQiwnO5GymC0EbYrf1FadqfXT4NY9lvr2rIbnX632ep3Nzub67321lavs7FqzS17s9_s9dobG93N9dZmt7fRfrdqvUn3bTXbrW6_1QGPXm-r1--23_0HmI87_A)

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