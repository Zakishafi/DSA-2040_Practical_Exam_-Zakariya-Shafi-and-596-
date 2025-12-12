# Zakariya Shafi 596

# Practical Exam: Data Warehousing and Data Mining

## Overview
This repository contains a complete project covering **Data Warehousing** and **Data Mining**.  
It demonstrates designing a data warehouse, implementing ETL processes, performing OLAP analysis, and applying data mining techniques including preprocessing, clustering, classification, and association rule mining.

The project is divided into two main sections:

1. Data Warehousing (50 Marks)  
2. Data Mining (50 Marks)  

---

## Section 1: Data Warehousing (50 Marks)

### Task 1: Data Warehouse Design
**Scenario:**  
Design a data warehouse for a retail company that tracks sales, customers, products, and time.

**Star Schema Design:**  
- **Fact Table:** `SalesFact`  
  - Measures: `TotalSales`, `Quantity`  
  - Foreign Keys: `CustomerID`, `ProductID`, `TimeID`  

- **Dimension Tables:**  
  1. `CustomerDim` – `CustomerID`, `Name`, `Country`  
  2. `ProductDim` – `ProductID`, `ProductName`, `Category`  
  3. `TimeDim` – `TimeID`, `Date`, `Month`, `Quarter`, `Year`  
  4. Optional: `CountryDim` – `CountryID`, `CountryName`  

**Schema Diagram:**  
![Star Schema](images/star_schema.png)  

**Why Star Schema?**  
The star schema simplifies queries, improves OLAP performance, and is easier to understand for business users. Denormalization reduces the number of joins required for analysis.

**SQL CREATE TABLE Statements (SQLite syntax):**

```sql
-- Dimension tables
CREATE TABLE CustomerDim (
    CustomerID INTEGER PRIMARY KEY,
    Name TEXT,
    Country TEXT
);

CREATE TABLE ProductDim (
    ProductID INTEGER PRIMARY KEY,
    ProductName TEXT,
    Category TEXT
);

CREATE TABLE TimeDim (
    TimeID INTEGER PRIMARY KEY,
    Date TEXT,
    Month INTEGER,
    Quarter INTEGER,
    Year INTEGER
);

-- Fact table
CREATE TABLE SalesFact (
    SaleID INTEGER PRIMARY KEY,
    CustomerID INTEGER,
    ProductID INTEGER,
    TimeID INTEGER,
    Quantity INTEGER,
    TotalSales REAL,
    FOREIGN KEY (CustomerID) REFERENCES CustomerDim(CustomerID),
    FOREIGN KEY (ProductID) REFERENCES ProductDim(ProductID),
    FOREIGN KEY (TimeID) REFERENCES TimeDim(TimeID)
);


Task 3: OLAP Queries and Analysis

Roll-up, Drill-down, Slice queries using SQL

Visualization of results (bar chart of sales by country)

Analysis of insights and decision-making support

Visualization Example:


Files:

olap_queries.sql

Analysis report in Markdown/PDF
