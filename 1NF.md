# First Normal Form (1NF)

## 📌 What is 1NF?

A table is in **First Normal Form (1NF)** when:

1. Every column contains **atomic (single) values**.
2. There are **no multiple values in a single cell**.
3. There are **no repeating groups**.

---

## ❌ Example: Table Not in 1NF

### Student

| Student_ID | Student_Name | Courses      |
| ---------- | ------------ | ------------ |
| 101        | Rahul        | Java, DBMS   |
| 102        | Priya        | Python, Java |

### Problem

The `Courses` column contains multiple values in a single cell.

For example:

```text
Java, DBMS
```

This violates the atomic-value rule.

Therefore, this table is **NOT in 1NF**.

---

## ✅ Convert to 1NF

We separate the multiple course values into individual rows.

### Student_Course

| Student_ID | Student_Name | Course |
| ---------- | ------------ | ------ |
| 101        | Rahul        | Java   |
| 101        | Rahul        | DBMS   |
| 102        | Priya        | Python |
| 102        | Priya        | Java   |

Now every cell contains a **single value**.

Therefore, the table is in **1NF** ✅.

---

## 🔑 Key Point

> **1NF means every cell should contain only one atomic value.**

### Easy way to remember

**1NF → Atomic Values**

```text
Multiple values in one cell ❌
            ↓
One value per cell ✅
```

---


> "First Normal Form means that every column should contain atomic values and there should be no repeating groups or multiple values in a single cell."
