# 🔍 Subquery Basics

## 📌 Definition

A **Subquery** (also called an **Inner Query** or **Nested Query**) is an SQL query nested inside another SQL query (such as `SELECT`, `INSERT`, `UPDATE`, or `DELETE`).

---

## 🔑 Key Concepts

* **Execution Order:** In standard non-correlated subqueries, the **inner query executes once first**, and its result is passed to the **outer query**.
* **Enclosed in Parentheses:** Subqueries must always be enclosed within parentheses `()`.
* **Placement Options:**
  * **`WHERE` Clause:** Used for filtering records dynamically.
  * **`FROM` Clause (Derived Table):** Acts as a temporary table (must be given a table alias in MySQL!).
  * **`SELECT` Clause:** Computes a scalar value per row.

---

## 💻 Syntax & Types

```sql
-- Subquery in WHERE clause
SELECT name, salary 
FROM employees 
WHERE salary > (SELECT AVG(salary) FROM employees);

-- Subquery in FROM clause (Derived Table)
SELECT dept_id, max_sal
FROM (
    SELECT dept_id, MAX(salary) AS max_sal 
    FROM employees 
    GROUP BY dept_id
) AS dept_summary; -- Table alias required in MySQL!
```

---

## 📋 Subquery Categories

| Category | Description | Suitable Operators |
| :--- | :--- | :--- |
| **Scalar Subquery** | Returns exactly 1 row and 1 column (Single value) | `=`, `>`, `<`, `>=`, `<=` |
| **Single-Row Subquery** | Returns 1 row with multiple columns | `=`, `IN` |
| **Multi-Row Subquery** | Returns multiple rows (1 column) | `IN`, `ANY`, `ALL` |
| **Correlated Subquery** | References columns from the outer query | `EXISTS`, `NOT EXISTS` |

---

# 🎯 Most Asked Interview Questions

### 1. What is a subquery in SQL?
> A subquery is a nested query enclosed in parentheses whose result is evaluated and used by the outer query.

---

### 2. Why must a derived table (subquery in `FROM` clause) have an alias in MySQL?
> MySQL requires every derived table in a `FROM` clause to have an explicit table alias so the outer query can uniquely reference its columns.

---

### 3. What is a scalar subquery?
> A scalar subquery is a subquery that returns exactly one single value (1 row, 1 column).

---

# 🧠 Quick Revision

```text
Outer Query
 └── Uses result from: (Inner Subquery)
                          ↓
                    Executes First
```

> **Memory Trick:** `Subquery = Nested Query inside Parentheses ()`
