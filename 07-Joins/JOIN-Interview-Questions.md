# 🎯 JOINs — Interview Questions & Row-Count Puzzles

## 📌 Join Type Comparison Matrix

| Join Type | Left Table Rows | Right Table Rows | Non-Matching Rows |
| :--- | :--- | :--- | :--- |
| **`INNER JOIN`** | Only matching | Only matching | Discarded completely |
| **`LEFT JOIN`** | **All preserved** | Only matching | Right columns filled with `NULL` |
| **`RIGHT JOIN`** | Only matching | **All preserved** | Left columns filled with `NULL` |
| **`FULL OUTER JOIN`** | **All preserved** | **All preserved** | Padded with `NULL` on missing side |
| **`CROSS JOIN`** | All paired | All paired | Every combination ($N \times M$) |
| **`SELF JOIN`** | Same table | Same table | Depends on join condition |

---

# 🧠 🔥 Must-Know Interview Row-Count Puzzles

### Puzzle 1: Duplicates in Both Tables

Given:
* **Table A:** `[1, 1, 1]` (3 rows)
* **Table B:** `[1, 1]` (2 rows)

> **Question:** How many rows are returned by:
> 1. `INNER JOIN` $\rightarrow \mathbf{6}$ rows ($3 \times 2$)
> 2. `LEFT JOIN` $\rightarrow \mathbf{6}$ rows
> 3. `RIGHT JOIN` $\rightarrow \mathbf{6}$ rows
> 4. `FULL OUTER JOIN` $\rightarrow \mathbf{6}$ rows
> 5. `CROSS JOIN` $\rightarrow \mathbf{6}$ rows ($3 \times 2$)

---

### Puzzle 2: Joins with `NULL` Values

Given:
* **Table A:** `[1, 1, NULL]` (3 rows)
* **Table B:** `[1, NULL]` (2 rows)

> **Question:** How many rows are returned by:
> 1. `INNER JOIN` $\rightarrow \mathbf{2}$ rows (Matches $2 \times 1 = 2$. `NULL = NULL` is FALSE!)
> 2. `LEFT JOIN` $\rightarrow \mathbf{3}$ rows (2 matched rows + 1 unmatched `NULL` row from Left)
> 3. `RIGHT JOIN` $\rightarrow \mathbf{3}$ rows (2 matched rows + 1 unmatched `NULL` row from Right)
> 4. `FULL OUTER JOIN` $\rightarrow \mathbf{4}$ rows (2 matched + 1 unmatched left + 1 unmatched right)
> 5. `CROSS JOIN` $\rightarrow \mathbf{6}$ rows ($3 \times 2$)

---

# 🎯 Frequently Asked Interview Questions

### 1. Does `NULL = NULL` match in an `INNER JOIN`?
> **No.** In SQL, `NULL` represents an unknown value, so `NULL = NULL` evaluates to `UNKNOWN`. Therefore, rows with `NULL` in join key columns do NOT match each other in joins.

---

### 2. What is the difference between placing a condition in `ON` vs `WHERE` in a `LEFT JOIN`?

```sql
-- Query A (Condition in ON clause)
SELECT * FROM A LEFT JOIN B ON A.id = B.id AND B.status = 'Active';

-- Query B (Condition in WHERE clause)
SELECT * FROM A LEFT JOIN B ON A.id = B.id WHERE B.status = 'Active';
```

> * **Query A:** Preserves **all rows from Table A**. If B is not active or missing, Table A rows are still returned with `NULL` for Table B columns.
> * **Query B:** Evaluates `WHERE B.status = 'Active'` **after** the join. This eliminates any `NULL` rows produced by the `LEFT JOIN`, effectively turning it into an **`INNER JOIN`**!

---

### 3. How do you optimize slow `JOIN` queries?
> 1. Ensure foreign key and join condition columns are **indexed**.
> 2. Select only required columns (avoid `SELECT *`).
> 3. Filter data early in subqueries or `WHERE` clauses before joining.
> 4. Ensure data types of join columns match exactly to avoid implicit type casting.

---

# 🧠 Quick Revision Rules

```text
Join Calculations
 ├── Matching keys count = (Count in A) × (Count in B)
 ├── NULLs NEVER match in joins!
 └── WHERE on Right table converts LEFT JOIN → INNER JOIN!
```
