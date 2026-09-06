# 📈 When to Use Indexes

## 📌 Use Indexes When

Indexes are useful when a column is frequently used for:

### 1. Filtering

```sql
SELECT *
FROM employees
WHERE department = 'IT';
```

### 2. Joining

```sql
SELECT *
FROM employees e
JOIN departments d
ON e.department_id = d.department_id;
```

### 3. Sorting

```sql
SELECT *
FROM employees
ORDER BY salary;
```

### 4. Searching for Specific Values

```sql
SELECT *
FROM employees
WHERE email = 'rahul@gmail.com';
```

---

# ⚠️ Avoid Unnecessary Indexes

Do not create indexes blindly.

Indexes may hurt performance when:

* The table is very small
* The column is rarely queried
* The table has heavy `INSERT`, `UPDATE`, or `DELETE` activity
* Too many indexes already exist

---

# 🎯 Important Interview Point

A column with **low selectivity** may not benefit much from an index.

Example:

```text
gender → Male / Female
```

If most rows have the same value, an index may provide limited benefit depending on the query and database optimizer.

---

# 🎯 Most Asked Interview Questions

### 1. When should we create an index?

> When columns are frequently used in filtering, joins, sorting, or searching and the performance benefit justifies the additional storage and write cost.

### 2. Should we create an index on every column?

> No. Too many indexes increase storage requirements and can slow down write operations.

### 3. Does indexing a column always improve performance?

> No. The optimizer decides whether an index is beneficial for a particular query.

---

# 🧠 Quick Revision

```text
Good candidates
→ WHERE
→ JOIN
→ ORDER BY
→ Frequent searches

Avoid blindly indexing
→ Every column
→ Rarely used columns
→ Small tables
```

> **Memory Trick:**
> **Index what you search, filter, join, or sort frequently.**
