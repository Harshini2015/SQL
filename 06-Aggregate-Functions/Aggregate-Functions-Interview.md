# 🎯 Aggregate Functions — Interview Questions & Cheatsheet

## 📌 Core Rules to Remember Before Any Interview

1. **`NULL` Handling:** ALL aggregate functions (`SUM`, `AVG`, `COUNT(col)`, `MIN`, `MAX`) **ignore `NULL` values**, EXCEPT `COUNT(*)` and `COUNT(1)`.
2. **`WHERE` vs `HAVING`:** Aggregate functions **cannot** appear in a `WHERE` clause. They must appear in `HAVING`, `SELECT`, or `ORDER BY`.
3. **Empty Tables:** `SUM()`, `AVG()`, `MIN()`, and `MAX()` return **`NULL`** on an empty table, whereas `COUNT()` returns **`0`**.

---

## 📊 Summary Comparison: Aggregate Functions & NULLs

| Function | Ignores `NULL`? | Result on Empty Table | Works on Strings? |
| :--- | :--- | :--- | :--- |
| **`COUNT(*)`** | ❌ No | `0` | ✅ Yes |
| **`COUNT(column)`** | ✅ Yes | `0` | ✅ Yes |
| **`SUM(column)`** | ✅ Yes | `NULL` | ❌ No |
| **`AVG(column)`** | ✅ Yes | `NULL` | ❌ No |
| **`MIN(column)`** | ✅ Yes | `NULL` | ✅ Yes (Alphabetical) |
| **`MAX(column)`** | ✅ Yes | `NULL` | ✅ Yes (Alphabetical) |

---

# 🎯 Top Interview Questions & Code Snippets

### 1. How do you count conditional items using `COUNT` or `SUM` with `CASE`?

> **Question:** Count total completed orders vs total canceled orders in a single query.

```sql
SELECT 
    COUNT(CASE WHEN status = 'Completed' THEN 1 END) AS completed_orders,
    SUM(CASE WHEN status = 'Canceled' THEN 1 ELSE 0 END) AS canceled_orders
FROM orders;
```

---

### 2. How do you find the 2nd highest salary using subqueries and `MAX()`?

> **Question:** Find 2nd highest salary without using `LIMIT` or window functions.

```sql
SELECT MAX(salary) AS second_highest_salary
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

---

### 3. What is the output of `AVG()` when 1 out of 4 rows is `NULL`?

> **Question:** Table has scores: `10, 20, 30, NULL`. What does `AVG(score)` return?

```text
Answer: 20
Calculation: (10 + 20 + 30) / 3 = 20  (NULL is ignored in BOTH sum and count)
```

> **Follow-up:** How do you treat `NULL` as `0` in the average calculation?

```sql
SELECT AVG(COALESCE(score, 0)) FROM tests; 
-- Result: (10 + 20 + 30 + 0) / 4 = 15
```

---

### 4. What is the difference between `COUNT(*)` and `COUNT(1)`?

> There is **no performance difference**. Modern RDBMS query planners execute both identically.

---

### 5. Why does `SELECT dept, name, AVG(salary) FROM emp GROUP BY dept;` fail in SQL standard?

> Because `name` is included in the `SELECT` list but is **neither aggregated nor included in the `GROUP BY` clause** (violates `ONLY_FULL_GROUP_BY` rule).

---

# 🧠 Quick Revision Pipeline

```text
Aggregate Query Pipeline
 ↓
1. WHERE (Filter individual rows before aggregation)
 ↓
2. GROUP BY (Group rows into categories)
 ↓
3. Aggregate Functions run (COUNT, SUM, AVG, MIN, MAX - ignore NULLs)
 ↓
4. HAVING (Filter summary groups based on aggregate results)
```
