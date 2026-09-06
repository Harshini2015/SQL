# 🔀 UNION Operator

## 📌 Definition

The **`UNION`** operator combines the result sets of two or more `SELECT` queries into a single result set, **automatically removing duplicate rows**.

---

## 🔑 Mandatory Rules for Set Operations

For any set operation (`UNION`, `UNION ALL`, `INTERSECT`, `EXCEPT`) to work:
1. Every `SELECT` query must return the **same number of columns**.
2. The columns must have **compatible data types** in the corresponding order.
3. Column names in the final result set are taken from the **first `SELECT` statement**.

---

## 💻 Syntax & Example

```sql
SELECT city FROM customers
UNION
SELECT city FROM suppliers;
```

---

## 📝 Example

### `customers` Cities: `['Mumbai', 'Delhi', 'Bangalore']`
### `suppliers` Cities: `['Delhi', 'Chennai', 'Mumbai']`

```sql
SELECT city FROM customers
UNION
SELECT city FROM suppliers;
```

### Result (Duplicates Removed):
`['Mumbai', 'Delhi', 'Bangalore', 'Chennai']`

---

## ⚖️ Important Difference: UNION vs UNION ALL

| Feature | `UNION` | `UNION ALL` |
| :--- | :--- | :--- |
| **Duplicates** | **Removes** duplicate rows | **Retains** all duplicate rows |
| **Performance** | **Slower** (Requires sorting/hash operation to deduplicate) | **Faster** (Direct append without sorting) |
| **Row Count** | Unique combined rows only | Total combined rows ($N_1 + N_2$) |

---

# 🎯 Most Asked Interview Questions

### 1. What are the rules for using the `UNION` operator in SQL?
> 1. Both queries must select the same number of columns.
> 2. The data types of columns in corresponding positions must be compatible.

---

### 2. Is `UNION` faster or slower than `UNION ALL`?
> `UNION` is slower than `UNION ALL` because `UNION` performs an internal sort/deduplication step to remove duplicate rows from the final result set.

---

### 3. How are column headers determined in a `UNION` query?
> The column names of the final result set are determined by the column aliases used in the **first `SELECT` statement**.

---

# 🧠 Quick Revision

```text
Query A  ∪  Query B
       ↓
Combine Rows
       ↓
Deduplicate (Sort/Hash)
       ↓
Returns Unique Combined Rows
```

> **Memory Trick:** `UNION = Combine + Deduplicate (Slower)`
