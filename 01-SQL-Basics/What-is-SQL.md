# 🗄️ What is SQL?

## 📌 Definition

**SQL (Structured Query Language)** is a standard **declarative language** used to communicate with and manage **relational databases**.

SQL is used to:

* Retrieve data
* Insert data
* Update data
* Delete data
* Create and modify database objects
* Control access
* Manage transactions

---

## 🗄️ What is a Relational Database?

A **relational database** stores data in **tables** consisting of rows and columns.

Example:

### employees

| employee_id | name  | department | salary |
| ----------: | ----- | ---------- | -----: |
|         101 | Rahul | IT         |  50000 |
|         102 | Priya | HR         |  60000 |

```text
Table
 ├── Row    → One record
 └── Column → One attribute
```

---

## 🔄 How SQL Works

```text
User / Application
        ↓
    SQL Query
        ↓
      RDBMS
        ↓
     Database
        ↓
      Result
```

Example:

```sql
SELECT name, salary
FROM employees
WHERE salary > 50000;
```

The query retrieves employees whose salary is greater than `50000`.

---

## 🧠 Why is SQL Declarative?

SQL tells the database **what we want**, not exactly **how to get it**.

```sql
SELECT name
FROM employees
WHERE salary > 50000;
```

We specify the required result.

The database decides how to execute the query efficiently.

---

## 🏗️ SQL vs RDBMS

| SQL                                | RDBMS                               |
| ---------------------------------- | ----------------------------------- |
| Language                           | Software                            |
| Used to communicate with databases | Used to store and manage databases  |
| Example: `SELECT`, `INSERT`        | Examples: MySQL, PostgreSQL, Oracle |

> **Remember:** SQL is the **language**; MySQL/PostgreSQL/Oracle are **database systems** that support SQL.

---

## 📋 SQL Command Categories

| Category | Purpose             | Common Commands                       |
| -------- | ------------------- | ------------------------------------- |
| DDL      | Define structure    | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` |
| DML      | Modify data         | `INSERT`, `UPDATE`, `DELETE`          |
| DQL      | Retrieve data       | `SELECT`                              |
| DCL      | Control permissions | `GRANT`, `REVOKE`                     |
| TCL      | Manage transactions | `COMMIT`, `ROLLBACK`, `SAVEPOINT`     |

Detailed explanation is covered in **SQL-Command-Types.md**.

---

# 🎯 Most Asked Interview Questions

### 1. What is SQL?

> SQL stands for Structured Query Language. It is a declarative language used to communicate with and manage data in relational databases.

---

### 2. Is SQL a programming language?

> SQL is generally considered a **declarative, domain-specific language**, specifically designed for working with relational databases.

---

### 3. Why is SQL called a declarative language?

> Because we specify **what result we want**, while the database determines **how to execute the query**.

---

### 4. What is the difference between SQL and RDBMS?

> SQL is a language used to interact with databases, whereas an RDBMS is software used to store and manage relational data.

---

### 5. What is a relational database?

> A relational database stores data in tables consisting of rows and columns, with relationships between tables established using keys.

---

### 6. What is an SQL query?

> An SQL query is a statement used to perform an operation on a database, such as retrieving or modifying data.

---

# ⚡ Quick Revision

```text
SQL
 ↓
Structured Query Language
 ↓
Declarative language
 ↓
Works mainly with relational databases
 ↓
Data → Tables → Rows + Columns
 ↓
Used to retrieve and manage data
```

### Remember

```text
SQL  → Language
RDBMS → Software
Table → Rows + Columns
Row → Record
Column → Attribute
```

> **Interview Definition:**
> **"SQL is a declarative, domain-specific language used to communicate with and manage data in relational databases."**
