# 🪟 Window Functions Basics

## 📌 Definition

A **Window Function** performs calculations across a set of related rows (called a "window") while **retaining individual row identities** in the output (unlike `GROUP BY` which collapses rows into summary outputs).

---

## 🔑 Key Concepts

* **`OVER()` Clause:** Defines the window of rows for the function to operate on.
* **Does NOT Collapse Rows:** Every original input row remains present in the result set, with calculated window values appended as new columns.
* **MySQL Support:** Supported starting from **MySQL 8.0+**.
* **Key Components:**
  * **`PARTITION BY`:** Splits dataset into subset partitions/groups.
  * **`ORDER BY`:** Sorts rows within each partition.

---

## 💻 Syntax

```sql
FUNCTION_NAME() OVER (
    [PARTITION BY partition_column]
    [ORDER BY sort_column ASC|DESC]
)
```

---

## ⚖️ Critical Difference: `GROUP BY` vs Window Function

| Feature | `GROUP BY` | Window Function (`OVER()`) |
| :--- | :--- | :--- |
| **Row Count** | Collapses rows $\rightarrow$ Returns 1 row per group | **Preserves all rows** (Original row count unchanged) |
| **Output Detail** | Summary stats only | Detail rows + calculated group stats side-by-side |

---

## 📝 Example

### `employees` Table

| emp_id | name  | department | salary |
| -----: | :---- | :--------- | -----: |
|    101 | Rahul | IT         |  60000 |
|    102 | Priya | IT         |  80000 |
|    103 | Amit  | HR         |  50000 |

```sql
SELECT 
    name, 
    department, 
    salary,
    AVG(salary) OVER(PARTITION BY department) AS avg_dept_salary
FROM employees;
```

### Result:

| name  | department | salary | avg_dept_salary |
| :---- | :--------- | -----: | --------------: |
| Rahul | IT         |  60000 |           70000 |
| Priya | IT         |  80000 |           70000 |
| Amit  | HR         |  50000 |           50000 |

*(Notice how all 3 original rows are preserved alongside the department average!)*

---

# 🎯 Most Asked Interview Questions

### 1. What is the fundamental difference between `GROUP BY` and a Window Function?
> `GROUP BY` collapses multiple rows into a single summary row per group, whereas a Window Function calculates aggregate or ranking values across a window while preserving every individual row in the output.

---

### 2. Can you use Window Functions in a `WHERE` clause?
> **No.** Window functions run late in query execution (after `WHERE`, `GROUP BY`, and `HAVING`). To filter based on a window function result, wrap the query in a **CTE** or subquery.

---

# 🧠 Quick Revision

```text
Input Rows (Preserved 100%)
       ↓
OVER (PARTITION BY col ORDER BY col)
       ↓
Appends Calculated Window Value to Each Row
```

> **Memory Trick:** `Window Functions calculate WITHOUT collapsing rows!`
