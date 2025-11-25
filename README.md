# 📦SQL Data Warehousing Project

Building a data warehouse in **MS SQL Server** using a robust ETL pipeline and the **medallion architecture** for analytics and reporting.

---


## 📚 Project Overview

This project builds a data warehouse on **Microsoft SQL Server** to support analytics and reporting. The goal is to ingest raw transactional data, transform it into a curated form, and make it available for business intelligence tools. The medallion (or multi-layer) architecture ensures clean separation of concerns, scalability, and data quality.
The project involves:
1. 🏗️ **Data Architecture**: Designing a Modern Data Warehouse Using Medallion Architecture Bronze, Silver, and Gold layers.
2. ⚙️ **ETL Pipelines**: Extracting, transforming, and loading data from source systems into the warehouse.
3. 📊 **Data Modeling**: Developing fact and dimension tables optimized for analytical queries.

## 🏛️ Architecture
![Medallion Architecture](https://github.com/LamaNima/sql-data-warehousing-project/blob/main/documents/data_architecture.png)

### Medallion Architecture Layers

- 🥉 **Bronze (Raw) Layer**: Raw, minimally transformed data.  
- 🥈 **Silver (Cleansed) Layer**: Cleaned, deduplicated, standardized datasets.  
- 🥇**Gold (Analytics) Layer**: Business-ready tables, aggregates, fact/dimension models.

This design helps ensure data integrity and supports incremental loading, backfilling, and data lineage.

---

## 📌 Project Requirements

### 🎯 Objective
Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision-making.

### 📁 Specifications
- Data Sources: Import data from two source systems (ERP and CRM) provided as CSV files.
- Data Quality: Cleanse and resolve data quality issues prior to analysis.
- Integration: Combine both sources into a single, user-friendly data model designed for analytical queries.
- Documentation: Provide clear documentation of the data model to support both business stakeholders and analytics teams.

---

## 🔄 ETL / ELT Pipeline

The ETL pipeline is responsible for:

1. **Extraction**: Pulling data from source systems into staging.  
2. **Transformation**: Cleaning, validating, deduplicating data.  
3. **Loading**: Populating the Bronze, Silver, and Gold layers.  

---

## 🔀 Data Flow Diagram

The diagram below illustrates the end-to-end data flow in the warehouse following the Medallion Architecture — Bronze → Silver → Gold. It shows how data is ingested from CRM and ERP systems, processed through multiple transformation layers, and finally modeled into analytics-ready fact and dimension tables.

![Data Lineage](https://github.com/LamaNima/sql-data-warehousing-project/blob/main/documents/data_flow.png)

---

## ⭐ Sales Data Mart (Star Schema)

The diagram below represents the **Gold Layer** of the Medallion Architecture — the **Sales Data Mart**, modeled using a **Star Schema**.  
It is optimized for reporting, dashboarding, and analytical queries on customer behavior, product performance, and sales trends.

![Sales Data Mart](https://raw.githubusercontent.com/LamaNima/sql-data-warehousing-project/main/documents/data_model.png)

---

### 📘 Fact Table: `gold.fact_sales`

The central **fact table** stores measurable business events (sales transactions).  
It contains **foreign keys** referencing dimension tables, as well as numeric metrics.

**Key Attributes:**
- `order_number` — Transaction identifier  
- `product_key` — FK → `gold.dim_products`  
- `customer_key` — FK → `gold.dim_customers`  
- `order_date`, `shipping_date`, `due_date` — DateTime attributes  
- `quantity` — Number of units sold  
- `price` — Unit price  
- `sales_amount` — Derived metric (`quantity * price`)

This table supports analysis by date, product, and customer.

---

### 🟨 Dimension: `gold.dim_customers`

Descriptive attributes about customers.

**Key Attributes:**
- `customer_key` (PK)  
- `customer_id`  
- `customer_number`  
- `first_name`, `last_name`  
- `gender`  
- `marital_status` (e.g., Married, Single)  
- `birthdate`  
- `country`

This dimension enables demographic and geographic analysis, customer segmentation, and reporting on customer profiles.

---

### 🟦 Dimension: `gold.dim_products`

Descriptive attributes about products.

**Key Attributes:**
- `product_key` (PK)  
- `product_id`  
- `product_number`  
- `product_name`  
- `category`, `subcategory`  
- `maintenance` (Yes / No)  
- `cost`  
- `product_line`  
- `start_date`

This dimension supports analyses of product hierarchy, categories, profitability, and lifecycle.

---

### 📌 Schema Relationships

- `fact_sales.product_key` → `dim_products.product_key`  
- `fact_sales.customer_key` → `dim_customers.customer_key`

This star schema layout is designed for **high-performance analytical queries**, enabling:

- Revenue by product / category  
- Customer lifetime value  
- Sales trends over time  
- Product performance by line / category  
- Customer segmentation and demographics

---

### 📈 Benefits of This Model

- **Simplicity**: Star schema is easy to understand and query  
- **Performance**: Fast aggregation and filtering  
- **Scalability**: Easy to extend with new dimensions  
- **Clarity**: Clear relationships make lineage and maintenance easier  

