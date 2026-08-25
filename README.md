# 📊 Indian FMCG Retail Sales Analysis – Power BI

## 📌 Project Overview

I built this Power BI project to analyze Indian FMCG retail sales data and turn raw transaction data into an interactive business dashboard.

The main goal of this project was to understand sales performance, profitability, customer behavior, sales channels, store formats, brands, categories, and city-level performance, and present the insights in a simple and business-friendly way.

> **Note:** This is a self-built project that I created independently to practice and demonstrate my Power BI and Data Analytics skills.

---

## 🎯 Business Questions

Through this project, I wanted to answer the following questions:

* What is the total revenue generated?
* What is the total profit?
* How many orders and units were sold?
* What is the overall profit margin?
* What is the average order value?
* How does revenue change month by month?
* Which categories generate the highest revenue?
* Which categories are more profitable?
* Which sales channel performs better?
* Which store formats generate more revenue?
* Which brands are the top performers?
* Which cities contribute the most revenue?
* How does customer behavior vary by gender and loyalty status?
* Can users interactively filter and explore the dashboard?

---

## 🛠️ Tools & Technologies

* Power BI
* Power Query
* DAX
* Data Cleaning
* Data Modeling
* Data Visualization
* Business Analysis

---

## 🔄 Project Workflow

### 1. Data Preparation

I first loaded the dataset into Power BI and checked the data for:

* Missing values
* Data types
* Column quality
* Duplicate or inconsistent values

Most columns were complete. The `Customer_Age` column contained a significant amount of missing data, so I avoided blindly replacing all missing values with the average.

### 2. Data Modeling

I renamed the main transaction table to:

`FactSales`

I then created a separate Date table named:

`DimDate`

using the following DAX:

```DAX
DimDate =
CALENDAR(
    MIN(FactSales[Invoice_Date]),
    MAX(FactSales[Invoice_Date])
)
```

I created the following columns in the Date table:

* Year
* Month
* Quarter
* Month Number

I also sorted the Month column using Month Number so that months appear in the correct chronological order.

### 3. Handling Date & Time

The original `Invoice_Date` column contained both date and time.

To create a proper relationship with the Date table, I created a date-only column:

```DAX
Invoice Date Only =
DATE(
    YEAR(FactSales[Invoice_Date]),
    MONTH(FactSales[Invoice_Date]),
    DAY(FactSales[Invoice_Date])
)
```

The relationship used was:

`DimDate[Date] → FactSales[Invoice Date Only]`

with a **One-to-Many** relationship.

---

## 📌 DAX Measures

### Total Revenue

```DAX
Total Revenue =
SUM(FactSales[Revenue])
```

### Total Cost

```DAX
Total Cost =
SUM(FactSales[Cost])
```

### Total Profit

```DAX
Total Profit =
SUM(FactSales[Margin])
```

### Total Units

```DAX
Total Units =
SUM(FactSales[Units])
```

### Total Orders

```DAX
Total Orders =
DISTINCTCOUNT(FactSales[Invoice_ID])
```

### Profit Margin %

```DAX
Profit Margin % =
DIVIDE(
    [Total Profit],
    [Total Revenue],
    0
)
```

### Average Order Value

```DAX
Average Order Value =
DIVIDE(
    [Total Revenue],
    [Total Orders],
    0
)
```

---

## 📈 Dashboard Pages

### 1. Executive Dashboard

The first page provides a high-level overview of business performance.

It includes:

* Total Revenue
* Total Profit
* Total Orders
* Total Units
* Profit Margin
* Average Order Value
* Monthly Revenue Trend
* Revenue by Category
* Profit by Category
* Channel Analysis

This page is designed to give a quick understanding of overall business performance.

### 2. Sales Performance

This page focuses on sales and profitability analysis.

It includes:

* Revenue by Channel
* Profit by Channel
* Revenue by Store Format
* Top 10 Brands
* City Performance
* Revenue by Category
* Profit by Category

This helps identify which business segments are performing better.

### 3. Customer & Inventory Analysis

This page focuses on customer and inventory-related insights.

It includes:

* Revenue by Customer Gender
* Revenue by Loyalty Flag
* Units Sold by Category
* Stock vs Reorder Level
* Customer Age Analysis

This page helps understand customer behavior and inventory conditions.

### 4. Interactive Analysis

I created a separate interactive analysis page using synchronized slicers.

The slicers include:

* Year
* Category
* Channel
* City

These slicers were synchronized across the dashboard pages so users can filter and explore the report interactively.

---

## 📊 Key KPIs

| KPI                 |  Value |
| ------------------- | -----: |
| Total Revenue       | 39.34M |
| Total Profit        |  7.87M |
| Total Orders        |   100K |
| Total Units         |   300K |
| Profit Margin       | 20.02% |
| Average Order Value | 393.60 |

---

## 💡 Key Insights

### Revenue & Profit

The business generated approximately **39.34M in total revenue** and **7.87M in total profit**.

The overall profit margin is approximately **20.02%**.

### Orders & Units

The business processed approximately **100K orders** and sold approximately **300K units**.

### Average Order Value

The calculated Average Order Value is approximately **393.60**, providing a useful benchmark for understanding the average revenue generated per order.

### Category & Channel Analysis

Revenue and profit were analyzed separately because high revenue does not always mean high profitability.

This helps identify categories and channels that generate strong sales as well as those that contribute better profit.

### Customer Analysis

Customer gender, loyalty status, and age were included to understand customer behavior and revenue contribution.

---

## 🧠 What I Learned From This Project

This project helped me practice more than just creating charts.

I worked on:

* Cleaning business data using Power Query
* Handling missing values
* Creating a Date table
* Creating relationships between tables
* Writing DAX measures
* Creating business KPIs
* Building interactive dashboards
* Comparing revenue and profitability
* Using slicers for interactive analysis
* Turning raw data into business-focused insights

One of the main things I learned is that **revenue alone does not tell the complete business story**.

A category or channel can generate high revenue but still have a lower profit margin. Therefore, I included both revenue and profit analysis in the dashboard.

---

## 🚀 Future Improvements

If I extend this project further, I would like to add:

* Year-over-Year Growth
* MTD / QTD / YTD Analysis
* Advanced Customer Segmentation
* Profitability Analysis by Brand
* Inventory Risk Indicators
* Drill-through Pages
* Dynamic KPI Titles
* More Advanced DAX Calculations

---

## 👩‍💻 About This Project

This is a **self-built Power BI project created independently by me** to practice and demonstrate practical Data Analytics and Business Intelligence skills.

The project focuses on:

**Sales Analytics | Business Insights | Data Visualization | Power BI | DAX**

I built this project to improve my ability to take raw business data, analyze it, create meaningful KPIs, and present the results through an interactive dashboard.

---

## ⭐ Skills Demonstrated

**Power BI | Power Query | DAX | Data Cleaning | Data Modeling | Data Visualization | KPI Development | Business Analysis | Interactive Dashboard Design**
