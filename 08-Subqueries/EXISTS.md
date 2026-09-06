# ✅ EXISTS Operator

## 📌 Definition

The **`EXISTS`** operator is a logical operator used in a `WHERE` clause to test for the **existence of any record** returned by a subquery.

---

## 🔑 Key Concepts

* **Boolean Outcome:** Evaluates to `TRUE` if the subquery returns **one or more rows**; evaluates to `FALSE` if 0 rows are returned.
* **Short-Circuit Evaluation:** Stops scanning as soon as the **first matching record** is found, making it highly efficient.
* **Select List Irrelevant:** The columns specified in the subquery `SELECT` clause do not matter (`SELECT 1` or `SELECT *` perform identically).
* **`NULL` Safe:** Works reliably even if the subquery columns contain `NULL` values.

---

## 💻 Syntax & Example

### Find Customers Who Have Placed At Least One Order

```sql
SELECT c.customer_id, c.name
FROM customers c
WHERE EXISTS (
    SELECT 1 
    FROM orders o
    WHERE o.customer_id = c.customer_id
);
```

---

## ⚖️ Important Difference: `EXISTS` vs `IN`

| Feature | `EXISTS` | `IN` |
| :--- | :--- | :--- |
| **Primary Check** | Checks for **existence of rows** | Compares **values against a set/list** |
| **Short-Circuiting** | Stops scanning on 1st match | Scans entire subquery result set |
| **`NULL` Handling** | Safe with `NULL`s | Vulnerable to `NULL` trap in `NOT IN` |
| **Performance** | Faster for large candidate datasets | Faster for small literal lists |

---

# 🎯 Most Asked Interview Questions

### 1. What does the `EXISTS` operator return?
> `EXISTS` returns a boolean value (`TRUE` or `FALSE`). It returns `TRUE` if the inner subquery returns at least one row.

---

### 2. Why is `SELECT 1` commonly used inside an `EXISTS` subquery?
> Because `EXISTS` only checks for row presence, not actual data values. Using `SELECT 1` is a common convention signaling that column contents are ignored.

---

### 3. When should you prefer `EXISTS` over `IN`?
> Prefer `EXISTS` when checking existence against large datasets (due to short-circuit evaluation) or when subquery results might contain `NULL` values.

---

# 🧠 Quick Revision

```text
Outer Row
   ↓
Subquery checks for matching record
   ↓
Found 1 row? → Stop search & return TRUE
Found 0 rows? → Return FALSE
```

> **Memory Trick:** `EXISTS = Returns TRUE if row count > 0 (Short-circuits!)`
