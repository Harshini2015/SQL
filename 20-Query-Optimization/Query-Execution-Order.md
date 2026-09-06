# 🔄 SQL Query Execution Order

## 📌 Definition

SQL is **written** in one order but logically **processed** in another order.

Consider:

```sql
SELECT department, AVG(salary)
FROM employees
WHERE salary > 30000
GROUP BY department
HAVING AVG(salary) > 50000
ORDER BY AVG(salary) DESC
LIMIT 3;
```

---

# 🧠 Logical Execution Order

Remember:

```text
FROM
  ↓
WHERE
  ↓
GROUP BY
  ↓
HAVING
  ↓
SELECT
  ↓
DISTINCT
  ↓
ORDER BY
  ↓
LIMIT
```

### Easy Memory

> **From Where Groups Have Selected Distinct Ordered Limits**

---

# 🔍 What Happens?

### 1. FROM

Chooses the source table.

### 2. WHERE

Filters individual rows.

### 3. GROUP BY

Creates groups.

### 4. HAVING

Filters groups.

### 5. SELECT

Chooses the output columns/expressions.

### 6. DISTINCT

Removes duplicate results.

### 7. ORDER BY

Sorts the result.

### 8. LIMIT

Restricts the number of rows returned.

---

# 🎯 Most Asked Interview Questions

### 1. What is the SQL query execution order?

> `FROM → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY → LIMIT`.

### 2. Which executes first, WHERE or GROUP BY?

> `WHERE` executes before `GROUP BY`.

### 3. Which executes first, WHERE or HAVING?

> `WHERE` executes before `HAVING`.

### 4. Why can't we normally use an aggregate function in WHERE?

> Because `WHERE` filters rows before grouping and aggregation occurs. `HAVING` is used to filter groups based on aggregate results.

---

# 🧠 Quick Revision

```text
FROM
 ↓
WHERE
 ↓
GROUP BY
 ↓
HAVING
 ↓
SELECT
 ↓
DISTINCT
 ↓
ORDER BY
 ↓
LIMIT
```

> **Most Important:** **WHERE filters rows; HAVING filters groups.**
