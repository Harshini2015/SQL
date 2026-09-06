# 🔽 MIN Function

## 📌 Definition

The **`MIN()`** aggregate function returns the minimum (smallest) value in a column or expression across a group of rows.

---

## 🔑 Key Concepts

* **Multi-Data Type Support:** Works on numbers, strings (alphabetical sorting), and date/time data types.
* **Ignores `NULL` Values:** `MIN()` ignores `NULL` values when evaluating the minimum.
* **Returns `NULL` for Empty Set:** If no matching non-null rows exist, `MIN()` returns `NULL`.

---

## 💻 Syntax & Examples

### 1. Minimum Salary per Department
```sql
SELECT department, MIN(salary) AS lowest_salary
FROM employees
GROUP BY department;
```

### 2. Earliest Hire Date and First Alphabetical Name
```sql
SELECT 
    MIN(hire_date) AS earliest_join_date,
    MIN(name) AS first_name_alphabetically
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
    MIN(salary) AS min_sal,      -- Returns 45000
    MIN(hire_date) AS min_date,  -- Returns '2021-05-10'
    MIN(name) AS min_name        -- Returns 'Amit'
FROM employees;
```

---

# 🎯 Most Asked Interview Questions

### 1. Can `MIN()` be used on non-numeric columns like strings or dates?
> Yes. For strings, `MIN()` returns the value that appears first alphabetically. For dates, it returns the earliest date.

---

### 2. Does `MIN()` consider `NULL` values?
> No. `MIN()` ignores `NULL` values.

---

### 3. How do you find the full details of the employee with the minimum salary?
> Use a subquery or window function (`ORDER BY salary LIMIT 1` or subquery `WHERE salary = (SELECT MIN(salary) FROM employees)`).

---

# 🧠 Quick Revision

```text
MIN Function
 ├── Smallest number / Earliest date / First alphabetical string
 ├── Ignores NULL values
 └── Returns NULL on empty result sets
```

> **Memory Trick:** `MIN = Lowest number / Earliest date / First A-Z string`
