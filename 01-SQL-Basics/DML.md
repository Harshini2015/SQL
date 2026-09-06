# 📝 DML — Data Manipulation Language

## 📌 Definition

**DML (Data Manipulation Language)** is used to **insert, modify, and delete data** stored in database tables.

### Main DML Commands

| Command  | Purpose                   |
| -------- | ------------------------- |
| `INSERT` | Adds new records          |
| `UPDATE` | Modifies existing records |
| `DELETE` | Removes records           |

---

# 1. INSERT

Used to add new records to a table.

### Syntax

```sql
INSERT INTO table_name (column1, column2)
VALUES (value1, value2);
```

### Example

```sql
INSERT INTO employees (employee_id, name, salary)
VALUES (101, 'Rahul', 50000);
```

### Insert multiple rows

```sql
INSERT INTO employees (employee_id, name, salary)
VALUES
(102, 'Priya', 60000),
(103, 'Amit', 55000);
```

---

# 2. UPDATE

Used to modify existing records.

### Syntax

```sql
UPDATE table_name
SET column = value
WHERE condition;
```

### Example

```sql
UPDATE employees
SET salary = 55000
WHERE employee_id = 101;
```

Only employee `101` is updated.

> ⚠️ **Important:** Always be careful with `UPDATE` without a `WHERE` clause.

```sql
UPDATE employees
SET salary = 55000;
```

This updates **every row** in the table.

---

# 3. DELETE

Used to remove records from a table.

### Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

### Example

```sql
DELETE FROM employees
WHERE employee_id = 101;
```

Only employee `101` is deleted.

### Delete all rows

```sql
DELETE FROM employees;
```

This removes all records but keeps the table structure.

---

# 🔥 DELETE vs TRUNCATE

| Feature               | `DELETE` | `TRUNCATE` |
| --------------------- | -------- | ---------- |
| Type                  | DML      | DDL*       |
| Removes rows          | ✅        | ✅          |
| `WHERE` allowed       | ✅        | ❌          |
| Removes selected rows | ✅        | ❌          |
| Keeps table structure | ✅        | ✅          |
| Removes all rows      | ✅        | ✅          |

*Classification can vary by database system.

---

# 🎯 Most Asked Interview Questions

### 1. What is DML?

> DML stands for Data Manipulation Language. It is used to insert, update, and delete data in database tables.

---

### 2. What are the DML commands?

> `INSERT`, `UPDATE`, and `DELETE`.

---

### 3. What is the difference between DELETE and TRUNCATE?

> `DELETE` can remove selected rows using `WHERE`, whereas `TRUNCATE` removes all rows and does not support `WHERE`.

---

### 4. What happens if WHERE is omitted in UPDATE?

```sql
UPDATE employees
SET salary = 50000;
```

> The update is applied to **all rows** in the table.

---

### 5. What happens if WHERE is omitted in DELETE?

```sql
DELETE FROM employees;
```

> **All rows** are deleted, but the table structure remains.

---

### 6. Can DELETE remove the table?

> No. `DELETE` removes rows, not the table structure.

---

### 7. Can INSERT insert multiple rows?

> Yes.

```sql
INSERT INTO employees (employee_id, name)
VALUES
(101, 'Rahul'),
(102, 'Priya');
```

---

# 🧠 Quick Revision

```text
DML
│
├── INSERT → Add data
├── UPDATE → Modify data
└── DELETE → Remove data
```

### Remember

```text
INSERT → Add
UPDATE → Change
DELETE → Remove
```

> **Interview Tip:** The most important DML interview area is understanding `INSERT`, `UPDATE`, `DELETE` and the effect of omitting `WHERE`.
