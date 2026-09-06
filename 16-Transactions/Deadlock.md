# 💀 Deadlock in SQL

## 📌 Definition

A **Deadlock** occurs in a database when two or more concurrent transactions hold locks on resources that the other transactions need, creating a **circular dependency** where none of the transactions can proceed.

---

## 🔑 Deadlock Scenario Example

```text
Transaction 1                   Transaction 2
─────────────                   ─────────────
Holds Lock on Row A             Holds Lock on Row B
Tries to acquire Lock on Row B  Tries to acquire Lock on Row A
(Blocked waiting for Txn 2)     (Blocked waiting for Txn 1)

             💥 DEADLOCK OCCURS! 💥
```

---

## 🛡️ How Database Engine Handles Deadlocks

1. **Automatic Detection:** InnoDB (MySQL) continuously monitors for circular wait locks.
2. **Victim Selection:** When a deadlock is detected, MySQL automatically selects one transaction as the **"victim"** (typically the transaction that has made the fewest modifications).
3. **Automatic Rollback:** The engine rolls back the victim transaction, throwing:
   `ERROR 1213 (40001): Deadlock found when trying to get lock; try restarting transaction`.

---

## 💡 How to Prevent Deadlocks

1. **Consistent Lock Order:** Always access/update tables and rows in the **same order** across all application code.
2. **Keep Transactions Short:** Minimize transaction duration to reduce lock hold times.
3. **Use Indexes:** Ensure query conditions use indexes so the engine acquires **fine-grained row locks** instead of table-level locks.
4. **Lower Isolation Level:** Use `READ COMMITTED` if application requirements permit.

---

# 🎯 Most Asked Interview Questions

### 1. What is a database deadlock?
> A deadlock is a situation where two or more transactions are blocked waiting for each other to release locks, forming a circular dependency that stops execution.

---

### 2. How does MySQL InnoDB resolve a deadlock when it occurs?
> InnoDB detects deadlocks automatically, selects the transaction with the smallest volume of uncommitted changes as a victim, rolls it back, and returns error code `1213`.

---

### 3. Name 2 ways developers can prevent deadlocks in application code.
> 1. Always access and update database rows in a consistent, standardized order across all services.
> 2. Keep transactions small and commit as quickly as possible.

---

# 🧠 Quick Revision

```text
Txn 1 (Holds A, Wants B) ──┐
                           ├── Circular Dependency (DEADLOCK!)
Txn 2 (Holds B, Wants A) ──┘
       ↓
Engine detects deadlock & Rolls back Victim Transaction
```

> **Memory Trick:** `Deadlock = Circular Wait for Locks (Engine rolls back victim)`
