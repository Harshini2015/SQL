# 🔗 FOREIGN KEY Constraint

## 📌 Definition

The **`FOREIGN KEY` constraint** is used to prevent actions that would destroy links between tables, enforcing **referential integrity**.

*(For key concepts and parent-child table details, see [Foreign-Key.md](../02-Database-Keys/Foreign-Key.md))*

---

## 🔑 Key Constraint Rules

* Ensures that values inserted into a foreign key column must exist in the referenced primary key column of the parent table.
* Prevents deleting parent rows that have corresponding child rows (unless cascade actions are specified).

---

## 💻 Syntax & Constraint Declaration

### 1. Named Foreign Key Constraint
```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    CONSTRAINT fk_orders_customer 
        FOREIGN KEY (customer_id) 
        REFERENCES customers(customer_id)
        ON DELETE CASCADE
        ON UPDATE CASCADE
);
```

### 2. Adding Constraint to Existing Table
```sql
ALTER TABLE orders
ADD CONSTRAINT fk_orders_customer
FOREIGN KEY (customer_id) REFERENCES customers(customer_id);
```

### 3. Dropping a Foreign Key Constraint (MySQL)
```sql
ALTER TABLE orders
DROP FOREIGN KEY fk_orders_customer;
```

---

## 📝 Example

```sql
-- Inserting non-existent parent value fails
INSERT INTO orders (order_id, customer_id) VALUES (5001, 9999);
-- Error: Cannot add or update a child row: a foreign key constraint fails
```

---

# 🎯 Most Asked Interview Questions

### 1. How do you drop a Foreign Key constraint in MySQL?
> Use `ALTER TABLE table_name DROP FOREIGN KEY constraint_name;`.

---

### 2. What happens if you try to insert a value into a foreign key column that doesn't exist in the parent table?
> The database engine throws a foreign key constraint violation error and rejects the `INSERT` operation.

---

### 3. What is the default `ON DELETE` action for a foreign key?
> The default action is `RESTRICT` (or `NO ACTION`), which blocks the deletion of a parent row if child records exist.

---

# 🧠 Quick Revision

```text
FOREIGN KEY Constraint
 ↓
Enforces Referential Integrity
 ↓
Syntax: FOREIGN KEY (col) REFERENCES parent(col)
 ↓
Drop: ALTER TABLE tbl DROP FOREIGN KEY fk_name;
```
