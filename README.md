# Guyton-Klinger Withdrawals Database Documentation

**Database Name:** `[Guyton-Klinger-Withdrawals]`

**Developer:** Cave Arnold

**AI Assistant:** Gemini

**Script Date:** February 21, 2026


## Overview
This database implements a financial withdrawal strategy based on the Guyton-Klinger decision rules. It manages account balances, tracks portfolio performance against moving averages, calculates inflation adjustments (CPI-U), and enforces capital preservation and prosperity guardrails to determine safe withdrawal rates.

## Mermaid Data Flow Visualization

[![](https://mermaid.ink/img/pako:eNqVWN1u2zYUfhVCRYsUiB3Hjp1EWzskcZsFSZsgThpkdRFQEmWrkUWVpOK4Te92sQ0DuqHAhu1mV90z7Hn2Atsj7JA0KcmRnc43kc4fP348P1TeOT4NiOM6A4bTITrp9hMEv_v3UZeEUUJQT0xiwrXUjzHnIEdj4qEwimP3HlkN2yFZ5oLRS-Lea6y21ze96WttHAVi6DbT6y9m_APjHobhpr9m3UPPbzSDO91TRn2z_kbYJps2QJOsB63mnQFoJgyAFmmHbeu_7q2GuNJfR-CZp4k6I95Fj2bMJxy97Dv__vHjT1KGulhgNFX0nVfaS_565E1GEp8sSeMPfyKcpvUBEXwqrkf0S4-tPF7a8n2aJQJt4xgnMro3QSf4Gp1MUvKw7zx0XRfYz-P6ceRf2uio7wyFSLm7snJ7gZW-A_rDlCTomPiUBX0nj7N90FPQPn4nH-sDeqXx7Bzt1U7RXhLGWEQ0URucjwNcCxDG43Hdi7kMtuKn0QqEIFzUkmzkEcbrQzFahOgZZpdEyPU0sO8hFyl9U_fpSEPTBmgnpjxKBuiIRcDXfGx5vAJEbkIuQnJGcCyGIaOJMFAKohzQXnIF-xsROL4jykRI44guAFSIMUPauBx94cHtJWBBDrBnoMmDj5Qwxh5lWFA2UVE0yB71IxxDxvgZi8QEPT96MR-iDV4AWBl7EcKtOBoMLXP6TWM5IgmXSYWTAB1EIYH1eMZk3i-GpWPMkIaVcCEakgS3KlkmhIc50WX867f__PUB7WYTQZPafgx5RVjtLBLDgOExjrk1LxV3_mTD7oEnlxVzcYK92HSJj59yBdKKUiBVidPKfwmMBR6tm3dg4xXQEXhlcyhQYwmPB6rEnusKm-ehC0bXi_UtCuc42qTeoUkYDYyrFVe4FRgv0bODYz_TLeXiSTKQkwYI-vv33yT9BSWaKpeg9hkJoMipT4KMqUKfIe6Q-UPYvMrKlxAt4-nF7v5pGgAnpmNwQVjJUIaRoOVMKYebIQ0w2ZOZCQ79WR6lUW9PunbFrcGAkYE8FNvF-fwl5SLyPGfig-jUdBjTh7eC15nuNYvD7e7n0Qq8FlnZzTCD9I4gux-g4yxehLAnWSODiQ1KRF4dRjndOufQna84wOBQZsSPZK3_H757AotbZCuhXuGcniP5GkE9-XfRSkcpZLggJp4hg1iNzn0d-ozIZiITjrCQspE82OoF5mY45Gu59n9QMnRAB5E_r_jlIfHh05iOTXXlEo2sCwc1KZaImjBV5bq7rwm0gc4JZodXhMm_SjWvQViuTHOwFC0odfk7P-nexg3CeZ1hQQM9JiksBi3p4gBPoGg1hz_n8kIvQEtPrn0So6eEBBWNAVwuFKU2lSBtDbrtiaRD-aszmZtFMspMRqrXz3SV1BWqxjL5me5fQ5Ib92mjkSIKZI0-M8QxTi5NCPkMHN4F3h5S1eQ8zESaiWl2__JJdu4XEc9gDr_VPeoB2kpwPJHFWToTtejStCb0yXXhNDwKfYjroQ839Nz-RfTW3E3V9a20yqxDAan8ipH2-ciVBz79mLFX5lrt8c3W0d6NHbxaL6-yUtXzYbOE38hBqzWFi6T1LY_PZObWqOye4QRQ38xO0QLY4tzLZxS8aYvi2EKPHj0uzaQFJhZ4pXZ3f4FSd4kkL1FAqftXgUn7qQK7rMBUlCgiTlNOmABG8xZhSACoNoqFPX2Z-gZqmOaD8H5VnFxiw5l9miGlwqm9uJALcYzUvOIIdi99v7opeennEoQjPAHG4Db6AO6uo6h6QxVACpxCZ6wS29dZuqY2U6tiyuWsmVatjWaSbZ5ZSaSNcgN78nnrLZz-zA5NrzVKu4-8f85HZvpkRV6ZHjhHJftZAaluTUWYBpfyUD0nl-cYZxQSS5VcAqmSSxQL40Anc5adAYsCxxUsI8vOiMDlQr4676R93xFDMoJm7MJjQEKcxUJ-vbwHtxQn31A6Mp6MZoOh44bwVQJvmcrKboTlQLAm0AwJ25H_UHDc1Uajo4I47jvn2nFrnbV6s9Nptdca623QrbaXnQmImxv1RrvdaTU77Xaz3Wptrr9fdt6qhRv1jbW1VmejubrZWm93Vhtr7_8D6d_pCg?type=png)](https://mermaid.live/edit#pako:eNqVWN1u2zYUfhVCRYsUiB3Hjp1EWzskcZsFSZsgThpkdRFQEmWrkUWVpOK4Te92sQ0DuqHAhu1mV90z7Hn2Atsj7JA0KcmRnc43kc4fP348P1TeOT4NiOM6A4bTITrp9hMEv_v3UZeEUUJQT0xiwrXUjzHnIEdj4qEwimP3HlkN2yFZ5oLRS-Lea6y21ze96WttHAVi6DbT6y9m_APjHobhpr9m3UPPbzSDO91TRn2z_kbYJps2QJOsB63mnQFoJgyAFmmHbeu_7q2GuNJfR-CZp4k6I95Fj2bMJxy97Dv__vHjT1KGulhgNFX0nVfaS_565E1GEp8sSeMPfyKcpvUBEXwqrkf0S4-tPF7a8n2aJQJt4xgnMro3QSf4Gp1MUvKw7zx0XRfYz-P6ceRf2uio7wyFSLm7snJ7gZW-A_rDlCTomPiUBX0nj7N90FPQPn4nH-sDeqXx7Bzt1U7RXhLGWEQ0URucjwNcCxDG43Hdi7kMtuKn0QqEIFzUkmzkEcbrQzFahOgZZpdEyPU0sO8hFyl9U_fpSEPTBmgnpjxKBuiIRcDXfGx5vAJEbkIuQnJGcCyGIaOJMFAKohzQXnIF-xsROL4jykRI44guAFSIMUPauBx94cHtJWBBDrBnoMmDj5Qwxh5lWFA2UVE0yB71IxxDxvgZi8QEPT96MR-iDV4AWBl7EcKtOBoMLXP6TWM5IgmXSYWTAB1EIYH1eMZk3i-GpWPMkIaVcCEakgS3KlkmhIc50WX867f__PUB7WYTQZPafgx5RVjtLBLDgOExjrk1LxV3_mTD7oEnlxVzcYK92HSJj59yBdKKUiBVidPKfwmMBR6tm3dg4xXQEXhlcyhQYwmPB6rEnusKm-ehC0bXi_UtCuc42qTeoUkYDYyrFVe4FRgv0bODYz_TLeXiSTKQkwYI-vv33yT9BSWaKpeg9hkJoMipT4KMqUKfIe6Q-UPYvMrKlxAt4-nF7v5pGgAnpmNwQVjJUIaRoOVMKYebIQ0w2ZOZCQ79WR6lUW9PunbFrcGAkYE8FNvF-fwl5SLyPGfig-jUdBjTh7eC15nuNYvD7e7n0Qq8FlnZzTCD9I4gux-g4yxehLAnWSODiQ1KRF4dRjndOufQna84wOBQZsSPZK3_H757AotbZCuhXuGcniP5GkE9-XfRSkcpZLggJp4hg1iNzn0d-ozIZiITjrCQspE82OoF5mY45Gu59n9QMnRAB5E_r_jlIfHh05iOTXXlEo2sCwc1KZaImjBV5bq7rwm0gc4JZodXhMm_SjWvQViuTHOwFC0odfk7P-nexg3CeZ1hQQM9JiksBi3p4gBPoGg1hz_n8kIvQEtPrn0So6eEBBWNAVwuFKU2lSBtDbrtiaRD-aszmZtFMspMRqrXz3SV1BWqxjL5me5fQ5Ib92mjkSIKZI0-M8QxTi5NCPkMHN4F3h5S1eQ8zESaiWl2__JJdu4XEc9gDr_VPeoB2kpwPJHFWToTtejStCb0yXXhNDwKfYjroQ839Nz-RfTW3E3V9a20yqxDAan8ipH2-ciVBz79mLFX5lrt8c3W0d6NHbxaL6-yUtXzYbOE38hBqzWFi6T1LY_PZObWqOye4QRQ38xO0QLY4tzLZxS8aYvi2EKPHj0uzaQFJhZ4pXZ3f4FSd4kkL1FAqftXgUn7qQK7rMBUlCgiTlNOmABG8xZhSACoNoqFPX2Z-gZqmOaD8H5VnFxiw5l9miGlwqm9uJALcYzUvOIIdi99v7opeennEoQjPAHG4Db6AO6uo6h6QxVACpxCZ6wS29dZuqY2U6tiyuWsmVatjWaSbZ5ZSaSNcgN78nnrLZz-zA5NrzVKu4-8f85HZvpkRV6ZHjhHJftZAaluTUWYBpfyUD0nl-cYZxQSS5VcAqmSSxQL40Anc5adAYsCxxUsI8vOiMDlQr4676R93xFDMoJm7MJjQEKcxUJ-vbwHtxQn31A6Mp6MZoOh44bwVQJvmcrKboTlQLAm0AwJ25H_UHDc1Uajo4I47jvn2nFrnbV6s9Nptdca623QrbaXnQmImxv1RrvdaTU77Xaz3Wptrr9fdt6qhRv1jbW1VmejubrZWm93Vhtr7_8D6d_pCg)

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