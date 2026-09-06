# ⚖️ Subquery vs JOIN

## 📌 Overview

Both **Subqueries** and **JOINs** are used to combine data from multiple tables. However, they differ in execution strategy, performance, and readability.

---

## ⚖️ Detailed Comparison

| Feature | Subquery | JOIN |
| :--- | :--- | :--- |
| **Execution** | Often executes nested queries row-by-row or creates temporary tables | Joins tables directly in memory using indexed algorithms (Nested Loop, Hash Join, Merge Join) |
| **Performance** | Can be slower for complex/correlated queries | Generally **faster** due to engine optimization and index utilization |
| **Readability** | Easier to read for nested logic or filtering checks | Easier to read when displaying columns from multiple tables |
| **Output Columns** | Selected columns must come from **outer query only** | Can select columns from **any joined table** |

---

## 💻 Query Equivalences

### Example: Find Employees in IT Department

#### 1. Subquery Version
```sql
SELECT name, salary 
FROM employees
WHERE department_id IN (
    SELECT dept_id FROM departments WHERE dept_name = 'IT'
);
```

#### 2. JOIN Version (Preferred for performance)
```sql
SELECT e.name, e.salary 
FROM employees e
INNER JOIN departments d ON e.department_id = d.dept_id
WHERE d.dept_name = 'IT';
```

---

# 🎯 Most Asked Interview Questions

### 1. Are JOINs always faster than subqueries?
> In general, **JOINs are faster** because RDBMS query optimizers can better optimize join operations using indexes (Hash Joins / Merge Joins). However, modern optimizers often rewrite simple subqueries into JOINs internally.

---

### 2. When should you choose a subquery over a JOIN?
> 1. When computing aggregate values for comparison (e.g. `WHERE salary > (SELECT AVG(salary)...)`).
> 2. When checking for existence without duplicating rows (`EXISTS`).
> 3. When readability is improved for complex logic.

---

### 3. When MUST you use a JOIN instead of a subquery?
> When you need to retrieve and display columns from **multiple tables** in the final output result set.

---

# 🧠 Quick Revision

```text
Subquery vs JOIN Decision Tree
 ├── Display columns from 2+ tables? → Use JOIN
 ├── Filter based on aggregate (AVG/MAX)? → Use Subquery
 └── General Rule: Prefer JOIN for performance
```

> **Memory Trick:** `Need columns from both tables? Use JOIN! Comparing against aggregates? Use Subquery!`
