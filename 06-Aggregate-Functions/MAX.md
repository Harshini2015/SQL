# 🔼 MAX Function

## 📌 Definition

The **`MAX()`** aggregate function returns the maximum (largest) value in a column or expression across a group of rows.

---

## 🔑 Key Concepts

* **Multi-Data Type Support:** Works on numbers, strings (last alphabetical sorting), and date/time data types (latest date).
* **Ignores `NULL` Values:** `MAX()` ignores `NULL` values when computing the maximum.
* **Returns `NULL` for Empty Set:** If no matching non-null rows exist, `MAX()` returns `NULL`.

---

## 💻 Syntax & Examples

### 1. Maximum Salary per Department
```sql
SELECT department, MAX(salary) AS highest_salary
FROM employees
GROUP BY department;
```

### 2. Latest Hire Date and Last Alphabetical Name
```sql
SELECT 
    MAX(hire_date) AS latest_join_date,
    MAX(name) AS last_name_alphabetically
FROM employees;
```

---

## 📝 Example

### `employees` Table

| name  | salary | hire_date  |
| :---- | -----: | :--------- |
| Amit  |  75000 | 2021-05-10 |
| Priya |  60000 | 2022-01-15 |
| Rahul |  45000 | 2023-09-01 |

```sql
SELECT 
    MAX(salary) AS max_sal,      -- Returns 75000
    MAX(hire_date) AS max_date,  -- Returns '2023-09-01'
    MAX(name) AS max_name        -- Returns 'Rahul'
FROM employees;
```

---

# 🎯 Most Asked Interview Questions

### 1. Can `MAX()` be used with string columns?
> Yes. For string columns, `MAX()` returns the last value when sorted alphabetically (e.g., 'Z' comes before 'A').

---

### 2. What does `MAX()` return on a date column?
> It returns the most recent (latest) date.

---

### 3. How do you select the employee record who has the highest salary without window functions?
> Using a subquery:
> ```sql
> SELECT * FROM employees 
> WHERE salary = (SELECT MAX(salary) FROM employees);
> ```

---

# 🧠 Quick Revision

```text
MAX Function
 ├── Largest number / Latest date / Last alphabetical string
 ├── Ignores NULL values
 └── Returns NULL on empty result sets
```

> **Memory Trick:** `MAX = Highest number / Latest date / Last Z-A string`
