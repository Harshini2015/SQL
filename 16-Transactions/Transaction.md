# 🔄 Database Transactions

## 📌 Definition

A **Transaction** is a single logical unit of work (LUW) consisting of one or more SQL statements executed as an **all-or-nothing atomic operation**.

---

## 🔑 Key Concepts

* **All-or-Nothing Principle:** If all statements succeed, the transaction is permanently saved (`COMMIT`). If any statement fails, all changes are discarded (`ROLLBACK`).
* **Classic Real-World Example (Bank Transfer):**
  1. Deduct ₹5000 from Account A.
  2. Add ₹5000 to Account B.
  *(Both operations must succeed together; otherwise, money vanishes if power fails midway!)*

---

## 💻 Syntax & Commands (MySQL)

```sql
-- 1. Start Transaction
START TRANSACTION; -- Or BEGIN;

-- 2. Execute SQL DML Statements
UPDATE accounts SET balance = balance - 5000 WHERE acc_id = 101;
UPDATE accounts SET balance = balance + 5000 WHERE acc_id = 102;

-- 3. Commit Changes Permanently (If all succeed)
COMMIT;

-- OR Rollback Changes (If an error occurs)
-- ROLLBACK;
```

---

## 🔄 Transaction State Lifecycle

```text
       Active (Executing SQL)
       /                  \
      ↓                    ↓
Partially Committed     Failed
      │                    │
      ↓ (COMMIT)           ↓ (ROLLBACK)
  Committed             Aborted
```

---

# 🎯 Most Asked Interview Questions

### 1. What is a transaction in SQL?
> A transaction is a sequence of one or more SQL operations executed as a single logical unit of work that succeeds entirely or fails entirely.

---

### 2. What is Autocommit mode in MySQL?
> In MySQL, `autocommit` is enabled by default (`autocommit = 1`), automatically committing every individual DML statement immediately unless an explicit `START TRANSACTION` command is issued.

---

# 🧠 Quick Revision

```text
START TRANSACTION
       ↓
Execute Queries
 ├── All Success? → COMMIT (Permanent)
 └── Any Error?   → ROLLBACK (Undo All)
```

> **Memory Trick:** `Transaction = All statements succeed OR none take effect!`
