# 🎯 Candidate Key

## 📌 Definition

A **Candidate Key** is a column (or minimal set of columns) that can uniquely identify any database record without introducing unnecessary columns.

---

## 🔑 Key Concepts

* **Eligible for Primary Key:** All candidate keys are eligible to be chosen as the table's Primary Key.
* **Minimality:** A Candidate Key is a **Super Key** with no redundant attributes (minimal super key).
* **Multiple Candidate Keys:** A table can have **multiple** candidate keys.
* **Primary Key & Alternate Keys:**
  * **1 Candidate Key** is selected as the **Primary Key**.
  * The **remaining Candidate Keys** become **Alternate Keys**.

---

## 💻 Syntax / Schema Example

```sql
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    email VARCHAR(100) UNIQUE NOT NULL,
    ssn VARCHAR(11) UNIQUE NOT NULL,
    name VARCHAR(50)
);
```

In this table:
* Candidate Keys = `{user_id}`, `{email}`, `{ssn}`
* Selected Primary Key = `{user_id}`
* Alternate Keys = `{email}`, `{ssn}`

---

## 📝 Example

### `students` Table

| student_id | roll_no | email | name |
| ---------: | ------: | :---- | :--- |
|          1 |     101 | rahul@gmail.com | Rahul |
|          2 |     102 | priya@gmail.com | Priya |

* `{student_id}` can uniquely identify a student.
* `{roll_no}` can uniquely identify a student.
* `{email}` can uniquely identify a student.

Therefore, `{student_id}`, `{roll_no}`, and `{email}` are **Candidate Keys**.

---

## ⚖️ Important Difference: Candidate Key vs Super Key vs Primary Key

| Key Type | Minimality | Limit per Table | Role |
| :--- | :--- | :--- | :--- |
| **Super Key** | May contain extra unnecessary columns | Many | Any set of columns ensuring uniqueness |
| **Candidate Key** | Minimal set of columns (no redundancy) | One or Many | Qualified candidates for Primary Key |
| **Primary Key** | Minimal set chosen from Candidate Keys | Exactly **1** | The chosen primary unique identifier |

---

# 🎯 Most Asked Interview Questions

### 1. What is a Candidate Key?
> A Candidate Key is a minimal Super Key that uniquely identifies each record in a table without any redundant attributes.

---

### 2. Can a table have multiple Candidate Keys?
> Yes. A table can have multiple Candidate Keys, but only one of them will be chosen as the Primary Key.

---

### 3. What is the relation between Candidate Key, Super Key, and Primary Key?
> Every Candidate Key is a Super Key, but not every Super Key is a Candidate Key (due to minimality). The Primary Key is simply one candidate key chosen by the database designer.

---

### 4. What happens to Candidate Keys that are not chosen as the Primary Key?
> Candidate Keys not selected as the Primary Key are known as **Alternate Keys** (or Secondary Keys).

---

# 🧠 Quick Revision

```text
Super Keys (All unique combinations)
 ↓ (Apply Minimality)
Candidate Keys (Minimal unique sets)
 ├── Chosen one → Primary Key
 └── Remaining  → Alternate Keys
```

> **Memory Trick:** `Candidate Key = Minimal Super Key`
