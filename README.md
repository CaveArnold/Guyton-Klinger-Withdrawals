# Guyton-Klinger-Withdrawals Database Documentation

## Overview
The **Guyton-Klinger-Withdrawals** database implements a financial withdrawal strategy based on the Guyton-Klinger decision rules. It tracks account balances, daily closing prices, and composite portfolio performance to manage retirement withdrawals. Its primary engine calculates a 2-week moving average of the portfolio's value relative to its historical maximum, determining whether withdrawals should come from "Cash" or "Asset Sales" based on specific guardrails (80% - 90%).

## Schema Summary

### Tables

| Table Name | Description | Key Columns |
| :--- | :--- | :--- |
| **`Accounts`** | Stores static metadata for financial accounts, categorizing them by tax treatment and purpose. | `ID`, `Name`, `TaxType`, `Category` |
| **`Balances`** | Historical ledger of account balances. Supports versioning by tracking multiple updates per sequence. | `ID`, `SequenceID`, `Name`, `Balance`, `LastUpdate` |
| **`Portfolio`** | Defines the target composition of the investment portfolio, assigning weights (percentages) to specific stock/fund symbols. | `ID`, `Symbol`, `TaxType`, `Percent`, `Active` |
| **`ClosingPrices`** | Records daily closing prices for the symbols tracked in the portfolio. | `ID`, `Closing`, `Symbol`, `Price` |
| **`CompositePortfolio`** | Stores the calculated daily value of the portfolio composites based on the weighted performance of underlying symbols. | `ID`, `TaxType`, `Closing`, `CompositePrice` |
| **`CPILatestNumbers`** | **(New)** Stores monthly Consumer Price Index (CPI) reports to track inflation metrics (NSA/SA monthly and yearly changes). | `ReportMonth`, `NSA_Monthly_Change`, `NSA_Yearly_Change` |

---

### Views

#### `vw_MostRecentBalances`
Filters the raw `Balances` table to return only the single most recent, non-zero record for each unique account name.
* **Logic:** Partitions data by `Name` and orders by `LastUpdate` DESC.

#### `vw_AccountBalancesByTaxTypeAndCategory`
Aggregates current net worth by bucket.
* **Exclusions:** Filters out non-investment categories ('529', 'Liability', 'Operational-Cash').
* **Usage:** Provides a high-level summary of investable assets grouped by `TaxType` and `Category`.

#### `vw_CompositePortfolio_MovingAverage`
The core analytical view for the withdrawal strategy.
1.  **Moving Average:** Computes the average `CompositePrice` over the last 14 entries (rows) for each `TaxType`.
2.  **Ratios:**
    * `CompositePercent`: Current Price vs. All-Time Max Price.
    * `MovingAverage_2Week_Percent`: Current Moving Average vs. All-Time Max Moving Average.

---

### Stored Procedures

#### `usp_CalculateCompositePrices`
* **Purpose:** Populates the `CompositePortfolio` table.
* **Logic:** Joins `ClosingPrices` with `Portfolio` weights to calculate a weighted index value for each day. Transactions are used to ensure data integrity.

#### `usp_GetWithdrawalStrategy`
* **Purpose:** Returns the specific withdrawal instruction based on the "Guardrail" logic.
* **Rules:**
    * **> 90%:** "100% from sale of assets." (Upper Guardrail)
    * **< 80%:** "100% from cash." (Lower Guardrail)
    * **80% - 90%:** Linear interpolation (e.g., 85% = "50.0% from sale of assets").

#### `sp_Alert_CompositePortfolioUpdate`
* **Purpose:** Monitors market movements and alerts the user via Database Mail if the Moving Average crosses a 10% threshold (e.g., dropping from 90s to 80s).
* **Output:** Sends an HTML-formatted email to the configured recipient.

#### `usp_GetBalanceUpdateHistogram_Pivot`
* **Purpose:** A reporting tool that generates a heatmap-style pivot table of data entry frequency.
* **Output:** Shows how many balance updates occurred for every hour of the day (0-23) across each day of the week (Sun-Sat). Useful for auditing automated data ingestion schedules.

#### `usp_UpsertCPILatest`
* **Purpose:** Inserts new CPI inflation data into the `CPILatestNumbers` table.
* **Logic:** Takes raw string inputs for monthly and yearly changes (NSA/SA) and logs the report month.

#### `usp_AddManualBalance`
* **Purpose:** A workaround procedure to manually insert a balance for a specific "Voya" account, bypassing external API limitations.

---

## Configuration Notes
* **Database Settings:** `COMPATIBILITY_LEVEL = 150` (SQL Server 2019), `RECOVERY SIMPLE`.
* **Email:** The alert system requires a configured Database Mail profile named `'MyMailProfile'`.
* **Date Formats:** The CPI table currently stores dates and changes as `NVARCHAR`, likely to accommodate raw scraper output formats before cleaning.