# GlobalTech-Financial-Data-Analytics-Audit

An end-to-end automated data engineering pipeline and executive analytics dashboard built to ingest, clean, deduplicate, and reconcile multi-source enterprise data for **GlobalTech & EuroSystems**.

## Executive Summary
* **Audited Total Revenue:** **$148,274,622.91 USD**
* **Reconciled Transactions:** **53,899** active transactions
* **Active User Accounts:** **14,183** verified accounts
* **Pipeline Speed:** **< 2.0 seconds** total execution time

## Architecture & Pipeline Workflow

1. **Phase 1: SQL Deduplication**  
   Extracted account records from SQLite using SQL Window Functions (`ROW_NUMBER() OVER (PARTITION BY user_id ORDER BY updated_at DESC)`) to isolate active user statuses.
2. **Phase 2: Unstructured Log Parsing**  
   Parsed over 100,000 `.txt` server log entries using Regex to filter out ~5,098 system error messages and extract valid Euro payload values.
3. **Phase 3: Temporal Exchange Rate Alignment**  
   Reindexed calendar dates across 2023 and applied forward-filling (`ffill`) on Friday currency exchange rates to account for weekend transactions.
4. **Phase 4: Power BI Export**  
   Normalized currency to USD and exported `power_bi_ready_dataset.csv` for executive reporting.


## Technology Stack
* **Language & Core:** Python 3.x, Pandas
* **Database & Querying:** SQLite3, SQL Window Functions
* **Text Processing:** Regular Expressions (`re`)
* **Visualization & Reporting:** Power BI Desktop, Matplotlib, Seaborn
