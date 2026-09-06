# What is SQL?

## 📌 Definition

**SQL (Structured Query Language)** is a standard language used to **communicate with and manage relational databases**.

SQL is used to:

* Create databases and tables
* Insert data
* Retrieve data
* Update data
* Delete data
* Modify database structures
* Control access to data
* Manage transactions

---

## 🗄️ What is a Database?

A **database** is an organized collection of data that can be stored, accessed, and managed efficiently.

### Example

An employee database may contain:

| Employee_ID | Name  | Department | Salary |
| ----------: | ----- | ---------- | -----: |
|         101 | Rahul | IT         |  50000 |
|         102 | Priya | HR         |  45000 |
|         103 | Amit  | Finance    |  60000 |

SQL allows us to work with this data.

---

## 🔄 How SQL Works

A simple SQL interaction looks like:

```text
User / Application
        ↓
      SQL Query
        ↓
   Database System
        ↓
 Process the Query
        ↓
    Result / Data
```

### Example

```sql
SELECT * 
FROM employees;
```

This query asks the database to return all records from the `employees` table.

---

# 🧩 What Can We Do Using SQL?

## 1. Create a Table

```sql
CREATE TABLE employees (
    employee_id INT,
    name VARCHAR(50),
    department VARCHAR(50),
    salary DECIMAL(10,2)
);
```

---

## 2. Insert Data

```sql
INSERT INTO employees
(employee_id, name, department, salary)
VALUES
(101, 'Rahul', 'IT', 50000);
```

---

## 3. Retrieve Data

```sql
SELECT *
FROM employees;
```

---

## 4. Update Data

```sql
UPDATE employees
SET salary = 55000
WHERE employee_id = 101;
```

---

## 5. Delete Data

```sql
DELETE FROM employees
WHERE employee_id = 101;
```

---

# 🏗️ SQL and Relational Databases

SQL is primarily used with **relational database management systems (RDBMS)**.

Popular RDBMS products include:

* MySQL
* PostgreSQL
* Oracle Database
* Microsoft SQL Server
* SQLite

These systems use tables to organize related data.

---

# 📊 Basic Database Terminology

| Term        | Meaning                                      |
| ----------- | -------------------------------------------- |
| Database    | Collection of organized data                 |
| Table       | Collection of related records                |
| Row         | A single record                              |
| Column      | An attribute/field                           |
| Primary Key | Uniquely identifies a row                    |
| Foreign Key | Links one table to another                   |
| Query       | Request made to the database                 |
| RDBMS       | Software used to manage relational databases |

### Example

```text
employees
│
├── employee_id   → Column
├── name          → Column
├── department    → Column
└── salary        → Column

101, Rahul, IT, 50000 → Row
```

---

# 🔥 Why is SQL Important?

SQL is important because it allows developers to interact directly with application data.

For example, in a web application:

```text
Frontend
   ↓
Backend
   ↓
SQL Query
   ↓
Database
   ↓
Result
   ↓
Backend
   ↓
Frontend
```

A Java application, for example, can use **JDBC** to send SQL queries to a database.

---

# ⚡ SQL Characteristics

### 1. Declarative Language

SQL mainly describes **what data you want**, rather than exactly how the database should retrieve it.

Example:

```sql
SELECT name
FROM employees
WHERE salary > 50000;
```

We specify what we want; the database determines how to execute the query.

### 2. Used for Data Manipulation

SQL can retrieve, insert, update, and delete data.

### 3. Used for Database Definition

SQL can create and modify database objects such as tables.

### 4. Supports Security

SQL provides commands for controlling access and permissions.

### 5. Supports Transactions

SQL supports transaction operations such as:

```sql
COMMIT;
ROLLBACK;
SAVEPOINT;
```

---

# 📝 Simple Example

Suppose we have:

### employees

| employee_id | name  | salary |
| ----------: | ----- | -----: |
|         101 | Rahul |  50000 |
|         102 | Priya |  65000 |
|         103 | Amit  |  45000 |

Query:

```sql
SELECT name, salary
FROM employees
WHERE salary > 50000;
```

### Output

| name  | salary |
| ----- | -----: |
| Priya |  65000 |

---

# 🎯 Common Interview Questions

### 1. What is SQL?

**Answer:**

> SQL stands for Structured Query Language. It is a standard language used to communicate with and manage data in relational databases.

---

### 2. Is SQL a programming language?

**Answer:**

> SQL is generally considered a declarative or domain-specific language rather than a general-purpose programming language. It is specifically designed for working with relational databases.

---

### 3. What is a database?

**Answer:**

> A database is an organized collection of data that can be stored, accessed, and managed efficiently.

---

### 4. What is a table?

**Answer:**

> A table is a collection of related data organized into rows and columns.

---

### 5. What is a row?

**Answer:**

> A row represents a single record in a table.

---

### 6. What is a column?

**Answer:**

> A column represents an attribute or field of the data stored in a table.

---

### 7. What is an SQL query?

**Answer:**

> An SQL query is a statement used to perform an operation on a database, such as retrieving, inserting, updating, or deleting data.

---

### 8. What is RDBMS?

**Answer:**

> RDBMS stands for Relational Database Management System. It is software used to store and manage data in related tables using relational concepts.

Examples include MySQL, PostgreSQL, Oracle Database, and SQL Server.

---



Remember these five points:

```text
SQL
 ↓
Structured Query Language
 ↓
Used with relational databases
 ↓
Works mainly with tables
 ↓
Used to create, retrieve, modify and manage data
```


> **"SQL is a declarative, domain-specific language used to communicate with and manage data in relational databases."**
