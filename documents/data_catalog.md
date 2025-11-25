# Data Catalog for Gold Layer

## Overview

The Gold Layer is the business-level data representation, structured to support analytical and reporting use cases. It consists of **dimension tables** and **fact tables** for specific business metrics.

---

### 1. **gold.dim_customers**

- **Objective:** Provides customer details.
- **Columns:**

| Column Name     | Data Type   | Description                                                                           |
| --------------- | ----------- | ------------------------------------------------------------------------------------- |
| customer_key    | INT         | Surrogate key uniquely identifying each customer record in the dimension table.       |
| customer_id     | INT         | Unique numerical identifier assigned to each customer.                                |
| customer_number | VARCHAR(50) | Alphanumeric identifier representing the customer, used for tracking and referencing. |
| first_name      | VARCHAR(50) | Customer's first name                                                                 |
| last_name       | VARCHAR(50) | Customer's last name                                                                  |
| country         | VARCHAR(50) | Country of residence for the customer (e.g., 'Australia').                            |
| marital_status  | VARCHAR(50) | Marital status of the customer (e.g., 'Married', 'Single').                           |
| gender          | VARCHAR(50) | Gender of the customer (e.g., 'Male', 'Female', 'n/a').                               |
| birthdate       | DATE        | Date of birth of the customer, formatted as YYYY-MM-DD (e.g., 1971-10-06).            |
| create_date     | DATE        | Date and time when the customer record was created in the system                      |

---

### 2. **gold.dim_products**

- **Purpose:** Provides information about products.
- **Columns:**

| Column Name          | Data Type   | Description                                                                                        |
| -------------------- | ----------- | -------------------------------------------------------------------------------------------------- |
| product_key          | INT         | Surrogate key uniquely identifying each product record in the dimension table.                     |
| product_id           | INT         | Unique identifier assigned to the product for internal tracking and referencing.                   |
| product_number       | VARCHAR(50) | Structured alphanumeric code representing the product, often used for categorization or inventory. |
| product_name         | VARCHAR(50) | Descriptive name of the product, including key details such as type, color, and size.              |
| category_id          | VARCHAR(50) | Unique identifier for the product's category, linking to its high-level classification.            |
| category             | VARCHAR(50) | Broader classification of the product to group related items.(e.g., Bikes, Components)             |
| subcategory          | VARCHAR(50) | More detailed classification of the product within the category, such as product type.             |
| maintenance_required | VARCHAR(50) | Indicates whether the product requires maintenance (e.g., 'Yes', 'No').                            |
| cost                 | INT         | Cost or base price of the product, measured in monetary units.                                     |
| product_line         | VARCHAR(50) | Specific product or series to which the product belongs (e.g., Road, Mountain).                    |
| start_date           | DATE        | Date when the product became available for sale or use, stored in                                  |

---

### 3. **gold.fact_sales**

- **Purpose:** Stores transactional sales data for analytical purposes.
- **Columns:**

| Column Name   | Data Type   | Description                                                                             |
| ------------- | ----------- | --------------------------------------------------------------------------------------- |
| order_number  | VARCHAR(50) | A unique alphanumeric identifier for each sales order (e.g., 'SO54496').                |
| product_key   | INT         | Surrogate key linking the order to the product dimension table.                         |
| customer_key  | INT         | Surrogate key linking the order to the customer dimension table.                        |
| order_date    | DATE        | Date when the order was placed.                                                         |
| shipping_date | DATE        | Date when the order was shipped to the customer.                                        |
| due_date      | DATE        | Date when the order payment was due.                                                    |
| sales_amount  | INT         | Total monetary value of the sale for the line item, in whole currency units (e.g., 25). |
| quantity      | INT         | number of units of the product ordered for the item (e.g., 1).                          |
| price         | INT         | price per unit of the product for the item, in whole currency units (e.g., 25).         |
