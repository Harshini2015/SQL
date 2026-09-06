# 🌐 FULL OUTER JOIN

## 📌 Definition

A **`FULL OUTER JOIN`** (or `FULL JOIN`) returns **all records when there is a match in either left or right table**. Rows that do not match in either table are retained and padded with `NULL` values.

---

## 🔑 Key Concepts

* **Union of Sets:** Combines the results of both `LEFT JOIN` and `RIGHT JOIN`.
* **Complete Visibility:** Ensures no rows from either table are discarded.
* **⚠️ MySQL Limitation:** **MySQL does NOT natively support `FULL OUTER JOIN` syntax.** In MySQL, it must be emulated using `UNION`.

---

## 📐 Conceptual Representation

```text
Table A                       Table B
[ Row 1 (Matches Row 1) ] <----> [ Row 1 ]
[ Row 2 (Unmatched)     ] ------> [ NULL  ]
[ NULL                  ] <------ [ Row 3 (Unmatched) ]
```

---

## 💻 Syntax

### 1. Standard ANSI SQL (PostgreSQL, Oracle, SQL Server)
```sql
SELECT e.emp_id, e.name, d.dept_name
FROM employees e
FULL OUTER JOIN departments d
    ON e.dept_id = d.dept_id;
```

### 2. MySQL Emulation (Using `UNION`)
```sql
SELECT e.emp_id, e.name, d.dept_name
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id

UNION

SELECT e.emp_id, e.name, d.dept_name
FROM employees e
RIGHT JOIN departments d ON e.dept_id = d.dept_id;
```

---

## 📝 Example

### Table A: `employees` & Table B: `departments`

| emp_id | name | dept_id |
| -----: | :--- | ------: |
| 101 | Rahul | 10 |
| 103 | Amit | 30 |

| dept_id | dept_name |
| ------: | :-------- |
| 10 | IT |
| 40 | Finance |

### Result:

| emp_id | name | dept_name |
| -----: | :--- | :-------- |
| 101 | Rahul | IT |
| 103 | Amit | **NULL** |
| **NULL** | **NULL** | Finance |

---

# 🎯 Most Asked Interview Questions

### 1. What is a `FULL OUTER JOIN`?
> A `FULL OUTER JOIN` returns all records from both tables, joining matched rows and filling `NULL`s for unmatched rows on either side.

---

### 2. Does MySQL support `FULL OUTER JOIN`? How do you write it in MySQL?
> MySQL does **not** support `FULL OUTER JOIN` syntax. In MySQL, you achieve it by combining a `LEFT JOIN` and a `RIGHT JOIN` using the `UNION` operator.

---

# 🧠 Quick Revision

```text
FULL OUTER JOIN
 ├── Standard SQL: FULL OUTER JOIN tableB ON ...
 └── MySQL: (LEFT JOIN) UNION (RIGHT JOIN)
```

> **Memory Trick:** `FULL OUTER JOIN = LEFT JOIN + RIGHT JOIN (All Rows Retained)`
