# ➕ SUM Function

## 📌 Definition

The **`SUM()`** aggregate function calculates the total sum of all values in a numeric column or expression.

---

## 🔑 Key Concepts

* **Ignores `NULL` Values:** `SUM()` automatically ignores `NULL` values during calculation.
* **Empty Set / All-NULL Result:** If the table is empty or all values in the column are `NULL`, `SUM()` returns **`NULL`** (not `0`).
* **`SUM(DISTINCT column)`:** Calculates the sum of only distinct (unique) non-null values.
* **Combining with `COALESCE`:** Use `COALESCE(SUM(column), 0)` to safely return `0` instead of `NULL` for empty results.

---

## 💻 Syntax & Examples

### 1. Simple Total Sum
```sql
SELECT SUM(salary) AS total_payroll
FROM employees;
```

### 2. Department-Wise Sum with `GROUP BY`
```sql
SELECT department, SUM(salary) AS dept_payroll
FROM employees
GROUP BY department;
```

### 3. Handling `NULL` Results Safely
```sql
SELECT COALESCE(SUM(amount), 0) AS total_sales
FROM orders
WHERE order_date = '2025-01-01';
```

---

## 📝 Example

### `orders` Table

| order_id | customer_id | amount |
| -------: | ----------: | -----: |
|        1 |         101 |    500 |
|        2 |         102 |   1000 |
|        3 |         101 |    500 |
|        4 |         103 |   NULL |

```sql
SELECT 
    SUM(amount) AS total_amount,                -- Returns 2000
    SUM(DISTINCT amount) AS total_unique_amount -- Returns 1500 (500 + 1000)
FROM orders;
```

---

# 🎯 Most Asked Interview Questions

### 1. What does `SUM()` return if a table is empty or all values are `NULL`?
> It returns `NULL`.

---

### 2. How can you ensure `SUM()` returns `0` instead of `NULL` when no records match?
> Wrap the `SUM()` function in `COALESCE` or `IFNULL`: `COALESCE(SUM(amount), 0)`.

---

### 3. Does `SUM()` work on non-numeric columns?
> No. `SUM()` operates exclusively on numeric numeric data types (integer, decimal, float). Using it on strings will throw an error or produce 0 depending on the database engine.

---

# 🧠 Quick Revision

```text
SUM Function
 ├── Ignores NULL values
 ├── Returns NULL for empty sets (Use COALESCE to return 0)
 └── SUM(DISTINCT col) adds unique values only
```

> **Memory Trick:** `SUM ignores NULL | Empty sum = NULL (unless COALESCE used)`
