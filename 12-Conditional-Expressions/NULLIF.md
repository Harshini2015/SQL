# 🚫 NULLIF Function

## 📌 Definition

The **`NULLIF(expr1, expr2)`** function compares two expressions and returns **`NULL` if `expr1 = expr2`**; otherwise, it returns **`expr1`**.

---

## 🔑 Key Concepts & Behavior

* **Logic Equivalent:**
  ```sql
  CASE 
      WHEN expr1 = expr2 THEN NULL 
      ELSE expr1 
  END
  ```
* **Primary Use Case (Division by Zero Prevention):** Prevents division-by-zero crashes or `NULL` errors by replacing zero denominators with `NULL` (since dividing by `NULL` returns `NULL` safely).

---

## 💻 Syntax & Examples

### 1. Basic Comparisons
```sql
SELECT NULLIF(10, 10); -- Returns NULL (Values are equal)
SELECT NULLIF(10, 20); -- Returns 10 (Values are different)
```

### 2. Preventing Division-by-Zero Error (Classic Interview Pattern)
```sql
SELECT 
    sales,
    quantity,
    sales / NULLIF(quantity, 0) AS unit_price
FROM order_items;
```
*(If `quantity = 0`, `NULLIF(quantity, 0)` returns `NULL`, and `sales / NULL` safely evaluates to `NULL` instead of throwing a divide-by-zero database error!)*

---

# 🎯 Most Asked Interview Questions

### 1. What does `NULLIF(a, b)` return if `a` and `b` are equal?
> It returns **`NULL`**.

---

### 2. How do you prevent division by zero errors in SQL queries?
> By wrapping the denominator inside `NULLIF(denominator, 0)`:
> `SELECT total_amount / NULLIF(total_count, 0)`.

---

### 3. What does `NULLIF('Apple', 'Orange')` return?
> It returns **`'Apple'`** (the first argument `expr1`).

---

# 🧠 Quick Revision

```text
NULLIF(expr1, expr2)
 ├── Equal?     → Returns NULL
 └── Different? → Returns expr1
```

> **Memory Trick:** `NULLIF(val, 0) converts 0 to NULL to prevent Divide-by-Zero!`
