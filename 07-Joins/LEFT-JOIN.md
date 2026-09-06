# 👈 LEFT JOIN (LEFT OUTER JOIN)

## 📌 Definition

A **`LEFT JOIN`** (or `LEFT OUTER JOIN`) returns **all records from the left table**, and the matching records from the right table. If there is no match in the right table, **`NULL`** values are returned for the right table's columns.

---

## 🔑 Key Concepts

* **Preserves Left Table:** Every single row from the left table appears in the output at least once.
* **`NULL` Fill:** Non-matching rows from the left table get `NULL` in right table columns.
* **Finding Unmatched Rows (Anti-Join):** Filtering with `WHERE right_table.key IS NULL` finds records in the left table that have **no corresponding match** in the right table (e.g., customers with no orders).

---

## 📐 Conceptual Representation

```text
Left Table (A)          Right Table (B)
  [   1   ]  <-- MATCH --> [   1   ]  --> [ 1, Match ]
  [   2   ]               [   -   ]  --> [ 2, NULL  ]
  [   3   ]  <-- MATCH --> [   3   ]  --> [ 3, Match ]
```

---

## 💻 Syntax

```sql
SELECT columns
FROM tableA (Left Table)
LEFT JOIN tableB (Right Table)
    ON tableA.matching_column = tableB.matching_column;
```

---

## 📝 Example

### Table A: `employees` (Left)

| emp_id | name  | dept_id |
| -----: | :---- | ------: |
|    101 | Rahul |      10 |
|    102 | Priya |      20 |
|    103 | Amit  |      30 |

### Table B: `departments` (Right)

| dept_id | dept_name |
| ------: | :-------- |
|      10 | IT        |
|      20 | HR        |

```sql
SELECT e.emp_id, e.name, d.dept_name
FROM employees e
LEFT JOIN departments d
    ON e.dept_id = d.dept_id;
```

### Result:

| emp_id | name  | dept_name |
| -----: | :---- | :-------- |
|    101 | Rahul | IT        |
|    102 | Priya | HR        |
|    103 | Amit  | **NULL**  |

---

## 💡 Finding Left-Only Records (Anti-Join Example)

Find employees **not assigned to any valid department**:

```sql
SELECT e.emp_id, e.name
FROM employees e
LEFT JOIN departments d
    ON e.dept_id = d.dept_id
WHERE d.dept_id IS NULL;
```

---

## ⚖️ Important Difference: INNER JOIN vs LEFT JOIN

| Feature | INNER JOIN | LEFT JOIN |
| :--- | :--- | :--- |
| **Output Rows** | Only matching rows | **All** rows from Left table + matches from Right table |
| **Unmatched Rows** | Discarded | Left unmatched rows preserved (filled with `NULL`) |
| **Use Case** | Strict matches only | Preserving primary entity data (e.g., all customers & their orders) |

---

# 🎯 Most Asked Interview Questions

### 1. What is the difference between `INNER JOIN` and `LEFT JOIN`?
> `INNER JOIN` returns only records that match in both tables. `LEFT JOIN` returns all records from the left table, plus matched records from the right table (filling with `NULL` where there is no match).

---

### 2. How do you find customers who have never placed an order?
> By performing a `LEFT JOIN` from `customers` to `orders` and filtering with `WHERE orders.customer_id IS NULL`.

---

### 3. Is `LEFT OUTER JOIN` the same as `LEFT JOIN`?
> Yes. `OUTER` is an optional keyword.

---

# 🧠 Quick Revision

```text
All Rows in Left Table
       ↓
Matches in Right Table → Appended
       ↓
No Match in Right Table → Filled with NULL
```

> **Memory Trick:** `LEFT JOIN = Keep EVERYTHING on the Left`
