# 📈 Index Optimization

## 📌 Definition

**Index optimization** means designing and using indexes so that frequently executed queries can retrieve data efficiently without creating unnecessary write and storage costs.

---

# 🔑 Important Rules

## 1. Index Frequently Filtered Columns

Example:

```sql
SELECT *
FROM employees
WHERE department = 'IT';
```

An index on `department` may help if the table and query pattern justify it.

---

## 2. Index Join Columns

Example:

```sql
SELECT *
FROM employees e
JOIN departments d
ON e.department_id = d.department_id;
```

Appropriate indexes on join columns can improve performance.

---

## 3. Consider Composite Indexes

For:

```sql
WHERE department = 'IT'
AND salary > 50000
```

a composite index may be useful:

```sql
CREATE INDEX idx_dept_salary
ON employees(department, salary);
```

Column order matters.

---

## 4. Avoid Too Many Indexes

Every index:

* Uses storage
* Must be maintained
* Can increase write cost

---

## 5. Check the Query Plan

Use:

```sql
EXPLAIN
SELECT *
FROM employees
WHERE department = 'IT';
```

Do not create an index simply because a column appears in a query. Verify whether it actually helps.

---

# 🎯 Most Asked Interview Questions

### 1. Which columns should be indexed?

> Columns frequently used in filtering, joins, sorting, or other performance-critical queries are common candidates.

### 2. Why not create indexes on every column?

> Because indexes consume storage and increase the cost of insert, update, and delete operations.

### 3. What is a composite index?

> An index created on multiple columns.

### 4. Does the order of columns matter in a composite index?

> Yes. The leading columns determine which queries can efficiently use the index.

---

# 🧠 Quick Revision

```text
Index Optimization
 ↓
WHERE
JOIN
ORDER BY
 ↓
Composite indexes when appropriate
 ↓
Avoid unnecessary indexes
 ↓
Verify with EXPLAIN
```

> **Memory Trick:** **Index what you frequently search, join, or sort.**
