# Bank Jatim Banking Dashboard

A Power BI dashboard project analyzing customer, transaction, loan, card, and support-call data for **Bank Jatim**. The report is built as a multi-page interactive dashboard with a star-schema data model behind it.

---

## 📊 Project Overview

This dashboard gives a 360° view of the bank's operations, covering:

- Customer growth and account holdings
- Transaction volume and value trends
- Loan performance by type and duration
- Card issuance and expiration tracking
- Customer support call resolution rates

**Headline KPIs** (shown on every page):

| Metric | Value |
|---|---|
| Number of Customers | 5,000 |
| Total Balance | 249M |
| Total Transactions | $100.11M |
| Number of Transactions | 20K |
| Total Loans | $616.66M |

---

## 🗂️ Pages / Navigation

| Page | Contents |
|---|---|
| **Home Page** | Landing page with logo and navigation buttons |
| **Over View** | Card type distribution, active customer growth by year, avg interest rate by loan type, card expirations next month, total balance by account type |
| **Customer** | Top customers with multiple accounts, top 10 customers by total loans, customer growth rate by year, top 10 customers by number of transactions |
| **Transaction** | Total transaction count/amount by year, average transaction value by transaction type, transaction growth rate by year |
| **Loan** | Average loan duration by loan type, loan type distribution, loan amount per year, loans ending next month by loan type |
| **Support Calls** | Resolution rate by issue type, number of calls by issue type, top customers with issues, number of calls resolved vs. unresolved |

Each analytical page (Over View, Customer, Transaction, Loan, Support Calls) includes **Month Name** and **Quarter** slicers for filtering.

---

## 🧩 Data Model

The model follows a **star schema** with fact tables at the center and surrounding dimension tables.

### Fact Tables
- **FactTransactions** — AccountID, Amount, CustomerID, TransactionDate, ∑ TransactionID, TransactionTypeID
- **FactLoans** — CustomerID, InterestRate, LoanDuration, ∑ LoanAmount, LoanEndDate, ∑ LoanID, LoanStartDate, LoanTypeID
- **FactSupportCalls** — CallDate, ∑ CallID, CustomerID, IssueTypeID, Resolved

### Dimension Tables
- **DimCustomers** — CustomerID, Full Name, JoinDate
- **DimAccounts** — AccountID, AccountType, ∑ Balance, CreatedDate, CustomerID
- **DimCards** — ∑ CardID, CardType, CustomerID, ExpirationDate, IssuedDate
- **DimTransactionType** — TransactionType, TransactionTypeID
- **DimLoanType** — LoanType, LoanTypeID
- **DimIssueType** — IssueType, IssueTypeID
- **DimDate** — Date, Is Weekend, Month Name, ∑ Month Number, Quarter

### Relationships
- `DimCustomers` → `FactTransactions`, `FactLoans`, `FactSupportCalls`, `DimAccounts`, `DimCards` (1-to-many)
- `DimAccounts` → `FactTransactions` (1-to-many)
- `DimTransactionType` → `FactTransactions`
- `DimLoanType` → `FactLoans`
- `DimIssueType` → `FactSupportCalls`
- `DimDate` → `FactTransactions`, `FactLoans`, `FactSupportCalls` (via respective date fields)

---

## 🛠️ Tech Stack

- **Tool:** Microsoft Power BI Desktop
- **Model type:** Star schema (fact + dimension tables)
- **Visuals used:** KPI cards, bar charts, line charts, pie charts, gauge-style progress bars, slicers

---

## 📁 Project Files

| File | Description |
|---|---|
| `Banking_Dashboard.pdf` | Exported view of all dashboard pages |
| `Data_Modeling.PNG` | Screenshot of the Power BI data model / relationships view |
| `README.md` | This file |

---

## 🚀 Getting Started

1. Open the `.pbix` source file in Power BI Desktop (not included in this export — add your own source file here).
2. Refresh the data source connections under **Transform Data**.
3. Use the **Month Name** and **Quarter** slicers on each page to filter results.
4. Navigate between pages using the left-hand icon menu or the Home Page buttons.

---

## 📌 Notes

- Card, loan, and account figures appear to be built on placeholder/sample data (e.g., round customer count of 5,000).
- Several charts (e.g., "Active Customer Growth by Year", "Loan Amount Per Year") show declining trends toward 2025–2026 — worth validating against source data if these are meant to reflect real trends rather than incomplete/partial-year data.
