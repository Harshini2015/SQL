# 🛡️ COALESCE Function

## 📌 Definition

The **`COALESCE()`** function evaluates a list of arguments in order and returns the **first non-null value** in the list.

---

## 🔑 Key Concepts

* **ANSI SQL Standard:** Supported across all major database engines (MySQL, PostgreSQL, SQL Server, Oracle, SQLite).
* **Multiple Arguments:** Can accept two or more parameters: `COALESCE(val1, val2, val3, ..., valN)`.
* **Fallback Chain:** Perfect for fallback logic (e.g., preference: Mobile Phone $\rightarrow$ Home Phone $\rightarrow$ Email $\rightarrow$ 'N/A').
* **All-`NULL` Result:** Returns `NULL` only if **every single argument** evaluates to `NULL`.

---

## 💻 Syntax & Examples

### 1. Basic Fallback Value
```sql
SELECT 
    name, 
    COALESCE(phone, mobile, email, 'No Contact Info') AS contact_info
FROM customers;
```

### 2. Handling Aggregations Returning NULL
```sql
SELECT COALESCE(SUM(salary), 0) AS total_payroll
FROM employees
WHERE department = 'Marketing';
```

---

## ⚖️ Important Comparison: `COALESCE` vs `IFNULL` / `NVL` / `ISNULL`

| Function | Standard | Parameter Limit | Engine |
| :--- | :--- | :--- | :--- |
| **`COALESCE(a, b, c, ...)`** | **ANSI Standard** | **Unlimited** ($2+$) | All RDBMS engines |
| **`IFNULL(a, b)`** | Non-standard | Strictly 2 arguments | MySQL only |
| **`NVL(a, b)`** | Non-standard | Strictly 2 arguments | Oracle only |
| **`ISNULL(a, b)`** | Non-standard | Strictly 2 arguments | SQL Server only |

---

# 🎯 Most Asked Interview Questions

### 1. What does the `COALESCE()` function do in SQL?
> `COALESCE()` returns the first non-null expression from its list of arguments.

---

### 2. What is the difference between `COALESCE()` and `IFNULL()` in MySQL?
> `COALESCE()` is an ANSI standard SQL function that accepts multiple arguments, whereas `IFNULL()` is MySQL-specific and accepts exactly two arguments.

---

### 3. What does `COALESCE(NULL, NULL, 'Third', 'Fourth')` return?
> It returns **`'Third'`** (the first non-null value encountered).

---

# 🧠 Quick Revision

```text
COALESCE(val1, val2, val3, fallback)
 ├── Evaluates left to right
 ├── Returns 1st NON-NULL item
 └── Standard ANSI function (Works everywhere)
```

> **Memory Trick:** `COALESCE = First Non-NULL in the Chain`
