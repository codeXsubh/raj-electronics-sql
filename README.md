# Raj Electronics — SQL Analytics (Anonymized)

SQL-based analysis of **accounts receivable** for a wholesale business — focusing on **sales, collections, and outstanding dues** across teams and regions.

---

## 🧠 What this project does

This project represents a real-world business scenario:

- Track how much each client **purchased**
- Track how much they **paid**
- Identify how much is still **outstanding (due)**

Instead of Excel, all analysis is performed using **SQL queries**, making it structured, repeatable, and scalable.

---

## ⚙️ Dataset

- Source: Real operational workflow (anonymized)
- Rows: **200 clients**
- One row = one client

### Key fields:
- `total_sale` → total value sold  
- `total_payment` → amount received  
- `due` → outstanding balance  
- `team_code` → salesperson/team  
- `region_code` → anonymized location  

---

## 🧹 Data Cleaning

- Removed all personal data (names, addresses)
- Replaced identifiers with:
  - `client_id`
  - `team_code`
  - `region_code`
- Standardized column names (`snake_case`)
- Ensured data integrity: due = total_sale - total_payment

---

## 🚀 How to Run (SQLite — Recommended)

No setup required (works out of the box):

```bash
cd raj-electronics-sql
chmod +x scripts/*.sh
./scripts/load_sqlite.sh
./scripts/run_all_sql.sh
```

Run a specific query:
sqlite3 -header -column data/raj_electronics.db < sql/02_kpis.sql

📊 Key Analyses
	•	Overall KPIs (sales, collections, outstanding due)
	•	Team-wise performance
	•	Top clients by pending dues
	•	Region-wise exposure
	•	Due segmentation using buckets (low / medium / high risk)

raj-electronics-sql/
│
├── data/clients.csv        # cleaned dataset
├── sql/                    # SQLite queries
├── postgres/               # PostgreSQL queries
├── scripts/                # automation scripts
├── README.md
