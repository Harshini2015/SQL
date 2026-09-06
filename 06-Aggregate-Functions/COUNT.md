# 🔢 COUNT Function

## 📌 Definition

The **`COUNT()`** aggregate function returns the number of rows that match a specified criteria in a query.

---

## 🔑 Key Variants & Rules

| Expression | Behavior | Ignores `NULL`? |
| :--- | :--- | :--- |
| **`COUNT(*)`** | Counts **all rows** in the table/group | ❌ No (Includes rows with NULLs) |
| **`COUNT(1)`** | Counts all rows (Identical performance to `COUNT(*)`) | ❌ No |
| **`COUNT(column_name)`** | Counts rows where `column_name` is **NOT NULL** | ✅ Yes |
| **`COUNT(DISTINCT col)`** | Counts **unique, non-null** values in `col` | ✅ Yes |

---

## 💻 Syntax & Examples

### `employees` Table

| emp_id | name  | department | bonus |
| -----: | :---- | :--------- | ----: |
|    101 | Rahul | IT         |  5000 |
|    102 | Priya | HR         |  6000 |
|    103 | Amit  | IT         |  NULL |
|    104 | Neha  | IT         |  NULL |

```sql
SELECT 
    COUNT(*) AS total_rows,                 -- Returns 4
    COUNT(bonus) AS employees_with_bonus,  -- Returns 2 (Ignores NULLs)
    COUNT(DISTINCT department) AS depts    -- Returns 2 ('IT', 'HR')
FROM employees;
```

---

## ⚖️ Important Difference: `COUNT(*)` vs `COUNT(column)`

| Feature | `COUNT(*)` | `COUNT(column)` |
| :--- | :--- | :--- |
| **Target** | Whole row | Specific column |
| **`NULL` Handling** | Includes rows containing `NULL` | Skips rows where column is `NULL` |
| **Result** | Total row count | Total non-null value count |

---

# 🎯 Most Asked Interview Questions

### 1. What is the difference between `COUNT(*)` and `COUNT(column_name)`?
> `COUNT(*)` counts all rows in the result set regardless of NULL values, whereas `COUNT(column_name)` counts only non-null values in that specific column.

---

### 2. Is `COUNT(1)` faster than `COUNT(*)` in SQL?
> No. In modern relational database management systems (MySQL, PostgreSQL, Oracle, SQL Server), query optimizers treat `COUNT(1)` and `COUNT(*)` identically with identical execution plans and performance.

---

### 3. What will `COUNT(DISTINCT column)` return if the column contains 3 duplicate values and 2 `NULL` values?
> It will return `1` (it counts the single distinct non-null value and ignores the `NULL`s).

---

# 🧠 Quick Revision

```text
COUNT Aggregations
 ├── COUNT(*) → Total rows (includes NULLs)
 ├── COUNT(col) → Non-null rows only
 └── COUNT(DISTINCT col) → Unique non-null rows
```

> **Memory Trick:** `COUNT(*) counts rows | COUNT(col) ignores NULLs`
