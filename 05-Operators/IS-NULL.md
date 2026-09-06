# ❓ IS NULL & IS NOT NULL Operators

## 📌 Definition

The **`IS NULL`** and **`IS NOT NULL`** operators test whether an expression or column contains a **`NULL` (missing or unassigned) value**.

---

## 🔑 Key Concepts

* **Why `= NULL` Fails:** In SQL's Three-Valued Logic, any comparison using standard operators (`=`, `!=`, `<>`) against `NULL` evaluates to **`UNKNOWN`** (which is treated as `FALSE` by `WHERE`).
* **Correct Syntax:** Always use `IS NULL` or `IS NOT NULL`.
* **Replacing NULLs:** Functions like `COALESCE(column, default)` or `IFNULL(column, default)` can be used to handle `NULL` values in queries.

---

## 💻 Syntax & Examples

### 1. Finding Records with Missing Data
```sql
SELECT emp_id, name, department
FROM employees
WHERE department IS NULL;
```

### 2. Finding Records with Present Data
```sql
SELECT emp_id, name, manager_id
FROM employees
WHERE manager_id IS NOT NULL;
```

---

## 📝 Comparison Table: `= NULL` vs `IS NULL`

| Query Expression | Evaluation Result | Rows Returned |
| :--- | :--- | :--- |
| `department = NULL` | `UNKNOWN` | **0 rows** (Always fails) |
| `department != NULL` | `UNKNOWN` | **0 rows** (Always fails) |
| `department IS NULL` | `TRUE` (if column is NULL) | Returns records with NULL |
| `department IS NOT NULL` | `TRUE` (if column has value) | Returns records with non-NULL values |

---

# 🎯 Most Asked Interview Questions

### 1. Why doesn't `WHERE column = NULL` work in SQL?
> In SQL, `NULL` represents an unknown value. Comparing an unknown value with anything using `=` yields `UNKNOWN`, not `TRUE`. Therefore, SQL provides the dedicated `IS NULL` operator.

---

### 2. How do you select rows where a column is NOT NULL?
> By using `WHERE column_name IS NOT NULL`.

---

### 3. What function in MySQL allows replacing NULL values with a fallback value?
> `IFNULL(column, fallback_value)` or ANSI-standard `COALESCE(column, fallback_value)`.

---

# 🧠 Quick Revision

```text
Handling NULLs
 ├── NEVER USE: = NULL  or  != NULL
 ├── ALWAYS USE: IS NULL  or  IS NOT NULL
 └── REPLACE NULLs: COALESCE(col, fallback)
```

> **Memory Trick:** `NULL is UNKNOWN — Always ask "IS NULL?"`
