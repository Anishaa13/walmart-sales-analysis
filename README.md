
# 📊 Walmart Sales Analysis

## 🚀 Project Overview
This project analyzes **Walmart sales data** to uncover key trends, optimize strategies, and understand customer behavior. The goal is to extract actionable insights using **SQL-based data analysis** techniques.

### ✨ Features:
- **Data Cleaning**: Ensured structured and accurate sales data
- **Time-Based Analysis**: Categorized transactions into **Morning, Afternoon, and Evening** for trend identification
- **Profitability Metrics**: Calculated **gross income and margin percentages** for business strategy
- **Customer Behavior Analysis**: Examined customer types, payment methods, and product performance
- **Performance Optimization**: Indexed key columns and used efficient SQL queries for improved database performance

---

## 📂 Dataset Information
- **Source**: [Kaggle - Walmart Sales Forecasting](https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting)
- **Size**: 1000 rows, 17 columns
- **Stores**: Walmart branches in **Mandalay, Yangon, and Naypyitaw**
- **Data Includes**: Sales transactions, product categories, customer demographics, pricing, taxes, and revenue metrics.

---

## 🔧 Installation & Setup

### 1️⃣ Clone the Repository  
```bash
git clone https://github.com/Anishaa13/walmart-sales-analysis.git
cd walmart-sales-analysis
```

### 2️⃣ Set Up MySQL Database  
- Create a **walmartSales** database:
```sql
CREATE DATABASE IF NOT EXISTS walmartSales;
```
- Create the **sales** table:
```sql
CREATE TABLE IF NOT EXISTS sales (
    invoice_id VARCHAR(30) NOT NULL PRIMARY KEY,
    branch VARCHAR(5) NOT NULL,
    city VARCHAR(30) NOT NULL,
    customer_type VARCHAR(30) NOT NULL,
    gender VARCHAR(30) NOT NULL,
    product_line VARCHAR(100) NOT NULL,
    unit_price DECIMAL(10,2) NOT NULL,
    quantity INT NOT NULL,
    tax_pct FLOAT(6,4) NOT NULL,
    total DECIMAL(12,4) NOT NULL,
    date DATETIME NOT NULL,
    time TIME NOT NULL,
    payment VARCHAR(15) NOT NULL,
    cogs DECIMAL(10,2) NOT NULL,
    gross_margin_pct FLOAT(11,9),
    gross_income DECIMAL(12,4),
    rating FLOAT(2,1)
);
```

### 3️⃣ Run SQL Queries  
- Load sales data into the database  
- Execute the **analysis queries** from `SQL_queries.sql`

---

## 🛠️ SQL Workflow & Analysis

### 🔹 Step 1: Data Cleaning
- Ensured accurate data loading into the `sales` table  
- Verified and handled any missing or inconsistent records  

### 🔹 Step 2: Data Transformation
- Added a **time_of_day** column to categorize transactions:
```sql
ALTER TABLE sales ADD COLUMN time_of_day VARCHAR(10);

UPDATE sales
SET time_of_day = 
    CASE 
        WHEN time BETWEEN '00:00:00' AND '12:00:00' THEN 'Morning'
        WHEN time BETWEEN '12:01:00' AND '16:00:00' THEN 'Afternoon'
        ELSE 'Evening'
    END;
```

### 🔹 Step 3: Profitability Analysis
- Calculated **gross income & gross margin percentage**:
```sql
UPDATE sales
SET gross_income = total - cogs,
    gross_margin_pct = (gross_income / total) * 100;
```

---

## 📈 Key Insights & Business Impact
📌 **Peak sales hours identified**, optimizing staffing & promotions  
📌 **Most & least profitable product lines analyzed**, guiding pricing strategies  
📌 **Customer payment preferences tracked**, aiding business decisions  
📌 **Efficient data transformations automated**, reducing manual errors  

---

## 📊 Tools & Technologies Used
- **Database**: MySQL  
- **Key Techniques**: Data cleaning, transformation, profitability analysis  
- **Focus Areas**: Structured querying, indexing, and optimization  

---

## 💡 Future Enhancements
- ✅ **Visualizations**: Integrate with Python (Pandas & Matplotlib) for sales dashboards  
- ✅ **Advanced Analytics**: Apply machine learning for **sales forecasting**  
- ✅ **Automation**: Use **stored procedures & triggers** for data updates  

---

## 📜 License
This project is open-source under the **MIT License**.

---
