# 🆚 Clustered vs Non-Clustered Index

## 📌 Clustered Index

A **clustered index** determines the physical/order organization of table data according to the indexed key, depending on the database system.

In **MySQL InnoDB**, the table's data is organized according to the **primary key**, which is the clustered index.

---

## 📌 Non-Clustered Index

A **non-clustered index** is a separate index structure that stores indexed values and references to the corresponding table records.

In MySQL InnoDB, secondary indexes contain the indexed columns and the primary key value used to locate the row.

---

# 📊 Difference

| Feature           | Clustered                                     | Non-Clustered            |
| ----------------- | --------------------------------------------- | ------------------------ |
| Data organization | Determines organization of table data         | Separate index structure |
| Number            | Generally one per table                       | Multiple possible        |
| MySQL InnoDB      | Primary key is clustered                      | Secondary indexes        |
| Storage           | Table data is associated with clustered index | Separate index structure |

> **Important:** The exact implementation differs between database systems.

---

# 🎯 Most Asked Interview Questions

### 1. What is a clustered index?

> A clustered index determines how table data is organized according to the index key.

### 2. How many clustered indexes can a table have?

> Generally, a table can have only one clustered index because the table data can have only one physical organization.

### 3. Can a table have multiple non-clustered indexes?

> Yes. A table can have multiple secondary/non-clustered indexes.

### 4. What is the clustered index in MySQL InnoDB?

> In InnoDB, the primary key is the clustered index.

---

# 🧠 Quick Revision

```text
Clustered
→ Table data organized around index
→ One

Non-Clustered
→ Separate index structure
→ Multiple
```

> **Memory Trick:**
> **Clustered = Data organization | Non-Clustered = Separate index**
