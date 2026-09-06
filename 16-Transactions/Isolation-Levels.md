# 🔒 Isolation Levels & Read Phenomena

## 📌 Definition

**Transaction Isolation Levels** define the degree to which data modifications made by one concurrent transaction are visible to other transactions running simultaneously.

---

## ⚠️ 3 Classic Concurrency Read Phenomena

1. **Dirty Read:** A transaction reads data modified by another transaction that has **not yet been committed** (if the second transaction rolls back, the first read invalid "dirty" data).
2. **Non-Repeatable Read:** A transaction re-reads the same row within its timeframe and finds that the row data was **modified/updated by another committed transaction**.
3. **Phantom Read:** A transaction re-executes a range query (e.g. `WHERE salary > 50000`) and finds **new rows inserted or deleted** by another committed transaction.

---

## 🔑 The 4 ANSI SQL Isolation Levels

| Isolation Level | Dirty Read | Non-Repeatable Read | Phantom Read | Default In |
| :--- | :---: | :---: | :---: | :--- |
| **Read Uncommitted** | ❌ Allowed | ❌ Allowed | ❌ Allowed | — |
| **Read Committed** | ✅ **Prevented** | ❌ Allowed | ❌ Allowed | PostgreSQL, Oracle, SQL Server |
| **Repeatable Read** | ✅ **Prevented** | ✅ **Prevented** | ⚠️ Allowed (Prevented in MySQL InnoDB!) | **MySQL (InnoDB)** |
| **Serializable** | ✅ **Prevented** | ✅ **Prevented** | ✅ **Prevented** | — |

---

## 💻 Syntax (MySQL)

```sql
-- Check current isolation level
SELECT @@transaction_isolation;

-- Set session isolation level
SET SESSION TRANSACTION ISOLATION LEVEL REPEATABLE READ;
```

---

# 🎯 Most Asked Interview Questions

### 1. What is the default transaction isolation level in MySQL InnoDB?
> **`REPEATABLE READ`**. In InnoDB, `REPEATABLE READ` uses MVCC and Next-Key Locks to prevent Dirty Reads, Non-Repeatable Reads, **and Phantom Reads**.

---

### 2. What is a Dirty Read?
> A Dirty Read occurs when a transaction reads uncommitted changes made by another concurrent transaction that is subsequently rolled back.

---

### 3. What is the difference between Non-Repeatable Read and Phantom Read?
> * **Non-Repeatable Read:** Concerns **updates/deletions to existing rows** (re-reading the same row returns different column values).
> * **Phantom Read:** Concerns **newly inserted or deleted rows matching a range query** (re-running a query returns a different number of rows).

---

# 🧠 Quick Revision

```text
Isolation Levels (Lowest to Highest Security)
 ├── Read Uncommitted (Dirty Reads possible)
 ├── Read Committed   (No Dirty Reads)
 ├── Repeatable Read  (No Dirty / Non-Repeatable Reads - MySQL Default)
 └── Serializable     (Highest security, strict locking, zero phenomena)
```

> **Memory Trick:** `Read Uncommitted < Read Committed < Repeatable Read < Serializable`
