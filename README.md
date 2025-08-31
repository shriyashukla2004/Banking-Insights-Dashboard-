🏦 Banking Insights Analysis

End-to-end analytics project that generates a relational banking dataset in SQL Server (~10k rows), injects realistic data-quality issues, and delivers a Power BI dashboard with core banking KPIs (financial health + customer/account insights).

🔍 What’s Inside

Data Generator (SQL): Creates 5 core tables with keys & relationships: Customers, Accounts, Branches, Transactions, Loans.

Dirty Data Scenarios: Nulls, mixed date formats, numbers-as-text, duplicates, typos, case inconsistencies, orphaned FKs, and outliers—perfect for Power Query cleaning practice.

Power BI Report (.pbix): Two pages of KPIs with cards/gauges/trend & branch comparisons, plus ready-to-use DAX measures.

🧱 Data Model & Volume (Approx.)

Customers: ~2,000

Accounts: ~2,500

Transactions: ~5,000

Loans: ~500

Branches: ~25–50

Relationships:
Customers (1) ── (∞) Accounts
Branches (1) ── (∞) Accounts
Accounts (1) ── (∞) Transactions
Customers (1) ── (∞) Loans and Accounts (1) ── (∞) Loans (with a few intentional orphans)

🗃️ Table Schemas (Example)

Customers: CustomerID (PK), Name, Email, DOB, Gender, City, Phone, JoinDate
Accounts: AccountID (PK), CustomerID (FK), BranchID (FK), AccountType, Status, OpenDate, Balance
Branches: BranchID (PK), BranchName, City
Transactions: TransactionID (PK), AccountID (FK), TransactionType, Amount, Date, Channel, (optional) InterestIncome, InterestExpense
Loans: LoanID (PK), CustomerID (FK), AccountID (FK), LoanAmount, LoanStatus, InterestRate, StartDate, EndDate

🧼 Deliberately Injected Data Issues

Nulls/Blanks: Email, Phone, Balance, AccountType

Wrong Types: "ten" in numeric columns, balances as text

Dates: Mixed MM/DD/YYYY and DD-MM-YYYY

Duplicates: Same customer name, different CustomerID

Outliers: Negative balances/loan amounts, extreme transaction values

Typos: “Depositt”, “withdrwal” in TransactionType

Orphans: Loans.AccountID not present in Accounts

Casing: “mumbai” vs “Mumbai”

📊 KPIs & Visuals

Page 1 – Financial Health (KPIs 1–5):
Cards/Gauges + one trend: NIM, Loan-to-Deposit, NPL Ratio, Cost-to-Income, ROA

Page 2 – Customers & Accounts (KPIs 6–10):
Cards + Columns: Total Customers, Active Accounts, Total Deposits, Total Loan Amount, Branch-wise Revenue

🚀 Getting Started

SQL Server

Create a database (e.g., BankingSim).

Run the provided /sql/01_schema.sql (tables + constraints).

Run /sql/02_seed_clean.sql (clean baseline data).

Run /sql/03_inject_dirty.sql (data-quality issues for Power Query practice).

Power BI Desktop

Connect to SQL Server (BankingSim).

Use Power Query to:

Remove duplicates (Customers)

Standardize casing (AccountType, City)

Fix types & parse dates to a single format

Replace erroneous values & flag nulls

Identify & handle orphaned loans

Load model, create relationships, add DAX, and build visuals using the report pages.

✅ Learning Outcomes

Model a banking relational schema with realistic constraints

Practice Power Query data cleaning on messy, multi-table data

Build finance-grade KPIs with DAX and intuitive Power BI visuals

Validate data with SQL tests (duplicates, outliers)
