
# ☕ Coffee Shop Data Warehouse
Data warehouse project for a coffee shop using Star Schema, SQL Server, and SSIS ETL for sales analysis.

## 📌 Project Overview

This project demonstrates the development of a data warehouse to organize coffee shop transactional data for reporting and analysis.

The project implements a **Star Schema** consisting of several dimension tables and a sales transaction fact table. ETL processes were developed to extract, transform, and load data from source systems into the data warehouse.

## ⭐ Star Schema

The data warehouse consists of the following components:

- `DimTransaction`
- `DimStore`
- `DimProduct`
- `DimDate`
- `SalesTransaction` Fact Table

The star schema is designed to support analysis of sales performance based on transaction, store, product, and date information.

## 🔄 ETL Process

The ETL packages were developed to populate the dimension and fact tables.

### 1. Transaction Dimension

The Transaction Dimension ETL process:

- Deletes existing records to prevent duplication.
- Extracts transaction data using an OLE DB Source.
- Loads the processed data into the Transaction Dimension table.
- Produces clean and structured transaction data for analysis.

### 2. Store Dimension

The Store Dimension ETL process:

- Clears existing records using an SQL Task.
- Extracts store data from the source system.
- Loads the data into the Store Dimension table.
- Structures store information for reporting and analysis.

### 3. Product Dimension

The Product Dimension ETL process:

- Deletes existing records from the Product Dimension.
- Extracts product information from the source.
- Loads the processed data into `DimProduct`.
- Provides structured product data for reporting and analysis.

### 4. Date Dimension

The Date Dimension is generated programmatically through SQL tasks.

The process:

- Removes existing date records.
- Generates new date records.
- Populates the Date Dimension with structured date information.
- Supports time-based analysis within the data warehouse.

### 5. Sales Transaction Fact

The Sales Transaction Fact table is the central fact table of the warehouse.

The ETL process:

- Extracts transactional data from multiple source systems.
- Applies transformations to the source data.
- Processes and aggregates transactional information.
- Loads the final data into the Sales Transaction Fact table.

This provides a foundation for analyzing coffee shop sales performance.

## 🛠️ Tools & Technologies

- SQL
- SQL Server
- SQL Server Integration Services (SSIS)
- OLE DB
- Data Warehousing
- ETL
- Star Schema

## 📊 Data Warehouse Structure

```text
                 ┌───────────────┐
                 │  DimProduct   │
                 └───────┬───────┘
                         │
                         │
┌───────────────┐   ┌────▼──────────────────┐   ┌───────────────┐
│ DimTransaction│──►│ SalesTransaction Fact │◄──│   DimStore    │
└───────────────┘   └────▲──────────────────┘   └───────────────┘
                         │
                         │
                 ┌───────┴───────┐
                 │    DimDate    │
                 └───────────────┘
