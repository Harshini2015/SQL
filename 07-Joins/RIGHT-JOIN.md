# 👉 RIGHT JOIN (RIGHT OUTER JOIN)

## 📌 Definition

A **`RIGHT JOIN`** (or `RIGHT OUTER JOIN`) returns **all records from the right table**, and matching records from the left table. If there is no match in the left table, **`NULL`** values are returned for the left table's columns.

---

## 🔑 Key Concepts

* **Preserves Right Table:** Every single row from the right table appears in the output.
* **Mirror Image of LEFT JOIN:** `tableA RIGHT JOIN tableB` produces the exact same dataset as `tableB LEFT JOIN tableA`.
* **Readability Practice:** In practice, most database engineers avoid `RIGHT JOIN` and rewrite queries using `LEFT JOIN` for consistency and readability.

---

## 💻 Syntax

```sql
SELECT columns
FROM tableA (Left Table)
RIGHT JOIN tableB (Right Table)
    ON tableA.matching_column = tableB.matching_column;
```

---

## 📝 Example

### Table A: `employees` (Left)

| emp_id | name  | dept_id |
| -----: | :---- | ------: |
|    101 | Rahul |      10 |
|    102 | Priya |      20 |

### Table B: `departments` (Right)

| dept_id | dept_name |
| ------: | :-------- |
|      10 | IT        |
|      20 | HR        |
|      40 | Finance   |

```sql
SELECT e.emp_id, e.name, d.dept_name
FROM employees e
RIGHT JOIN departments d
    ON e.dept_id = d.dept_id;
```

### Result:

| emp_id | name  | dept_name |
| -----: | :---- | :-------- |
|    101 | Rahul | IT        |
|    102 | Priya | HR        |
|   **NULL** | **NULL** | Finance   |

---

# 🎯 Most Asked Interview Questions

### 1. What is a `RIGHT JOIN`?
> A `RIGHT JOIN` returns all records from the right table, plus matched records from the left table (filling with `NULL` where left records are missing).

---

### 2. Can every `RIGHT JOIN` be converted into a `LEFT JOIN`?
> Yes. By reversing the order of the tables in the `FROM` and `JOIN` clauses, any `RIGHT JOIN` can be rewritten as a `LEFT JOIN`.

---

# 🧠 Quick Revision

```text
All Rows in Right Table
       ↓
Matches in Left Table → Appended
       ↓
No Match in Left Table → Filled with NULL
```

> **Memory Trick:** `RIGHT JOIN = Keep EVERYTHING on the Right`
