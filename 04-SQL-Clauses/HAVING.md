# 🎯 HAVING Clause

## 📌 Definition

The **`HAVING`** clause is used to **filter groups** created by the `GROUP BY` clause based on aggregate conditions (e.g., filtering departments where average salary exceeds 60,000).

---

## 🔑 Key Concepts

* **Group-Level Filter:** Applied **after** the data has been grouped by `GROUP BY` and aggregated.
* **Allows Aggregate Functions:** Specifically designed to work with aggregate conditions like `AVG()`, `COUNT()`, `SUM()`, `MIN()`, `MAX()`.
* **Cannot Replace WHERE:** Row-level conditions should stay in `WHERE` to minimize data before grouping.

---

## 💻 Syntax

```sql
SELECT column1, AGGREGATE_FUNCTION(column2)
FROM table_name
WHERE row_condition
GROUP BY column1
HAVING aggregate_condition;
```

---

## 📝 Example

### `employees` Table

| emp_id | name  | department | salary |
| -----: | :---- | :--------- | -----: |
|    101 | Rahul | IT         |  60000 |
|    102 | Priya | HR         |  50000 |
|    103 | Amit  | IT         |  80000 |
|    104 | Neha  | HR         |  40000 |

Find departments where the **average salary is greater than 55,000**:

```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 55000;
```

### Result:

| department | avg_salary |
| :--------- | ---------: |
| IT         |      70000 |

---

## ⚖️ Important Difference: WHERE vs HAVING

| Feature | WHERE Clause | HAVING Clause |
| :--- | :--- | :--- |
| **Applied To** | Individual rows | Groups of rows |
| **Execution Timing** | **Before** `GROUP BY` aggregation | **After** `GROUP BY` aggregation |
| **Aggregate Functions** | Not allowed (`WHERE AVG(s) > 500` ❌) | Allowed (`HAVING AVG(s) > 500` ✅) |
| **Performance Impact** | Reduces dataset size early (Faster) | Operates on aggregated dataset |

---

# 🎯 Most Asked Interview Questions

### 1. What is the purpose of the `HAVING` clause?
> The `HAVING` clause filters aggregated groups produced by a `GROUP BY` clause.

---

### 2. Can we use `HAVING` without a `GROUP BY` clause?
> Yes. If `HAVING` is used without `GROUP BY`, the entire table acts as a single group, though this is rarely used in practice.

---

### 3. Why can't we use aggregate functions in a `WHERE` clause instead of `HAVING`?
> Because `WHERE` evaluates rows individually before any aggregation happens. Aggregation occurs later during `GROUP BY`, so aggregate values are only available when `HAVING` is evaluated.

---

# 🧠 Quick Revision

```text
WHERE Clause (Filters rows first)
       ↓
GROUP BY (Groups remaining rows)
       ↓
HAVING Clause (Filters grouped summaries)
```

> **Memory Trick:** `WHERE filters Rows → HAVING filters Groups`
