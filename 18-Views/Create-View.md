# 🛠️ CREATE VIEW

## 📌 Definition

`CREATE VIEW` is used to create a **virtual table based on a SQL query**.

---

# 💻 Syntax

```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;
```

---

# 📝 Example

Suppose we have:

### employees

|  id | name  | department | salary |
| --: | ----- | ---------- | -----: |
| 101 | Rahul | IT         |  50000 |
| 102 | Priya | HR         |  60000 |
| 103 | Amit  | IT         |  70000 |

Create a view containing only IT employees:

```sql
CREATE VIEW it_employees AS
SELECT id, name, salary
FROM employees
WHERE department = 'IT';
```

---

# 🔍 Query the View

```sql
SELECT *
FROM it_employees;
```

### Result

|  id | name  | salary |
| --: | ----- | -----: |
| 101 | Rahul |  50000 |
| 103 | Amit  |  70000 |

---

# 🔄 Replace a View

In MySQL:

```sql
CREATE OR REPLACE VIEW it_employees AS
SELECT id, name, salary
FROM employees
WHERE department = 'IT'
AND salary > 60000;
```

---

# 🗑️ Delete a View

```sql
DROP VIEW it_employees;
```

The view is removed, but the underlying table is not deleted.

---

# 🔐 View for Security

A view can expose only required columns.

```sql
CREATE VIEW employee_public AS
SELECT id, name, department
FROM employees;
```

The `salary` column is not exposed through this view.

---

# 🎯 Most Asked Interview Questions

### 1. How do you create a view?

> Use `CREATE VIEW view_name AS SELECT ...`.

### 2. How do you delete a view?

> Use `DROP VIEW view_name`.

### 3. Does dropping a view delete the original table?

> No. It only removes the view.

### 4. Can we modify an existing view?

> Yes. In MySQL, `CREATE OR REPLACE VIEW` can be used to replace its definition.

---

# 🧠 Quick Revision

```text
CREATE VIEW
     ↓
Saved SQL Query
     ↓
Virtual Table
     ↓
SELECT from View
```

> **Remember:**
> `CREATE VIEW` → Create | `SELECT` → Use | `DROP VIEW` → Remove
