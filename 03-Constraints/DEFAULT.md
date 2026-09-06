# ⚙️ DEFAULT Constraint

## 📌 Definition

The **`DEFAULT`** constraint sets a default value for a column when no value is explicitly supplied during an `INSERT` statement.

---

## 🔑 Key Concepts

* **Fallback Value:** Provides a default value (literal, string, expression, or function call) if the column is omitted during insertion.
* **Explicit NULL Behavior:** If you explicitly insert `NULL` into a column with a `DEFAULT` constraint, the column will store `NULL` (it will **not** trigger the default value).
* **Dynamic Defaults:** Can store dynamic default values like `CURRENT_TIMESTAMP` or `(CURRENT_DATE)`.

---

## 💻 Syntax

### 1. Specifying `DEFAULT` on Table Creation
```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    order_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    status VARCHAR(20) DEFAULT 'Pending',
    country VARCHAR(50) DEFAULT 'India'
);
```

### 2. Adding `DEFAULT` Constraint to Existing Table (MySQL)
```sql
ALTER TABLE orders
ALTER COLUMN status SET DEFAULT 'Processing';
```

### 3. Dropping a `DEFAULT` Constraint (MySQL)
```sql
ALTER TABLE orders
ALTER COLUMN status DROP DEFAULT;
```

---

## 📝 Example

### Insertion Scenarios

```sql
-- Scenario A: Column omitted (DEFAULT triggered)
INSERT INTO orders (order_id) VALUES (101);
-- Result: order_date = Current Time, status = 'Pending', country = 'India'

-- Scenario B: Explicit NULL provided (DEFAULT NOT triggered)
INSERT INTO orders (order_id, status) VALUES (102, NULL);
-- Result: status = NULL
```

---

# 🎯 Most Asked Interview Questions

### 1. What does the `DEFAULT` constraint do?
> The `DEFAULT` constraint inserts a default value into a column if no explicit value is passed during an `INSERT` operation.

---

### 2. What happens if you explicitly insert `NULL` into a column with a `DEFAULT` value?
> Explicitly inserting `NULL` stores `NULL` in the column. The `DEFAULT` value is applied only when the column is **omitted** from the `INSERT` column list (or when the keyword `DEFAULT` is explicitly used).

---

### 3. Can a `DEFAULT` constraint call a SQL function?
> Yes. Modern databases allow `DEFAULT` constraints to use standard functions such as `CURRENT_TIMESTAMP` or `CURRENT_DATE`.

---

# 🧠 Quick Revision

```text
DEFAULT Constraint
 ↓
Fills value when column is omitted in INSERT
 ↓
Does NOT override explicit NULL
 ↓
Syntax: ALTER TABLE tbl ALTER COLUMN col SET DEFAULT val;
```

> **Memory Trick:** `DEFAULT = Fallback Value on Omission`
