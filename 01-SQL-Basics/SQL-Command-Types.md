# 🧩 SQL Command Types

## 📌 Definition

SQL commands are divided into **5 main categories** based on what they are used for:

```text
DDL → Structure
DML → Data
DQL → Retrieve
DCL → Permissions
TCL → Transactions
```

---

# 1. 🏗️ DDL — Data Definition Language

DDL is used to **define and modify the structure** of database objects such as tables.

### Commands

* `CREATE`
* `ALTER`
* `DROP`
* `TRUNCATE`

### Example

```sql
CREATE TABLE employees (
    id INT,
    name VARCHAR(50)
);
```

```sql
ALTER TABLE employees
ADD salary INT;
```

---

# 2. 📝 DML — Data Manipulation Language

DML is used to **insert, modify, and delete data** in tables.

### Commands

* `INSERT`
* `UPDATE`
* `DELETE`

### Example

```sql
INSERT INTO employees
VALUES (101, 'Rahul', 50000);
```

```sql
UPDATE employees
SET salary = 55000
WHERE id = 101;
```

```sql
DELETE FROM employees
WHERE id = 101;
```

---

# 3. 🔍 DQL — Data Query Language

DQL is used to **retrieve data** from the database.

### Command

* `SELECT`

### Example

```sql
SELECT *
FROM employees;
```

---

# 4. 🔐 DCL — Data Control Language

DCL is used to **control access and permissions**.

### Commands

* `GRANT`
* `REVOKE`

### Example

```sql
GRANT SELECT
ON employees
TO user1;
```

```sql
REVOKE SELECT
ON employees
FROM user1;
```

---

# 5. 🔄 TCL — Transaction Control Language

TCL is used to **manage transactions**.

### Commands

* `COMMIT`
* `ROLLBACK`
* `SAVEPOINT`

### Example

```sql
UPDATE employees
SET salary = 60000
WHERE id = 101;

COMMIT;
```

To undo an uncommitted transaction:

```sql
ROLLBACK;
```

---

# 📊 DDL vs DML vs DQL vs DCL vs TCL

| Type | Full Form                    | Purpose       | Commands                              |
| ---- | ---------------------------- | ------------- | ------------------------------------- |
| DDL  | Data Definition Language     | Structure     | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` |
| DML  | Data Manipulation Language   | Modify data   | `INSERT`, `UPDATE`, `DELETE`          |
| DQL  | Data Query Language          | Retrieve data | `SELECT`                              |
| DCL  | Data Control Language        | Permissions   | `GRANT`, `REVOKE`                     |
| TCL  | Transaction Control Language | Transactions  | `COMMIT`, `ROLLBACK`, `SAVEPOINT`     |

---

# 🎯 Most Asked Interview Questions

### 1. What are the different types of SQL commands?

> The main categories are DDL, DML, DQL, DCL, and TCL.

---

### 2. What is DDL?

> DDL is used to define and modify the structure of database objects. Examples are `CREATE`, `ALTER`, `DROP`, and `TRUNCATE`.

---

### 3. What is DML?

> DML is used to insert, update, and delete data. Examples are `INSERT`, `UPDATE`, and `DELETE`.

---

### 4. What is DQL?

> DQL is used to retrieve data from the database. The main command is `SELECT`.

---

### 5. What is DCL?

> DCL is used to control database permissions. The commands are `GRANT` and `REVOKE`.

---

### 6. What is TCL?

> TCL is used to manage database transactions. Common commands are `COMMIT`, `ROLLBACK`, and `SAVEPOINT`.

---

### 7. Which command is used to retrieve data?

> `SELECT`

---

### 8. Which command is used to remove a table completely?

> `DROP TABLE`

---

### 9. Which command removes all rows but keeps the table structure?

> `TRUNCATE`

---

# 🧠 Quick Revision

```text
DDL → Structure → CREATE, ALTER, DROP, TRUNCATE

DML → Data      → INSERT, UPDATE, DELETE

DQL → Retrieve  → SELECT

DCL → Permission → GRANT, REVOKE

TCL → Transaction → COMMIT, ROLLBACK, SAVEPOINT
```

> **Memory Trick:**
> **DDL = Define | DML = Modify | DQL = Query | DCL = Control | TCL = Transaction**
