# ➕ Arithmetic Operators

## 📌 Definition

**Arithmetic Operators** perform mathematical operations on numeric data types (such as integers, decimals, or floats) in SQL statements.

---

## 🔑 Key Operators & Concepts

| Operator | Description | Example Expression | Result |
| :--- | :--- | :--- | :--- |
| **`+`** | Addition | `10 + 5` | `15` |
| **`-`** | Subtraction | `10 - 5` | `5` |
| **`*`** | Multiplication | `10 * 5` | `50` |
| **`/`** | Division | `10 / 4` | `2.5` |
| **`%`** / **`MOD`** | Modulus (Remainder) | `10 % 3` | `1` |

### Critical Rules:
* **`NULL` Propagation:** Any arithmetic operation with `NULL` yields `NULL` (`5 + NULL = NULL`).
* **Division by Zero:** In MySQL, dividing by zero returns `NULL` without throwing a fatal crash.

---

## 💻 Syntax & Examples

### 1. Calculating Bonus and Total Salary
```sql
SELECT 
    name, 
    salary, 
    salary * 0.10 AS bonus,
    salary + (salary * 0.10) AS total_salary
FROM employees;
```

### 2. Updating Prices using Multiplication
```sql
UPDATE products
SET price = price * 1.05; -- 5% price increase
```

---

## 📝 Example Result

### Input `employees`:

| name  | salary |
| :---- | -----: |
| Rahul |  50000 |

### Query Output:

| name  | salary | bonus | total_salary |
| :---- | -----: | ----: | -----------: |
| Rahul |  50000 |  5000 |        55000 |

---

# 🎯 Most Asked Interview Questions

### 1. What is the result of any arithmetic operation involving `NULL` in SQL?
> Any arithmetic operation with `NULL` returns `NULL` (e.g., `100 + NULL` evaluates to `NULL`).

---

### 2. What happens when you divide a number by zero in MySQL?
> In MySQL, dividing by zero evaluates to `NULL` (unless strict mode flags alter warning outputs).

---

### 3. How do you select even or odd employee IDs in SQL?
> Use the modulus operator (`%`):
> * Even IDs: `WHERE emp_id % 2 = 0`
> * Odd IDs: `WHERE emp_id % 2 != 0`

---

# 🧠 Quick Revision

```text
Arithmetic Operators
 ├── + , - , * , / , %
 ├── NULL + Number → NULL
 └── Number / 0 → NULL (in MySQL)
```

> **Memory Trick:** `NULL in arithmetic always ruins the result (returns NULL)`
