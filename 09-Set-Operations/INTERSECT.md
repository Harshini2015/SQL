# 🎯 INTERSECT Operator

## 📌 Definition

The **`INTERSECT`** operator returns only the **distinct rows that are present in both** `SELECT` query result sets (Set Intersection $A \cap B$).

---

## 🔑 Key Concepts

* **Common Records Only:** A row must exist in Query A **and** Query B to appear in the output.
* **Deduplication:** Automatically eliminates duplicate rows from the final output set.
* **Dialect Support:** Supported natively in **MySQL 8.0+**, PostgreSQL, Oracle, and SQL Server.

---

## 💻 Syntax & Example

```sql
SELECT city FROM customers
INTERSECT
SELECT city FROM suppliers;
```

---

## 📝 Example

### `customers` Cities: `['Mumbai', 'Delhi', 'Bangalore']`
### `suppliers` Cities: `['Delhi', 'Chennai', 'Mumbai']`

```sql
SELECT city FROM customers
INTERSECT
SELECT city FROM suppliers;
```

### Result (Common Cities Only):
`['Mumbai', 'Delhi']`

---

## 💡 How to Emulate `INTERSECT` (Using `INNER JOIN` or `IN`)

If working in an older database system without native `INTERSECT` support:

```sql
-- Emulation Option 1: Using IN
SELECT DISTINCT city 
FROM customers 
WHERE city IN (SELECT city FROM suppliers);

-- Emulation Option 2: Using INNER JOIN
SELECT DISTINCT c.city 
FROM customers c
INNER JOIN suppliers s ON c.city = s.city;
```

---

# 🎯 Most Asked Interview Questions

### 1. What does the `INTERSECT` operator do in SQL?
> `INTERSECT` returns only the distinct rows that appear in the result sets of both queries.

---

### 2. How can you emulate `INTERSECT` if a database does not support it?
> By using `SELECT DISTINCT ... WHERE column IN (subquery)` or performing an `INNER JOIN` between the two tables.

---

# 🧠 Quick Revision

```text
Query A  ∩  Query B
       ↓
Filter Common Rows
       ↓
Returns Only Rows Present in BOTH Sets
```

> **Memory Trick:** `INTERSECT = Intersection / Common Elements Only`
