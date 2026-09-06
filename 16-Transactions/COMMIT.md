# 💾 COMMIT Command

## 📌 Definition

The **`COMMIT`** command permanently saves all changes made during the current transaction to the database disk storage.

---

## 🔑 Key Concepts

* **Permanence:** Once a `COMMIT` statement is executed, the changes **cannot be undone or reverted** using `ROLLBACK`.
* **Releases Locks:** Releases any row or table locks held during the transaction lifecycle, making updated data visible to other concurrent sessions.
* **Autocommit Mode:** In MySQL, `SET autocommit = 0;` disables automatic transaction commits, allowing manual multi-statement control.

---

## 💻 Syntax & Example

```sql
START TRANSACTION;

UPDATE accounts SET balance = balance - 2000 WHERE acc_id = 101;
UPDATE accounts SET balance = balance + 2000 WHERE acc_id = 102;

-- Make all updates permanent
COMMIT;
```

---

# 🎯 Most Asked Interview Questions

### 1. What does the `COMMIT` command do in SQL?
> `COMMIT` permanently saves all data modifications made since the beginning of the transaction to the database.

---

### 2. Can you `ROLLBACK` a transaction after running `COMMIT`?
> **No.** Once `COMMIT` executes, the transaction ends and changes are written permanently to storage; `ROLLBACK` has no effect.

---

# 🧠 Quick Revision

```text
START TRANSACTION
       ↓
DML Statements
       ↓
COMMIT (Changes written permanently to disk & locks released)
```

> **Memory Trick:** `COMMIT = Save Changes Permanently`
