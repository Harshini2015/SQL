# ⬅️ LAG() Function

## 📌 Definition

The **`LAG()`** window function accesses data from a **previous row** at a specified physical offset before the current row within the partition.

---

## 🔑 Key Concepts

* **Look Backward:** Accesses column values from earlier rows without requiring a self-join.
* **Arguments:** `LAG(column_name, [offset], [default_value])`
  * `column_name`: Column to fetch from the prior row.
  * `offset` *(Optional)*: Number of rows back to look (default is `1`).
  * `default_value` *(Optional)*: Value returned if no previous row exists (default is `NULL`).
* **Use Cases:** Year-over-Year (YoY) revenue calculations, day-over-day temperature changes, session interval analysis.

---

## 💻 Syntax & Example

```sql
SELECT 
    order_date, 
    sales,
    LAG(sales, 1, 0) OVER(ORDER BY order_date) AS prev_day_sales,
    sales - LAG(sales, 1, 0) OVER(ORDER BY order_date) AS sales_diff
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

| order_date | sales | prev_day_sales | sales_diff |
| :--------- | ----: | -------------: | ---------: |
| 2025-01-01 |   100 |          **0** |     **100** |
| 2025-01-02 |   150 |        **100** |      **50** |
| 2025-01-03 |   120 |        **150** |     **-30** |

---

# 🎯 Most Asked Interview Questions

### 1. What does the `LAG()` function do in SQL?
> `LAG()` accesses data from a previous row in the result set at a given offset within the defined window partition.

---

### 2. What value does `LAG()` return for the very first row in a partition?
> It returns `NULL` by default, unless a custom fallback default value parameter is explicitly specified in the `LAG()` call.

---

### 3. How do you calculate Year-over-Year (YoY) growth using `LAG()`?
```sql
SELECT 
    year, 
    revenue,
    LAG(revenue, 1) OVER(ORDER BY year) AS prev_year_revenue,
    ((revenue - LAG(revenue, 1) OVER(ORDER BY year)) / LAG(revenue, 1) OVER(ORDER BY year)) * 100 AS yoy_growth_pct
FROM annual_revenue;
```

---

# 🧠 Quick Revision

```text
Row N-1 (Previous Row) ──┐
                         ├── Access with LAG(col, 1)
Row N   (Current Row)  ──┘
```

> **Memory Trick:** `LAG = Look Backwards to Previous Rows`
