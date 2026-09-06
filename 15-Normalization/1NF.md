# 1️⃣ First Normal Form (1NF)

## 📌 Definition

A table is in **First Normal Form (1NF)** if every column contains **atomic (indivisible) values** and there are **no repeating groups or comma-separated lists** stored within a single cell.

---

## 🔑 Key Rules for 1NF

1. **Atomic Values:** Each cell must contain a single, non-decomposable value.
2. **No Repeating Groups:** Multi-valued attributes (e.g. storing multiple phone numbers or courses in one cell) are prohibited.
3. **Unique Column Names:** Each column in the table must have a distinct name.
4. **Primary Key Defined:** Table must have a primary key to uniquely identify each record.

---

## 📝 Example: Converting Non-1NF to 1NF

### ❌ Non-1NF Table (Violates 1NF due to multi-valued `courses` cell)

| student_id | name  | courses |
| ---------: | :---- | :------ |
|        101 | Rahul | Java, SQL, Python |
|        102 | Priya | SQL, HTML |

---

### ✅ 1NF Table (Atomic values per cell)

| student_id | name  | course |
| ---------: | :---- | :----- |
|        101 | Rahul | Java   |
|        101 | Rahul | SQL    |
|        101 | Rahul | Python |
|        102 | Priya | SQL    |
|        102 | Priya | HTML   |

---

# 🎯 Most Asked Interview Questions

### 1. What makes a table satisfy First Normal Form (1NF)?
> A table is in 1NF if all column values are atomic (single indivisible values) and there are no repeating groups or array values in any cell.

---

### 2. Why is storing comma-separated values (e.g. `'Java, SQL'`) in a single column a bad design?
> It violates 1NF, prevents database indexing, makes searching/filtering with `LIKE` slow and prone to errors, and complicates foreign key enforcement.

---

# 🧠 Quick Revision

```text
Non-1NF (Multi-valued cells: 'Java, SQL')
       ↓
    Atomize values
       ↓
1NF (1 Value per cell + Primary Key)
```

> **Memory Trick:** `1NF = Atomic Values Only (No comma-separated lists!)`
