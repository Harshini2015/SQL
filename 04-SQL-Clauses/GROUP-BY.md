# 📊 GROUP BY Clause

## 📌 Definition

The **`GROUP BY`** clause groups rows that share the same values in specified columns into **summary / aggregate rows** (e.g., finding total salary or total employees per department).

---

## 🔑 Key Concepts

* **Aggregation Partner:** Almost always used together with aggregate functions (`COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()`).
* **Non-Aggregated Column Rule:** Any column in the `SELECT` list that is **not** wrapped inside an aggregate function **must** be included in the `GROUP BY` clause.
* **`NULL` Grouping:** Treats all `NULL` values in the grouping column as a single group.
* **Execution Phase:** Executed **after** `WHERE` filters individual rows, but **before** `HAVING` filters groups.

---

## 💻 Syntax

```sql
SELECT column1, AGGREGATE_FUNCTION(column2)
FROM table_name
WHERE condition
GROUP BY column1;
```

---

## 📝 Example

### `employees` Table

| emp_id | name  | department | salary |
| -----: | :---- | :--------- | -----: |
|    101 | Rahul | IT         |  60000 |
|    102 | Priya | HR         |  50000 |
|    103 | Amit  | IT         |  80000 |
|    104 | Neha  | HR         |  70000 |

```sql
SELECT department, COUNT(*) AS total_employees, AVG(salary) AS avg_salary
FROM employees
GROUP BY department;
```

### Result:

| department | total_employees | avg_salary |
| :--------- | --------------: | ---------: |
| IT         |               2 |      70000 |
| HR         |               2 |      60000 |

---

# 🎯 Most Asked Interview Questions

### 1. What is the main purpose of `GROUP BY`?
> The `GROUP BY` clause collapses multiple rows sharing identical column values into summary rows, enabling aggregate functions to run on each group.

---

### 2. What is the rule regarding non-aggregated columns in a `GROUP BY` query?
> Every non-aggregated column present in the `SELECT` list must be included in the `GROUP BY` clause (enforced by `ONLY_FULL_GROUP_BY` SQL mode in MySQL).

---

### 3. How does `GROUP BY` handle `NULL` values?
> If the grouping column contains `NULL` values, all `NULL` records are grouped together into a single summary row.

---

### 4. What is the execution order of `WHERE`, `GROUP BY`, and `HAVING`?
> 1. `WHERE` (Filters rows) → 2. `GROUP BY` (Groups rows) → 3. `HAVING` (Filters groups).

---

# 🧠 Quick Revision

```text
Individual Rows
 ↓ (Filtered by WHERE)
Identical Values Grouped
 ↓ (GROUP BY col)
Aggregate Functions Applied
 ↓ (COUNT, SUM, AVG)
Summary Rows Returned
```

> **Memory Trick:** `GROUP BY = Categorize Rows for Aggregation`
