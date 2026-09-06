# ⚖️ Comparison Operators

## 📌 Definition

**Comparison Operators** (also known as Relational Operators) are used in SQL conditions (like `WHERE` clauses) to compare two values, returning `TRUE`, `FALSE`, or `UNKNOWN`.

---

## 🔑 Key Operators

| Operator | Meaning | Example |
| :--- | :--- | :--- |
| **`=`** | Equal to | `salary = 50000` |
| **`!=`** or **`<>`** | Not equal to | `department != 'HR'` |
| **`>`** | Greater than | `age > 21` |
| **`<`** | Less than | `price < 100` |
| **`>=`** | Greater than or equal to | `experience >= 5` |
| **`<=`** | Less than or equal to | `score <= 90` |

---

## 💻 Syntax & Examples

```sql
SELECT name, salary
FROM employees
WHERE salary >= 60000 AND department <> 'HR';
```

---

## ⚠️ Important Note: Comparison with `NULL`

Standard comparison operators (`=`, `!=`, `<`, `>`) **do not work with `NULL`**.

```sql
-- INCORRECT (Returns no rows)
SELECT * FROM employees WHERE department = NULL;

-- CORRECT
SELECT * FROM employees WHERE department IS NULL;
```

---

# 🎯 Most Asked Interview Questions

### 1. What is the difference between `!=` and `<>` in SQL?
> Both `!=` and `<>` mean "Not Equal To". `<>` is standard ANSI SQL syntax, while `!=` is widely supported across almost all modern database engines.

---

### 2. What does `SELECT * FROM table WHERE column = NULL;` return?
> It returns an empty result set (0 rows). In SQL, comparing anything to `NULL` using `=` evaluates to `UNKNOWN` instead of `TRUE`. You must use `IS NULL`.

---

### 3. What is the `<=>` (NULL-safe equal to) operator in MySQL?
> In MySQL, `<=>` is the **NULL-safe equal operator**. Unlike `=`, `NULL <=> NULL` evaluates to `TRUE` (`1`), allowing direct equality comparisons with `NULL`.

---

# 🧠 Quick Revision

```text
Comparison Operators
 ├── = , != / <> , > , < , >= , <=
 ├── Output: TRUE | FALSE | UNKNOWN
 └── Use IS NULL for NULL comparisons (or <=> in MySQL)
```

> **Memory Trick:** `Never use = NULL! Always use IS NULL!`
