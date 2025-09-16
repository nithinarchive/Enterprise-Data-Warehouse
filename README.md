Enterprise Data Warehouse (EDW)

Author: Nithin Suresh (@nithinarchive)
 What’s This

A hands-on example of building an Enterprise Data Warehouse from raw transactional data, transforming it, and building a star schema for analytics & insights. The repo shows how to go from CSVs → staging → dimension & fact tables with SCD-Type2 support, to support BI-style queries.

📦 Contents

Here’s what this repo has:

Folder / File	What it does
*.csv & *_updated.csv (Customers, Orders, Products, Stores, etc.)	Simulated source data (initial + incremental updates)
Staging_Upsert.py	Loads raw & updated data into staging, handles upserts
data_verification.py	Checks data quality / integrity in staging or after transformations
fact_table_population.py	Populates the fact table in the star schema
dimension_tables.sql & creating_table.sql	Schema definitions (dimensions & fact), creation scripts
staging.sql & queries.sql	Staging layer SQL + sample analytics queries
lambda_triggering.py	(optional / placeholder) for triggering ETL pieces — maybe for Lambda or similar services
🧠 Architecture & Data Flow

Here’s how the pipeline works:

Raw CSVs (transactions + updates)
     ↓ Extract / Upsert into Staging
     ↓ Data Cleansing & Validation
     ↓ Transformations + Slowly Changing Dimensions (Type 2)
     ↓ Load into Star Schema:
           • fact_sales (metrics / sales)
           • dim_customer, dim_product, dim_store, dim_date
     ↓ Analytical / BI queries & reports


Key features:

Incremental loads (updates) supported

SCD-Type2 on dimension tables (track history)

Referential integrity between fact & dimension tables

Verifications to ensure data quality

⚙️ Tech Stack

Language: Python (ETL scripts, upsert logic, validation etc.)

SQL: For schema definitions, transformations, queries

Data Source: CSV files (raw + incremental)

DW Layer: Could be PostgreSQL / Redshift / etc. (depends on your infra)

Other Concepts: SCD-Type2, star schema, staging layer, fact & dimension, etc.

🔍 Sample Use-Cases / Queries

Some business questions this setup can help answer:

What are the top 10 products by revenue?

How’s revenue trending monthly / quarterly?

Which stores are underperforming or outperforming?

What’s customer purchase frequency / average order value over time?

How do changes in product attributes or customer details over time affect sales? (via historical tracking)

🛣️ Roadmap / Ideas for Next Level

Here’s where this can grow:

Automate the whole ETL pipeline (Airflow / Prefect / Dagster etc.)

Add real-time or near-real-time data ingest (Change Data Capture, streaming)

Add more source domains: marketing, promotions, returns, logistics etc.

Add dashboards / viz layer (Tableau, PowerBI, Looker, Superset etc.)

Add alerts for data anomalies

Optimize for scale: partitioning, indexing, possibly OLAP features

🧩 How To Run It

Clone the repo.

Set up a database (e.g. PostgreSQL) & create needed schema / tables (using SQL scripts).

Place the raw CSVs & the updated ones in expected folder(s).

Run Staging_Upsert.py to load data into staging.

Run transformation scripts / SQL to apply SCD, build dim & fact.

Use data_verification.py to check integrity.

Run sample queries in queries.sql to validate analytics.

(You may need to configure database connection credentials / paths etc. in the Python scripts.)
