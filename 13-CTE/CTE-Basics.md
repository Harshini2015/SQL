# 🏗️ CTE Basics (Common Table Expression)

## 📌 Definition

A **Common Table Expression (CTE)** is a temporary named result set created using the **`WITH`** clause. It exists only during the execution of a single `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement.

---

## 🔑 Key Concepts

* **Readability & Modularization:** Replaces complex, deeply nested subqueries with clean, modular, top-down queries.
* **Reusable within Query:** A CTE can be referenced multiple times in the main query.
* **Scope:** Exists **only during query execution** (unlike Temporary Tables which persist throughout a database session).
* **MySQL Support:** Supported in **MySQL 8.0+** (PostgreSQL, SQL Server, and Oracle also support CTEs).

---

## 💻 Syntax

```sql
WITH cte_name AS (
    SELECT column1, column2
    FROM table_name
    WHERE condition
)
SELECT * 
FROM cte_name;
```

---

## 📝 Example

### Find Employees Earning Above Department Average

```sql
WITH dept_avg AS (
    SELECT department_id, AVG(salary) AS avg_sal
    FROM employees
    GROUP BY department_id
)
SELECT e.emp_id, e.name, e.salary, d.avg_sal
FROM employees e
JOIN dept_avg d ON e.department_id = d.department_id
WHERE e.salary > d.avg_sal;
```

---

## ⚖️ Important Comparison: CTE vs Subquery vs Temp Table

| Feature | CTE (`WITH`) | Subquery | Temp Table (`#temp`) |
| :--- | :--- | :--- | :--- |
| **Scope** | Single query execution | Single query execution | Current DB session |
| **Reusability** | Multiple times in 1 query | Defined each time | Multiple queries in session |
| **Readability** | **High** (Top-down flow) | Low (Nested inside query) | Medium |
| **Indexing** | Cannot be indexed | Cannot be indexed | **Can be indexed** |

---

# 🎯 Most Asked Interview Questions

### 1. What is a CTE in SQL?
> A Common Table Expression (CTE) is a temporary named result set defined using the `WITH` clause that simplifies and modularizes complex queries.

---

### 2. What is the difference between a CTE and a Temporary Table?
> A CTE exists only during the execution of a single SQL query and cannot be indexed. A Temporary Table persists across multiple queries within a database session and can have indexes.

---

### 3. Does a CTE improve query performance over a subquery?
> In most modern query optimizers, simple CTEs and subqueries produce identical execution plans. However, CTEs drastically improve code readability and maintainability.

---

# 🧠 Quick Revision

```text
WITH cte_name AS (
    Subquery Logic Here
)
SELECT / JOIN using cte_name
```

> **Memory Trick:** `CTE = Temporary Named Query defined with WITH`
