# 🔄 TCL — Transaction Control Language

## 📌 Definition

**TCL (Transaction Control Language)** is used to **manage transactions** in a database.

A **transaction** is a group of SQL operations treated as a single unit of work.

### Main TCL Commands

| Command     | Purpose                                   |
| ----------- | ----------------------------------------- |
| `COMMIT`    | Permanently saves changes                 |
| `ROLLBACK`  | Undoes uncommitted changes                |
| `SAVEPOINT` | Creates a point to which we can roll back |

---

# 1. COMMIT

`COMMIT` permanently saves the changes made in the current transaction.

```sql
UPDATE employees
SET salary = 60000
WHERE employee_id = 101;

COMMIT;
```

After `COMMIT`, the changes are saved.

---

# 2. ROLLBACK

`ROLLBACK` undoes changes made since the last `COMMIT` or transaction start, depending on the database and transaction state.

```sql
UPDATE employees
SET salary = 70000
WHERE employee_id = 101;

ROLLBACK;
```

The update is undone if it has not been committed.

---

# 3. SAVEPOINT

`SAVEPOINT` creates a point inside a transaction that you can roll back to.

```sql
UPDATE employees
SET salary = 60000
WHERE employee_id = 101;

SAVEPOINT sp1;

UPDATE employees
SET salary = 70000
WHERE employee_id = 102;

ROLLBACK TO sp1;

COMMIT;
```

The second update is undone, while the first update remains part of the transaction and is committed.

---

# 🧩 Transaction Example

Suppose a bank transfers ₹5,000 from Account A to Account B.

```text
Account A → Debit ₹5,000
Account B → Credit ₹5,000
```

Both operations should succeed together.

```sql
UPDATE accounts
SET balance = balance - 5000
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 5000
WHERE account_id = 2;

COMMIT;
```

If something goes wrong before the transaction is committed:

```sql
ROLLBACK;
```

The uncommitted changes can be undone.

---

# 🎯 Most Asked Interview Questions

### 1. What is TCL?

> TCL stands for Transaction Control Language. It is used to manage transactions in a database.

---

### 2. What are the main TCL commands?

> `COMMIT`, `ROLLBACK`, and `SAVEPOINT`.

---

### 3. What is COMMIT?

> `COMMIT` permanently saves the changes made in a transaction.

---

### 4. What is ROLLBACK?

> `ROLLBACK` undoes uncommitted changes in a transaction.

---

### 5. What is SAVEPOINT?

> `SAVEPOINT` creates a point within a transaction to which we can roll back without undoing the entire transaction.

---

### 6. Difference between COMMIT and ROLLBACK?

| COMMIT                                  | ROLLBACK                                        |
| --------------------------------------- | ----------------------------------------------- |
| Saves changes                           | Undoes uncommitted changes                      |
| Makes the transaction changes permanent | Returns changes to an earlier transaction state |

---

### 7. What is the difference between ROLLBACK and ROLLBACK TO SAVEPOINT?

> `ROLLBACK` can undo the transaction's uncommitted changes, while `ROLLBACK TO SAVEPOINT` undoes changes made after a specific savepoint and keeps the transaction active.

---

# 🧠 Quick Revision

```text
TCL
│
├── COMMIT       → Save changes
├── ROLLBACK     → Undo changes
└── SAVEPOINT    → Create rollback point
```

> **Memory Trick:**
> **COMMIT = Save | ROLLBACK = Undo | SAVEPOINT = Checkpoint**
