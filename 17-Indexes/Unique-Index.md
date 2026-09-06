# 🔐 Unique Index

## 📌 Definition

A **unique index** ensures that the indexed column or combination of columns does not contain duplicate non-NULL values, subject to the database's NULL rules.

### Example

```sql
CREATE UNIQUE INDEX idx_email
ON employees(email);
```

Now duplicate email values are rejected.

---

## 💻 Example

```sql
INSERT INTO employees
VALUES (101, 'Rahul', 'rahul@gmail.com');

INSERT INTO employees
VALUES (102, 'Priya', 'rahul@gmail.com');
```

The second insert fails because the indexed `email` value must be unique.

---

# 🔑 UNIQUE Constraint vs Unique Index

A `UNIQUE` constraint expresses a **data-integrity rule**.

A unique index is an **index structure that enforces uniqueness**.

Example:

```sql
CREATE TABLE employees (
    id INT,
    email VARCHAR(100) UNIQUE
);
```

The database creates/enforces uniqueness using an appropriate unique index mechanism.

---

# 🎯 Most Asked Interview Questions

### 1. What is a unique index?

> A unique index prevents duplicate values in its indexed key.

### 2. Why use a unique index?

> To enforce uniqueness while also providing an index for efficient lookup.

### 3. Is a primary key unique?

> Yes. A primary key uniquely identifies each row and cannot contain NULL.

---

# 🧠 Quick Revision

```text
Unique Index
     ↓
No duplicate indexed values
     ↓
Supports efficient lookup
```

> **Memory Trick:**
> **UNIQUE = No duplicate key values**
