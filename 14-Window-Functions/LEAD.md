# ➡️ LEAD() Function

## 📌 Definition

The **`LEAD()`** window function accesses data from a **subsequent (following) row** at a specified physical offset after the current row within the partition.

---

## 🔑 Key Concepts

* **Look Forward:** Accesses column values from future rows without requiring a self-join.
* **Arguments:** `LEAD(column_name, [offset], [default_value])`
  * `column_name`: Column to fetch from the subsequent row.
  * `offset` *(Optional)*: Number of rows forward to look (default is `1`).
  * `default_value` *(Optional)*: Value returned if no subsequent row exists (default is `NULL`).
* **Use Cases:** Calculating duration until the next customer order, lead-time processing analysis.

---

## 💻 Syntax & Example

```sql
SELECT 
    order_date, 
    sales,
    LEAD(sales, 1, 0) OVER(ORDER BY order_date) AS next_day_sales
FROM daily_sales;
```

---

## 📝 Example Result

### `daily_sales` Table

| order_date | sales |
| :--------- | ----: |
| 2025-01-01 |   100 |
| 2025-01-02 |   150 |
| 2025-01-03 |   120 |

### Query Result:

| order_date | sales | next_day_sales |
| :--------- | ----: | -------------: |
| 2025-01-01 |   100 |        **150** |
| 2025-01-02 |   150 |        **120** |
| 2025-01-03 |   120 |          **0** *(Last row fallback)* |

---

## ⚖️ Important Comparison: LAG vs LEAD

| Function | Direction | Accesses | Last / First Row Behavior |
| :--- | :--- | :--- | :--- |
| **`LAG()`** | Look **Backward** | Previous row(s) | First row returns `NULL` (or default) |
| **`LEAD()`** | Look **Forward** | Following row(s) | Last row returns `NULL` (or default) |

---

# 🎯 Most Asked Interview Questions

### 1. What is the difference between `LAG()` and `LEAD()`?
> `LAG()` looks backward to fetch values from previous rows, while `LEAD()` looks forward to fetch values from future/following rows within the window.

---

### 2. What value does `LEAD()` return for the last row in a partition?
> `LEAD()` returns `NULL` for the last row in a partition (unless a custom default parameter is supplied).

---

# 🧠 Quick Revision

```text
Row N   (Current Row)    ──┐
                           ├── Access with LEAD(col, 1)
Row N+1 (Following Row)  ──┘
```

> **Memory Trick:** `LEAD = Look Ahead to Future Rows`
