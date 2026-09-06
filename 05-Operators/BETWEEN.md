# ↔️ BETWEEN Operator

## 📌 Definition

The **`BETWEEN`** operator filters a result set by testing whether an expression falls within a specified **inclusive range** (numbers, dates, or strings).

---

## 🔑 Key Concepts

* **Inclusive Range:** The range is **inclusive**, meaning both the minimum and maximum boundary values are included.
* **Equivalent Expression:** `expression BETWEEN min AND max` is identical to:
  ```sql
  expression >= min AND expression <= max
  ```
* **`NOT BETWEEN`:** Excludes values falling within the range (strictly `< min OR > max`).
* **Date Filtering:** When filtering date-time columns, ensure dates are properly formatted (`YYYY-MM-DD`).

---

## 💻 Syntax

```sql
SELECT column1, column2
FROM table_name
WHERE column_name BETWEEN min_value AND max_value;
```

---

## 📝 Example

### `employees` Table

| emp_id | name  | salary | hire_date  |
| -----: | :---- | -----: | :--------- |
|    101 | Rahul |  45000 | 2022-03-15 |
|    102 | Priya |  60000 | 2023-01-10 |
|    103 | Amit  |  75000 | 2023-06-20 |

### Query:
```sql
SELECT name, salary
FROM employees
WHERE salary BETWEEN 45000 AND 60000;
```

### Result:

| name  | salary |
| :---- | -----: |
| Rahul |  45000 |
| Priya |  60000 |

*(Both 45,000 and 60,000 are included in the result)*

---

# 🎯 Most Asked Interview Questions

### 1. Is the `BETWEEN` operator inclusive or exclusive of its boundary values?
> The `BETWEEN` operator is **inclusive**. Both the minimum and maximum boundary values are included in the filtered result.

---

### 2. Rewrite `WHERE age BETWEEN 18 AND 30` without using `BETWEEN`.
> `WHERE age >= 18 AND age <= 30`

---

### 3. What does `NOT BETWEEN` do?
> `NOT BETWEEN` selects values that fall outside the specified range (strictly less than the minimum or strictly greater than the maximum).

---

# 🧠 Quick Revision

```text
BETWEEN Operator
 ↓
Filters within inclusive range
 ↓
min <= value <= max
 ↓
Works on Numbers, Dates, and Strings
```

> **Memory Trick:** `BETWEEN includes both start and end boundaries!`
