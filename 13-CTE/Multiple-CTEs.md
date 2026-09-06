# 🔗 Multiple CTEs

## 📌 Definition

SQL allows defining **multiple CTEs in a single query** by separating them with commas after a single **`WITH`** keyword.

---

## 🔑 Key Concepts

* **Single `WITH` Keyword:** Write `WITH` only once at the beginning of the query.
* **Chaining CTEs:** Later CTEs can reference previously defined CTEs defined in the same `WITH` statement.
* **Multi-Stage Data Pipeline:** Ideal for building multi-step analytical pipelines in clean readable steps.

---

## 💻 Syntax

```sql
WITH cte_one AS (
    SELECT ...
),
cte_two AS (
    -- Can reference cte_one here!
    SELECT ... FROM cte_one
)
SELECT * 
FROM cte_two;
```

---

## 📝 Realistic Example

Find high-performing departments and list their top-earning employees:

```sql
-- Step 1: Calculate department total sales
WITH dept_sales AS (
    SELECT department_id, SUM(sales_amount) AS total_sales
    FROM sales
    GROUP BY department_id
),
-- Step 2: Filter high performing departments (Referencing Step 1)
high_performing_depts AS (
    SELECT department_id 
    FROM dept_sales 
    WHERE total_sales > 100000
)
-- Step 3: Fetch employees belonging to high performing departments
SELECT e.emp_id, e.name, e.department_id, e.salary
FROM employees e
JOIN high_performing_depts h ON e.department_id = h.department_id;
```

---

# 🎯 Most Asked Interview Questions

### 1. How do you define multiple CTEs in a single SQL query?
> By specifying `WITH cte1 AS (...), cte2 AS (...)` using commas to separate each CTE block, writing the `WITH` keyword only once at the beginning.

---

### 2. Can a CTE reference another CTE defined in the same query?
> Yes. A CTE can reference any other CTE defined **before** it in the same `WITH` clause.

---

# 🧠 Quick Revision

```text
WITH cte1 AS (...),
     cte2 AS (... references cte1 ...),
     cte3 AS (... references cte2 ...)
SELECT * FROM cte3;
```

> **Memory Trick:** `One WITH keyword, multiple CTEs separated by commas`
