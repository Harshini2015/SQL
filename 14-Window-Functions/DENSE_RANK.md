# 🏆 DENSE_RANK() Function

## 📌 Definition

The **`DENSE_RANK()`** window function assigns a rank to each row within a partition **without leaving any gaps** in the ranking sequence when duplicate values (ties) occur.

---

## 🔑 Key Concepts

* **Handles Ties:** Assigns the **same rank number** to rows with identical sorting values.
* **No Gaps:** Consecutive rank numbers are strictly maintained without skipping numbers.
* **Sequence Example:** For values `[100, 100, 90, 80]`, `DENSE_RANK()` returns $\mathbf{1, 1, 2, 3}$ (No numbers skipped!).
* **Top Interview Choice:** Ideal for finding the **Nth Highest Salary** across departments.

---

## 💻 Syntax & Example

```sql
SELECT 
    name, 
    department, 
    salary,
    DENSE_RANK() OVER(PARTITION BY department ORDER BY salary DESC) AS dense_rnk
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
| Neha  | IT         |  50000 |

### Query Result:

| name  | department | salary | dense_rnk |
| :---- | :--------- | -----: | --------: |
| Priya | IT         |  80000 | **1** |
| Rahul | IT         |  80000 | **1** |
| Amit  | IT         |  60000 | **2** *(No gap!)* |
| Neha  | IT         |  50000 | **3** |

---

## ⚖️ Important Comparison: ROW_NUMBER vs RANK vs DENSE_RANK

Given Salaries: `[100, 100, 80]`

| Function | Output Ranks | Has Ties? | Has Gaps? |
| :--- | :--- | :--- | :--- |
| **`ROW_NUMBER()`** | `1, 2, 3` | ❌ No | ❌ No |
| **`RANK()`** | `1, 1, 3` | ✅ Yes | ✅ **Yes (Skips 2)** |
| **`DENSE_RANK()`** | `1, 1, 2` | ✅ Yes | ❌ **No Gaps** |

---

# 🎯 Most Asked Interview Questions

### 1. How do you find the 2nd highest salary in each department using `DENSE_RANK()`?
```sql
WITH RankedSalaries AS (
    SELECT name, department, salary,
           DENSE_RANK() OVER(PARTITION BY department ORDER BY salary DESC) AS dr
    FROM employees
)
SELECT name, department, salary
FROM RankedSalaries
WHERE dr = 2;
```

---

### 2. Why is `DENSE_RANK()` preferred over `RANK()` for Nth highest salary queries?
> Because if multiple employees share the top salary (tie for 1st), `RANK()` will skip rank 2 and assign 3 to the next salary. `DENSE_RANK()` correctly assigns rank 2 to the next distinct salary level.

---

# 🧠 Quick Revision

```text
DENSE_RANK() OVER(PARTITION BY ... ORDER BY ...)
 ├── Tied values → Same Rank Number
 └── Next distinct value → NEXT CONSECUTIVE integer (NO GAPS!)
```

> **Memory Trick:** `DENSE_RANK = Same rank for ties + NO GAPS (Consecutive)`
