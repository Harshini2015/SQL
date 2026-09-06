# 🔍 WHERE Clause

## 📌 Definition

The **`WHERE`** clause is used to **filter individual rows** in a table before any grouping or aggregation takes place.

---

## 🔑 Key Concepts

* **Row-Level Filtering:** Filters individual records based on conditional logic (`TRUE`, `FALSE`, or `UNKNOWN`).
* **Execution Phase:** Executed **before** `GROUP BY` and aggregate functions.
* **No Aggregates Allowed:** You **cannot** use aggregate functions (`SUM`, `AVG`, `COUNT`, etc.) directly inside a `WHERE` clause.
* **Used Across Commands:** Can be used with `SELECT`, `UPDATE`, and `DELETE` queries.

---

## 💻 Syntax

```sql
SELECT column1, column2
FROM table_name
WHERE condition;
```

---

## 📝 Example

### `employees` Table

| emp_id | name  | department | salary |
| -----: | :---- | :--------- | -----: |
|    101 | Rahul | IT         |  60000 |
|    102 | Priya | HR         |  45000 |
|    103 | Amit  | IT         |  75000 |

```sql
SELECT name, salary
FROM employees
WHERE department = 'IT' AND salary > 50000;
```

### Result:

| name  | salary |
| :---- | -----: |
| Rahul |  60000 |
| Amit  |  75000 |

---

## ⚖️ Important Difference: WHERE vs HAVING

| Feature | WHERE Clause | HAVING Clause |
| :--- | :--- | :--- |
| **Filtered Data** | Filters **individual rows** | Filters **groups** of rows |
| **Execution Order** | Executed **BEFORE** `GROUP BY` | Executed **AFTER** `GROUP BY` |
| **Aggregate Functions** | **Cannot** contain aggregate functions | **Can** contain aggregate functions (`AVG() > 5000`) |
| **Usage** | Can be used with `SELECT`, `UPDATE`, `DELETE` | Can be used only with `SELECT` |

---

# 🎯 Most Asked Interview Questions

### 1. What is the purpose of the `WHERE` clause in SQL?
> The `WHERE` clause filters individual records based on specified search conditions.

---

### 2. Can we use aggregate functions like `SUM()` or `COUNT()` in a `WHERE` clause?
> No. Aggregate functions work on sets of rows after grouping, while `WHERE` filters individual rows before grouping. To filter on aggregate values, use the `HAVING` clause.

---

### 3. What happens if you run an `UPDATE` or `DELETE` statement without a `WHERE` clause?
> Without a `WHERE` clause, the `UPDATE` or `DELETE` statement will modify or delete **all rows** in the entire table.

---

# 🧠 Quick Revision

```text
WHERE Clause
 ↓
Row-level filter
 ↓
Executed BEFORE GROUP BY
 ↓
Cannot use aggregate functions
 ↓
Works with SELECT, UPDATE, DELETE
```

> **Memory Trick:** `WHERE = Filter Rows BEFORE Grouping`
