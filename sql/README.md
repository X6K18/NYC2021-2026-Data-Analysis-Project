# 🗄️ SQL Directory

This folder contains all SQL scripts used for data extraction, transformation, and database management. These scripts serve as the primary interface between the raw data warehouse and the Python analysis environment.

## 📂 Structure

- `extraction/`: Scripts used to pull data from production databases into our local environment.
- `transformations/`: Complex logic used to create views or temporary tables for analysis.
- `queries/`: Ad-hoc analysis queries and quality checks.
- `schemas/`: Definitions for table structures and data dictionaries.

## 🚀 SQL Workflow

1. **Connect**: Use the credentials defined in `/config/config.yaml` to connect to the database.
2. **Extract**: Run the scripts in `extraction/` to generate the `.csv` files found in `data/raw/`.
3. **Transform**: For heavy data processing, we utilize SQL (CTE and Window Functions) to minimize the load on Python's memory.

## 📝 Script Inventory

| File Name | Description | Source Table(s) | Target Output |
| :--- | :--- | :--- | :--- |
| `get_user_activity.sql` | Extracts daily login and session data. | `users`, `sessions` | `user_activity.csv` |
| `calc_monthly_kpi.sql` | Calculates MoM growth and retention rates. | `orders`, `transactions` | `monthly_metrics` |
| `data_cleaning.sql` | Identifies and filters out duplicate records. | `stg_sales` | `clean_sales_view` |

## 🛠 Database Environment

- **Dialect**: [e.g., PostgreSQL / MySQL / T-SQL]
- **Warehouse**: [e.g., BigQuery / Snowflake / Local Server]
- **Connection Method**: Python `SQLAlchemy` or `pyodbc` (see `src/data_loader.py`).

## ⚠️ Best Practices

- **Performance**: Use Common Table Expressions (CTEs) instead of deeply nested subqueries for better readability.
- **Formatting**: Use uppercase for keywords (`SELECT`, `FROM`, `WHERE`) and lowercase for table/column names.
- **Security**: **NEVER** include hardcoded passwords or API keys in these files. Use environment variables or config files.
- **Comments**: Explain complex join logic or specific business rules (e.g., why a certain status code is excluded) directly in the `.sql` file.