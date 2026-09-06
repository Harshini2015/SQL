# 📋 IN Operator

## 📌 Definition

The **`IN`** operator allows you to specify a list of discrete values in a `WHERE` clause, serving as a shorthand for multiple `OR` conditions.

---

## 🔑 Key Concepts

* **Shorthand for `OR`:** `column IN ('A', 'B', 'C')` is functionally equivalent to `column = 'A' OR column = 'B' OR column = 'C'`.
* **Supports Subqueries:** Can evaluate against a subquery returning a list of values (`column IN (SELECT id FROM ...)`).
* **`NOT IN` Trap with `NULL`:** If the list inside `NOT IN` contains a `NULL` value, the overall expression evaluates to `UNKNOWN` and returns **0 rows**!

---

## 💻 Syntax

### 1. Literal Value List
```sql
SELECT * FROM employees
WHERE department IN ('IT', 'HR', 'Finance');
```

### 2. Subquery List
```sql
SELECT * FROM employees
WHERE department_id IN (
    SELECT dept_id FROM departments WHERE location = 'Mumbai'
);
```

---

## ⚠️ Critical Interview Trap: `NOT IN` with `NULL`

Consider this query:
```sql
SELECT * FROM employees
WHERE emp_id NOT IN (101, 102, NULL);
```

### Explanation:
This expands internally to:
```sql
emp_id != 101 AND emp_id != 102 AND emp_id != NULL
```
Since `emp_id != NULL` evaluates to `UNKNOWN`, the entire `AND` chain evaluates to `UNKNOWN`, resulting in **zero rows returned**.

> 💡 **Solution:** Use `NOT EXISTS` or ensure `NULL` values are filtered out of subqueries used with `NOT IN`.

---

# 🎯 Most Asked Interview Questions

### 1. What is the difference between `IN` and multiple `OR` conditions?
> `IN` provides a cleaner, more concise syntax when matching a column against multiple discrete values, and it can also accept subquery results.

---

### 2. What happens if a subquery in a `NOT IN` clause returns a `NULL` value?
> If the subquery returns even a single `NULL` value, `NOT IN` evaluates to `UNKNOWN` for all rows, causing the entire query to return **no records**.

---

### 3. How do you prevent the `NOT IN` NULL trap?
> Filter `NULL`s in the subquery (`WHERE col IS NOT NULL`) or use `NOT EXISTS` instead.

---

# 🧠 Quick Revision

```text
IN Operator
 ├── Shorthand for multiple OR conditions
 ├── Works with literal lists and subqueries
 └── DANGER: NOT IN (..., NULL) returns ZERO rows!
```

> **Memory Trick:** `IN = Multiple ORs | NOT IN + NULL = 0 Rows!`
