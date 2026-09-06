# ☝️ Single-Row Subquery

## 📌 Definition

A **Single-Row Subquery** is a nested query that returns **exactly one single row** (or scalar value) to the outer query.

---

## 🔑 Key Concepts

* **Allowed Operators:** Uses single-value comparison operators (`=`, `>`, `<`, `>=`, `<=`, `<>`).
* **Error Trigger:** If a single-row subquery accidentally returns **more than one row**, the database throws an error:
  `ERROR 1242 (21000): Subquery returns more than 1 row`.

---

## 💻 Syntax & Examples

### 1. Find Employees Earning Above Average Salary
```sql
SELECT name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
*(The inner query `(SELECT AVG(salary) FROM employees)` calculates a single number, e.g., 65000)*

---

### 2. Find Employee Details for the Highest Earner
```sql
SELECT emp_id, name, salary
FROM employees
WHERE salary = (SELECT MAX(salary) FROM employees);
```

---

## 📝 Example Result

### `employees` Table

| emp_id | name  | salary |
| -----: | :---- | -----: |
|    101 | Rahul |  50000 |
|    102 | Priya |  80000 |
|    103 | Amit  |  65000 |

* `AVG(salary)` = `65000`
* Outer Query output for `salary > 65000`:

| name  | salary |
| :---- | -----: |
| Priya |  80000 |

---

# 🎯 Most Asked Interview Questions

### 1. What is a single-row subquery?
> A subquery that evaluates to a single row/value and is used with single-value comparison operators (`=`, `>`, `<`, etc.).

---

### 2. What error occurs if a single-row subquery returns multiple rows?
> The database engine returns an error such as `Subquery returns more than 1 row`. To fix this, use multi-row operators like `IN` or `LIMIT 1`.

---

# 🧠 Quick Revision

```text
Single-Row Subquery
 ↓
Returns exactly 1 row / value
 ↓
Uses: =, >, <, >=, <=, <>
 ↓
More than 1 row → Error!
```

> **Memory Trick:** `Single-Row Subquery = 1 Result Value Only`
