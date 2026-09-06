# 🛑 LIMIT Clause

## 📌 Definition

The **`LIMIT`** clause specifies the **maximum number of rows** a `SELECT` query will return. It is commonly used for top-N analysis and pagination.

---

## 🔑 Key Concepts

* **Row Restriction:** Prevents queries from returning excessively large datasets.
* **Pagination with `OFFSET`:** `OFFSET` specifies how many initial rows to skip before returning the limited rows.
* **Dialect Differences:**
  * **MySQL / PostgreSQL / SQLite:** `LIMIT count OFFSET offset` (or MySQL shorthand `LIMIT offset, count`).
  * **SQL Server:** `TOP n` or `OFFSET x ROWS FETCH NEXT y ROWS ONLY`.
  * **Oracle:** `FETCH FIRST n ROWS ONLY`.
* **Always Pair with `ORDER BY`:** To get consistent top/bottom records, always combine `LIMIT` with `ORDER BY`.

---

## 💻 Syntax (MySQL)

### 1. Simple LIMIT
```sql
SELECT column1, column2
FROM table_name
ORDER BY column1 DESC
LIMIT count;
```

### 2. LIMIT with OFFSET (Pagination)
```sql
-- Standard SQL / MySQL
SELECT column1, column2
FROM table_name
ORDER BY column1
LIMIT 5 OFFSET 10; -- Skips first 10 rows, returns next 5 rows

-- MySQL Alternative Shorthand (LIMIT offset, count)
SELECT column1, column2
FROM table_name
ORDER BY column1
LIMIT 10, 5;
```

---

## 📝 Example

### `employees` Table (Sorted by Salary DESC)

| emp_id | name  | salary |
| -----: | :---- | -----: |
|    103 | Amit  |  80000 |
|    102 | Priya |  75000 |
|    101 | Rahul |  60000 |
|    104 | Neha  |  50000 |

### Find 2nd Highest Salary:
```sql
SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;
```

### Result:

| salary |
| -----: |
|  75000 |

---

# 🎯 Most Asked Interview Questions

### 1. What is the `LIMIT` clause used for?
> The `LIMIT` clause limits the number of records returned in a query result set.

---

### 2. How do you find the 2nd or Nth highest salary in MySQL?
> By ordering salaries in descending order and using `LIMIT 1 OFFSET (N-1)`. For 2nd highest: `LIMIT 1 OFFSET 1`.

---

### 3. What is the formula for page pagination using `LIMIT` and `OFFSET`?
> * `LIMIT = page_size`
> * `OFFSET = (page_number - 1) * page_size`

---

# 🧠 Quick Revision

```text
Query Execution
 ↓
Sort records (ORDER BY)
 ↓
Skip initial rows (OFFSET x)
 ↓
Take next N rows (LIMIT n)
```

> **Memory Trick:** `LIMIT = Max Rows | OFFSET = Rows to Skip`
