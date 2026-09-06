# 🔍 EXPLAIN

## 📌 Definition

`EXPLAIN` is used to understand **how the database plans to execute a query**.

It helps identify:

* Which indexes may be used
* Which tables are accessed
* Join strategy
* Estimated rows examined
* Possible performance problems

---

# 💻 Example

```sql
EXPLAIN
SELECT *
FROM employees
WHERE employee_id = 101;
```

MySQL returns information about the query execution plan.

---

# 🔑 Important EXPLAIN Columns in MySQL

| Column          | Meaning                          |
| --------------- | -------------------------------- |
| `type`          | Access/join method               |
| `possible_keys` | Indexes that could be used       |
| `key`           | Index actually chosen            |
| `rows`          | Estimated rows examined          |
| `Extra`         | Additional execution information |

---

# ⚠️ Important `type` Values

Generally, from better to less desirable:

```text
const
eq_ref
ref
range
index
ALL
```

`ALL` commonly indicates a full table scan.

> Do not assume every `ALL` is automatically bad; the optimizer may choose it when appropriate, especially for small tables.

---

# 💻 Example

```sql
EXPLAIN
SELECT *
FROM employees
WHERE email = 'rahul@gmail.com';
```

If `email` has an appropriate index, the execution plan may show that index being used.

---

# 🎯 Most Asked Interview Questions

### 1. What is EXPLAIN?

> `EXPLAIN` shows the execution plan that the database uses or expects to use for a query.

### 2. Why is EXPLAIN used?

> It is used to analyze query performance and identify issues such as full table scans or inefficient access paths.

### 3. What does `key` mean in MySQL EXPLAIN?

> It shows the index that MySQL chose to use.

### 4. What does `rows` indicate?

> It is the optimizer's estimate of the number of rows that may need to be examined.

---

# 🧠 Quick Revision

```text
EXPLAIN
   ↓
Execution Plan
   ↓
Indexes
   ↓
Rows examined
   ↓
Query performance analysis
```

> **Memory Trick:** **EXPLAIN = See how the database plans to execute the query**
