# ✨ DISTINCT Clause

## 📌 Definition

The **`DISTINCT`** keyword is used in conjunction with `SELECT` to **remove duplicate rows** and return only unique values from the dataset.

---

## 🔑 Key Concepts

* **Unique Rows:** Evaluates specified columns and filters out identical duplicate rows.
* **Multi-Column Uniqueness:** `SELECT DISTINCT col1, col2` evaluates uniqueness across the **combination** of `col1` and `col2`.
* **`NULL` Value Handling:** Treats all `NULL` values as duplicate values, returning only a **single `NULL`** entry.
* **With Aggregate Functions:** Can be used inside aggregate functions, such as `COUNT(DISTINCT column_name)`.

---

## 💻 Syntax

```sql
SELECT DISTINCT column1, column2
FROM table_name;
```

---

## 📝 Example

### `employees` Table

| emp_id | name  | department |
| -----: | :---- | :--------- |
|    101 | Rahul | IT         |
|    102 | Priya | HR         |
|    103 | Amit  | IT         |
|    104 | Neha  | NULL       |
|    105 | Pooja | NULL       |

```sql
SELECT DISTINCT department
FROM employees;
```

### Result:

| department |
| :--------- |
| IT         |
| HR         |
| NULL       |

---

## ⚖️ Important Difference: DISTINCT vs GROUP BY

| Feature | `SELECT DISTINCT` | `GROUP BY` |
| :--- | :--- | :--- |
| **Primary Purpose** | Removes duplicate values from result set | Groups data for performing summary aggregations |
| **Aggregate Functions** | Does not perform aggregations by default | Specifically designed for `SUM`, `COUNT`, `AVG`, etc. |
| **Performance** | Equivalent performance for basic uniqueness queries | Allows filtering with `HAVING` clause |

---

# 🎯 Most Asked Interview Questions

### 1. What does `SELECT DISTINCT` do?
> `SELECT DISTINCT` removes duplicate records from the query output and returns only unique values.

---

### 2. How does `DISTINCT` handle `NULL` values?
> `DISTINCT` considers all `NULL` values to be equal (duplicates of each other) and returns only one single `NULL` in the result set.

---

### 3. What is the difference between `COUNT(*)` and `COUNT(DISTINCT column)`?
> `COUNT(*)` counts all rows including duplicates and `NULL`s. `COUNT(DISTINCT column)` counts only unique non-null values in that column.

---

# 🧠 Quick Revision

```text
Dataset with Duplicates
 ↓
SELECT DISTINCT
 ↓
Identical values collapsed
 ↓
Returns Unique Records (Multiple NULLs → Single NULL)
```

> **Memory Trick:** `DISTINCT = Keep Unique Values Only`
