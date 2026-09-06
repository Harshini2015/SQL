# 🛡️ ACID Properties

## 📌 Definition

**ACID** is an acronym representing 4 core properties that guarantee reliable transaction processing in a Relational Database Management System (RDBMS).

---

## 🔑 The 4 ACID Properties

### 1. 🅰️ Atomicity ("All or Nothing")
* **Concept:** Ensures that all operations within a transaction complete successfully, or **none of them take effect**.
* **Mechanism:** Handled via **Undo Logs** and `ROLLBACK` operations.

---

### 2. 🅲 Consistency ("Preserve Rules")
* **Concept:** Ensures that a transaction brings the database from **one valid state to another**, enforcing all rules, schema constraints, foreign keys, and triggers.
* **Mechanism:** Enforced by database schema rules, constraints (`NOT NULL`, `CHECK`, `FK`), and application logic.

---

### 3. 🅸 Isolation ("Independent Execution")
* **Concept:** Ensures that concurrent transactions execute **independently without interfering with each other** until committed.
* **Mechanism:** Handled via **Locks** and **MVCC** (Multi-Version Concurrency Control). *(See [Isolation-Levels.md](Isolation-Levels.md))*.

---

### 4. 🅳 Durability ("Permanent Persistence")
* **Concept:** Ensures that once a transaction is committed, its changes are **permanently saved**, even in the event of a power loss or system crash.
* **Mechanism:** Handled via **Redo Logs** (Write-Ahead Logging / WAL) and disk flushing.

---

## 📊 Summary Comparison

| Property | Core Question Answered | Underlying Database Mechanism |
| :--- | :--- | :--- |
| **Atomicity** | Did all statements run or zero? | Undo Logs |
| **Consistency** | Did schema constraints stay valid? | Constraints & Triggers |
| **Isolation** | Can concurrent users interfere? | Locks & MVCC |
| **Durability** | Will data survive a server crash? | Redo Logs (WAL) |

---

# 🎯 Most Asked Interview Questions

### 1. What does ACID stand for in databases?
> Atomicity, Consistency, Isolation, and Durability.

---

### 2. Which ACID property ensures data is not lost if the server loses power right after a `COMMIT`?
> **Durability**, which writes changes to non-volatile storage using Redo Logs (Write-Ahead Logging).

---

### 3. How does InnoDB (MySQL) enforce Atomicity?
> Through **Undo Logs**, which record the original un-modified state of data so changes can be reverted during a `ROLLBACK`.

---

# 🧠 Quick Revision

```text
A - Atomicity   → All or Nothing (Undo Log)
C - Consistency → Schema Constraints Validated
I - Isolation   → Concurrent Isolation (Locks/MVCC)
D - Durability  → Crash Resilience (Redo Log / WAL)
```

> **Memory Trick:** `ACID = Atomicity (Undo) | Consistency (Rules) | Isolation (Locks) | Durability (Redo)`
