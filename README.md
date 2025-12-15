# SQL Data Warehousing Project

Building a data warehouse in **MS SQL Server** using a robust ETL pipeline and the **medallion architecture** for analytics and reporting.

## 📚 **Project Overview**

This project builds a data warehouse on **Microsoft SQL Server** to support analytics and reporting. The goal is to ingest raw transactional data, transform it into a curated form, and make it available for business intelligence tools. The medallion (or multi-layer) architecture ensures clean separation of concerns, scalability, and data quality.

The project involves:

- 🏗️ **Data Architecture:** Designing a Modern Data Warehouse Using Medallion Architecture Bronze, Silver, and Gold layers.
- ⚙️ **ETL Pipelines:** Extracting, transforming, and loading data from source systems into the warehouse.
- 📊 **Data Modeling:** Developing fact and dimension tables optimized for analytical queries.

## 🏛️ **Architecture**

![Architecture](https://github.com/LamaNima/sql-data-warehousing-project/blob/main/docs/data_architecture.png)

### 🧱 Medallion Architecture Layers

- 🥉 **Bronze (Raw) Layer:** Raw, minimally transformed data.
- 🥈 **Silver (Cleansed) Layer:** Cleaned, deduplicated, standardized datasets.
- 🥇 **Gold (Analytics) Layer:** Business-ready tables, aggregates, fact/dimension models.

This design helps ensure data integrity and supports incremental loading, backfilling, and data lineage.

## 📌 **Project Requirements**

### 🎯 Objective

Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision-making.

### 📁 Specifications

- **Data Sources:** Import data from two source systems (ERP and CRM) provided as CSV files.
- **Data Quality:** Cleanse and resolve data quality issues prior to analysis.
- **Integration:** Combine both sources into a single, user-friendly data model designed for analytical queries.
- **Documentation:** Provide clear documentation of the data model to support both business stakeholders and analytics teams.

## 🔄 **ETL / ELT Pipeline**

The ETL pipeline is responsible for:

- 📥 **Extraction:** Pulling data from source systems into staging.
- 🧹 **Transformation:** Cleaning, validating, deduplicating data.
- 📤 **Loading:** Populating the Bronze, Silver, and Gold layers.

## 🔀 **Data Flow Diagram**

![DataFlow](https://github.com/LamaNima/sql-data-warehousing-project/blob/main/docs/data_flow.png)

Illustrates the Medallion Architecture data lifecycle from CRM & ERP sources through Bronze → Silver → Gold transformation layers.

## ⭐ **Sales Data Mart (Star Schema)**

![DataModel](https://github.com/LamaNima/sql-data-warehousing-project/blob/main/docs/data_model.png)

Represents the **Gold Layer**, optimized for reporting, dashboarding, and analytical queries on customer behavior, product performance, and sales trends.

## 📘 **Fact Table: `gold.fact_sales`**

Stores measurable business events (sales transactions) with foreign keys referencing dimension tables.

**Key Attributes:**

- `order_number`
- `product_key` → `gold.dim_products`
- `customer_key` → `gold.dim_customers`
- `order_date`, `shipping_date`, `due_date`
- `quantity`
- `price`
- `sales_amount`

## 🟨 **Dimension: `gold.dim_customers`**

Descriptive attributes about customers.

**Key Attributes:**

- `customer_key` (PK)
- `customer_id`
- `customer_number`
- `first_name`, `last_name`
- `gender`
- `marital_status`
- `birthdate`
- `country`

## 🟦 **Dimension: `gold.dim_products`**

Descriptive attributes about products.

**Key Attributes:**

- `product_key` (PK)
- `product_id`
- `product_number`
- `product_name`
- `category`, `subcategory`
- `maintenance`
- `cost`
- `product_line`
- `start_date`

## 🔗 **Schema Relationships**

- `fact_sales.product_key` → `dim_products.product_key`
- `fact_sales.customer_key` → `dim_customers.customer_key`

Supports high‑performance analytical queries including:

- Revenue by product/category
- Customer lifetime value
- Sales trends
- Product performance
- Demographic insights

## 📈 **Benefits of This Model**

- **Simplicity:** Easy to understand/star-schema design
- **Performance:** Fast aggregations and filtering
- **Scalability:** New dimensions can be added easily
- **Clarity:** Clear relationships improve lineage & maintenance
