# ↩️ ROLLBACK Command

## 📌 Definition

The **`ROLLBACK`** command undoes (reverts) all data modifications made during the current uncommitted transaction, restoring data to its state before the transaction began.

---

## 🔑 Key Concepts

* **Atomicity Enforcer:** Restores data state using **Undo Logs** when an error occurs or when an operational condition fails.
* **Partial Rollback:** Can roll back to a specific marker using `ROLLBACK TO SAVEPOINT savepoint_name;`.
* **⚠️ Implicit Commit Warning (DDL Commands):** In MySQL, executing DDL statements (`CREATE`, `ALTER`, `DROP`, `TRUNCATE`) causes an **implicit commit**. You **cannot** roll back DDL operations!

---

## 💻 Syntax & Example

```sql
START TRANSACTION;

UPDATE accounts SET balance = balance - 5000 WHERE acc_id = 101;

-- Error detected! Cancel all changes
ROLLBACK;
```

---

# 🎯 Most Asked Interview Questions

### 1. What does the `ROLLBACK` command do?
> `ROLLBACK` reverts all uncommitted modifications made during the current transaction and restores data to its pre-transaction state.

---

### 2. Can you roll back a `DROP TABLE` or `TRUNCATE TABLE` statement in MySQL?
> **No.** In MySQL, DDL statements (`CREATE`, `ALTER`, `DROP`, `TRUNCATE`) trigger an **implicit commit**, terminating the current transaction immediately.

---

# 🧠 Quick Revision

```text
START TRANSACTION
       ↓
Modify Records
       ↓
Error Occurs! → ROLLBACK (Restores original data via Undo Log)
```

> **Memory Trick:** `ROLLBACK = Undo Uncommitted Modifications`
