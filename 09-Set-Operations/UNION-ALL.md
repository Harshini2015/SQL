# ➕ UNION ALL Operator

## 📌 Definition

The **`UNION ALL`** operator combines the result sets of two or more `SELECT` queries into a single result set, **retaining all duplicate rows**.

---

## 🔑 Key Concepts

* **No Deduplication:** Appends the results of queries directly without checking for or removing duplicate rows.
* **Maximum Performance:** Significantly faster than `UNION` because it avoids expensive memory sorting and deduplication algorithms.
* **Preserves Row Counts:** The total number of rows returned is strictly the sum of rows returned by each individual query ($N_1 + N_2$).

---

## 💻 Syntax & Example

```sql
SELECT city FROM customers
UNION ALL
SELECT city FROM suppliers;
```

---

## 📝 Example

### `customers` Cities: `['Mumbai', 'Delhi', 'Bangalore']`
### `suppliers` Cities: `['Delhi', 'Chennai', 'Mumbai']`

```sql
SELECT city FROM customers
UNION ALL
SELECT city FROM suppliers;
```

### Result (Includes Duplicates):
`['Mumbai', 'Delhi', 'Bangalore', 'Delhi', 'Chennai', 'Mumbai']`

*(Total 6 rows returned)*

---

## ⚖️ Important Comparison: UNION vs UNION ALL

| Feature | `UNION` | `UNION ALL` |
| :--- | :--- | :--- |
| **Duplicates** | Filtered out | Retained |
| **Performance** | Slower | **Faster** |
| **Use Case** | When unique distinct set is mandatory | When duplicate values are acceptable or impossible |

---

# 🎯 Most Asked Interview Questions

### 1. When should you use `UNION ALL` instead of `UNION`?
> Use `UNION ALL` whenever duplicate rows are acceptable or when you know the input query result sets are mutually exclusive (no overlap), because `UNION ALL` avoids the performance overhead of deduplication sorting.

---

### 2. What is the total row count of `SELECT 1 UNION ALL SELECT 1`?
> It will return **2 rows** (both containing the value `1`). `SELECT 1 UNION SELECT 1` would return 1 row.

---

# 🧠 Quick Revision

```text
Query A  +  Query B
       ↓
Direct Append (No Sorting)
       ↓
Returns ALL Combined Rows (Including Duplicates)
```

> **Memory Trick:** `UNION ALL = Direct Append (Faster, Keeps Duplicates)`
