# Guyton-Klinger Withdrawals Database Documentation

**Database Name:** `[Guyton-Klinger-Withdrawals]`

**Developer:** Cave Arnold

**AI Assistant:** Gemini

**Script Date:** February 17, 2026


## Overview
This database implements a financial withdrawal strategy based on the Guyton-Klinger decision rules. It manages account balances, tracks portfolio performance against moving averages, calculates inflation adjustments (CPI-U), and enforces capital preservation and prosperity guardrails to determine safe withdrawal rates.

## Mermaid Data Flow Visualization

[![](https://mermaid.ink/img/pako:eNqVV91OIzcUfhVrVqxYibAkJE2YdqmA7KYIWhCBRZSskGfGk8wyGae2Bwg_d71oq0rbaqVW7U2vts_Q5-kLtI_QY3vsmQkT2OaG8fn5fPydH5sbx6cBcVxnyPBkhA67gwTBb2EBdUkYJQT1xTQmXEv9GHMOcnRJPBRGcew-IfWwFZIlLhg9J-6TlXqrveZly9plFIiR25hcfTrjHxj3MAzX_KZ1Dz1_pRE86j5h1Df7d8IWWbMADdIOVhuPAtBUmABWSStsWf-2Vw9xpb9G4KmniTom3lmfpswnHJ0OnH__-PEnKUNdLDDKFAPnjfaSv_0YR8GitHz3p16g52gTJ-f8M489X1_c8H2aJgJEMU7A2ZuiQ3yFDqcT8mzgPHNdF0jP4TZ3-wrs_Xfyc3lILzTM1v527QhtJ2GMRUQTFU-V_5eYnRMhtRrme0g0pd8s-3SsgbQB2oopj5Ih2mcRBDWLRJLgHjMS08OcaFp-_fafv96hXjoVNKntxABFWO04EqOA4Uscc2teIiv_srDb4Mnlkc4OsRcb1t9_yBVIK0pAiqqM0VM4aeDRZbOGs7yBwwRe2RwYNJbwuYsFoH-Vjj3C5npojjRF1rconOO4T5kIaRzRLZqE0dC4WnGFW4HxEj1bOPZTnfOzl8lQdi4Q9Pfvv0n6C0qUKRch3YwEkFfqkyBlKrczxO0xfwSHZxhMTwEt5ZOz3s7RJABOTJFwQVjJUMLIoGWPluFmSIOYbGZmwKHwZSqNenPatTtuDIeMDGVSbHvw-VvKTWQ-Z_BBdKTh8kbZCN6mXIxJIh6G6-3kaAVei6z0UsygvCOo7qfoII0firAvWSPDqQUlIu8Oo8yOzjk05AWHMDi0GfEjDhv_H777Aot7ZCuh3uGEniC5jKCf_MdopeMJVLggBs-QQaxG176GPibRcCRkwREWUjaWia3eYG6FQ72We_8HJUO7dBj585pfJomPXsX00nRXLtGRdSFR02KLqClX1a69HU2gBTohmO1dECb_KtW8AWG5MsPBUvRAq8vfyWH3ftwgnDcZHhigB2QCm8FIOtvFU2hazeHPubwwC9DiyyufxOgVIUHFYACXM0WpLSUoWxPd5lTSofxVTuZWkUSZqUi1_EhXSV2hayyTH-n-BRS5cc8GjRRRIGv8kRAHcHsbCPkNHD4WvE1S1c25l4pJKrLq_uWDnNyvI57iOLrWM-op2khwPJXNWcqJ2nQx6wmduS5kw6Mwh7i-suHFk9u_jq7N40G9V0q7zDoUIpWvQmmfX7ky4dnjUL9parX124397Vt762olvFGUqu_DSQm_lbes1uQPkdy3fHfmmxfvsfzOgZW2KF5D6MWL9dId84CJjaVS29t5QKm7PslbDqLU86jAjAlBHrAipqJEcXA04YQJIClveUMChGpRbNjZIvMN1OWYX2wLVTi5xMKZc5pLR8Gps7ioT-IYqfuHIzi99P38tuSlv0sh7OMpMOafQ9nuRuOo-kAVgRQ4hUlXJbbLWboym8yqWEU5a2b0ZlVbfoLNMyuJtFFuYDOfj9JC9mdOaGanUdpz5PNwfmRm7lXUlZlpc1RyPhUi1aOmGKaJS3moGZLL8xhnFDKWKrkMpEouo5iV63klhTCWnCX4RzQKHFewlCw5YwIvBbl0bqTxwBEjMobJ6sJnQEKcxmLgDJI7cJvg5GtKx8aT0XQ4ctwQ_sWAVapKshthOd2tlMFoI2xL_tvluPXOigJx3BvnynHby41Go9Ve7dQ7rcZqp9lZcqaOW6uvLjdbK51mG37NtWandbfkXKtt68srjZV6u11vdhrtziedxt1_AafwQw?type=png)](https://mermaid.live/edit#pako:eNqVV91OIzcUfhVrVqxYibAkJE2YdqmA7KYIWhCBRZSskGfGk8wyGae2Bwg_d71oq0rbaqVW7U2vts_Q5-kLtI_QY3vsmQkT2OaG8fn5fPydH5sbx6cBcVxnyPBkhA67gwTBb2EBdUkYJQT1xTQmXEv9GHMOcnRJPBRGcew-IfWwFZIlLhg9J-6TlXqrveZly9plFIiR25hcfTrjHxj3MAzX_KZ1Dz1_pRE86j5h1Df7d8IWWbMADdIOVhuPAtBUmABWSStsWf-2Vw9xpb9G4KmniTom3lmfpswnHJ0OnH__-PEnKUNdLDDKFAPnjfaSv_0YR8GitHz3p16g52gTJ-f8M489X1_c8H2aJgJEMU7A2ZuiQ3yFDqcT8mzgPHNdF0jP4TZ3-wrs_Xfyc3lILzTM1v527QhtJ2GMRUQTFU-V_5eYnRMhtRrme0g0pd8s-3SsgbQB2oopj5Ih2mcRBDWLRJLgHjMS08OcaFp-_fafv96hXjoVNKntxABFWO04EqOA4Uscc2teIiv_srDb4Mnlkc4OsRcb1t9_yBVIK0pAiqqM0VM4aeDRZbOGs7yBwwRe2RwYNJbwuYsFoH-Vjj3C5npojjRF1rconOO4T5kIaRzRLZqE0dC4WnGFW4HxEj1bOPZTnfOzl8lQdi4Q9Pfvv0n6C0qUKRch3YwEkFfqkyBlKrczxO0xfwSHZxhMTwEt5ZOz3s7RJABOTJFwQVjJUMLIoGWPluFmSIOYbGZmwKHwZSqNenPatTtuDIeMDGVSbHvw-VvKTWQ-Z_BBdKTh8kbZCN6mXIxJIh6G6-3kaAVei6z0UsygvCOo7qfoII0firAvWSPDqQUlIu8Oo8yOzjk05AWHMDi0GfEjDhv_H777Aot7ZCuh3uGEniC5jKCf_MdopeMJVLggBs-QQaxG176GPibRcCRkwREWUjaWia3eYG6FQ72We_8HJUO7dBj585pfJomPXsX00nRXLtGRdSFR02KLqClX1a69HU2gBTohmO1dECb_KtW8AWG5MsPBUvRAq8vfyWH3ftwgnDcZHhigB2QCm8FIOtvFU2hazeHPubwwC9DiyyufxOgVIUHFYACXM0WpLSUoWxPd5lTSofxVTuZWkUSZqUi1_EhXSV2hayyTH-n-BRS5cc8GjRRRIGv8kRAHcHsbCPkNHD4WvE1S1c25l4pJKrLq_uWDnNyvI57iOLrWM-op2khwPJXNWcqJ2nQx6wmduS5kw6Mwh7i-suHFk9u_jq7N40G9V0q7zDoUIpWvQmmfX7ky4dnjUL9parX124397Vt762olvFGUqu_DSQm_lbes1uQPkdy3fHfmmxfvsfzOgZW2KF5D6MWL9dId84CJjaVS29t5QKm7PslbDqLU86jAjAlBHrAipqJEcXA04YQJIClveUMChGpRbNjZIvMN1OWYX2wLVTi5xMKZc5pLR8Gps7ioT-IYqfuHIzi99P38tuSlv0sh7OMpMOafQ9nuRuOo-kAVgRQ4hUlXJbbLWboym8yqWEU5a2b0ZlVbfoLNMyuJtFFuYDOfj9JC9mdOaGanUdpz5PNwfmRm7lXUlZlpc1RyPhUi1aOmGKaJS3moGZLL8xhnFDKWKrkMpEouo5iV63klhTCWnCX4RzQKHFewlCw5YwIvBbl0bqTxwBEjMobJ6sJnQEKcxmLgDJI7cJvg5GtKx8aT0XQ4ctwQ_sWAVapKshthOd2tlMFoI2xL_tvluPXOigJx3BvnynHby41Go9Ve7dQ7rcZqp9lZcqaOW6uvLjdbK51mG37NtWandbfkXKtt68srjZV6u11vdhrtziedxt1_AafwQw)

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
