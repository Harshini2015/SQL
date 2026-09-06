# 🤝 INNER JOIN

## 📌 Definition

An **`INNER JOIN`** returns only the records (rows) that have **matching values in both tables**. Non-matching records from either table are excluded.

---

## 🔑 Key Concepts

* **Intersection of Sets:** Only rows satisfying the join condition (`ON tableA.key = tableB.key`) are included in the result.
* **Default Join:** In SQL, writing `JOIN` without specifying a type defaults to `INNER JOIN`.
* **Multi-Table Joins:** Can chain multiple `INNER JOIN` statements to combine 3 or more tables.

---

## 📐 Conceptual Representation

```text
Table A (Left)          Table B (Right)
  [   1   ]               [   2   ]
  [   2   ]  <-- MATCH --> [   2   ]
  [   3   ]               [   4   ]
             
       Result: [ 2 ] (Only matching rows)
```

---

## 💻 Syntax

```sql
SELECT columns
FROM tableA
INNER JOIN tableB
    ON tableA.matching_column = tableB.matching_column;
```

---

## 📝 Example

### Table A: `employees`

| emp_id | name  | dept_id |
| -----: | :---- | ------: |
|    101 | Rahul |      10 |
|    102 | Priya |      20 |
|    103 | Amit  |      30 |

### Table B: `departments`

| dept_id | dept_name |
| ------: | :-------- |
|      10 | IT        |
|      20 | HR        |
|      40 | Finance   |

```sql
SELECT e.emp_id, e.name, d.dept_name
FROM employees e
INNER JOIN departments d
    ON e.dept_id = d.dept_id;
```

### Result:

| emp_id | name  | dept_name |
| -----: | :---- | :-------- |
|    101 | Rahul | IT        |
|    102 | Priya | HR        |

*(Amit with `dept_id = 30` and Finance with `dept_id = 40` are excluded because they have no matches)*

---

# 🎯 Most Asked Interview Questions

### 1. What is an `INNER JOIN`?
> An `INNER JOIN` matches rows from two tables based on a join condition and returns only rows where a match exists in both tables.

---

### 2. What happens if there are duplicate matching keys in both tables?
> If Table A has 2 rows with key `X` and Table B has 3 rows with key `X`, the result set will contain $2 \times 3 = 6$ rows for key `X` (Cartesian product of the matching subset).

---

### 3. What is the difference between `JOIN` and `INNER JOIN`?
> There is no difference. `JOIN` is a shorthand syntax for `INNER JOIN`.

---

# 🧠 Quick Revision

```text
Table A ∩ Table B
 ↓
Matches ON condition
 ↓
Returns ONLY matching records
 ↓
Non-matching rows discarded
```

> **Memory Trick:** `INNER JOIN = Exact Matches Only (Intersection)`
