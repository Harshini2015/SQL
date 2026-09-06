# Second Normal Form (2NF)

## 📌 What is 2NF?

A table is in **Second Normal Form (2NF)** when:

1. It is already in **1NF**.
2. There is **no partial dependency**.

A non-key attribute must depend on the **whole primary key**, not just a part of it.

> Partial dependency mainly occurs when the table has a **composite primary key**.

---

## ❌ Example: Table Not in 2NF

### Student_Course

| Student_ID | Course_ID | Student_Name | Course_Name | Marks |
| ---------- | --------- | ------------ | ----------- | ----: |
| 101        | C01       | Rahul        | Java        |    85 |
| 101        | C02       | Rahul        | DBMS        |    90 |
| 102        | C01       | Priya        | Java        |    80 |

### Primary Key

The primary key is:

```text
(Student_ID, Course_ID)
```

because a student can enroll in multiple courses.

---

## 🔍 Dependencies

```text
Student_ID → Student_Name

Course_ID → Course_Name

(Student_ID, Course_ID) → Marks
```

### Problem

`Student_Name` depends only on `Student_ID`.

`Course_Name` depends only on `Course_ID`.

They do **not** depend on the complete composite key.

This is called **partial dependency**.

Therefore, the table is **NOT in 2NF** ❌.

---

## ✅ Convert to 2NF

We divide the table into three tables.

### 1. Student

| Student_ID | Student_Name |
| ---------- | ------------ |
| 101        | Rahul        |
| 102        | Priya        |

### 2. Course

| Course_ID | Course_Name |
| --------- | ----------- |
| C01       | Java        |
| C02       | DBMS        |

### 3. Enrollment

| Student_ID | Course_ID | Marks |
| ---------- | --------- | ----: |
| 101        | C01       |    85 |
| 101        | C02       |    90 |
| 102        | C01       |    80 |

Now:

```text
Student_ID → Student_Name

Course_ID → Course_Name

(Student_ID, Course_ID) → Marks
```

Every non-key attribute depends on the appropriate **whole key**.

Therefore, the tables satisfy **2NF** ✅.

---

## 🔑 Key Point

> **2NF removes partial dependency.**

### Easy way to remember

```text
1NF
 ↓
Remove partial dependency
 ↓
2NF
```

**2NF → Depend on the whole key**

---


> "Second Normal Form means the table should already be in 1NF and should not have partial dependency. Every non-key attribute must depend on the entire primary key."
