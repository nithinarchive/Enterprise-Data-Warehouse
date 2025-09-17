# Enterprise Data Warehouse
**Author:** Nithin Suresh 
([GitHub](https://github.com/nithinarchive))

*Building a star schema ETL pipeline on AWS Redshift from raw S3 data to analytics-ready fact & dimension tables.*

## Project Overview
This repository demonstrates a complete Enterprise Data Warehouse workflow using Amazon Redshift:
- Load raw relational data from S3
- Transform and clean the data in staging tables
- Populate dimension tables with SCD Type 2 for historical tracking
- Populate fact tables for analytics
- Support BI & SQL-based insights with star schema architecture

## Architecture & Data Flow
S3 (CSV files / relational data) → Redshift Staging Tables → Data Cleansing & Validation → Transform & Apply SCD Type 2 → Star Schema: dim_customer, dim_product, dim_store, dim_date, fact_sales → Analytics & BI queries

## Key Features
- Incremental loads (upserts for updated data)
- Redshift optimized: sort keys, distribution keys
- Star schema for efficient BI queries
- SCD Type 2 to track historical changes in dimension tables
- Data quality verification at each stage
- Supports both DC2 & RA3 nodes
- Modular Python ETL scripts for staging, upsert, and transformations
- Sample analytics queries for BI tools
- Optional AWS Lambda triggers for automation

## Contents
- `*.csv` → Raw S3 source data
- `*_updated.csv` → Incremental updates to simulate real-world changes
- `Staging_Upsert.py` → Python script to load CSVs into Redshift staging tables with upsert logic
- `data_verification.py` → Validates data integrity after staging and transformations
- `dimension_tables.sql` → SQL scripts to create Redshift dimension tables with SCD Type 2
- `fact_table_population.py` → Populates fact tables in Redshift
- `queries.sql` → Sample analytical queries for BI use-cases
- `lambda_triggering.py` → Optional ETL automation trigger (AWS Lambda ready)

## Tech Stack
- Database / DW: Amazon Redshift (DC2 / RA3 nodes)
- ETL: Python (pandas, psycopg2)
- Data Storage: CSVs on local / S3
- Schema Design: Star Schema with Slowly Changing Dimensions (Type 2)
- Analytics: SQL queries optimized for Redshift
- Automation: Optional AWS Lambda triggers

## Sample Analytics Questions
- Top products by revenue per month
- Customer purchase behavior and retention analysis
- Store performance tracking & comparison
- Historical trends for products, customers, and stores
- Monthly revenue by product category
- Customer segmentation based on purchase history
- Identify high-value customers & loyalty patterns

## How to Run
1. Create a Redshift cluster (DC2 or RA3)
2. Set up database and schema in Redshift
3. Upload CSVs to S3 or local machine
4. Configure connection in `Staging_Upsert.py`
5. Run staging load script → transformations → fact & dimension population
6. Use `data_verification.py` to ensure data integrity
7. Run queries in `queries.sql` for analytics
8. 
Pro Tip: Use sort keys and distribution keys on fact tables in Redshift for faster queries

## Roadmap / Next Steps
- Automate the ETL pipeline using Airflow / Prefect / Dagster
- Add real-time data ingestion with streaming / CDC
- Add dashboards in PowerBI / Tableau / Superset
- Optimize for scale & performance with Redshift best practices
- Add logging & alerting for data anomalies
- Expand data sources: marketing, promotions, returns, logistics

## Diagram
![Data Warehouse](Data%20Warehouse.jpg)

