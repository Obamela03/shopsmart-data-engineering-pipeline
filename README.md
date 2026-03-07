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

---

## 3. Data Extraction Layer

### 3.1 Extracting from CSV Files

CSV simulates data exported from operational system (POS, ERP).

#### Engineering Considerations:

- Encoding consistancy
- Schema validation
- Handling malformed rows
- Data type inference control

### 3.2 More Extraction Sources [to be implemented]

---

