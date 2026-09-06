# 🔢 ORDER BY Clause

## 📌 Definition

The **`ORDER BY`** clause is used to sort the result set of a query in **ascending (`ASC`)** or **descending (`DESC`)** order based on one or more columns.

---

## 🔑 Key Concepts

* **Default Sort:** Defaults to **`ASC` (Ascending)** if no sort order is specified.
* **Multi-Column Sorting:** Sorts by the first column; if duplicate values exist, sorts those rows by the second column, and so on.
* **Sorting by Column Position:** Allows sorting by column index number (e.g. `ORDER BY 2 DESC`), though explicit column names are preferred.
* **Execution Phase:** Executed near the very end of query execution (just before `LIMIT` / `OFFSET`).
* **`NULL` Sorting Behavior:**
  * **MySQL:** Treats `NULL` as the lowest possible value (`ASC` places `NULL`s first, `DESC` places `NULL`s last).
  * **PostgreSQL/Oracle:** Supports explicit `NULLS FIRST` or `NULLS LAST` modifiers.

---

## 💻 Syntax

```sql
SELECT column1, column2
FROM table_name
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC];
```

---

## 📝 Example

### `employees` Table

| emp_id | name  | department | salary |
| -----: | :---- | :--------- | -----: |
|    101 | Rahul | IT         |  60000 |
|    102 | Priya | HR         |  75000 |
|    103 | Amit  | IT         |  75000 |

```sql
SELECT name, department, salary
FROM employees
ORDER BY salary DESC, name ASC;
```

### Result:

| name  | department | salary |
| :---- | :--------- | -----: |
| Amit  | IT         |  75000 |
| Priya | HR         |  75000 |
| Rahul | IT         |  60000 |

---

# 🎯 Most Asked Interview Questions

### 1. What is the default sorting order of the `ORDER BY` clause?
> Ascending order (`ASC`).

---

### 2. How are `NULL` values handled by `ORDER BY` in MySQL?
> In MySQL, `NULL` values are considered smaller than non-null values. So in `ASC` order, `NULL`s appear first; in `DESC` order, `NULL`s appear last.

---

### 3. Can you sort by a column that is not selected in the `SELECT` list?
> Yes. You can sort by columns that are not included in the `SELECT` list, provided `SELECT DISTINCT` is not used.

---

### 4. What does `ORDER BY 2 DESC` mean?
> It sorts the result set in descending order based on the 2nd column specified in the `SELECT` list.

---

# 🧠 Quick Revision

```text
ORDER BY Clause
 ↓
Sorts result set (ASC by default)
 ↓
Multi-column sorting: ORDER BY col1 DESC, col2 ASC
 ↓
MySQL NULLs: ASC → NULLs top, DESC → NULLs bottom
 ↓
Executed near end of query pipeline
```

> **Memory Trick:** `ORDER BY = Sort Results (Default: ASC)`
