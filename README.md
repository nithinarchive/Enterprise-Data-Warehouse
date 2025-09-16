📦 Enterprise Data Warehouse (EDW)

Author: Nithin Suresh

📖 Overview

This project demonstrates the design and implementation of an Enterprise Data Warehouse (EDW) solution. It takes raw transactional data, applies ETL processes, and transforms it into a star schema model suitable for analytics and business intelligence.

The warehouse is built to:

Handle incremental loads with updated records.

Implement Slowly Changing Dimensions (Type-2) to track historical changes.

Provide a robust foundation for reporting and decision-making.

🏗️ Architecture
flowchart TD
    A[Raw CSV Data] --> B[Staging Layer]
    B --> C[Transformations & SCD Type-2]
    C --> D[Star Schema: Fact + Dimensions]
    D --> E[Analytics & Insights]

🗂️ Data Model
Source Data (Relational CSVs)

Customers

Products

Stores

Orders

OrderDetails

Data Warehouse (Star Schema)

Fact Table

fact_sales: Central table capturing sales metrics.

Dimension Tables

dim_customer – Customer attributes with SCD2 handling.

dim_product – Product catalog with historical tracking.

dim_store – Store metadata.

dim_date – Calendar dimension for time-based analysis.

🔄 ETL Process

Extract

Load raw & updated CSVs into staging tables.

Transform

Cleanse data (remove duplicates, validate integrity).

Apply business rules (e.g., revenue calculation).

Implement SCD Type-2 for historical tracking.

Load

Populate star schema tables.

Ensure referential integrity across facts and dimensions.

📊 Business Insights

This warehouse supports queries such as:

Top 10 products by sales & revenue.

Monthly and quarterly revenue trends.

Store-wise sales performance.

Customer purchase frequency and average order value.

⚙️ Tech Stack

Python – ETL scripting, upserts, validation.

SQL – Table creation, transformations, analytics queries.

PostgreSQL / Amazon Redshift – Data warehouse layer.

CSV – Simulated source system files.

🚀 Future Roadmap

Automate pipeline using Airflow / Prefect.

Extend schema with marketing & promotions data.

Introduce Change Data Capture (CDC) for real-time updates.

Add visualization layer (Power BI, QuickSight, Tableau).

👤 Author

Nithin Suresh
GitHub: nithinarchive

**Dimesional Modelling Flow Diagram**
![Flow Diagram](https://github.com/SaadAhmedWaqar/Data-Warehousing-Redshift/assets/105427072/12932ef0-4a52-4c31-a190-910439385980)




