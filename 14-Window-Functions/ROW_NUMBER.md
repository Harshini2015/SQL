# 🔢 ROW_NUMBER() Function

## 📌 Definition

The **`ROW_NUMBER()`** window function assigns a **unique sequential integer (1, 2, 3, ...)** to each row within a partition, based on a specified ordering.

---

## 🔑 Key Concepts

* **Unique Sequential Sequence:** Never produces duplicate numbers or ties, even when duplicate values exist in the sorting column.
* **Top Use Cases:**
  1. **Removing Duplicate Records:** (Filter `WHERE row_num > 1`).
  2. **Top-N Records per Category:** (e.g. Most recent order per customer).
  3. **Pagination.**

---

## 💻 Syntax & Example

```sql
SELECT 
    name, 
    department, 
    salary,
    ROW_NUMBER() OVER(PARTITION BY department ORDER BY salary DESC) AS row_num
FROM employees;
```

---

## 📝 Example Result

### `employees` Table

| name  | department | salary |
| :---- | :--------- | -----: |
| Priya | IT         |  80000 |
| Rahul | IT         |  80000 |
| Amit  | IT         |  60000 |

### Query Result:

| name  | department | salary | row_num |
| :---- | :--------- | -----: | ------: |
| Priya | IT         |  80000 |  **1**  |
| Rahul | IT         |  80000 |  **2**  |
| Amit  | IT         |  60000 |  **3**  |

*(Even though Priya and Rahul share the exact same salary, `ROW_NUMBER()` assigns unique sequential ranks: 1 and 2)*

---

# 🎯 Most Asked Interview Questions

### 1. Can `ROW_NUMBER()` return duplicate rank values for tied rows?
> **No.** `ROW_NUMBER()` strictly guarantees unique sequential integer values for every row within a partition, regardless of duplicate sorting values.

---

### 2. How do you delete duplicate records from a table using `ROW_NUMBER()`?
> Assign `ROW_NUMBER() OVER(PARTITION BY unique_cols ORDER BY id)` inside a CTE, then delete rows `WHERE row_num > 1`.

```sql
WITH CTE AS (
    SELECT id, ROW_NUMBER() OVER(PARTITION BY email ORDER BY id) AS rn
    FROM users
)
DELETE FROM users WHERE id IN (SELECT id FROM CTE WHERE rn > 1);
```

---

# 🧠 Quick Revision

```text
ROW_NUMBER() OVER(PARTITION BY ... ORDER BY ...)
 ├── Sequential numbers: 1, 2, 3, 4, 5
 └── NO TIES allowed (Always unique numbers)
```

> **Memory Trick:** `ROW_NUMBER = Strictly Unique Sequential Numbers (No Ties)`
