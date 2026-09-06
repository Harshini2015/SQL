# 🏗️ DDL — Data Definition Language

## 📌 Definition

**DDL (Data Definition Language)** is used to **create, modify, and remove the structure of database objects** such as tables.

### Main DDL Commands

| Command    | Purpose                                  |
| ---------- | ---------------------------------------- |
| `CREATE`   | Creates a database object                |
| `ALTER`    | Modifies the structure                   |
| `DROP`     | Removes the object completely            |
| `TRUNCATE` | Removes all rows but keeps the structure |

---

# 1. CREATE

Used to create a database object such as a table.

### Syntax

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype
);
```

### Example

```sql
CREATE TABLE employees (
    employee_id INT,
    name VARCHAR(50),
    salary INT
);
```

---

# 2. ALTER

Used to **modify the structure** of an existing table.

### Add a column

```sql
ALTER TABLE employees
ADD department VARCHAR(50);
```

### Modify a column

```sql
ALTER TABLE employees
MODIFY salary DECIMAL(10,2);
```

### Rename a column

```sql
ALTER TABLE employees
RENAME COLUMN name TO employee_name;
```

---

# 3. DROP

Used to **completely remove a database object**.

```sql
DROP TABLE employees;
```

This removes:

* Table structure
* All rows
* Table definition

> ⚠️ After `DROP`, the table no longer exists.

---

# 4. TRUNCATE

Used to **remove all rows from a table while keeping the table structure**.

```sql
TRUNCATE TABLE employees;
```

After `TRUNCATE`:

```text
Rows       → Removed
Table      → Exists
Structure  → Exists
```

---

# 🔥 DROP vs TRUNCATE vs DELETE

This is a **very common interview question**.

| Feature                                | `DROP` | `TRUNCATE` | `DELETE`       |
| -------------------------------------- | ------ | ---------- | -------------- |
| Removes rows                           | ✅      | ✅          | ✅              |
| Removes table structure                | ✅      | ❌          | ❌              |
| `WHERE` allowed                        | ❌      | ❌          | ✅              |
| Removes selected rows                  | ❌      | ❌          | ✅              |
| Removes all rows                       | ✅      | ✅          | ✅              |
| DDL/DML*                               | DDL    | DDL        | DML            |
| Generally faster for removing all rows | —      | ✅          | Usually slower |

*Classification can vary by database system and documentation.

### Remember

```text
DROP      → Remove table
TRUNCATE  → Remove all rows
DELETE    → Remove selected rows
```

---

# 🎯 Most Asked Interview Questions

### 1. What is DDL?

> DDL stands for Data Definition Language. It is used to define and modify the structure of database objects.

---

### 2. What are the main DDL commands?

> `CREATE`, `ALTER`, `DROP`, and `TRUNCATE`.

---

### 3. Difference between DROP and TRUNCATE?

> `DROP` removes the table completely, including its structure. `TRUNCATE` removes all rows but keeps the table structure.

---

### 4. Difference between DELETE and TRUNCATE?

> `DELETE` can remove selected rows using `WHERE`, while `TRUNCATE` removes all rows and does not support `WHERE`.

---

### 5. Can we use WHERE with TRUNCATE?

> No. `TRUNCATE` always removes all rows.

---

### 6. Can we use WHERE with DROP?

> No. `DROP` removes the entire database object.

---

### 7. Which command removes the table structure?

> `DROP`.

---

### 8. Which command removes all records but keeps the table?

> `TRUNCATE`.

---

# 🧠 Quick Revision

```text
DDL
│
├── CREATE     → Create structure
├── ALTER      → Modify structure
├── DROP       → Remove structure + data
└── TRUNCATE   → Remove all rows
```

### One-line memory trick

> **DROP = Table gone | TRUNCATE = Data gone | DELETE = Selected data gone**
