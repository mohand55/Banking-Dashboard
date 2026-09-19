Bank Jatim Banking Dashboard
A Power BI dashboard project analyzing customer, transaction, loan, card, and support-call data for Bank Jatim. The report is built as a multi-page interactive dashboard with a star-schema data model behind it.

📊 Project Overview
This dashboard gives a 360° view of the bank's operations, covering:

Customer growth and account holdings
Transaction volume and value trends
Loan performance by type and duration
Card issuance and expiration tracking
Customer support call resolution rates
Headline KPIs (shown on every page):

Metric	Value
Number of Customers	5,000
Total Balance	249M
Total Transactions	$100.11M
Number of Transactions	20K
Total Loans	$616.66M
🗂️ Pages / Navigation
The report has 6 pages, reachable from the left-hand icon menu (or the buttons on the Home Page). Every analytical page (all except Home Page) repeats the 5 top KPI cards and includes Month Name and Quarter slicers on the left for filtering.

1️⃣ Home Page
The landing/cover page of the report.

Bank Jatim logo and tagline
Navigation buttons: Home Page, Over View, Customer, Transaction, Loan, SupportCalls
Purpose: entry point only — no data visuals here
2️⃣ Over View
A general summary page giving a snapshot of the whole bank's activity.

Card Type Distribution (bar chart) — count of cards by type: Debit (1,363), Prepaid (1,355), Credit (1,282)
Active Customer Growth by Year (line chart) — trend of active customers from 2023 to 2026 (shows a declining slope)
Avg Interest Rate by Loan Type (pie chart) — interest rate share split across Personal, Home, Education, Car (~24–26% each)
Number of Card Type Expired Next Month (bar chart) — cards expiring soon: Prepaid (33), Debit (23), Credit (22)
Total Balance by Account Type (bar chart) — Business (87M), Checking (83M), Savings (79M)
3️⃣ Customer
Focused on customer-level insights and rankings.

Top Customers Having More Than One Account (bar chart) — customers holding multiple accounts (up to 7)
Top 10 Customers Per Total Loans (bar chart) — highest-value loan holders, led by Paul Merritt ($1.61M)
Customer Growth Rate by Year (line chart) — year-over-year % growth in customer base (2016–2026), showing a sharp drop toward the end
Top 10 Customers Per Number of Transactions (bar chart) — most active customers by transaction count, led by Kimberly Smith (35)
4️⃣ Transaction
Dedicated to analyzing transaction behavior and value.

Total Transaction and Transaction Amount by Year (combo bar + line chart) — transaction count (bars) and total amount (line) from 2022–2025
Average Transaction Value by Transaction Type (pie chart) — Payment, Deposit, Transfer, Withdrawal — each roughly 25% share, ~$5K average
Transaction Growth Rate by Year (line chart) — % growth in transactions 2023–2026, dropping from +52.63% to -100%
5️⃣ Loan
Covers loan portfolio structure and performance.

Average Loan Duration by Loan Type (bar chart) — Education (5.6), Car/Home/Personal (5.5 yrs each)
Loan Type Distribution (bar chart) — Car (633), Home (626), Education (624), Personal (617)
Loan Amount Per Year (line chart) — total loan amount disbursed 2020–2024, peaking at $167M in 2021, dropping to $61M by 2024
Loans Ending Next Month by Loan Type (bar chart) — Education (10), Car (8), Home (6), Personal (6)
6️⃣ Support Calls
Tracks customer service call volume and outcomes.

Resolution Rate by Issue Type (bar chart) — Loan Query and Transaction Dispute (51% each), Account Access (48%), Card Issue (47%)
Number of Calls by Issue Type (bar chart) — Transaction Dispute (774), Account Access (768), Card Issue (729), Loan Query (729)
Top Customers Having Issue (bar chart) — customers with the most support tickets (up to 7)
Number of Calls by Resolved (pie chart) — resolved (No: 50.7%) vs. unresolved (Yes: 49.3%) — label mapping should be double-checked in the source model
🧩 Data Model
The model follows a star schema with fact tables at the center and surrounding dimension tables.

Fact Tables
FactTransactions — AccountID, Amount, CustomerID, TransactionDate, ∑ TransactionID, TransactionTypeID
FactLoans — CustomerID, InterestRate, LoanDuration, ∑ LoanAmount, LoanEndDate, ∑ LoanID, LoanStartDate, LoanTypeID
FactSupportCalls — CallDate, ∑ CallID, CustomerID, IssueTypeID, Resolved
Dimension Tables
DimCustomers — CustomerID, Full Name, JoinDate
DimAccounts — AccountID, AccountType, ∑ Balance, CreatedDate, CustomerID
DimCards — ∑ CardID, CardType, CustomerID, ExpirationDate, IssuedDate
DimTransactionType — TransactionType, TransactionTypeID
DimLoanType — LoanType, LoanTypeID
DimIssueType — IssueType, IssueTypeID
DimDate — Date, Is Weekend, Month Name, ∑ Month Number, Quarter
Relationships
DimCustomers → FactTransactions, FactLoans, FactSupportCalls, DimAccounts, DimCards (1-to-many)
DimAccounts → FactTransactions (1-to-many)
DimTransactionType → FactTransactions
DimLoanType → FactLoans
DimIssueType → FactSupportCalls
DimDate → FactTransactions, FactLoans, FactSupportCalls (via respective date fields)
🛠️ Tech Stack
Tool: Microsoft Power BI Desktop
Model type: Star schema (fact + dimension tables)
Visuals used: KPI cards, bar charts, line charts, pie charts, gauge-style progress bars, slicers
📁 Project Files
File	Description
Banking_Dashboard.pdf	Exported view of all dashboard pages
Data_Modeling.PNG	Screenshot of the Power BI data model / relationships view
README.md	This file
🚀 Getting Started
Open the .pbix source file in Power BI Desktop (not included in this export — add your own source file here).
Refresh the data source connections under Transform Data.
Use the Month Name and Quarter slicers on each page to filter results.
Navigate between pages using the left-hand icon menu or the Home Page buttons.
📌 Notes
Card, loan, and account figures appear to be built on placeholder/sample data (e.g., round customer count of 5,000).
Several charts (e.g., "Active Customer Growth by Year", "Loan Amount Per Year") show declining trends toward 2025–2026 — worth validating against source data if these are meant to reflect real trends rather than incomplete/partial-year data.
