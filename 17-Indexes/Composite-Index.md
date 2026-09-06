# 🔗 Composite Index

## 📌 Definition

A **composite index** is an index created on **two or more columns**.

### Example

```sql
CREATE INDEX idx_dept_salary
ON employees(department, salary);
```

This index contains:

```text
department + salary
```

---

## 💡 Why Use It?

Suppose queries frequently use:

```sql
SELECT *
FROM employees
WHERE department = 'IT'
AND salary > 50000;
```

A composite index on:

```text
(department, salary)
```

may help this query.

---

# ⭐ Column Order Matters

For:

```sql
CREATE INDEX idx_name
ON employees(department, salary);
```

The index follows the order:

```text
department → salary
```

This is related to the **leftmost-prefix principle**.

The index can generally be useful for:

```sql
WHERE department = 'IT'
```

and:

```sql
WHERE department = 'IT'
AND salary > 50000
```

But it may not be as useful for a query filtering only on:

```sql
WHERE salary > 50000
```

---

# 🎯 Most Asked Interview Questions

### 1. What is a composite index?

> An index created using two or more columns.

### 2. Does column order matter in a composite index?

> Yes. The order of columns affects which queries can efficiently use the index.

### 3. What is the leftmost-prefix principle?

> A composite index can generally be used efficiently for queries that use its leading columns.

---

# 🧠 Quick Revision

```text
Composite Index
       ↓
Multiple columns
       ↓
Column order matters
       ↓
Leftmost column is important
```

> **Memory Trick:**
> **Composite = Multiple columns in one index**
