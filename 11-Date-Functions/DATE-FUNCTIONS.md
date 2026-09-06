# 🗓️ Date Extraction Functions (YEAR, MONTH, DAY, EXTRACT)

## 📌 Definition

Date Extraction functions extract specific components (such as year, month, day, quarter, or day of week) from date or datetime expressions.

---

## 🔑 Core Extraction Functions (MySQL)

| Function | Output Description | Output Example |
| :--- | :--- | :--- |
| **`YEAR(date)`** | Four-digit year | `2025` |
| **`MONTH(date)`** | Month number (1 to 12) | `6` |
| **`DAY(date)`** / **`DAYOFMONTH(date)`** | Day of month (1 to 31) | `15` |
| **`QUARTER(date)`** | Quarter of year (1 to 4) | `2` |
| **`DAYOFWEEK(date)`** | Day of week index (1 = Sun, 7 = Sat) | `4` |
| **`MONTHNAME(date)`** | Full month name string | `'June'` |

---

## 💻 Standard ANSI SQL: `EXTRACT()`

```sql
SELECT 
    EXTRACT(YEAR FROM order_date) AS order_year,
    EXTRACT(MONTH FROM order_date) AS order_month
FROM orders;
```

---

## 💻 MySQL Shorthand Examples

```sql
-- Find all employees hired in the year 2023
SELECT name, hire_date
FROM employees
WHERE YEAR(hire_date) = 2023;

-- Total sales grouped by year and month
SELECT 
    YEAR(order_date) AS yr,
    MONTH(order_date) AS mth,
    SUM(amount) AS monthly_sales
FROM orders
GROUP BY YEAR(order_date), MONTH(order_date);
```

---

# 🎯 Most Asked Interview Questions

### 1. How do you group data by year and month in SQL?
> Use `GROUP BY YEAR(date_column), MONTH(date_column)`.

---

### 2. What is the standard ANSI SQL method to extract date parts?
> The ANSI SQL standard function is `EXTRACT(part FROM date)`.

---

# 🧠 Quick Revision

```text
Date Parts Extraction
 ├── YEAR(date)  → YYYY
 ├── MONTH(date) → 1 to 12
 ├── DAY(date)   → 1 to 31
 └── EXTRACT(YEAR FROM date) (ANSI Standard)
```

> **Memory Trick:** `YEAR(), MONTH(), DAY() extract individual components`
