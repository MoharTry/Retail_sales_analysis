# Retail Sales Analysis SQL Project

## Project Overview
**Project Title:** Retail Sales Analysis  
**Level:** Beginner  
**Database:** retail_sales_db  

This project showcases SQL skills used for analyzing retail sales data. It involves setting up a database, performing exploratory data analysis (EDA), and answering business-related questions using SQL queries. This is an excellent project for those starting with SQL and data analysis.

---

## Objectives
- **Set up a retail sales database:** Create and populate a sales database.
- **Data Cleaning:** Identify and handle missing or null values.
- **Exploratory Data Analysis (EDA):** Understand key trends in the dataset.
- **Business Analysis:** Use SQL to answer essential business questions.

---

## Project Structure

### 1. Database Setup
The project begins by creating a database and a `retail_sales` table to store sales data.

```sql
CREATE DATABASE retail_sales_db;

CREATE TABLE retail_sales (
    transactions_id INT PRIMARY KEY,
    sale_date DATE,
    sale_time TIME,
    customer_id INT,
    gender VARCHAR(15),
    age INT,
    category VARCHAR(15),
    quantity INT,
    price_per_unit FLOAT,
    cogs FLOAT,
    total_sale FLOAT
);
```

### 2. Data Exploration & Cleaning
- **Record Count:** Total number of records.
- **Unique Customers & Categories:** Identify distinct customers and product categories.
- **Handling Missing Values:** Detect and remove null values.

```sql
SELECT COUNT(*) FROM retail_sales;
SELECT COUNT(DISTINCT customer_id) FROM retail_sales;
SELECT DISTINCT category FROM retail_sales;
DELETE FROM retail_sales WHERE 
    sale_date IS NULL OR sale_time IS NULL OR customer_id IS NULL OR 
    gender IS NULL OR age IS NULL OR category IS NULL OR 
    quantity IS NULL OR price_per_unit IS NULL OR cogs IS NULL;
```

---

## Data Analysis & Findings
Several SQL queries were developed to derive business insights:

- **Retrieve all sales made on a specific date**
- **Find transactions where the category is 'Clothing' and quantity > 4 in Nov-2022**
- **Calculate total sales per category**
- **Find the average age of customers who bought 'Beauty' products**
- **Identify high-value transactions (sales > 1000)**
- **Determine the best-selling month per year**
- **Find the top 5 customers based on total sales**

```sql
SELECT 
    EXTRACT(YEAR FROM sale_date) AS year,
    EXTRACT(MONTH FROM sale_date) AS month,
    AVG(total_sale) AS avg_sale,
    RANK() OVER(PARTITION BY EXTRACT(YEAR FROM sale_date) ORDER BY AVG(total_sale) DESC) AS rank
FROM retail_sales
GROUP BY year, month;
```

---

## Key Insights
- **Customer Demographics:** Sales distribution across different age groups and categories.
- **High-Value Transactions:** Identified premium purchases.
- **Sales Trends:** Monthly variations in sales, helping identify peak seasons.
- **Customer Behavior:** Recognized top-spending customers and popular product categories.

---

## How to Use
1. **Clone the Repository:** Download the project files from GitHub.
2. **Set Up the Database:** Execute the SQL script to create and populate the database.
3. **Run SQL Queries:** Use the provided queries to analyze the dataset.
4. **Explore & Modify:** Customize queries to gain deeper insights.

---

## Conclusion
This project is a great starting point for SQL-based data analysis. The findings provide actionable insights into sales trends, customer behavior, and business performance. Feel free to modify and extend the queries to explore more business insights!
