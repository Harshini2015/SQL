# ➕ DATE_ADD & DATE_SUB Functions

## 📌 Definition

The **`DATE_ADD()`** and **`DATE_SUB()`** functions add or subtract a specified time interval (days, months, years, hours) to/from a date value.

---

## 🔑 Key Concepts & Intervals

* **`DATE_ADD(date, INTERVAL value unit)`:** Adds specified interval to date.
* **`DATE_SUB(date, INTERVAL value unit)`:** Subtracts specified interval from date.
* **Supported Units:** `DAY`, `WEEK`, `MONTH`, `YEAR`, `HOUR`, `MINUTE`, `SECOND`.

---

## 💻 Syntax & Examples (MySQL)

### 1. Adding Intervals
```sql
-- Add 30 days to order_date
SELECT DATE_ADD('2025-01-01', INTERVAL 30 DAY); 
-- Returns '2025-01-31'

-- Add 1 year
SELECT DATE_ADD('2025-01-01', INTERVAL 1 YEAR); 
-- Returns '2026-01-01'
```

### 2. Subtracting Intervals
```sql
-- Get active users in the last 7 days
SELECT * FROM users
WHERE last_login >= DATE_SUB(CURRENT_DATE, INTERVAL 7 DAY);
```

---

## ⚖️ Dialect Comparisons

| Engine | Add 1 Month Syntax |
| :--- | :--- |
| **MySQL** | `DATE_ADD(hire_date, INTERVAL 1 MONTH)` |
| **SQL Server** | `DATEADD(month, 1, hire_date)` |
| **PostgreSQL** | `hire_date + INTERVAL '1 month'` |
| **Oracle** | `ADD_MONTHS(hire_date, 1)` |

---

# 🎯 Most Asked Interview Questions

### 1. How do you find all orders placed within the last 30 days in MySQL?
> Use `WHERE order_date >= DATE_SUB(CURRENT_DATE, INTERVAL 30 DAY)`.

---

### 2. Can `DATE_ADD()` be used with a negative interval number?
> Yes. In MySQL, `DATE_ADD('2025-01-10', INTERVAL -5 DAY)` is equivalent to `DATE_SUB('2025-01-10', INTERVAL 5 DAY)`.

---

# 🧠 Quick Revision

```text
Date Addition & Subtraction
 ├── MySQL: DATE_ADD(date, INTERVAL 10 DAY)
 ├── MySQL: DATE_SUB(date, INTERVAL 1 MONTH)
 └── SQL Server: DATEADD(day, 10, date)
```

> **Memory Trick:** `DATE_ADD(date, INTERVAL x UNIT)`
