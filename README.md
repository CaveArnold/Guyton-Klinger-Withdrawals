# Guyton-Klinger Withdrawals Database Documentation

**Database Name:** `[Guyton-Klinger-Withdrawals]`

**Developer:** Cave Arnold

**AI Assistant:** Gemini

**Script Date:** February 21, 2026


## Overview
This database implements a financial withdrawal strategy based on the Guyton-Klinger decision rules. It manages account balances, tracks portfolio performance against moving averages, calculates inflation adjustments (CPI-U), and enforces capital preservation and prosperity guardrails to determine safe withdrawal rates.

## Mermaid Data Flow Visualization

[![](https://mermaid.ink/img/pako:eNqVV9tu2zYYfhVCRYoUiJ3YieNEWzskcZsFSZcghwZZXQSURNlaZFElqThu07tdbMOAbiiwYbvZVfcMe569wPYI-ymK1CGS0-Um4n_ix-8_kH5rudQjlm2NGI7H6HQwjBD8LSygAfGDiKATMQsJV1I3xJyDHE2Jg_wgDO0HpOP3fLLEBaNXxH6w0un1N51s2ZoGnhjb3fjms4q_p919399014y777grXe9e95hRV--_4ffIpgnQJX1vtXtvAJoIDWCV9Pye8e87HR_X-qsIPHEUUefEuTyhCXMJRy-H1r9__PiTlKEBFhhliqH1SnnJvxPyOiGRSxal8fs_EY7j9ogInonbAf3cYctPFrdclyaRQNs4xJGM7szQKb5Bp7OYPBpaj2zbBvbzuG4YuFcmOhpaYyFibi8v391geWiB_jAmETomLmXe0MrjbB-cpNA-fCc_2yN6rfDsHO21ztBe5IdYBDRKD9iMA1wLEKbTadsJuQy27MbBMoQgXLSiZOIQxttjMZmH6DlmV0TI_RSw76EWKX3ddulEQVMGaCekPIhG6IgFwFcztjxeASLXIechOSc4FGOf0UhoKAVRDmgvuobzTQik74gy4dMwoHMAFWLA3oVVExYSeXcKUZ7HwZyoKvz123_-eo92k5mgUWs_BFoIa50HYuwxPMUhN-al2sy_TNg98OQy4Zen2Al1kX_4mCuQUpQCpYWUFe5LoMpzaFuvgYZXwIPnlM2hvrQlfB6kFfKVKpAmD5VvlW7jWxQ2OJqc7NDID0ba1Yhr3AqMl-jZwaGbqI64fBqN5KAEgv7-_TdJf0GJMuUilC4jHtQodYmXsLROK8QdMncMh2cYTF9CtITHl7v7Z7EHnOiC54KwkqEMI0HLkVgOVyENMJnMVILDeJGp1Ort2cDsuDUaMTKSSTFDiDdvKTeR-azEB9GZbhA9Rra8bxLVKvPD7e7n0Qq8FlnZTTCD8g6guh-i4ySch_BEskZGMxOUiLw7tDI7OucwXK45wODQZsQNOGz8f_g-EVjcITsVqh0u6AWSywD6yb2PVjqJocIF0fE0GcRoVO2r0OckGI2FLDjCfMomMrH1GzRWONRrufd_SGXogI4Ct6n5ZZL4-FlIp7q7colCNoBEzYotkg7Iunbd3VcEmkAXBLPDa8Lk_1TVNCAMV3o4GIrmtLr8uzgd3MUNwqbJMGeAHpMYNoORdHmAZ9C0isOfc3lhFqDFpzcuCdEzQryawQAulymlppSgbDW67ZmkI_VPc9JYRTJKpSLT5Se6SuoKXWOY_ET3L6HItXs2aKSIAlmTTwxxjKMrHUJ-A4f3gTdJqrs5DxMRJyKr7l8-ysn9IuAJDoM3akY9RFsRDmeyOUs5STddzHpCZW4A2XAozCGubnt4YOb2L4I3-mmVvj5Ku1QdCkjlI1za51euTHj2Fjcvvlbrye3W0d6tuXiVXr7EpOrEhcMSfisvWqUpvIOMb_n6jCqPntTuOY4A9W31Fi2ALd57-R0FK2VRvLbQ48dPSnfSHBMDvFa7uz9HqaZElLcooFTzq8CkeWnDKWswFSUpEWcxJ0wAo_mI0CQAVBPFwM4Wma-XXqb5RbhQFyeXmHD6nPqSSsOlZ7GhFsIQpfcVR3B66fvFbclLfZcgHOEZMAbP0IfoIJgE9QeqAVLgFCZjndgsq3RlNplVseRy1vSoVkaVYmsyK4mUUW5gMp-P3kL2KyfUs1YrzTny-dmMTM_JmrrSM7BBJedZAakaTUWYGlfqkc6cXJ5jrCgkljq5BFInlyiqcjXfpBDGmLVkjVjgWbZgCVmyJgReFnJpvZXGQ0uMyQQmsQ2fHvFxEgr50-UduMU4-prSifZkNBmNLduHnySwStKSHARY3gZGymAUErYjfw1bdmetkwax7LfWjWW3Vjd67c5Gb311faXf3dzsr64tWTPLXt9o9_vdtbXe-kpnvddf675bst6k-3ba3U5vo7MKHv3-Zn-j1333H0CIfVE?type=png)](https://mermaid.live/edit#pako:eNqVV9tu2zYYfhVCRYoUiJ3YieNEWzskcZsFSZcghwZZXQSURNlaZFElqThu07tdbMOAbiiwYbvZVfcMe569wPYI-ymK1CGS0-Um4n_ix-8_kH5rudQjlm2NGI7H6HQwjBD8LSygAfGDiKATMQsJV1I3xJyDHE2Jg_wgDO0HpOP3fLLEBaNXxH6w0un1N51s2ZoGnhjb3fjms4q_p919399014y777grXe9e95hRV--_4ffIpgnQJX1vtXtvAJoIDWCV9Pye8e87HR_X-qsIPHEUUefEuTyhCXMJRy-H1r9__PiTlKEBFhhliqH1SnnJvxPyOiGRSxal8fs_EY7j9ogInonbAf3cYctPFrdclyaRQNs4xJGM7szQKb5Bp7OYPBpaj2zbBvbzuG4YuFcmOhpaYyFibi8v391geWiB_jAmETomLmXe0MrjbB-cpNA-fCc_2yN6rfDsHO21ztBe5IdYBDRKD9iMA1wLEKbTadsJuQy27MbBMoQgXLSiZOIQxttjMZmH6DlmV0TI_RSw76EWKX3ddulEQVMGaCekPIhG6IgFwFcztjxeASLXIechOSc4FGOf0UhoKAVRDmgvuobzTQik74gy4dMwoHMAFWLA3oVVExYSeXcKUZ7HwZyoKvz123_-eo92k5mgUWs_BFoIa50HYuwxPMUhN-al2sy_TNg98OQy4Zen2Al1kX_4mCuQUpQCpYWUFe5LoMpzaFuvgYZXwIPnlM2hvrQlfB6kFfKVKpAmD5VvlW7jWxQ2OJqc7NDID0ba1Yhr3AqMl-jZwaGbqI64fBqN5KAEgv7-_TdJf0GJMuUilC4jHtQodYmXsLROK8QdMncMh2cYTF9CtITHl7v7Z7EHnOiC54KwkqEMI0HLkVgOVyENMJnMVILDeJGp1Ort2cDsuDUaMTKSSTFDiDdvKTeR-azEB9GZbhA9Rra8bxLVKvPD7e7n0Qq8FlnZTTCD8g6guh-i4ySch_BEskZGMxOUiLw7tDI7OucwXK45wODQZsQNOGz8f_g-EVjcITsVqh0u6AWSywD6yb2PVjqJocIF0fE0GcRoVO2r0OckGI2FLDjCfMomMrH1GzRWONRrufd_SGXogI4Ct6n5ZZL4-FlIp7q7colCNoBEzYotkg7Iunbd3VcEmkAXBLPDa8Lk_1TVNCAMV3o4GIrmtLr8uzgd3MUNwqbJMGeAHpMYNoORdHmAZ9C0isOfc3lhFqDFpzcuCdEzQryawQAulymlppSgbDW67ZmkI_VPc9JYRTJKpSLT5Se6SuoKXWOY_ET3L6HItXs2aKSIAlmTTwxxjKMrHUJ-A4f3gTdJqrs5DxMRJyKr7l8-ysn9IuAJDoM3akY9RFsRDmeyOUs5STddzHpCZW4A2XAozCGubnt4YOb2L4I3-mmVvj5Ku1QdCkjlI1za51euTHj2Fjcvvlbrye3W0d6tuXiVXr7EpOrEhcMSfisvWqUpvIOMb_n6jCqPntTuOY4A9W31Fi2ALd57-R0FK2VRvLbQ48dPSnfSHBMDvFa7uz9HqaZElLcooFTzq8CkeWnDKWswFSUpEWcxJ0wAo_mI0CQAVBPFwM4Wma-XXqb5RbhQFyeXmHD6nPqSSsOlZ7GhFsIQpfcVR3B66fvFbclLfZcgHOEZMAbP0IfoIJgE9QeqAVLgFCZjndgsq3RlNplVseRy1vSoVkaVYmsyK4mUUW5gMp-P3kL2KyfUs1YrzTny-dmMTM_JmrrSM7BBJedZAakaTUWYGlfqkc6cXJ5jrCgkljq5BFInlyiqcjXfpBDGmLVkjVjgWbZgCVmyJgReFnJpvZXGQ0uMyQQmsQ2fHvFxEgr50-UduMU4-prSifZkNBmNLduHnySwStKSHARY3gZGymAUErYjfw1bdmetkwax7LfWjWW3Vjd67c5Gb311faXf3dzsr64tWTPLXt9o9_vdtbXe-kpnvddf675bst6k-3ba3U5vo7MKHv3-Zn-j1333H0CIfVE)

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