# 🎯 Window Functions — Interview Patterns & Cheatsheet

## 📌 Ranking Functions Comparison Cheatsheet

Given values: `[100, 100, 80]`

| Function | Output Ranks | Duplicate Ties Behavior | Subsequent Rank Gap |
| :--- | :--- | :--- | :--- |
| **`ROW_NUMBER()`** | `1, 2, 3` | Strictly unique numbers | ❌ No gaps |
| **`RANK()`** | `1, 1, 3` | Same rank for ties | ✅ **Skips rank 2 (Leaves gap)** |
| **`DENSE_RANK()`** | `1, 1, 2` | Same rank for ties | ❌ **No gaps (Consecutive numbers)** |

---

# 🎯 Top 4 Mandatory Window Function Interview Patterns

### Pattern 1: Department-Wise Nth Highest Salary

> **Problem:** Find the employee(s) who earn the **2nd highest salary** in each department.

```sql
WITH RankedEmployees AS (
    SELECT 
        emp_id, name, department_id, salary,
        DENSE_RANK() OVER(
            PARTITION BY department_id 
            ORDER BY salary DESC
        ) AS rnk
    FROM employees
)
SELECT emp_id, name, department_id, salary
FROM RankedEmployees
WHERE rnk = 2;
```

---

### Pattern 2: Calculating Running Total / Cumulative Sum

> **Problem:** Compute cumulative total revenue over time per customer.

```sql
SELECT 
    customer_id, order_date, amount,
    SUM(amount) OVER(
        PARTITION BY customer_id 
        ORDER BY order_date
    ) AS cumulative_amount
FROM orders;
```

---

### Pattern 3: Identifying and Removing Duplicate Records

> **Problem:** Select unique user records keeping only the earliest registered record per email.

```sql
WITH DeduplicatedUsers AS (
    SELECT 
        user_id, email, created_at,
        ROW_NUMBER() OVER(
            PARTITION BY email 
            ORDER BY created_at ASC
        ) AS row_num
    FROM users
)
SELECT user_id, email, created_at
FROM DeduplicatedUsers
WHERE row_num = 1;
```

---

### Pattern 4: Consecutive Days / Rising Values (`LAG` Pattern)

> **Problem:** Find dates where temperature was higher than the previous day.

```sql
WITH TempWithPrev AS (
    SELECT 
        id, recordDate, temperature,
        LAG(temperature, 1) OVER(ORDER BY recordDate) AS prev_temp,
        LAG(recordDate, 1) OVER(ORDER BY recordDate) AS prev_date
    FROM Weather
)
SELECT id
FROM TempWithPrev
WHERE temperature > prev_temp 
  AND DATEDIFF(recordDate, prev_date) = 1;
```

---

# 🧠 Quick Revision Rules

```text
Window Functions Decision Matrix
 ├── Remove duplicates? → ROW_NUMBER() = 1
 ├── Nth Highest Salary? → DENSE_RANK() = N
 ├── Cumulative Running Sum? → SUM() OVER(PARTITION BY ... ORDER BY ...)
 └── Compare with Prev/Next row? → LAG() / LEAD()
```
