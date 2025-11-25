# SQL Data Warehousing Project

Building a data warehouse in **MS SQL Server** using a robust ETL pipeline and the **medallion architecture** for analytics and reporting.

---


## Project Overview

This project builds a data warehouse on **Microsoft SQL Server** to support analytics and reporting. The goal is to ingest raw transactional data, transform it into a curated form, and make it available for business intelligence tools. The medallion (or multi-layer) architecture ensures clean separation of concerns, scalability, and data quality.

---

## Architecture
![Medallion Architecture](https://github.com/LamaNima/sql-data-warehousing-project/blob/main/documents/data_architecture.png)


### Medallion Architecture Layers

- **Bronze (Raw) Layer**: Raw, minimally transformed data.  
- **Silver (Cleansed) Layer**: Cleaned, deduplicated, standardized datasets.  
- **Gold (Analytics) Layer**: Business-ready tables, aggregates, fact/dimension models.

This design helps ensure data integrity and supports incremental loading, backfilling, and data lineage.

---

## Data Sources

List of data sources ingested into the warehouse:
- CSV / flat files  

---

## ETL / ELT Pipeline

The ETL pipeline is responsible for:

1. **Extraction**: Pulling data from source systems into staging.  
2. **Transformation**: Cleaning, validating, deduplicating data.  
3. **Loading**: Populating the Bronze, Silver, and Gold layers.  

---
