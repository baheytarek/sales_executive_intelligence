# 📊 Executive Sales & Customer Intelligence Suite (Power BI)

## 📋 Project Overview
This project delivers a comprehensive 3-page business intelligence solution designed to transform raw transactional data into actionable executive insights. By building a robust semantic layer using **DAX (Data Analysis Expressions)**, this dashboard tracks performance across three critical business dimensions: **Sales, Customers, and Products.**

### 🔗 The "Data Source" Connection
This project is part of a modular data architecture. It consumes data from a structured **SQL Data Warehouse** (Gold Layer).
* **Source:** SQL Server (Import Mode)
* **Pre-processing:** While basic cleaning was done in SQL, the advanced business logic and interactivity were engineered directly in Power BI using DAX.
* **SQL Backend Repository:** (https://github.com/baheytarek/sql-data-warehouse-project/)

---

## 🏗️ Data Modeling (Star Schema)
The foundation of this analysis is a highly optimized Star Schema, ensuring scalability and calculation accuracy.

* **Fact Table:** `fact_sales` (Sales transactions and quantities).
* **Dimension Tables:** * `dim_customers`: Demographic and segmentation data.
  * `dim_products`: Product catalog and performance tiering.
  * `dim_date`: A custom-built time dimension.

### 📅 Custom Date Dimension (DAX)
To support advanced Time Intelligence, I generated a dedicated date table:
```dax
dim_date = CALENDAR(MIN('gold fact_sales'[order_date]), MAX('gold fact_sales'[order_date]))

Quarter = YEAR(dim_date[Date]) & " Q" & QUARTER(dim_date[Date])
----

### 🧠 Advanced DAX Engineering
I engineered a series of calculated columns and measures to handle complex business logic directly within the data model.


