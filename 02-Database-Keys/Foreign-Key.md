# 🔗 Foreign Key

## 📌 Definition

A **Foreign Key** is a column (or a set of columns) in one table that refers to the **Primary Key** (or Unique Key) of another table, establishing a relationship between the two tables.

---

## 🔑 Key Concepts

* **Referential Integrity:** Ensures that relationships between rows in two tables remain valid and data stays consistent.
* **Parent & Child Table:**
  * **Parent Table (Referenced):** Table containing the Primary Key.
  * **Child Table (Referencing):** Table containing the Foreign Key.
* **Allows NULLs:** Unlike Primary Keys, Foreign Keys **can** contain `NULL` values unless defined with `NOT NULL`.
* **Multiple Foreign Keys:** A table can have **multiple** Foreign Keys.

---

## 💻 Syntax

### 1. Creating Table with Foreign Key
```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    order_date DATE,
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

### 2. Adding Foreign Key with Referential Actions (`ON DELETE CASCADE`)
```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
    ON DELETE CASCADE
    ON UPDATE CASCADE
);
```

### 3. Common `ON DELETE` Options
* **`RESTRICT` / `NO ACTION` (Default):** Prevents deletion of parent row if child rows exist.
* **`CASCADE`:** Deletes matching rows in child table when parent row is deleted.
* **`SET NULL`:** Sets Foreign Key column in child table to `NULL` when parent row is deleted.

---

## 📝 Example

### Parent Table: `departments`
| dept_id | dept_name |
| ------: | :-------- |
|      10 | IT        |
|      20 | HR        |

### Child Table: `employees`
| emp_id | name  | dept_id (FK) |
| -----: | :---- | -----------: |
|    101 | Rahul |           10 |
|    102 | Priya |           20 |
|    103 | Amit  |         NULL |

* `dept_id` in `employees` references `dept_id` in `departments`.
* Employee 103 has `NULL` for `dept_id`, which is valid.
* Inserting `dept_id = 99` in `employees` will fail because `99` does not exist in `departments`.

---

## ⚖️ Important Difference: Primary Key vs Foreign Key

| Feature | Primary Key | Foreign Key |
| :--- | :--- | :--- |
| **Purpose** | Uniquely identifies a record in a table | Links two tables and enforces referential integrity |
| **NULL Values** | Cannot be `NULL` | Can be `NULL` (unless restricted) |
| **Duplicate Values** | Cannot contain duplicates | Can contain duplicates (multiple orders per customer) |
| **Limit per Table** | Maximum **1** per table | Multiple foreign keys allowed per table |
| **Referenced By** | Referenced by Foreign Key in child table | References Primary/Unique Key in parent table |

---

# 🎯 Most Asked Interview Questions

### 1. What is a Foreign Key?
> A Foreign Key is a field in a table that references the Primary Key of another table, maintaining referential integrity between the two tables.

---

### 2. Can a Foreign Key contain NULL values?
> Yes, a Foreign Key can contain `NULL` values, representing an unassigned or optional relationship (unless configured with `NOT NULL`).

---

### 3. Can a table have multiple Foreign Keys?
> Yes, a table can have multiple Foreign Keys linking it to different parent tables.

---

### 4. What is `ON DELETE CASCADE`?
> `ON DELETE CASCADE` ensures that when a row in the parent table is deleted, all matching child rows referencing that parent row are automatically deleted.

---

### 5. What is Referential Integrity?
> Referential Integrity is a database concept ensuring that relationships between tables remain consistent; a Foreign Key value must either match an existing Primary Key value in the parent table or be `NULL`.

---

# 🧠 Quick Revision

```text
Foreign Key
 ↓
References Primary Key of Parent Table
 ↓
Maintains Referential Integrity
 ↓
Can contain Duplicate and NULL values
 ↓
ON DELETE options: RESTRICT | CASCADE | SET NULL
```

> **Memory Trick:** `Parent Table (PK) ← Child Table (FK)`
