# Guyton-Klinger-Withdrawals
These SQL Server database scripts will recreate all the objects required for several of my GitHub applications.

# Guyton-Klinger-Withdrawals Database Documentation

## Overview
The **Guyton-Klinger-Withdrawals** database is designed to implement a financial withdrawal strategy (likely based on the Guyton-Klinger decision rules) by tracking account balances, daily closing prices, and composite portfolio performance. Its primary function is to calculate a 2-week moving average of the portfolio's value relative to its historical maximum, triggering alerts or suggesting specific withdrawal actions (e.g., "Cash" vs. "Asset Sale") based on defined guardrails (80% - 90%).

## Schema Summary

### Tables

| Table Name | Description | Key Columns |
| :--- | :--- | :--- |
| **`Accounts`** | Stores static metadata for financial accounts, categorizing them by tax treatment and purpose. | `ID`, `Name`, `TaxType`, `Category` |
| **`Balances`** | Stores historical balance entries for various financial instruments. Supports versioning by tracking multiple updates per sequence. | `ID`, `SequenceID`, `Name`, `Balance`, `LastUpdate` |
| **`Portfolio`** | Defines the composition of the investment portfolio, assigning weights (percentages) to specific stock/fund symbols within a tax bucket. | `ID`, `Symbol`, `TaxType`, `Percent`, `Active` |
| **`ClosingPrices`** | Records daily closing prices for the financial symbols tracked in the portfolio. | `ID`, `Closing` (Date), `Symbol`, `Price` |
| **`CompositePortfolio`** | Stores the calculated daily value of the portfolio composites based on the weighted performance of underlying symbols. | `ID`, `TaxType`, `Closing`, `CompositePrice` |

---

### Views

#### `vw_MostRecentBalances`
Filters the raw `Balances` table to return only the single most recent, non-zero record for each unique account name.
* **Logic:** Partitions data by `Name` and orders by `LastUpdate` DESC to find the latest entry.

#### `vw_AccountBalancesByTaxTypeAndCategory`
Aggregates the current balances of "Account" type assets, grouped by Tax Type and Category.
* **Exclusions:** Excludes categories '529', 'Liability', and 'Operational-Cash'.
* **Usage:** Provides a high-level summary of net worth or investable assets by bucket.

#### `vw_CompositePortfolio_MovingAverage`
The core analytical view for the withdrawal strategy.
1.  **Calculates 2-Week Moving Average:** Computes the average `CompositePrice` over the last 14 entries (rows) for each `TaxType`.
2.  **Calculates Percentages:**
    * `CompositePercent`: Current Price / Max Historical Price for that TaxType.
    * `MovingAverage_2Week_Percent`: Current Moving Average / Max Historical Moving Average.

---

### Stored Procedures

#### `usp_CalculateCompositePrices`
* **Purpose:** Populates the `CompositePortfolio` table.
* **Logic:**
    * Joins `ClosingPrices` with the `Portfolio` definition.
    * Calculates the weighted price for a given date (`Price * (Percent / 100)`).
    * Inserts new records only for dates/TaxTypes that do not yet exist.
* **Transactional:** Uses `BEGIN TRANSACTION` to ensure data integrity.

#### `sp_Alert_CompositePortfolioUpdate`
* **Purpose:** Monitors the `MovingAverage_2Week_Percent` and sends an HTML email alert if a 10% threshold is crossed (e.g., moving from a 90s bracket to an 80s bracket).
* **Logic:**
    * Compares the most recent percentage to the previous day's percentage.
    * Generates an HTML table of recent performance.
    * Uses `msdb.dbo.sp_send_dbmail` to notify the user.

#### `usp_GetWithdrawalStrategy`
* **Purpose:** Returns the specific withdrawal instruction based on the latest market performance (Sliding Scale Logic).
* **Rules:**
    * **> 90%:** "100% from sale of assets." (Upper Guardrail)
    * **< 80%:** "100% from cash." (Lower Guardrail)
    * **80% - 90%:** Calculates a linear interpolation (e.g., 85% = "50.0% from sale of assets").

#### `usp_AddManualBalance`
* **Purpose:** Allows for manual insertion of balance data (specifically hardcoded for a "Voya" 401(k) account) to bypass MFA/API issues.
* **Logic:**
    * Cleans currency inputs (removes '$' and ',').
    * Inserts a new record only if the balance differs from the currently recorded balance.

---

## Configuration & Usage Notes
* **Database Settings:** Created with `COMPATIBILITY_LEVEL = 150` (SQL Server 2019).
* **Recovery Model:** Set to `SIMPLE`.
* **Email Profile:** The alert procedure relies on a Database Mail profile named `'MyMailProfile'`.
