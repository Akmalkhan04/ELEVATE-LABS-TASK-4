# ELEVATE-LABS-TASK-4
# 🛒 Ecommerce SQL Data Analysis Project

## 📖 Overview
This project demonstrates how to perform **SQL-based data analysis** on an ecommerce dataset using **SQLite**.  
It includes table creation, data insertion, and analytical queries using core SQL operations such as:
- `SELECT`, `WHERE`, `ORDER BY`, `GROUP BY`
- `JOIN` (INNER, LEFT)
- Subqueries
- Aggregate functions (`SUM`, `AVG`)
- Views
- Index optimization

The goal is to learn how to query, analyze, and optimize structured data efficiently.

---

## 🧩 Tools & Setup

### 🛠 Tools Used
- **SQLite** (lightweight relational database)
- **DB Browser for SQLite** (for running queries and viewing results)

### ⚙️ Setup Instructions
1. Install [DB Browser for SQLite](https://sqlitebrowser.org)
2. Create a new database named `ecommerce_db.sqlite`
3. Open the `Execute SQL` tab
4. Copy and paste the code from `ecommerce_analysis.sql`
5. Click **▶ Execute All**
6. Switch to the **Browse Data** tab to view the results

---

## 🧱 Database Schema

### Tables
| Table | Description |
|--------|--------------|
| **customers** | Contains customer information |
| **products** | Contains product details and categories |
| **orders** | Holds order information and totals |
| **order_items** | Line items per order |

### Relationships
- `orders.customer_id → customers.customer_id`
- `order_items.order_id → orders.order_id`
- `order_items.product_id → products.product_id`

---

## 💾 Data Inserted

Sample data includes:
- **3 Customers**
- **5 Products**
- **4 Orders**
- **6 Order Items**

This data is fictional and used for demonstration only.

---

## 📊 Analysis Queries

| # | Query Description | SQL Feature Used |
|---|-------------------|------------------|
| 1 | List all customers | Basic `SELECT` |
| 2 | Top 10 most expensive products | `ORDER BY` |
| 3 | Total sales per category | `JOIN`, `GROUP BY`, `SUM()` |
| 4 | Orders with customer names | `INNER JOIN` |
| 5 | Customers who spent above average | Subquery + `HAVING` |
| 6 | Total revenue | `SUM()` |
| 7 | Average order value | `AVG()` |
| 8 | Create a view (`customer_sales`) | `CREATE VIEW` |
| 9 | Add indexes for optimization | `CREATE INDEX` |

---

## 🧠 View and Indexes

### View: `customer_sales`
```sql
CREATE VIEW customer_sales AS
SELECT c.customer_id, c.name, SUM(o.total_amount) AS total_spent
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id;
