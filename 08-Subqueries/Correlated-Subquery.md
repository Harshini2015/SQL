# 🔄 Correlated Subquery

## 📌 Definition

A **Correlated Subquery** is a nested subquery that **references one or more columns from the outer query**.

---

## 🔑 Key Concepts

* **Row-by-Row Execution:** Unlike a regular subquery which executes **once**, a correlated subquery **re-evaluates for every single row** processed by the outer query.
* **Outer-Inner Dependency:** The inner query cannot be executed independently of the outer query.
* **Performance Consideration:** Correlated subqueries can be computationally expensive ($O(N \times M)$ execution complexity) on large unindexed tables.

---

## 💻 Syntax & Classic Example

### Find Employees Earning Above Their Department's Average Salary

```sql
SELECT e1.emp_id, e1.name, e1.department_id, e1.salary
FROM employees e1
WHERE e1.salary > (
    SELECT AVG(e2.salary)
    FROM employees e2
    WHERE e2.department_id = e1.department_id -- References outer table e1!
);
```

### How It Works Step-by-Step:
1. Outer query fetches the first employee row (`e1`).
2. Inner query calculates the average salary **specifically for `e1`'s department**.
3. Outer query tests if `e1.salary > avg_dept_salary`.
4. Repeats step 1–3 for every row in `employees`.

---

## ⚖️ Important Difference: Regular Subquery vs Correlated Subquery

| Feature | Regular Subquery | Correlated Subquery |
| :--- | :--- | :--- |
| **Dependency** | Independent of outer query | Depends on outer query columns |
| **Executions** | Executes **once** total | Executes **once per outer row** |
| **Independent Run** | Inner query can be run separately | Inner query cannot run standalone |
| **Performance** | Generally faster | Can be slower on large datasets |

---

# 🎯 Most Asked Interview Questions

### 1. What is a correlated subquery?
> A correlated subquery is a subquery that references column values from the outer query, causing the inner query to execute once for every row processed by the outer query.

---

### 2. Can you execute the inner query of a correlated subquery independently?
> No, attempting to run the inner query alone will throw an "Unknown column" error because it relies on variables passed down from the outer query.

---

### 3. How do you rewrite a correlated subquery to make it faster?
> By replacing it with an `INNER JOIN` against an aggregated derived table or using **Window Functions** (e.g. `AVG(salary) OVER(PARTITION BY dept_id)`).

---

# 🧠 Quick Revision

```text
For each row in Outer Query:
       ↓
Pass row column to Inner Subquery
       ↓
Inner Subquery executes and returns result
       ↓
Outer Query checks WHERE condition
```

> **Memory Trick:** `Correlated Subquery = Re-evaluates for EVERY row!`
