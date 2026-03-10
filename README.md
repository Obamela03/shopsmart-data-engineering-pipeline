# **🛍️ SHOP SMART DATA ENGINEERING PIPELINE**

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://python.org)
[![Pandas](https://img.shields.io/badge/pandas-2.0%2B-green)](https://pandas.pydata.org/)
[![License](https://img.shields.io/badge/license-MIT-orange)](LICENSE)

**An ETL pipeline for processing retail transaction data**

***

</div>

## 📋 Summary

ShopSmart is a production-style end-to-end data engineering project that demonstrates how raw transactional data can be transformed into a structured analytical data warehouse and consumed by a business intelligence layer.

The project simulates a realistic mid-sized retail analytics environment and showcases competencies expected from a Mid-Level Data Engineer, including:

* Multi-source data ingestion (CSV & SQL) --- \[TO BE IMPLEMENTED]

* ETL pipeline design using Python (Pandas & NumPy)

* Data cleaning and validation

* Dimensional modeling (Star Schema)

* SQL Server data warehouse implementation

* Indexing and performance optimization

* Automated data loading

* BI integration with Power BI

* Documentation and architectural reasoning

***

## 1. Business Problem

Retail stakeholders require visibility into:

1. Revenue trends over time
2. Regional Performance
3. Product Category Performance
4. Promotion Effectiveness

This project objective is to structure, clean, model, and optimize data for reporting.

***

## 2. Architecture Design

### 2.1 High-Level Architecture

Raw Data Sources (CSV / SQL) ↓ Python ETL Layer (Pandas / NumPy) ↓ Data Validation & Transformation ↓ Dimensional Modeling (Star Schema) ↓ SQL Server Data Warehouse ↓ Power BI Semantic Layer & Reporting.

### 2.2 Architectural Decisions & Rationale

#### Why Python for ETL?

* Flexible transformation logic

* Strong ecosystem for data manipulation

* Industry-standard tool for data engineering

* Easy automation & scheduling

#### Why SQL Server as Data Warehouse?

* Strong relational integrity

* Widely used in enterprise environments

* Native integration with BI tools

* Indexing and performance capabilities

#### Why Star Schema?

* Optimized for analytical queries

* Simplifies BI modeling

* Improves performance for aggregations

* Industry best practice for OLAP workloads

***

## 3. Data Extraction Layer

### 3.1 Extracting from CSV Files

CSV simulates data exported from operational system (POS, ERP).

#### Engineering Considerations:

* Encoding consistancy

* Schema validation

* Handling malformed rows

* Data type inference control

### 3.2 More Extraction Sources \[to be implemented]

***

## 4. Data Tranformation Layer (ETL core)

### 4.1 Data Cleaning

Key operations:

* Remove Duplicates

* Handle nulls

* Enforce schema cosnistency

* Ntandardize naming conventions

* Convert data types

### 4.2 Data Validation

Validation checks include:

* Negative quantity detection

* Null foreign keys

* Outlier revenue detection

* Referential integrity validation

Example:

`assert transactions["qty"].min() >= 0`

### 4.3 Feature Engineering

Creation of the Revenue column (Number of items multiplied by the items unit price).

### 4.4 Dimensional Modeling Construction

**Dimension Tables:**

1. DimStore
2. DimProduct
3. DimCustomer
4. **FactSales**: captures measurable events.

***

## 5. Data Warehouse Implementation (SQL Server)

### 5.1 Database Creation

`CREATE DATABASE ShopSmartDW`

### 5.2 Table Creation

Foreign key constraints are added to enforce referential integrity.

Example:

```
CREATE TABLE dbo.FactSales (
    txn_id INT PRIMARY KEY,
    store_id INT NOT NULL,
    product_id INT NOT NULL,
    cust_id INT NOT NULL,
    qty INT,
    revenue DECIMAL(18,2),
    date DATE,
    month VARCHAR(7)
);
```

### 5.3 Indexing Strategy

***

## 6. Data Loading Strategy

***

## 7. BI Integration (Power BI)

### Connection Setup

1. Server: (localdb)\MSSQLLocalDB

2. Database: ShopSmartDW

3. Authentication: Windows

4. Mode: Import

### Data Model

Star schema with:

FactSales → DimStore FactSales → DimProduct FactSales → DimCustomer

Cardinality: Many-to-One

### Core Business Measures (DAX)

```
Total Revenue = SUM(FactSales[revenue])
Total Units = SUM(FactSales[qty])
Total Transactions = COUNT(FactSales[txn_id])
Avg Order Value = DIVIDE([Total Revenue], [Total Transactions])
```

***

## 8. Project Folder Structure

```
shopsmart_pipeline/
│
├── data/                # Raw CSV files
├── etl.py               # Transformation logic
├── load_to_sql.py       # Warehouse loading script
├── requirements.txt     # Dependencies
└── README.md
```

***

## 9. Scalability Roadmap

* To improve this project, the following can be done:

* Add logging framework (logging module)

* Implement incremental loads

* Add configuration file (.env)

* Containerize with Docker

* Deploy SQL to Azure SQL

* Automate with Airflow or Prefect

* Implement data quality checks

* Add CI/CD pipeline

***

# **CONCLUSION**

This project demonstrates a complete, production-style analytics pipeline. It reflects practical data engineering skills beyond basic data analysis by emphasizing architecture, modeling, optimization, and integration.

It showcases readiness for roles involving warehouse development, ETL design, and BI enablement.
