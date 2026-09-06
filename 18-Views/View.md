# 👁️ SQL View

## 📌 Definition

A **View** is a **virtual table** created from the result of a SQL query.

A view usually does **not store the actual data separately**. It stores the query definition and retrieves data from the underlying tables when queried.

---

## 💻 Example

Suppose we have:

### employees

|  id | name  | department | salary |
| --: | ----- | ---------- | -----: |
| 101 | Rahul | IT         |  50000 |
| 102 | Priya | HR         |  60000 |
| 103 | Amit  | IT         |  70000 |

Create a view:

```sql
CREATE VIEW it_employees AS
SELECT id, name, salary
FROM employees
WHERE department = 'IT';
```

Now we can query the view:

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

# 🔑 Why Use a View?

### 1. Simplify Complex Queries

Instead of repeatedly writing a complex query, create a view once.

### 2. Security

A view can expose only selected columns or rows.

```sql
CREATE VIEW employee_names AS
SELECT id, name
FROM employees;
```

Users can access the view without necessarily being given direct access to every column in the base table.

### 3. Reusability

The same query can be reused through the view.

---

# ⚠️ Important Points

* A view is based on one or more tables.
* A view can be queried like a table.
* A view does not normally store a separate copy of the underlying data.
* Changes in the underlying tables can be reflected when the view is queried.
* Some views can be updated, while others are not, depending on their definition and database rules.

---

# 🎯 Most Asked Interview Questions

### 1. What is a view?

> A view is a virtual table based on the result of a SQL query.

### 2. Why do we use views?

> Views are mainly used to simplify queries, improve security by restricting data exposure, and provide reusable query logic.

### 3. Does a view store data?

> A normal view generally stores the query definition rather than a separate copy of the data.

### 4. Can we query a view?

> Yes. A view can be queried using `SELECT` like a table.

### 5. Can a view be created using multiple tables?

> Yes. A view can be based on joins involving multiple tables.

---

# 🧠 Quick Revision

```text
View
 ↓
Virtual Table
 ↓
Based on SQL Query
 ↓
Simplifies queries
 ↓
Can restrict data exposure
```

> **Memory Trick:**
> **View = Saved Query + Virtual Table**
