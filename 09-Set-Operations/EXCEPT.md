# ➖ EXCEPT (MINUS) Operator

## 📌 Definition

The **`EXCEPT`** operator (known as **`MINUS`** in Oracle) returns distinct rows from the **first query that do not exist in the second query** (Set Difference $A - B$).

---

## 🔑 Key Concepts

* **Order Sensitive:** The order of queries matters! `Query A EXCEPT Query B` produces a different result than `Query B EXCEPT Query A`.
* **Deduplication:** Removes duplicate records from the final result set.
* **Dialect Terminology:**
  * **`EXCEPT`:** Standard SQL, PostgreSQL, SQL Server, **MySQL 8.0+**.
  * **`MINUS`:** Oracle Database.

---

## 💻 Syntax & Example

```sql
-- Returns cities in customers that are NOT in suppliers
SELECT city FROM customers
EXCEPT
SELECT city FROM suppliers;
```

---

## 📝 Example

### `customers` Cities: `['Mumbai', 'Delhi', 'Bangalore']`
### `suppliers` Cities: `['Delhi', 'Chennai', 'Mumbai']`

```sql
SELECT city FROM customers
EXCEPT
SELECT city FROM suppliers;
```

### Result ($A - B$):
`['Bangalore']`

*(Only 'Bangalore' exists in `customers` but not in `suppliers`)*

---

## 💡 How to Emulate `EXCEPT` (Using `NOT EXISTS` or `LEFT JOIN`)

If working in older database systems:

```sql
-- Emulation Option 1: Using NOT EXISTS
SELECT DISTINCT c.city 
FROM customers c
WHERE NOT EXISTS (
    SELECT 1 FROM suppliers s WHERE s.city = c.city
);

-- Emulation Option 2: Using LEFT JOIN
SELECT DISTINCT c.city
FROM customers c
LEFT JOIN suppliers s ON c.city = s.city
WHERE s.city IS NULL;
```

---

# 🎯 Most Asked Interview Questions

### 1. What does the `EXCEPT` operator do?
> `EXCEPT` returns distinct rows from the left query that are not present in the right query result set.

---

### 2. Is `EXCEPT` the same as `MINUS`?
> Yes. `EXCEPT` is the ANSI SQL standard operator name, whereas Oracle calls the exact same operator `MINUS`.

---

### 3. Does `A EXCEPT B` yield the same result as `B EXCEPT A`?
> No. `EXCEPT` is non-commutative. `A EXCEPT B` finds items unique to A, while `B EXCEPT A` finds items unique to B.

---

# 🧠 Quick Revision

```text
Query A  -  Query B
       ↓
Filter Out Any Row Present in B
       ↓
Returns Rows Unique to Query A
```

> **Memory Trick:** `EXCEPT / MINUS = Set Difference (A minus B)`
