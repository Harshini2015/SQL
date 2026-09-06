# 🧩 PARTITION BY Clause

## 📌 Definition

The **`PARTITION BY`** sub-clause divides a query result set into smaller subsets (partitions) for window functions to perform independent calculations within each subset.

---

## 🔑 Key Concepts

* **Resets Calculation:** Resets window function counters (such as `ROW_NUMBER()`, `RANK()`, running totals) at the start of each new partition boundary.
* **Does NOT Collapse Rows:** Unlike `GROUP BY`, `PARTITION BY` inside `OVER()` keeps all rows intact in the output.
* **Omission Behavior:** If `PARTITION BY` is omitted from `OVER()`, the **entire result set** is treated as one giant single partition.

---

## 💻 Syntax

```sql
FUNCTION_NAME() OVER (
    PARTITION BY column1, column2
    ORDER BY sort_column
)
```

---

## 📝 Example: Running Total per Customer

```sql
SELECT 
    customer_id,
    order_date,
    amount,
    SUM(amount) OVER(
        PARTITION BY customer_id 
        ORDER BY order_date
    ) AS running_total_per_customer
FROM orders;
```

---

## ⚖️ Important Comparison: `GROUP BY` vs `PARTITION BY`

| Feature | `GROUP BY` | `PARTITION BY` (in `OVER()`) |
| :--- | :--- | :--- |
| **Primary Effect** | Collapses rows into 1 summary row per group | Groups rows into calculation windows |
| **Output Row Count** | Equal to number of distinct groups | Equal to total input rows in query |
| **Usage Location** | Query body clause | Inside `OVER(...)` window specification |

---

# 🎯 Most Asked Interview Questions

### 1. What happens if you omit `PARTITION BY` in a window function?
> If `PARTITION BY` is omitted, the window function evaluates across the entire query result set as a single partition.

---

### 2. Can you partition by multiple columns in `PARTITION BY`?
> Yes. You can specify multiple comma-separated columns (e.g. `PARTITION BY country, department`).

---

# 🧠 Quick Revision

```text
Result Set
 ├── Partition A (Resets counter → 1, 2, 3...)
 └── Partition B (Resets counter → 1, 2, 3...)
```

> **Memory Trick:** `PARTITION BY = Reset window counter for each category`
