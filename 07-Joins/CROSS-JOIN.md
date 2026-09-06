# ✖️ CROSS JOIN (Cartesian Product)

## 📌 Definition

A **`CROSS JOIN`** returns the **Cartesian product** of two tables, matching **every single row** from the first table with **every single row** from the second table.

---

## 🔑 Key Concepts

* **Cartesian Product:** No join condition (`ON` clause) is required.
* **Row Count Formula:**
  $$\text{Total Rows} = \text{Rows in Table A} \times \text{Rows in Table B}$$
* **Use Cases:** Generating matrix combinations (e.g. products $\times$ sizes, colors $\times$ models, calendar dates $\times$ categories).

---

## 💻 Syntax

```sql
-- Explicit Syntax
SELECT columns
FROM tableA
CROSS JOIN tableB;

-- Implicit Syntax (Comma-separated)
SELECT columns
FROM tableA, tableB;
```

---

## 📝 Example

### Table A: `products` (2 rows)

| product_name |
| :----------- |
| Shirt        |
| Pants        |

### Table B: `sizes` (3 rows)

| size_code |
| :-------- |
| S         |
| M         |
| L         |

```sql
SELECT p.product_name, s.size_code
FROM products p
CROSS JOIN sizes s;
```

### Result ( $2 \times 3 = 6$ rows):

| product_name | size_code |
| :----------- | :-------- |
| Shirt        | S         |
| Shirt        | M         |
| Shirt        | L         |
| Pants        | S         |
| Pants        | M         |
| Pants        | L         |

---

# 🎯 Most Asked Interview Questions

### 1. What is a `CROSS JOIN` in SQL?
> A `CROSS JOIN` computes the Cartesian product of two tables, producing every possible pair combination of rows.

---

### 2. If Table A has 10 rows and Table B has 50 rows, how many rows will `SELECT * FROM TableA CROSS JOIN TableB` return?
> $10 \times 50 = 500$ rows.

---

### 3. Does a `CROSS JOIN` require an `ON` clause?
> No. A `CROSS JOIN` does not use an `ON` condition because every row is unconditionally matched with every row in the secondary table.

---

# 🧠 Quick Revision

```text
Table A (N rows)  ×  Table B (M rows)
           ↓
    Cartesian Product
           ↓
     Total: N × M Rows
```

> **Memory Trick:** `CROSS JOIN = Everything multiplied by Everything (N × M)`
