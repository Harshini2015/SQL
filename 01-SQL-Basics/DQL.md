# 🔍 DQL — Data Query Language

## 📌 Definition

**DQL (Data Query Language)** is used to **retrieve data from a database**.

### Main Command

```sql
SELECT
```

---

# 1. SELECT

Used to retrieve data from one or more tables.

### Retrieve all columns

```sql
SELECT *
FROM employees;
```

### Retrieve specific columns

```sql
SELECT name, salary
FROM employees;
```

---

# 2. SELECT with WHERE

Used to retrieve only records that satisfy a condition.

```sql
SELECT name, salary
FROM employees
WHERE salary > 50000;
```

---

# 3. SELECT with ORDER BY

Used to sort the result.

```sql
SELECT name, salary
FROM employees
ORDER BY salary DESC;
```

`ASC` → Ascending

`DESC` → Descending

---

# 4. SELECT with DISTINCT

Used to remove duplicate values from the result.

```sql
SELECT DISTINCT department
FROM employees;
```

---

# 5. SELECT with LIMIT

Used to restrict the number of rows returned.

```sql
SELECT *
FROM employees
LIMIT 5;
```

> `LIMIT` syntax is supported by MySQL and several other databases, but is not universal SQL syntax.

---

# 🧩 Basic SELECT Structure

```sql
SELECT column1, column2
FROM table_name
WHERE condition
ORDER BY column1
LIMIT number;
```

Example:

```sql
SELECT name, salary
FROM employees
WHERE salary > 40000
ORDER BY salary DESC
LIMIT 3;
```

This:

1. Selects `name` and `salary`
2. Keeps employees with salary above `40000`
3. Sorts by salary from highest to lowest
4. Returns the first 3 rows

---

# 🎯 Most Asked Interview Questions

### 1. What is DQL?

> DQL stands for Data Query Language. It is used to retrieve data from a database. `SELECT` is the main DQL command.

---

### 2. Which command is used to retrieve data?

> `SELECT`.

---

### 3. What is the difference between `SELECT *` and selecting specific columns?

```sql
SELECT * FROM employees;
```

> Retrieves all columns.

```sql
SELECT name, salary FROM employees;
```

> Retrieves only the specified columns.

Selecting required columns is generally preferred because it avoids retrieving unnecessary data.

---

### 4. What does DISTINCT do?

> `DISTINCT` removes duplicate combinations of the selected columns from the result.

Example:

```sql
SELECT DISTINCT department
FROM employees;
```

---

### 5. What is the purpose of WHERE?

> `WHERE` filters rows based on a condition.

---

### 6. What is the purpose of ORDER BY?

> `ORDER BY` sorts the result in ascending or descending order.

---

### 7. What is the purpose of LIMIT?

> `LIMIT` restricts the number of rows returned by the query in databases such as MySQL.

---

# 🧠 Quick Revision

```text
DQL
 ↓
SELECT
 ↓
Retrieve data
```

### Remember

```text
SELECT   → Retrieve
WHERE    → Filter
DISTINCT → Remove duplicates
ORDER BY → Sort
LIMIT    → Restrict rows
```

> **Interview Definition:**
> **"DQL is used to retrieve data from a database, and SELECT is its primary command."**
