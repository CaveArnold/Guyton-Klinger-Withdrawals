# Guyton-Klinger Withdrawals Database Documentation

**Database Name:** `[Guyton-Klinger-Withdrawals]`

**Developer:** Cave Arnold

**AI Assistant:** Gemini

**Script Date:** February 21, 2026


## Overview
This database implements a financial withdrawal strategy based on the Guyton-Klinger decision rules. It manages account balances, tracks portfolio performance against moving averages, calculates inflation adjustments (CPI-U), and enforces capital preservation and prosperity guardrails to determine safe withdrawal rates.

## Mermaid Data Flow Visualization

[![](https://mermaid.ink/img/pako:eNqtWN1u4zYWfhVCRSYpkDi2E-dHu53CSTqpkaQxxskE2XER0BJlqyOLKkXF8SS560V3UaBdFNiivWlvus-wz7MvsPsIPSRFUnIsO0XrG0vnj4fn5-Oh7h2P-sRxnZWV-zAOuYvu0SofkTF5g1mIBxFJVyUtoDHvhe8JvK1u1ZO71XVFe4XHYTQV1DbIR5p8RcLhiAvygEb-Knp8fFxZ6cdDhpMRujjqxwh-KyvoiARhTFCPT2ElRfUinKZARxMyQEEYRe4HpBG0ArKeckbfEfeDeqO1uz_IXzcmoc9H7nZy95cZfV-rB0Gw720b9WDg1Zv-UvWEUU-vvxe0yL4x0CS7_lZzqQGace3AFmkFLaO_O2gEuFLfRgXygGK6MYGgocNeD4kIllaI6ZXgTUYhJxtpgj3iAk3Igy0lm2YDFfQrMrjp0Yx5JEVv-87_f_7mO0FDR5hjlDP6zudKS_x65MuMxB5ZE8Lf_hvhJKkNCU9zci2kfx2wzZdrbc-jWczRAY5wLKwPpugC36GLaUI-7Dsfuq4LmbR2vSj03hnrqO-MOE9Sd3NzGPJRNqh5dLx5iG9Jm8VQOptasO-A6HlCYvSaeJT5fceaPDjtSS-__1o81ob0Vrl22O1sXKJOHESYhzSWe612CVSXegMWex7Ek7BF_pxh9o5wsZpy6-9Q4JR-KYwpx5QAOoxoGsZD1GUhBK7aM2tvqYNWtDNOKOOLHb0iOOKjgEHHak8LJOtvJ74lKR8TSHMXjAY0CukCfws2ljpckF3kaScGPXKKB9pPUY6hJEZ4QBnmlE2lbeVxj3oAR1BmXsZCPkWfdd9U-2uML_XWSC7ytR0J8DOOyjcbyy6JU1GMOPbRaRgQWD3NmGidxU4qqwUPJ5NJzRrfrPKIxL41ZZ8AZtpJEk1RyBGnEmsMVnSODNYYvCkBiAKeJxgjym6AU6IA5oev_vefb9FxNuU03jiJoNAJ27iCsPoMT3CUGvES7Ngn6w5opqKBby7kiaTMf_-rZSDFKBmSwJBj0ltIhj-gNf0OQf4couwPyuLQ3VoSHk8xB-ufZeMBYZUaqoNVAxvdIrFC0bTRIY2DcKhVDXmOmkzkH0jgkzCWs1gK-SGOvEyh5s0n8VCcRhD0__70o0hpgYly5hoAHCM-IBn1iJ8xiWYzyThn3ggckK36FqxlaXJzfHKZ-BBnDYspAFZJUJgRgRCncdncTCLAJ5PtGeNwGokNa_bB9Mis2B4OGRmKRJszK61eUiwiamTGPpAuNU7qo6btf5EpxFxs7vjEWivEtRiV4wwzaJkQOuYFep1FizzsiaiR4dQYJdx2nGbmW09TOIJuU3AjhdYlXihg6ffEu8cxfxJsSVQrXNNrJF5DqDpvWVgpHFcpzDHang4GMRzVT8q0mi9FwREWUDYWiZ2_wB_tmjmdsKhvoAvKKPUPSUOndBh6VTAlUp-OXkV0onHAUtR-jyD906Iv8vSdByzHJyotxtA1wez8ljDxL1lVUGYyoGHMBH4BKInf9cXRU7-BWIVhf8JhVIzzgnS8JmIGAiy-OcVTQBaVkn9aegGw0Nondx6J0CtC_DnoBSo3MkOm3qG39GYPpiK6Ul86VVnqwspM28jXZ6qKTBRa2yTmmeqfQidq9RwNBYlCsMbPNPEax--0CfEMMVzm_J-V89lklvM-Z5VnrqCsm9mlYrY5z3iS8byr__WrOAffhGkGA9h7hfgvUDvG0VRAXal4dHR6B5efruWQYG4_eRaQwk5kspGqMRCukDOGOl1905k7k1epQV--0orHJwryReFWyV-fX6sr1Q-_IFHaiAKCqCeNIbN6b8L33TO9hvEIndE4hHN8joIaa6Xa0rnb2DPmnj3s_q4q0FkuF4G4kovLl503Rezy7xUmlxsbLx_a3c6DmToVX1wrBUvdG9MHMWUqTuFaZ3TLs2M8c0mTcmc4hrJ7mB0hlbC9yhRFr_Unl_wS8YRn9lmc7ewcBm9KojiaoY8-elmauxaImD3P5R6fLGCqeotLCVWnaSEJ5uMD7GyOT0WK3PxlkhLGIRn2wNJBAFeNFeN2_pLr-nJgtMPeyjw7lmLM6X3qQUyak3txoYyiCMmZLEWwe6H78UNJSz2XXOjiKUQMuugFXCXH4fwNzXGkEFNI_zyyeZ0NVy6TSxWr1UZNDw5KaKZOq8RKJCVkBUzm7cldyP7MDvVRrZlmH_b4rfZMH7Nz6kofoRUscRwWPFVQUnRT-yU1DCxbnvXTYLBlCp8sr9O1HOGS5eQnjWULtxaw7aISiecsKOnOujNkoe-4nGVk3RkTmLnFq3MvNPqO_Gbcd1x49EmAs4gLSH4EtQTHf6N0rDUZzYYjxw1wlMJbJgv5KMTi0DMigOKEHYqvio6726hLG45779w5bqO5Vdtv7G3v1Bs7zZ39ne3mujN13K2dWr3e3Gs09-t7O3ut3Vbrcd15L5et1_ab9WarUd9tbLe26vvbrXWH-OIQOVOfvuUX8MffAO1gbFw?type=png)](https://mermaid.live/edit#pako:eNqtWN1u4zYWfhVCRSYpkDi2E-dHu53CSTqpkaQxxskE2XER0BJlqyOLKkXF8SS560V3UaBdFNiivWlvus-wz7MvsPsIPSRFUnIsO0XrG0vnj4fn5-Oh7h2P-sRxnZWV-zAOuYvu0SofkTF5g1mIBxFJVyUtoDHvhe8JvK1u1ZO71XVFe4XHYTQV1DbIR5p8RcLhiAvygEb-Knp8fFxZ6cdDhpMRujjqxwh-KyvoiARhTFCPT2ElRfUinKZARxMyQEEYRe4HpBG0ArKeckbfEfeDeqO1uz_IXzcmoc9H7nZy95cZfV-rB0Gw720b9WDg1Zv-UvWEUU-vvxe0yL4x0CS7_lZzqQGace3AFmkFLaO_O2gEuFLfRgXygGK6MYGgocNeD4kIllaI6ZXgTUYhJxtpgj3iAk3Igy0lm2YDFfQrMrjp0Yx5JEVv-87_f_7mO0FDR5hjlDP6zudKS_x65MuMxB5ZE8Lf_hvhJKkNCU9zci2kfx2wzZdrbc-jWczRAY5wLKwPpugC36GLaUI-7Dsfuq4LmbR2vSj03hnrqO-MOE9Sd3NzGPJRNqh5dLx5iG9Jm8VQOptasO-A6HlCYvSaeJT5fceaPDjtSS-__1o81ob0Vrl22O1sXKJOHESYhzSWe612CVSXegMWex7Ek7BF_pxh9o5wsZpy6-9Q4JR-KYwpx5QAOoxoGsZD1GUhBK7aM2tvqYNWtDNOKOOLHb0iOOKjgEHHak8LJOtvJ74lKR8TSHMXjAY0CukCfws2ljpckF3kaScGPXKKB9pPUY6hJEZ4QBnmlE2lbeVxj3oAR1BmXsZCPkWfdd9U-2uML_XWSC7ytR0J8DOOyjcbyy6JU1GMOPbRaRgQWD3NmGidxU4qqwUPJ5NJzRrfrPKIxL41ZZ8AZtpJEk1RyBGnEmsMVnSODNYYvCkBiAKeJxgjym6AU6IA5oev_vefb9FxNuU03jiJoNAJ27iCsPoMT3CUGvES7Ngn6w5opqKBby7kiaTMf_-rZSDFKBmSwJBj0ltIhj-gNf0OQf4couwPyuLQ3VoSHk8xB-ufZeMBYZUaqoNVAxvdIrFC0bTRIY2DcKhVDXmOmkzkH0jgkzCWs1gK-SGOvEyh5s0n8VCcRhD0__70o0hpgYly5hoAHCM-IBn1iJ8xiWYzyThn3ggckK36FqxlaXJzfHKZ-BBnDYspAFZJUJgRgRCncdncTCLAJ5PtGeNwGokNa_bB9Mis2B4OGRmKRJszK61eUiwiamTGPpAuNU7qo6btf5EpxFxs7vjEWivEtRiV4wwzaJkQOuYFep1FizzsiaiR4dQYJdx2nGbmW09TOIJuU3AjhdYlXihg6ffEu8cxfxJsSVQrXNNrJF5DqDpvWVgpHFcpzDHang4GMRzVT8q0mi9FwREWUDYWiZ2_wB_tmjmdsKhvoAvKKPUPSUOndBh6VTAlUp-OXkV0onHAUtR-jyD906Iv8vSdByzHJyotxtA1wez8ljDxL1lVUGYyoGHMBH4BKInf9cXRU7-BWIVhf8JhVIzzgnS8JmIGAiy-OcVTQBaVkn9aegGw0Nondx6J0CtC_DnoBSo3MkOm3qG39GYPpiK6Ul86VVnqwspM28jXZ6qKTBRa2yTmmeqfQidq9RwNBYlCsMbPNPEax--0CfEMMVzm_J-V89lklvM-Z5VnrqCsm9mlYrY5z3iS8byr__WrOAffhGkGA9h7hfgvUDvG0VRAXal4dHR6B5efruWQYG4_eRaQwk5kspGqMRCukDOGOl1905k7k1epQV--0orHJwryReFWyV-fX6sr1Q-_IFHaiAKCqCeNIbN6b8L33TO9hvEIndE4hHN8joIaa6Xa0rnb2DPmnj3s_q4q0FkuF4G4kovLl503Rezy7xUmlxsbLx_a3c6DmToVX1wrBUvdG9MHMWUqTuFaZ3TLs2M8c0mTcmc4hrJ7mB0hlbC9yhRFr_Unl_wS8YRn9lmc7ewcBm9KojiaoY8-elmauxaImD3P5R6fLGCqeotLCVWnaSEJ5uMD7GyOT0WK3PxlkhLGIRn2wNJBAFeNFeN2_pLr-nJgtMPeyjw7lmLM6X3qQUyak3txoYyiCMmZLEWwe6H78UNJSz2XXOjiKUQMuugFXCXH4fwNzXGkEFNI_zyyeZ0NVy6TSxWr1UZNDw5KaKZOq8RKJCVkBUzm7cldyP7MDvVRrZlmH_b4rfZMH7Nz6kofoRUscRwWPFVQUnRT-yU1DCxbnvXTYLBlCp8sr9O1HOGS5eQnjWULtxaw7aISiecsKOnOujNkoe-4nGVk3RkTmLnFq3MvNPqO_Gbcd1x49EmAs4gLSH4EtQTHf6N0rDUZzYYjxw1wlMJbJgv5KMTi0DMigOKEHYqvio6726hLG45779w5bqO5Vdtv7G3v1Bs7zZ39ne3mujN13K2dWr3e3Gs09-t7O3ut3Vbrcd15L5et1_ab9WarUd9tbLe26vvbrXWH-OIQOVOfvuUX8MffAO1gbFw)

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