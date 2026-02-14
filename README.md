# 🚀 Sales Insights Data Analysis Project

---

## 📌 Project Overview

AtliQ Hardware, a computer hardware and peripheral supplier operating across India, faced declining visibility into sales performance due to fragmented Excel-based reporting.

This project transforms the organization’s reporting system into a fully interactive **Power BI Dashboard**, enabling real-time, data-driven decision-making for leadership.

The solution integrates:

- MySQL database (source system)
- Power Query (ETL & Data Cleaning)
- Star Schema data modeling
- DAX calculations
- Power BI Service deployment

---

## 🏢 Business Problem

The Sales Director struggled with:

- Manual Excel report consolidation
- Delayed performance insights
- Lack of market-level visibility
- Currency inconsistencies
- Poor historical trend analysis

The organization required a centralized analytics solution to enable faster and smarter decision-making.

---

## 🎯 Project Objectives (AIMS Grid)

| Component | Description |
|-----------|------------|
| **Purpose** | Unlock hidden sales insights and automate reporting |
| **Stakeholders** | Sales Director, Marketing Team, IT Team, Data Analytics Team |
| **End Result** | Interactive real-time Power BI dashboard |
| **Success Criteria** | 10% cost reduction in reporting, 5% potential sales increase |

---

## 🛠️ Technology Stack

| Layer | Tool |
|-------|------|
| Database | MySQL |
| Query Tool | MySQL Workbench |
| ETL | Power Query Editor |
| Data Modeling | Star Schema |
| Analysis | DAX |
| Visualization | Power BI Desktop |
| Deployment | Power BI Service & Mobile App |

---

## 🗄️ Database Architecture

### Fact Table
- `sales_transactions`
  - Revenue
  - Sales Quantity
  - Currency
  - Customer Code
  - Product Code
  - Market Code

### Dimension Tables
- `customers`
- `products`
- `markets`
- `date`

---

## 🔎 Data Discovery (SQL Analysis)

Initial SQL exploration revealed:

- 150,000+ transaction records
- Invalid sales values (0 and -1)
- Duplicate currency labels (INR and INR\r)
- Markets outside India (New York, Paris)

These findings guided the ETL pipeline.

---

## 🧹 Data Cleaning & Transformation (Power Query)

### 1️⃣ Market Filtering
Removed non-Indian markets to align with business scope.

### 2️⃣ Invalid Transaction Removal
Filtered out records where:
- Sales Amount = 0
- Sales Amount = -1

### 3️⃣ Currency Normalization
Created a new column:

```
Normalized Sales Amount =
IF Currency = "USD"
THEN Sales Amount * 75
ELSE Sales Amount
```

### 4️⃣ Hidden Character Removal
Cleaned carriage return characters (`\r`) causing duplicate currency categories.

---

## ⭐ Data Modeling – Star Schema

A Star Schema was implemented to optimize performance.

- Central Fact Table: `sales_transactions`
- Connected Dimension Tables:
  - Customers
  - Products
  - Markets
  - Date

Benefits:
- Faster aggregation
- Scalable model
- Efficient time intelligence
- Clean relationships

---

## 📊 Key DAX Measures

```DAX
Total Revenue = SUM(sales_transactions[Normalized Sales Amount])

Total Sales Quantity = SUM(sales_transactions[sales_qty])

Revenue LY =
CALCULATE(
    [Total Revenue],
    SAMEPERIODLASTYEAR('date'[date])
)
```

---

## 📈 Dashboard Features

### KPI Cards
- Total Revenue
- Total Sales Quantity

### Revenue Analysis
- Revenue by Market
- Revenue by Customer
- Revenue by Product
- Revenue by Year & Month

### Top 5 Insights
- Top 5 Customers
- Top 5 Products

### Interactive Controls
- Year slicer
- Month slicer
- Cross-filtering visuals

### Revenue Trends
- Line chart showing monthly business performance

---



## 📥 How to Run This Project

### Step 1: Setup Database
1. Download `DB_dump.sql`
2. Import into MySQL Workbench
3. Create database named `sales`

### Step 2: Connect Power BI
1. Open Power BI Desktop
2. Click **Get Data → MySQL**
3. Connect to `localhost`
4. Select the `sales` database

### Step 3: Apply Transformations
1. Open Power Query
2. Apply cleaning steps
3. Click **Close & Apply**

### Step 4: Explore Dashboard
- Use slicers to filter
- Analyze revenue trends
- Identify top-performing customers and products

---

## 📊 Business Impact

This solution enables:

✔ Faster decision-making  
✔ Automated reporting  
✔ Market-level visibility  
✔ Historical trend comparison  
✔ Executive-ready insights  

Estimated Improvements:
- 10% operational reporting cost reduction
- 5% potential sales growth

---

## 📌 Future Enhancements

- Profit margin analysis
- Forecasting using Power BI Analytics
- Row-level security
- DirectQuery integration
- CRM data integration

---

