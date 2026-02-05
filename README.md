# Guyton-Klinger-Withdrawals Database Documentation

## Overview
The **Guyton-Klinger-Withdrawals** database is a specialized financial engine designed to automate a retirement withdrawal strategy. It implements the "Guardrail" decision rules (Guyton-Klinger) to dynamically adjust spending based on portfolio performance and inflation (CPI). 

The system tracks daily account balances, calculates moving averages, monitors inflation, and generates a specific "Paycheck" amount and funding source (Cash vs. Asset Sale) for every processing period.

## Mermaid Data Flow Visualization

graph TD
    %% Define Styles
    classDef web fill:#E1F5FE,stroke:#01579B,stroke-width:2px;
    classDef sp fill:#FFF3E0,stroke:#E65100,stroke-width:2px,stroke-dasharray: 5 5;
    classDef table fill:#E8F5E9,stroke:#1B5E20,stroke-width:2px;
    classDef view fill:#F3E5F5,stroke:#4A148C,stroke-width:2px;
    classDef output fill:#FFEBEE,stroke:#B71C1C,stroke-width:2px;

    %% 1. Web / External Sources
    subgraph "External Sources"
        Web_CPI[("🌐 BLS / Inflation Data")]:::web
        Web_Banks[("🌐 Financial Institutions")]:::web
		Web_Accounts[("🌐 Accounts & Taxable Type")]:::web
        Web_Market[("🌐 Stock Market Data")]:::web
    end

    %% 2. Ingestion Layer
    subgraph "Ingestion Stored Procedures"
        SP_UpsertCPI[usp_UpsertCPILatest]:::sp
        SP_AddBal[usp_AddManualBalance]:::sp
        SP_CalcComp[usp_CalculateCompositePrices]:::sp
    end

    %% 3. Data Storage
    subgraph "Database Tables"
        T_CPI[CPILatestNumbers]:::table
        T_Bal[Balances]:::table
        T_Close[ClosingPrices]:::table
        T_Port[Portfolio]:::table
        T_Comp[CompositePortfolio]:::table
        T_CashFlow[GKCashFlow]:::table
    end

    %% 4. Calculation & Views
    subgraph "Calculation Engine"
        SP_Master[usp_GKUpdate]:::sp
        SP_UpdateTax[usp_GKUpdateTaxableBalancesByDate]:::sp
        SP_UpdateCPI[usp_GKUpdateCPIU]:::sp
        SP_CalcMain[usp_GKCalculationUpdate]:::sp
        V_MovAvg[vw_CompositePortfolio_MovingAverage]:::view
        SP_Strat[usp_GetWithdrawalStrategy]:::sp
    end

    %% 5. Outputs
    subgraph "Outputs & Viz"
        Excel[("📊 Excel / Visualizations")]:::output
        Email[("📧 Email Alert<br/>(HTML Table)")]:::output
        SP_Alert[usp_Alert_CompositePortfolioUpdate]:::sp
    end

    %% Relationships
    %% External to Ingestion
    Web_CPI -->|Scraper Script| SP_UpsertCPI
    Web_Banks -->|Plaid/Script| T_Bal
    Web_Banks -->|Manual Override| SP_AddBal
    Web_Market -->|Script| T_Close

    %% Ingestion to Tables
    SP_UpsertCPI --> T_CPI
    SP_AddBal --> T_Bal
    T_Close --> SP_CalcComp
    T_Port --> SP_CalcComp
    SP_CalcComp --> T_Comp

    %% Calculation Flow (Orchestration)
    SP_Master -->|1. Aggregates| SP_UpdateTax
    SP_Master -->|2. Calc Inflation| SP_UpdateCPI
    SP_Master -->|3. Calc Paycheck| SP_CalcMain

    %% Data dependencies for Calculation
    T_Bal --> SP_UpdateTax
    T_CPI --> SP_UpdateCPI
    T_CashFlow -.->|Read Previous| SP_CalcMain
    SP_UpdateTax -->|Write| T_CashFlow
    SP_UpdateCPI -->|Write| T_CashFlow
    SP_CalcMain -->|Write| T_CashFlow

    %% Withdrawal Strategy Logic
    T_Comp --> V_MovAvg
    V_MovAvg --> SP_Strat
    SP_Strat -->|Guardrail Decision| SP_CalcMain

    %% Outputs
    T_CashFlow --> Excel
    V_MovAvg --> SP_Alert
    SP_Alert --> Email

## Core Logic & Data Flow
The database operates on a daily or periodic update cycle orchestrated by the master procedure `usp_GKUpdate`. 


1.  **Ingest:** Market data (Closing Prices), Account Balances, and Inflation numbers (CPI) are updated.
2.  **Aggregate:** Balances are summed by Tax Bucket (Taxable, Tax-Free, Deferred).
3.  **Calculate:** The `GKCashFlow` engine calculates the daily "Paycheck" by applying inflation adjustments and checking against Upper/Lower spending guardrails.
4.  **Decide:** The system determines the *Source* of the funds (Cash vs. Assets) based on the portfolio's 2-week moving average.

---

## Schema Summary

### 1. The Calculation Engine (Primary Tables)

| Table Name | Description | Key Columns |
| :--- | :--- | :--- |
| **`GKCashFlow`** | **The Master Ledger.** Records the daily state of the strategy, including total assets, calculated inflation rates, spending limits (Upper/Lower guardrails), and the final "Paycheck" amount. | `Date`, `Total_Assets`, `Inflated_Withdrawal_Amount`, `GK_Upper/Lower_Amount`, `Paycheck`, `Paycheck_Source` |
| **`GKYearOverYearStats`** | Stores aggregated statistical performance data for annual reporting and analysis. | `Year`, `Taxable_Percent`, `Spent`, `CPI_U` |
| **`CompositePortfolio`** | Tracks the calculated daily value of the investment portfolio based on weighted symbol performance. Used to trigger guardrails. | `ID`, `TaxType`, `Closing`, `CompositePrice` |

### 2. Core Data & Inputs

| Table Name | Description | Key Columns |
| :--- | :--- | :--- |
| **`Balances`** | Historical ledger of all account balances. Supports versioning by tracking multiple updates per sequence/date. | `ID`, `Name`, `Balance`, `LastUpdate` |
| **`CPILatestNumbers`** | Stores scraped CPI (Consumer Price Index) reports to calculate daily inflation rates. | `ReportMonth`, `NSA_Monthly_Change`, `SA_Monthly_Change` |
| **`ClosingPrices`** | Records daily market closing prices for symbols tracked in the portfolio. | `Closing`, `Symbol`, `Price` |
| **`Portfolio`** | Defines the target asset allocation weights for specific symbols within tax buckets. | `Symbol`, `TaxType`, `Percent`, `Active` |
| **`Accounts`** | Metadata mapping account names to Tax Types (Taxable, Roth, etc.) and Categories. | `Name`, `TaxType`, `Category` |

### 3. Reference Data

| Table Name | Description |
| :--- | :--- |
| **`FederalTaxRates`** | Stores historical and current federal tax brackets/rates by filing status. |
| **`FederalStandardDeductions`** | Stores standard deduction amounts by tax year and filing status. |

---

## Stored Procedures & Orchestration

### Master Orchestrator
#### `usp_GKUpdate`
* **Role:** The single entry point for daily updates.
* **Parameters:** `@Date` (Defaults to `GETDATE()`).
* **Execution Chain:**
    1.  `usp_GKUpdateTaxableBalancesByDate`: Aggregates raw balances into the Cash Flow table.
    2.  `usp_GKUpdateCPIU`: Fetches latest CPI, calculates daily inflation, and updates Cash Flow.
    3.  `usp_GKCalculationUpdate`: Runs the core Guyton-Klinger math (Guardrails & Paycheck).

### Calculation Procedures
#### `usp_GKCalculationUpdate`
* **Purpose:** The "Brain" of the system.
* **Logic:**
    * **Jan 1st Reset:** If run on Jan 1, it resets the Upper (+20%) and Lower (-20%) spending guardrails based on current portfolio value.
    * **Inflation Adjustment:** Adjusts the previous withdrawal amount by the calculated CPI-U.
    * **Guardrail Check:** If the adjusted withdrawal exceeds the Upper/Lower limits, it applies a "Pay Cut" (-10%) or "Pay Raise" (+10%).
    * **Paycheck Gen:** Calculates the final `Paycheck` amount and stamps the `Paycheck_Source` (from `usp_GetWithdrawalStrategy`).

#### `usp_GKUpdateCPIU`
* **Purpose:** Converts raw monthly CPI strings (e.g., "0.2%") into daily inflation factors.
* **Logic:**
    * Parses the latest `SA_Monthly_Change` from `CPILatestNumbers`.
    * Calculates a daily inflation rate based on days in the month.
    * Applies this rate to the `Inflated_Withdrawal_Percent` in `GKCashFlow`.

#### `usp_GetWithdrawalStrategy`
* **Purpose:** Determines *where* the money comes from.
* **Logic:** Checks the 2-Week Moving Average of the portfolio (via `vw_CompositePortfolio_MovingAverage`).
    * **> 90%:** Sell Assets.
    * **< 80%:** Use Cash.
    * **80-90%:** Linear sliding scale (mixed Cash/Assets).

### Utility & Reporting
* **`usp_Alert_CompositePortfolioUpdate`**: Checks if the Moving Average crossed a 10% threshold and sends an HTML email via Database Mail.
* **`usp_GetBalanceUpdateHistogram_Pivot`**: Generates a heatmap (Day of Week vs. Hour) of data entry frequency for auditing.
* **`usp_AddManualBalance`**: Helper to insert balances for accounts that cannot be automated (e.g., specific Voya 401k).

---

## Key Views

* **`vw_CompositePortfolio_MovingAverage`**: The "Speedometer" of the system. Calculates the 2-week moving average vs. the all-time high to determine the withdrawal strategy.
* **`vw_AccountBalancesByTaxTypeAndCategory`**: Summarizes net worth by tax bucket (Taxable, Tax-Free, Deferred, Cash), excluding non-investment assets like 529s or operational cash.

## Configuration Notes
* **Database Mail:** The alerting system requires a profile named `'MyMailProfile'`.
* **Hardcoded IDs:** Some procedures (e.g., `usp_AddManualBalance`) contain hardcoded `SequenceID`s specific to the owner's data.
* **SQL Version:** Script sets `COMPATIBILITY_LEVEL = 150` (SQL Server 2019).

## License

This project is licensed under the [GPL-3.0 License](LICENSE.txt).