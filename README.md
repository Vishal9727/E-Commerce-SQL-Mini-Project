# 🛒 E-Commerce SQL Mini Project — Data Analyst Portfolio

## 📌 Project Overview

This project is a SQL-based analysis of a demo e-commerce dataset created to simulate a real-world business scenario.

The project focuses on helping an Operations Manager quickly understand:

* Who are the biggest customers?
* Which orders are cancelled or returned?
* Which cities have the highest customer presence?
* Which orders have missing or incomplete information?
* What are the highest-value orders?
* Which payment methods are being used?
* How can SQL be used to identify important operational insights?

The project demonstrates practical SQL skills including **data filtering, sorting, aggregation, joins, pattern matching, NULL handling, calculated fields, and ranking**.

---

## 🏢 Business Scenario

> "The Operations Manager wants a quick weekly view: who are our biggest buyers, which orders are problematic (cancelled/returned), which customers sit in key cities, and which records have data quality gaps."

The objective is to transform raw customer and order data into useful business information using SQL.

---

## 🎯 Business Objectives

The analysis answers the following business questions:

1. Identify customers and their cities.
2. Identify all cities served by the business.
3. Calculate the number of unique customer cities.
4. Identify available payment methods.
5. Find high-value delivered orders.
6. Identify cancelled and returned orders.
7. Analyze orders placed during Q2 2024.
8. Identify customers from selected key cities.
9. Find high-quantity pending orders.
10. Identify orders within a specific value range.
11. Identify Gmail customers.
12. Find customers whose names start with "A".
13. Identify customers with surname "Patel".
14. Search customers using SQL pattern matching.
15. Identify the highest-value orders.
16. Identify the highest-value delivered orders.
17. Find the top 5 customers by delivered revenue.
18. Identify orders with missing payment information.
19. Identify orders not paid using UPI.
20. Find the third-highest order value.

---

## 🗂️ Dataset

The project contains two relational tables.

### 1. Customers

| Column        | Description                |
| ------------- | -------------------------- |
| customer_id   | Unique customer identifier |
| customer_name | Customer name              |
| city          | Customer city              |
| segment       | Customer segment           |
| signup_date   | Customer registration date |
| email         | Customer email address     |

### 2. Orders

| Column       | Description             |
| ------------ | ----------------------- |
| order_id     | Unique order identifier |
| customer_id  | Customer identifier     |
| order_date   | Date of order           |
| category     | Product category        |
| product      | Product name            |
| quantity     | Quantity ordered        |
| unit_price   | Price per unit          |
| status       | Order status            |
| payment_mode | Payment method          |

---

## 🔗 Data Relationship

The two tables are connected using:

```text
customers.customer_id
        ↓
orders.customer_id
```

### Relationship

```text
Customers
   |
   | customer_id
   |
   ↓
Orders
```

One customer can have multiple orders.

---

## 🛠️ SQL Concepts Used

This project demonstrates the following SQL concepts:

* `CREATE TABLE`
* `DROP TABLE`
* `INSERT INTO`
* `SELECT`
* `WHERE`
* `DISTINCT`
* `ORDER BY`
* `LIMIT`
* `OFFSET`
* `COUNT()`
* `SUM()`
* `GROUP BY`
* `JOIN`
* `IN`
* `BETWEEN`
* `LIKE`
* `IS NULL`
* `AND`
* `OR`
* Calculated columns
* Aggregate functions
* NULL handling
* Top-N analysis
* Ranking logic
* Date filtering

---

## 📊 Key Business Metrics

Some of the important metrics calculated in this project include:

### Order Value

```sql
quantity * unit_price
```

### Delivered Revenue

```sql
SUM(quantity * unit_price)
```

### Number of Orders

```sql
COUNT(*)
```

### Unique Cities

```sql
COUNT(DISTINCT city)
```

---

## 🔍 Sample SQL Analysis

### Top 5 Customers by Delivered Revenue

```sql
SELECT 
    c.customer_id,
    c.customer_name,
    SUM(o.quantity * o.unit_price) AS total_spent
FROM orders o
JOIN customers c 
    ON c.customer_id = o.customer_id
WHERE o.status = 'Delivered'
GROUP BY c.customer_id, c.customer_name
ORDER BY total_spent DESC
LIMIT 5;
```

### Cancelled and Returned Orders

```sql
SELECT *
FROM orders
WHERE status IN ('Cancelled', 'Returned');
```

### Orders with Missing Payment Mode

```sql
SELECT 
    order_id,
    status
FROM orders
WHERE payment_mode IS NULL;
```

### Customers from Key Cities

```sql
SELECT 
    customer_id,
    customer_name,
    city,
    signup_date
FROM customers
WHERE city IN ('Delhi', 'Mumbai', 'Bengaluru')
  AND signup_date >= '2022-01-01'
ORDER BY signup_date;
```

---

## 📈 Business Insights

Based on the analysis, the project can help management identify:

### Customer Insights

* Highest-value customers based on delivered revenue.
* Customer distribution across cities.
* Customers belonging to different business segments.
* Customers from strategically important cities.

### Order Insights

* High-value orders.
* Pending orders requiring operational attention.
* Cancelled orders.
* Returned orders.
* Orders with unusually high quantities.

### Data Quality Insights

The analysis also identifies records with missing payment information.

For example:

```sql
WHERE payment_mode IS NULL
```

This can help the operations/data team investigate incomplete transaction records.

---

## 🚨 Operational Recommendations

Based on the analysis, management could:

1. Prioritize high-value customers for retention programs.
2. Investigate recurring cancelled and returned orders.
3. Monitor pending high-quantity orders.
4. Review missing payment information.
5. Analyze customer concentration across major cities.
6. Monitor high-value orders for potential operational risks.
7. Improve data validation rules for payment information.

---

## 📁 Project Structure

```text
ecommerce-sql-mini-project/
│
├── README.md
│
├── sql/
│   └── ecommerce_mini_project.sql
│
├── data/
│   └── ecommerce_demo_data.sql
│
├── docs/
│   └── Business_Requirements.md
│
├── screenshots/
│   └── query_results.png
│
└── LICENSE
```

---

## ▶️ How to Run the Project

### Step 1 — Clone the repository

```bash
git clone <your-github-repository-url>
```

### Step 2 — Open the SQL file

Open:

```text
sql/ecommerce_mini_project.sql
```

### Step 3 — Run the script

Execute the SQL script in a compatible SQL environment such as:

* MySQL
* PostgreSQL with minor syntax adjustments
* SQL Server with syntax adjustments
* MySQL Workbench

### Step 4 — Run the analysis queries

Execute the queries from Q1 to Q20.

---

## 💼 Skills Demonstrated

This project demonstrates practical Data Analyst skills in:

**SQL | Data Analysis | Data Cleaning | Data Quality | Business Analysis | Customer Analysis | Order Analysis | Aggregation | Joins | NULL Handling | Business Insights**

---

## 👨‍💻 Author

**Vishal Kumar**

Aspiring Data Analyst | SQL | Power BI | Excel | Data Analytics

---

## ⭐ If you found this project useful

Feel free to ⭐ star the repository and use the project as a learning reference.
