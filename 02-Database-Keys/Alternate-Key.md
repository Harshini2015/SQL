# 🔄 Alternate Key

## 📌 Definition

An **Alternate Key** (also known as a **Secondary Key**) is a Candidate Key that was **NOT chosen** as the Primary Key for a table.

---

## 🔑 Key Concepts

* **Unchosen Candidate:** A table can have multiple Candidate Keys. Once one is selected as the Primary Key, all remaining Candidate Keys become Alternate Keys.
* **Unique Identification:** Alternate Keys can uniquely identify records in a table just like a Primary Key.
* **Implementation:** Alternate Keys are usually implemented in SQL databases using the `UNIQUE` constraint.

---

## 💻 Syntax / Schema Example

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,               -- Primary Key
    email VARCHAR(100) UNIQUE NOT NULL,   -- Alternate Key
    phone VARCHAR(15) UNIQUE NOT NULL     -- Alternate Key
);
```

---

## 📝 Example

### `students` Table

| student_id | passport_no | email | name |
| ---------: | :---------- | :---- | :--- |
|        101 | A1234567    | rahul@domain.com | Rahul |
|        102 | B9876543    | priya@domain.com | Priya |

* **Candidate Keys:** `{student_id}`, `{passport_no}`, `{email}`
* **Chosen Primary Key:** `{student_id}`
* **Alternate Keys:** `{passport_no}`, `{email}`

---

## ⚖️ Important Difference: Primary Key vs Alternate Key

| Feature | Primary Key | Alternate Key |
| :--- | :--- | :--- |
| **Selection** | Selected as the main unique identifier | Unselected Candidate Keys |
| **Constraint** | Defined using `PRIMARY KEY` | Defined using `UNIQUE` constraint |
| **Limit per Table** | Exactly **1** per table | Can be multiple per table |
| **NULL Values** | Never allowed | Allowed unless defined `NOT NULL` |

---

# 🎯 Most Asked Interview Questions

### 1. What is an Alternate Key?
> An Alternate Key is a Candidate Key that is not selected as the Primary Key of a table.

---

### 2. How is an Alternate Key defined in SQL?
> In SQL, an Alternate Key is usually enforced by applying a `UNIQUE` constraint (and optional `NOT NULL`) to the column.

---

### 3. Can a table have multiple Alternate Keys?
> Yes. If a table has 4 Candidate Keys and 1 is chosen as the Primary Key, the remaining 3 are all Alternate Keys.

---

# 🧠 Quick Revision

```text
Candidate Keys
 ├── Primary Key   (Selected 1)
 └── Alternate Key (Remaining Candidate Keys)
```

> **Memory Trick:** `Alternate Key = Candidate Key - Primary Key`
