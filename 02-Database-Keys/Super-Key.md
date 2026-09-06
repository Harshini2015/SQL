# 🦸 Super Key

## 📌 Definition

A **Super Key** is a set of one or more attributes (columns) that uniquely identifies a row (record) in a database table.

---

## 🔑 Key Concepts

* **Uniqueness:** Guarantees that no two rows share the exact same combination of super key values.
* **May Contain Extra Attributes:** Unlike a Candidate Key, a Super Key **can contain redundant attributes** that are not strictly necessary for unique identification.
* **Superset of Candidate Key:** Every Candidate Key is a Super Key, but not every Super Key is a Candidate Key.

---

## 📝 Example

### `employees` Table

| emp_id | email | name | department |
| -----: | :---- | :--- | :--------- |
|    101 | rahul@tech.com | Rahul | IT |
|    102 | priya@tech.com | Priya | HR |

Since `{emp_id}` and `{email}` are unique:

### Valid Super Keys:
1. `{emp_id}` *(Minimal → also a Candidate Key)*
2. `{email}` *(Minimal → also a Candidate Key)*
3. `{emp_id, name}` *(Contains redundant column `name`)*
4. `{emp_id, department}` *(Contains redundant column `department`)*
5. `{email, name}` *(Contains redundant column `name`)*
6. `{emp_id, email, name, department}` *(Contains all columns)*

---

## ⚖️ Important Difference: Super Key vs Candidate Key

| Feature | Super Key | Candidate Key |
| :--- | :--- | :--- |
| **Definition** | Any set of attributes uniquely identifying a row | A **minimal** set of attributes uniquely identifying a row |
| **Redundant Columns** | Allowed | NOT allowed |
| **Relationship** | All Candidate Keys are Super Keys | Only minimal Super Keys are Candidate Keys |
| **Number per Table** | Usually very large number of combinations | Limited number of minimal attributes |

---

# 🎯 Most Asked Interview Questions

### 1. What is a Super Key?
> A Super Key is any single column or combination of columns that uniquely identifies a row in a table. It may include extra non-essential columns.

---

### 2. Is Primary Key a Super Key?
> Yes. Since a Primary Key uniquely identifies a row, it is both a Candidate Key and a Super Key.

---

### 3. What is the difference between a Super Key and a Candidate Key?
> A Candidate Key is a minimal Super Key with no redundant attributes. A Super Key can contain additional redundant attributes.

---

# 🧠 Quick Revision

```text
All Unique Column Combinations
 ↓
SUPER KEYS
 ↓ (Remove redundant columns)
CANDIDATE KEYS
 ↓ (Select best one)
PRIMARY KEY
```

> **Memory Trick:** `Super Key = Unique Identification (Redundancy Allowed)`
