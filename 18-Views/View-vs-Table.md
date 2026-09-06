# 🆚 View vs Table

## 📌 Basic Difference

A **table** physically stores data.

A **view** is a virtual table based on a SQL query.

---

## 📊 Difference

| Feature                      | Table                | View                       |
| ---------------------------- | -------------------- | -------------------------- |
| Stores data                  | Yes                  | Usually no separate copy   |
| Physical storage             | Stores rows          | Stores query definition    |
| Based on                     | Directly stores data | One or more tables/queries |
| Can contain data directly    | Yes                  | No                         |
| Used for security            | Possible             | Very useful                |
| Can simplify complex queries | No                   | Yes                        |

---

## 💻 Example

### Table

```sql
CREATE TABLE employees (
    id INT,
    name VARCHAR(50),
    salary INT
);
```

### View

```sql
CREATE VIEW high_salary AS
SELECT id, name, salary
FROM employees
WHERE salary > 50000;
```

---

# 🎯 Most Asked Interview Questions

### 1. What is the difference between a table and a view?

> A table stores data physically, while a view is a virtual table based on a SQL query.

### 2. Which is better, table or view?

> They serve different purposes. Tables store data, while views simplify queries and can restrict data exposure.

### 3. Does a view contain a copy of table data?

> A normal view generally does not store a separate copy of the data.

---

# 🧠 Quick Revision

```text
TABLE → Stores data
VIEW  → Stores query definition
```

> **Memory Trick:** **Table = Data | View = Query**
