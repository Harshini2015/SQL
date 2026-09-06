# ⚡ Query Optimization

## 📌 Definition

**Query optimization** is the process of improving a SQL query so that it executes efficiently while producing the same result.

---

# 🔑 Common Optimization Techniques

## 1. Select Only Required Columns

Avoid:

```sql
SELECT *
FROM employees;
```

Prefer:

```sql
SELECT name, salary
FROM employees;
```

---

## 2. Filter Early

Use appropriate conditions to reduce the number of rows processed.

```sql
SELECT name
FROM employees
WHERE department = 'IT';
```

---

## 3. Use Appropriate Indexes

Indexes can improve queries that frequently filter, join, or sort by indexed columns.

```sql
CREATE INDEX idx_department
ON employees(department);
```

---

## 4. Avoid Unnecessary DISTINCT

`DISTINCT` requires additional work to remove duplicates.

Use it only when duplicates actually need to be removed.

---

## 5. Avoid Unnecessary Subqueries

Sometimes a suitable join or CTE can make the query clearer or more efficient.

Always verify with the execution plan rather than assuming one form is faster.

---

## 6. Check the Execution Plan

Use:

```sql
EXPLAIN
SELECT *
FROM employees
WHERE department = 'IT';
```

Use the plan to identify expensive operations.

---

# ⚠️ Common Mistakes

### Function on Indexed Column

Instead of:

```sql
WHERE YEAR(joining_date) = 2026
```

a range condition may be more index-friendly:

```sql
WHERE joining_date >= '2026-01-01'
AND joining_date < '2027-01-01'
```

---

### Leading Wildcard

This:

```sql
WHERE name LIKE '%rahul'
```

may prevent efficient use of a normal B-tree index for the search.

---

# 🎯 Most Asked Interview Questions

### 1. What is query optimization?

> Query optimization is the process of improving query performance while maintaining the same result.

### 2. How can you optimize a SQL query?

> Select only required columns, filter efficiently, use appropriate indexes, avoid unnecessary operations, optimize joins, and analyze the execution plan using `EXPLAIN`.

### 3. Is `SELECT *` recommended?

> Generally no. Selecting only required columns can reduce unnecessary data retrieval and improve readability.

### 4. How do you identify a slow query?

> Analyze the query using tools such as `EXPLAIN`, inspect indexes, examine rows examined and access methods, and measure actual execution performance.

---

# 🧠 Quick Revision

```text
Optimize Query
 ↓
Select required columns
 ↓
Filter efficiently
 ↓
Use suitable indexes
 ↓
Avoid unnecessary work
 ↓
Check EXPLAIN
```

> **Memory Trick:** **Less Data + Better Index + Better Plan = Better Query**
