# Guyton-Klinger Withdrawals Database Documentation

**Database Name:** `[Guyton-Klinger-Withdrawals]`

**Developer:** Cave Arnold

**AI Assistant:** Gemini

**Script Date:** April 20, 2026


## Overview
This database implements a financial withdrawal strategy based on the Guyton-Klinger decision rules. It manages account balances, tracks portfolio performance against moving averages, calculates inflation adjustments (CPI-U), and enforces capital preservation and prosperity guardrails to determine safe withdrawal rates.

## Mermaid Data Flow Visualization

[![](https://mermaid.ink/img/pako:eNqtWd1u47gVfhVCg0wyQOzYTpwftzuFk2wyQZKNd5xMkB0vAlqibHVkUUNRSTxJ7nrRFgX2D9hFe9P2Ynvdy32evkD7CD0kRVLyWHIWu7mJeHjO4afzT_necalHnI6ztHQfRAHvoHu0zMdkQt5gFuBhSJJlSfNpxPvBBwKr5fVGfLe8qmgHeBKEU0HtAn-oyZckGI25IA9p6C2jx8fHpaVBNGI4HqPz_UGE4G9pCe0TP4gI6vMpnKSoboiTBOjolgyRH4Rh5xlp-m2frCac0Xek86zRbG_tDLNl7Tbw-LizEd_9Zkbe0-K-7--4G0bcH7qNlrdQPGbU1edv-22yYxS0yJa33lqogKZcA1gnbb9t5LeGTR-XylurgB9QRGu3YDS01-8jYcHCCRG9FHu344CTWhJjl3SAJvhBl-JN0qEy-iUZXvdpylySoLcD539__8vXgoZw5KFuHIeBi3lAI7SPOUYZ48D5UmkRf0eRSyfkBA9XhPR3f0I4juuBJIZ4SBnmlE3rsFz77ZCtvVzpUxcCAvWJm7KAT9FnvTcvBs6LTqcDjrVqXTj5nVWOBs6Y8zjprK2NAj5Oh1LjHr4hXRZBKK0ZzoEDvGcxidBr4lLmDRyrtBuK8JNAv_03wnIlFClkPRIl4lXFq58EPoHTk5ThyCXVIJXWHMLb29u6Vb5WhahP3qcETpCYvvqXNN6I8CQj1wOqsHVdl6YRR7s4FIASNJyic3yHzqcxKUemtS-0nmasgrp70lcu_qN4rI_ojYK21zuqXYCt_NBGSjkkEF2IBjT2XYhOwqrwnGL2jnBxmo68Pqf0vfXnPoYSlLGhvZAmQTRCPRaA-V5IjlopSqt7IVjLejSJKePVoC8JDvnYZ1ALdRjmSBb7UXRDEj4h4PIeKPVpGNCk3Ko5HQsB53irkH6egmISaZTZEuxHJgFhJEtmkPWEWaFMJyIgSQVIraKYKO8VVaKE2uqlLk_WZCkL3FqsTqtMofOUDSkcrZD-ZNYK4QHxCIN6I5K6zzEni1Bq8RxMLkgc30FZ42mgkvpZFaQvoLzT2yyGVWr_MyOijCrRoZVXULRUTJYjKmhb6N4CdxlI8Jo9xT5BjxE1f4oCjjiVjcY0iqN902hMsyl0D9V1PmowIjOGOCGqu_zwh__-9BU6TKecRrXjEEKHsNolvIjH8C0OE8Ne6DH2ycIByUTUm-tzOY4o9d_9aDeQ2igoknUsK6FvwTHekNb1Guz_JTjAGxbZoRhpTng8gQhK-GfpZEhYqYQqNarSGNk8sUTQZPoejfxgpEUNeY6YdOQvcOBHZix6sWDyPRy6qSry159GIzGKgNH_87e_CpfmNlG2uQL1mBEPwpu6xEuZzLoZZ5wxdwwA5JTwFrSlSXx9eHwRe2BnlcCnOIGaWmAUaoQhxChWVDfjCMBkvD2jHDJcvLDe3p3umxO7oxEjI-Fo02KT8iPFISJGZvQD6UKXct0Zu97vU1XUq9UdHlttObvmrXKYYgYpE0DGPEev07AKYV9YjYymRinhNuP0ZvbqSQK98iYBGAmkLnEDMRH9HHuLGvuRsSVRnXBFr2QdDiDq3EVmpdBRExhitT5tDGJ2VD4p1epyIQKOMJ-yiXDs_AN-adbMyYSqvIEsKFapP0saOqGjwC0rU8L1yfgAarmuA5aSn29yWGRXm1dYDo-VW4yiK4LZ2Q1h4r_cKitlxgO6jBnDVxQl8Xd1vv8xbiCW1bBfoRnl7VzhjtdEjGlQi69P8BQqi3LJN5aeK1ho5dM7l4TogBBvTvUCkWvpIRPvkFv6ZXenwrpSXoIqDXWhZSZt5PKJosITudQ2jnmi-CvIRC2eVUNBomCsyRNVvMbRO61CPIMNF4H_tXw-68yi3-ec8sQTlHYzu5TMNmcpj1OeZfX3P4o--CZIUrj7fVAV_znqRjicilJXCB5tnf7uxauVrCSYy1rmBaRqJzLeSNSESFM-o-iopy9mc68NZWKQlwda8PBYlXwRuGX8V2dX6gb4wz-QCG1EoYKoJ11DZuXeBB96p_oMgwid0iiAPj5HQE28UmzhpGv0GXVPHnZ_VhRoLxeDQHyPEfdDO28K22Ufq4wva7WXDzDNQYSmNEHd3tGDmT8Vp7gPCyZVzNXYnjyIqVPt526ilk3qKU6U0cztUnJ_DlMCDE_yFhxBWD7MjphKzH5lEULdSLAaiSv9WS77zFHFom94ggecwse5kw2TuWBVaSreeWbe3FrQuCI_ftpREVaKIz89ok8-eVkYDStYjBvm7h4eV2yqlIgKMacafi5OzOcceMM5mPIUaYSLOCGMQ3zYnqqNAFCNFgM7W2Synpxp7Ty6NE-PpRh1-j31rCjVyXfpQKSHIZJjY4Lg7YXs7x4KUuq5AKGHp2AxSPTn6CSYBPNfaA6QnE0hUuaRzXLWXBlPxpVPHWs1PdsopplUKWMrkBSTZTCet8NFzvszb6inCb1p3sNOCOXI9CQwJ650ly_ZEh07h1RVuzxMjUtKmM5h9yxO0ybspsBk9456dkdAsjtZM7TbAlbFtj1UNos5B0q6s-qMWOA5Hc5SsupMCFwLxNK5FxIDR_6mMXA68OgRH6chF13jEcRiHH1B6URLMpqOxk7Hx2ECq1QG8n6ARV82LNBoCNsT32mdTnN7R-pwOvfOHSxb6_Wd5vbGZqO52drc2dxorTpTp7O-WW80WtvN1k5je3O7vdVuP646H-SxjfpOq9FqNxtbzY32emNno73qEE_0uVP104z8hebx_x_EUKo?type=png)](https://mermaid.live/edit#pako:eNqtWd1u47gVfhVCg0wyQOzYTpwftzuFk2wyQZKNd5xMkB0vAlqibHVkUUNRSTxJ7nrRFgX2D9hFe9P2Ynvdy32evkD7CD0kRVLyWHIWu7mJeHjO4afzT_necalHnI6ztHQfRAHvoHu0zMdkQt5gFuBhSJJlSfNpxPvBBwKr5fVGfLe8qmgHeBKEU0HtAn-oyZckGI25IA9p6C2jx8fHpaVBNGI4HqPz_UGE4G9pCe0TP4gI6vMpnKSoboiTBOjolgyRH4Rh5xlp-m2frCac0Xek86zRbG_tDLNl7Tbw-LizEd_9Zkbe0-K-7--4G0bcH7qNlrdQPGbU1edv-22yYxS0yJa33lqogKZcA1gnbb9t5LeGTR-XylurgB9QRGu3YDS01-8jYcHCCRG9FHu344CTWhJjl3SAJvhBl-JN0qEy-iUZXvdpylySoLcD539__8vXgoZw5KFuHIeBi3lAI7SPOUYZ48D5UmkRf0eRSyfkBA9XhPR3f0I4juuBJIZ4SBnmlE3rsFz77ZCtvVzpUxcCAvWJm7KAT9FnvTcvBs6LTqcDjrVqXTj5nVWOBs6Y8zjprK2NAj5Oh1LjHr4hXRZBKK0ZzoEDvGcxidBr4lLmDRyrtBuK8JNAv_03wnIlFClkPRIl4lXFq58EPoHTk5ThyCXVIJXWHMLb29u6Vb5WhahP3qcETpCYvvqXNN6I8CQj1wOqsHVdl6YRR7s4FIASNJyic3yHzqcxKUemtS-0nmasgrp70lcu_qN4rI_ojYK21zuqXYCt_NBGSjkkEF2IBjT2XYhOwqrwnGL2jnBxmo68Pqf0vfXnPoYSlLGhvZAmQTRCPRaA-V5IjlopSqt7IVjLejSJKePVoC8JDvnYZ1ALdRjmSBb7UXRDEj4h4PIeKPVpGNCk3Ko5HQsB53irkH6egmISaZTZEuxHJgFhJEtmkPWEWaFMJyIgSQVIraKYKO8VVaKE2uqlLk_WZCkL3FqsTqtMofOUDSkcrZD-ZNYK4QHxCIN6I5K6zzEni1Bq8RxMLkgc30FZ42mgkvpZFaQvoLzT2yyGVWr_MyOijCrRoZVXULRUTJYjKmhb6N4CdxlI8Jo9xT5BjxE1f4oCjjiVjcY0iqN902hMsyl0D9V1PmowIjOGOCGqu_zwh__-9BU6TKecRrXjEEKHsNolvIjH8C0OE8Ne6DH2ycIByUTUm-tzOY4o9d_9aDeQ2igoknUsK6FvwTHekNb1Guz_JTjAGxbZoRhpTng8gQhK-GfpZEhYqYQqNarSGNk8sUTQZPoejfxgpEUNeY6YdOQvcOBHZix6sWDyPRy6qSry159GIzGKgNH_87e_CpfmNlG2uQL1mBEPwpu6xEuZzLoZZ5wxdwwA5JTwFrSlSXx9eHwRe2BnlcCnOIGaWmAUaoQhxChWVDfjCMBkvD2jHDJcvLDe3p3umxO7oxEjI-Fo02KT8iPFISJGZvQD6UKXct0Zu97vU1XUq9UdHlttObvmrXKYYgYpE0DGPEev07AKYV9YjYymRinhNuP0ZvbqSQK98iYBGAmkLnEDMRH9HHuLGvuRsSVRnXBFr2QdDiDq3EVmpdBRExhitT5tDGJ2VD4p1epyIQKOMJ-yiXDs_AN-adbMyYSqvIEsKFapP0saOqGjwC0rU8L1yfgAarmuA5aSn29yWGRXm1dYDo-VW4yiK4LZ2Q1h4r_cKitlxgO6jBnDVxQl8Xd1vv8xbiCW1bBfoRnl7VzhjtdEjGlQi69P8BQqi3LJN5aeK1ho5dM7l4TogBBvTvUCkWvpIRPvkFv6ZXenwrpSXoIqDXWhZSZt5PKJosITudQ2jnmi-CvIRC2eVUNBomCsyRNVvMbRO61CPIMNF4H_tXw-68yi3-ec8sQTlHYzu5TMNmcpj1OeZfX3P4o--CZIUrj7fVAV_znqRjicilJXCB5tnf7uxauVrCSYy1rmBaRqJzLeSNSESFM-o-iopy9mc68NZWKQlwda8PBYlXwRuGX8V2dX6gb4wz-QCG1EoYKoJ11DZuXeBB96p_oMgwid0iiAPj5HQE28UmzhpGv0GXVPHnZ_VhRoLxeDQHyPEfdDO28K22Ufq4wva7WXDzDNQYSmNEHd3tGDmT8Vp7gPCyZVzNXYnjyIqVPt526ilk3qKU6U0cztUnJ_DlMCDE_yFhxBWD7MjphKzH5lEULdSLAaiSv9WS77zFHFom94ggecwse5kw2TuWBVaSreeWbe3FrQuCI_ftpREVaKIz89ok8-eVkYDStYjBvm7h4eV2yqlIgKMacafi5OzOcceMM5mPIUaYSLOCGMQ3zYnqqNAFCNFgM7W2Synpxp7Ty6NE-PpRh1-j31rCjVyXfpQKSHIZJjY4Lg7YXs7x4KUuq5AKGHp2AxSPTn6CSYBPNfaA6QnE0hUuaRzXLWXBlPxpVPHWs1PdsopplUKWMrkBSTZTCet8NFzvszb6inCb1p3sNOCOXI9CQwJ650ly_ZEh07h1RVuzxMjUtKmM5h9yxO0ybspsBk9456dkdAsjtZM7TbAlbFtj1UNos5B0q6s-qMWOA5Hc5SsupMCFwLxNK5FxIDR_6mMXA68OgRH6chF13jEcRiHH1B6URLMpqOxk7Hx2ECq1QG8n6ARV82LNBoCNsT32mdTnN7R-pwOvfOHSxb6_Wd5vbGZqO52drc2dxorTpTp7O-WW80WtvN1k5je3O7vdVuP646H-SxjfpOq9FqNxtbzY32emNno73qEE_0uVP104z8hebx_x_EUKo)
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