# 🔥 N+1 Query Problem

## 📌 Definition

The **N+1 query problem** occurs when an application executes:

```text
1 query → Fetch N records
+
N queries → Fetch related data for each record
```

Total:

```text
N + 1 queries
```

This can cause serious performance problems.

---

# 💻 Example

Suppose we first fetch 100 employees:

```sql
SELECT *
FROM employees;
```

Then the application separately fetches the department for each employee:

```text
1 query → employees

100 queries → department for each employee

Total = 101 queries
```

---

# ❌ Problematic Pattern

```text
Application
    ↓
Query employees
    ↓
Employee 1 → Query department
Employee 2 → Query department
Employee 3 → Query department
...
Employee 100 → Query department
```

---

# ✅ Better Approach

Use a suitable join:

```sql
SELECT e.name, d.department_name
FROM employees e
JOIN departments d
ON e.department_id = d.department_id;
```

Now the required information can be retrieved using a single query.

---

# 🎯 Why is N+1 Bad?

It can cause:

* Too many database round trips
* Increased network overhead
* Higher database load
* Slower application performance

The problem becomes more significant as `N` increases.

---

# 🎯 Most Asked Interview Questions

### 1. What is the N+1 problem?

> The N+1 problem occurs when an application executes one query to retrieve N records and then executes another query for each individual record.

### 2. How can you solve the N+1 problem?

> Common approaches include using joins, batching related queries, or fetching related data efficiently according to the application's data-access strategy.

### 3. Is N+1 only a SQL problem?

> No. It is mainly an application/database interaction problem caused by inefficient data-access patterns.

### 4. Give a simple example.

> Fetching 100 employees with one query and then running 100 separate queries to fetch each employee's department results in 101 queries.

---

# 🧠 Quick Revision

```text
N+1 Problem

1 query
  +
N queries
  =
N+1 queries
```

### Better approach

```text
Use JOIN / Batch Fetching
        ↓
Reduce database round trips
        ↓
Improve performance
```

> **Memory Trick:** **One query for the list + one query per item = N+1 problem**
