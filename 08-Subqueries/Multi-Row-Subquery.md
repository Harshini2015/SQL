# 📑 Multi-Row Subquery

## 📌 Definition

A **Multi-Row Subquery** is a nested query that returns **more than one row** of results to the outer query.

---

## 🔑 Key Operators

Because the subquery returns multiple values, standard comparison operators (`=`, `>`) cannot be used directly. Instead, multi-row operators are required:

| Operator | Description | Equivalent Logic |
| :--- | :--- | :--- |
| **`IN`** | Matches any value in the subquery result set | Equal to `val1 OR val2 OR ...` |
| **`NOT IN`** | Excludes all values in the subquery result set | Not equal to all values |
| **`> ANY`** | Greater than **at least one** value in result set | `> MIN(subquery_results)` |
| **`< ANY`** | Less than **at least one** value in result set | `< MAX(subquery_results)` |
| **`> ALL`** | Greater than **every single** value in result set | `> MAX(subquery_results)` |
| **`< ALL`** | Less than **every single** value in result set | `< MIN(subquery_results)` |

---

## 💻 Syntax & Examples

### 1. Using `IN`
```sql
-- Find employees working in IT or HR departments
SELECT name, department_id 
FROM employees
WHERE department_id IN (
    SELECT dept_id FROM departments WHERE dept_name IN ('IT', 'HR')
);
```

### 2. Using `> ANY` vs `> ALL`
```sql
-- Employees earning more than AT LEAST ONE IT employee (> MIN)
SELECT name, salary FROM employees
WHERE salary > ANY (SELECT salary FROM employees WHERE department = 'IT');

-- Employees earning more than ALL IT employees (> MAX)
SELECT name, salary FROM employees
WHERE salary > ALL (SELECT salary FROM employees WHERE department = 'IT');
```

---

# 🎯 Most Asked Interview Questions

### 1. What operators are used with multi-row subqueries?
> `IN`, `NOT IN`, `ANY` (or `SOME`), and `ALL`.

---

### 2. What is the difference between `> ANY` and `> ALL`?
> * `> ANY` evaluates to true if the value is greater than the **minimum** value returned by the subquery.
> * `> ALL` evaluates to true only if the value is greater than the **maximum** value returned by the subquery.

---

# 🧠 Quick Revision

```text
Multi-Row Subquery
 ├── IN → Matches any item in list
 ├── > ANY → Greater than MIN value in list
 └── > ALL → Greater than MAX value in list
```

> **Memory Trick:** `> ANY = > MIN | > ALL = > MAX`
