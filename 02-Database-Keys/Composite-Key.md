# 🧩 Composite Key

## 📌 Definition

A **Composite Key** is a key (Primary Key, Foreign Key, or Candidate Key) that consists of **two or more columns** combined together to uniquely identify a row in a table.

---

## 🔑 Key Concepts

* **Multiple Columns:** Used when no single column alone is sufficient to uniquely identify a record.
* **Combined Uniqueness:** Individual columns in a composite key can contain duplicate values, but the **combination of values across all columns must be unique**.
* **Table-Level Definition:** Must be declared at the table level using `PRIMARY KEY (col1, col2)` syntax.

---

## 💻 Syntax

```sql
CREATE TABLE order_items (
    order_id INT,
    product_id INT,
    quantity INT NOT NULL,
    price DECIMAL(10, 2) NOT NULL,
    PRIMARY KEY (order_id, product_id)  -- Composite Primary Key
);
```

---

## 📝 Example

### `order_items` Table

| order_id | product_id | quantity | price |
| -------: | ---------: | -------: | ----: |
|     1001 |        501 |        2 | 25.00 |
|     1001 |        502 |        1 | 50.00 |
|     1002 |        501 |        5 | 25.00 |

* `order_id` alone has duplicates (`1001` appears twice).
* `product_id` alone has duplicates (`501` appears twice).
* But the combination `(order_id, product_id)` -> `(1001, 501)`, `(1001, 502)`, `(1002, 501)` is completely **unique**.

---

## ⚖️ Important Difference: Single Key vs Composite Key

| Feature | Single Key | Composite Key |
| :--- | :--- | :--- |
| **Column Count** | Consists of **1** column | Consists of **2 or more** columns |
| **Declaration** | Can be declared column-level or table-level | Must be declared at **table-level** |
| **Use Case** | Simple entity with surrogate ID (e.g. `emp_id`) | Junction/Mapping tables (e.g. Many-to-Many relationships) |

---

# 🎯 Most Asked Interview Questions

### 1. What is a Composite Key?
> A Composite Key is a key formed by combining two or more columns to uniquely identify a record in a table when no single column is unique.

---

### 2. Can individual columns of a Composite Primary Key contain duplicate values?
> Yes. Individual columns can have repeating values, as long as the combined set of values across all columns in the key remains unique.

---

### 3. Can any column in a Composite Primary Key contain NULL?
> No. Since it functions as a Primary Key, none of the participant columns in a Composite Primary Key can contain `NULL` values.

---

### 4. Where are Composite Keys most commonly used?
> Composite Keys are commonly used in **junction tables** (bridge tables) to manage Many-to-Many relationships between two entities.

---

# 🧠 Quick Revision

```text
Column A (Has duplicates)
       +
Column B (Has duplicates)
       ↓
(Column A + Column B) → Unique Composite Key
```

> **Memory Trick:** `Composite Key = Column1 + Column2 (Combined Uniqueness)`
