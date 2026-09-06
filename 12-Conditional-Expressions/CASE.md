# 🔀 CASE Expression

## 📌 Definition

The **`CASE`** expression provides **if-then-else conditional logic** in SQL queries to dynamically return values based on specific conditions.

---

## 🔑 Key Forms

### 1. Searched `CASE` (Most Flexible & Common)
Evaluates independent boolean conditions in order.
```sql
CASE 
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ELSE default_result
END
```

### 2. Simple `CASE`
Compares an expression against discrete values.
```sql
CASE expression
    WHEN value1 THEN result1
    WHEN value2 THEN result2
    ELSE default_result
END
```

---

## 💻 Syntax & Examples

### 1. Categorizing Salaries (Searched CASE)
```sql
SELECT name, salary,
    CASE 
        WHEN salary >= 80000 THEN 'High'
        WHEN salary >= 50000 THEN 'Medium'
        ELSE 'Low'
    END AS salary_tier
FROM employees;
```

### 2. Conditional Aggregation (Pivot Trick)
```sql
SELECT 
    COUNT(CASE WHEN department = 'IT' THEN 1 END) AS it_count,
    COUNT(CASE WHEN department = 'HR' THEN 1 END) AS hr_count
FROM employees;
```

---

## 📝 Example Output

### `employees` Output:

| name  | salary | salary_tier |
| :---- | -----: | :---------- |
| Amit  |  85000 | High        |
| Rahul |  60000 | Medium      |
| Priya |  40000 | Low         |

---

# 🎯 Most Asked Interview Questions

### 1. What happens if no `WHEN` condition is met and no `ELSE` clause is specified in a `CASE` statement?
> If no condition matches and there is no `ELSE` clause, the `CASE` statement returns **`NULL`**.

---

### 2. Can `CASE` statements be used inside aggregate functions like `SUM()` or `COUNT()`?
> Yes. Conditional aggregation using `SUM(CASE WHEN ... THEN 1 ELSE 0 END)` is one of the most powerful and common SQL interview patterns.

---

# 🧠 Quick Revision

```text
CASE Expression
 ├── WHEN condition THEN result
 ├── ELSE default (Returns NULL if omitted and no match)
 └── END (Mandatory terminating keyword)
```

> **Memory Trick:** `CASE = IF-THEN-ELSE inside SQL queries`
