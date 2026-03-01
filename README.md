# Guyton-Klinger Withdrawals Database Documentation

**Database Name:** `[Guyton-Klinger-Withdrawals]`

**Developer:** Cave Arnold

**AI Assistant:** Gemini

**Script Date:** February 21, 2026


## Overview
This database implements a financial withdrawal strategy based on the Guyton-Klinger decision rules. It manages account balances, tracks portfolio performance against moving averages, calculates inflation adjustments (CPI-U), and enforces capital preservation and prosperity guardrails to determine safe withdrawal rates.

## Mermaid Data Flow Visualization

[![](https://mermaid.ink/img/pako:eNqtWVtv48YV_isDLrz2ApYsyZYvarOFL7Fj2BsrK1_grgJjRA4lxhSHOxxa1tp-60NbBEjaAA3al_Ylfe5Lgfye_oH2J_TMDGeG1IqUg8QvJs-cc-abcx_qwXGpR5yOs7T0EEQB76AHtMxHZEwuMQvwICTJsqT5NOK94AOBt-X1Rny_vKpoh3gchFNB3QX-UJOvSDAccUEe0NBbRk9PT0tL_WjIcDxC5wf9CMHf0hI6IH4QEdTjU9hJUd0QJwnQ0YQMkB-EYecFafptn6wmnNFb0nnRaLa3dgbZa20SeHzU2YjvfzUj72lx3_d33A0j7g_cRstbKB4z6ur9t_022TEKWmTLW28tVEBTrgGsk7bfNvJbg6aPS-WtVcAPKKK1CRgN7fd6SFiwsENEr8TaZBRwUkti7JIO0AQ_6FK8STpQRr8ig5seTZlLEvSu7_zv719_K2gIRx7ajeMwcDEPaIQOMMcoY-w7Xyot4u84cumYnOLBipD-7g8Ix3E9kMQQDyjDnLJpHV7Xfj1ga69XetSFgEA94qYs4FP0effyVd951el0wLFWrQs731rlqO-MOI-TztraMOCjdCA17uM7sssiCKU1w9l3gPcsJhF6S1zKvL5jle6GIvwk0D__C2H5JhQpZF0SJeKo4uingU9g9yRlOHJJNUilNYdwMpnUrfK1KkQ98j4lsIPE9M0_pfGGhCcZuR5QhW3XdWkacbSHQwEoQYMpOsf36Hwak3JkWvtC62nGKqh7pz3l4t-Lx_qQ3ilo-93j2gXYyg9tpJRDAtGFaEBjz4XoJKwKzxvMbgkXu-nI63FK31t_Kga0H9IkiIaoywIwXDkyq28hQMt6PI4p49VArwgO-chnUP906OVIFu9xdEcSPibg5i4o9WkY0Aq8OR0LAed4q5B-kYJiEmmU2StYjowDwkiWwCDrCYNCaU5EEFYZVasoJsd7RZUooZ56qcuTNVm-ArcWq90q0-Y8ZQMKWyukP5p3hfCQeIRBjRGJ3OOYk0UotXgOJhckju-hlPE0UIn8ogrSJZ3ii9iD3ZhC9W9JgrCKUsCSJS7KWBTQjUZz5fZVOa6czoUuzvGWwQS_2R3sE3QWUemnKOCIU9leTHs4PjDtxbSYQs9QveajtiJyY4ATonrK97_774_foKN0ymlUOwkheAirXcExPIYnOEwMe6Gz2CcLByQTUWVuzuUQotR_94NdQGqhoEhWr6xwvgPneANa1-9g-y_B-N6gyA4lSHPC4ylYNeGfp-MBYaUSqsyoKmNk88QSQZPr-zTyg6EWNeQ5YtKRP8OBH5mx6MWCyfdx6KaqtN98Gg3FAAJG_8_f_ipcmltE2eIKVGFGPCga1CVeymTezTjjjLkjACBng3egLU3im6MTFb26dici6POMQo0whBjAiupmHAGYjLdnlEOOiwPr5b3pgdlxdzhkZCgcbRprUr6l2ETEyIx-IF3oYq774a73VarKerW6oxOrLWfXvFWOUswgZQLImJfobRpWIewJq5Hh1Cgl3GacXsyOniTQJ-8SgJFA6hI3EHPQT7G3qLIfGVsS1Q7X9FpW4gCizl1kVgo9NYHRVevTxiBmReWTUq2uFCLgCPMpGwvHzt_g52bNnEyoyhvIgmKV-qOkoVM6DNyyMiVcn4wOQzrRdcBS1HkPwP3TPBbZ1-YVlqMT5Raj6JpgdnZHmPgvl8pKmfGALmPG8BVFSfxdnx98jBuIZTXsF2hGeTtXuOMtEYMa1OKbUzyFyqJc8idLzxUstPLpvUtCdEiIN6d6gciN9JCJd8gtfdi9qbCulJegSkNdaJlJG_n6TFHhiVxqG8c8U_wzyEQtnlVDQaJgrPEzVbzF0a1WIZ7BhovA_1I-n3Vm0e9zdnnmDkq7mV1KZpuzlMcpz7L6Lz-IPngZJDDkBR9UxX-JdiMcTkWpKwSPtk5v7-KzlawkmCtacUBExhuJmg5pymcUHXf1dWzuxaFMDPLyUAsenaiSLwK3jP_67Frd-77_BxKhjShUEPWka8is3GXwoftG72EQoTc0CqCPzxHIpl0htnDONfqMumcPuz8pCrSXi0EgvsKIG6KdN4Xtsk9Uxpe12uvH3e7xo5k61bq4-4oldblNHsWUqVZyd08jW5wdo5mbpOT7AuYBGJPgROqW8Tg7TCox-xVFKo_khURLXOvPbtlnjCoWfZsTPGB-PsrtbJjMZapKU_5mI_hUV9Ns1mzG6vlJ006F8KY48oMi-uST14UpsILFeGDu6tFJxaKK_qgQXqq350LCfK-BQ87BlKdIO1zECWEcQsO2T20EgGq0GNjZSybryfHVjp5L8_RYilGnz6nHQqlOnqUDQR2GSE6ICYLTC9nfPBak1HMBQhdPwWKQ0y_RaTAO5h9oDpCcTSFU5pHN66y5Mp6MK5871mp6jFFMM7lSxlYgKSbLYDxv54ic92dOqAcHvWjOYYeBcmS66c-JK93QS5ZEc84hVYUtD1PjkhKmSdg1i9N0BLsoMNm1465dEZDsStb37LKAVbFsN5V9Yc6Gku6sOkMWeE6Hs5SsOmMCNwDx6jwIib4jf7ToOx149IiP05CLBvEEYjGOfkvpWEsymg5HTsfHYQJvqQzkgwCLFmxYoKcQti8-xDqd1vqW1OF0Hpx7p9Nsrdd3mtsbm43mZmtzZ3OjtepMnc76Zr3RaG03WzuN7c3t9la7_bTqfJDbNuo7rUar3WxsNTfa642djfaqQzzR0t6o317kTzBP_wcduEUC?type=png)](https://mermaid.live/edit#pako:eNqtWVtv48YV_isDLrz2ApYsyZYvarOFL7Fj2BsrK1_grgJjRA4lxhSHOxxa1tp-60NbBEjaAA3al_Ylfe5Lgfye_oH2J_TMDGeG1IqUg8QvJs-cc-abcx_qwXGpR5yOs7T0EEQB76AHtMxHZEwuMQvwICTJsqT5NOK94AOBt-X1Rny_vKpoh3gchFNB3QX-UJOvSDAccUEe0NBbRk9PT0tL_WjIcDxC5wf9CMHf0hI6IH4QEdTjU9hJUd0QJwnQ0YQMkB-EYecFafptn6wmnNFb0nnRaLa3dgbZa20SeHzU2YjvfzUj72lx3_d33A0j7g_cRstbKB4z6ur9t_022TEKWmTLW28tVEBTrgGsk7bfNvJbg6aPS-WtVcAPKKK1CRgN7fd6SFiwsENEr8TaZBRwUkti7JIO0AQ_6FK8STpQRr8ig5seTZlLEvSu7_zv719_K2gIRx7ajeMwcDEPaIQOMMcoY-w7Xyot4u84cumYnOLBipD-7g8Ix3E9kMQQDyjDnLJpHV7Xfj1ga69XetSFgEA94qYs4FP0effyVd951el0wLFWrQs731rlqO-MOI-TztraMOCjdCA17uM7sssiCKU1w9l3gPcsJhF6S1zKvL5jle6GIvwk0D__C2H5JhQpZF0SJeKo4uingU9g9yRlOHJJNUilNYdwMpnUrfK1KkQ98j4lsIPE9M0_pfGGhCcZuR5QhW3XdWkacbSHQwEoQYMpOsf36Hwak3JkWvtC62nGKqh7pz3l4t-Lx_qQ3ilo-93j2gXYyg9tpJRDAtGFaEBjz4XoJKwKzxvMbgkXu-nI63FK31t_Kga0H9IkiIaoywIwXDkyq28hQMt6PI4p49VArwgO-chnUP906OVIFu9xdEcSPibg5i4o9WkY0Aq8OR0LAed4q5B-kYJiEmmU2StYjowDwkiWwCDrCYNCaU5EEFYZVasoJsd7RZUooZ56qcuTNVm-ArcWq90q0-Y8ZQMKWyukP5p3hfCQeIRBjRGJ3OOYk0UotXgOJhckju-hlPE0UIn8ogrSJZ3ii9iD3ZhC9W9JgrCKUsCSJS7KWBTQjUZz5fZVOa6czoUuzvGWwQS_2R3sE3QWUemnKOCIU9leTHs4PjDtxbSYQs9QveajtiJyY4ATonrK97_774_foKN0ymlUOwkheAirXcExPIYnOEwMe6Gz2CcLByQTUWVuzuUQotR_94NdQGqhoEhWr6xwvgPneANa1-9g-y_B-N6gyA4lSHPC4ylYNeGfp-MBYaUSqsyoKmNk88QSQZPr-zTyg6EWNeQ5YtKRP8OBH5mx6MWCyfdx6KaqtN98Gg3FAAJG_8_f_ipcmltE2eIKVGFGPCga1CVeymTezTjjjLkjACBng3egLU3im6MTFb26dici6POMQo0whBjAiupmHAGYjLdnlEOOiwPr5b3pgdlxdzhkZCgcbRprUr6l2ETEyIx-IF3oYq774a73VarKerW6oxOrLWfXvFWOUswgZQLImJfobRpWIewJq5Hh1Cgl3GacXsyOniTQJ-8SgJFA6hI3EHPQT7G3qLIfGVsS1Q7X9FpW4gCizl1kVgo9NYHRVevTxiBmReWTUq2uFCLgCPMpGwvHzt_g52bNnEyoyhvIgmKV-qOkoVM6DNyyMiVcn4wOQzrRdcBS1HkPwP3TPBbZ1-YVlqMT5Raj6JpgdnZHmPgvl8pKmfGALmPG8BVFSfxdnx98jBuIZTXsF2hGeTtXuOMtEYMa1OKbUzyFyqJc8idLzxUstPLpvUtCdEiIN6d6gciN9JCJd8gtfdi9qbCulJegSkNdaJlJG_n6TFHhiVxqG8c8U_wzyEQtnlVDQaJgrPEzVbzF0a1WIZ7BhovA_1I-n3Vm0e9zdnnmDkq7mV1KZpuzlMcpz7L6Lz-IPngZJDDkBR9UxX-JdiMcTkWpKwSPtk5v7-KzlawkmCtacUBExhuJmg5pymcUHXf1dWzuxaFMDPLyUAsenaiSLwK3jP_67Frd-77_BxKhjShUEPWka8is3GXwoftG72EQoTc0CqCPzxHIpl0htnDONfqMumcPuz8pCrSXi0EgvsKIG6KdN4Xtsk9Uxpe12uvH3e7xo5k61bq4-4oldblNHsWUqVZyd08jW5wdo5mbpOT7AuYBGJPgROqW8Tg7TCox-xVFKo_khURLXOvPbtlnjCoWfZsTPGB-PsrtbJjMZapKU_5mI_hUV9Ns1mzG6vlJ006F8KY48oMi-uST14UpsILFeGDu6tFJxaKK_qgQXqq350LCfK-BQ87BlKdIO1zECWEcQsO2T20EgGq0GNjZSybryfHVjp5L8_RYilGnz6nHQqlOnqUDQR2GSE6ICYLTC9nfPBak1HMBQhdPwWKQ0y_RaTAO5h9oDpCcTSFU5pHN66y5Mp6MK5871mp6jFFMM7lSxlYgKSbLYDxv54ic92dOqAcHvWjOYYeBcmS66c-JK93QS5ZEc84hVYUtD1PjkhKmSdg1i9N0BLsoMNm1465dEZDsStb37LKAVbFsN5V9Yc6Gku6sOkMWeE6Hs5SsOmMCNwDx6jwIib4jf7ToOx149IiP05CLBvEEYjGOfkvpWEsymg5HTsfHYQJvqQzkgwCLFmxYoKcQti8-xDqd1vqW1OF0Hpx7p9Nsrdd3mtsbm43mZmtzZ3OjtepMnc76Zr3RaG03WzuN7c3t9la7_bTqfJDbNuo7rUar3WxsNTfa642djfaqQzzR0t6o317kTzBP_wcduEUC)

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