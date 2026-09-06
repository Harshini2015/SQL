# 📍 SAVEPOINT Command

## 📌 Definition

A **`SAVEPOINT`** is a marker or checkpoint created within a transaction that allows a **partial rollback**, reverting changes made *after* the savepoint while keeping earlier changes intact.

---

## 🔑 Key Concepts

* **Partial Rollback:** `ROLLBACK TO SAVEPOINT savepoint_name;` cancels statements executed after the savepoint without aborting the entire transaction.
* **Multiple Savepoints:** A single transaction can declare multiple named savepoints.
* **`RELEASE SAVEPOINT`:** Removes a specified savepoint marker from the transaction context without rolling back changes.

---

## 💻 Syntax & Example

```sql
START TRANSACTION;

-- Step 1: Insert Order Header
INSERT INTO orders (order_id, customer_id) VALUES (501, 10);
SAVEPOINT header_created;

-- Step 2: Insert Order Item 1
INSERT INTO order_items (order_id, item_id) VALUES (501, 1);
SAVEPOINT item1_created;

-- Step 3: Insert Order Item 2 (Fails or invalid condition)
INSERT INTO order_items (order_id, item_id) VALUES (501, 9999);

-- Revert ONLY Step 3 (Item 2), preserving Header and Item 1
ROLLBACK TO SAVEPOINT item1_created;

-- Step 4: Commit Header + Item 1 permanently
COMMIT;
```

---

# 🎯 Most Asked Interview Questions

### 1. What is a `SAVEPOINT` in SQL?
> A `SAVEPOINT` creates a checkpoint within a transaction, allowing you to selectively roll back a portion of the transaction without canceling the entire unit of work.

---

### 2. What happens to savepoints when a transaction is committed or completely rolled back?
> When a transaction is finalized via `COMMIT` or full `ROLLBACK`, all savepoints associated with that transaction are automatically cleared and released.

---

# 🧠 Quick Revision

```text
START TRANSACTION
 ├── Action 1
 ├── SAVEPOINT sp1
 ├── Action 2
 └── ROLLBACK TO SAVEPOINT sp1 (Action 2 undone, Action 1 preserved)
```

> **Memory Trick:** `SAVEPOINT = Intermediate Transaction Checkpoint`
