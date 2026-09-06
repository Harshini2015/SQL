# 2️⃣ Second Normal Form (2NF)

## 📌 Definition

A table is in **Second Normal Form (2NF)** if:
1. It is already in **First Normal Form (1NF)**.
2. It has **NO Partial Dependencies** (every non-key attribute must be **fully functionally dependent** on the primary key).

---

## 🔑 Key Concepts

* **Partial Dependency:** Occurs when a non-key column depends on only *part* of a composite primary key rather than the entire key.
* **Single-Column Primary Key Rule:** If a table is in 1NF and its primary key consists of a **single column**, the table is **automatically in 2NF** (since partial key dependencies are impossible).

---

## 📝 Example: Converting 1NF to 2NF

### ❌ 1NF Table (Has Partial Dependency)

Primary Key = `(student_id, course_id)` (Composite Primary Key)

| student_id | course_id | student_name | course_fee |
| ---------: | --------: | :----------- | ---------: |
|        101 |       C01 | Rahul        |       5000 |
|        101 |       C02 | Rahul        |       6000 |

* `student_name` depends **only on `student_id`** (Partial dependency!).
* `course_fee` depends **only on `course_id`** (Partial dependency!).

---

### ✅ 2NF Solution (Decomposed into 3 Tables)

#### 1. `Students` Table (`student_id` PK)
| student_id | student_name |
| ---------: | :----------- |
|        101 | Rahul        |

#### 2. `Courses` Table (`course_id` PK)
| course_id | course_fee |
| :-------- | ---------: |
| C01       |       5000 |
| C02       |       6000 |

#### 3. `Student_Courses` Mapping Table (`(student_id, course_id)` Composite PK)
| student_id | course_id |
| ---------: | :-------- |
|        101 | C01       |
|        101 | C02       |

---

# 🎯 Most Asked Interview Questions

### 1. What is a partial dependency in 2NF?
> A partial dependency occurs when a non-key attribute depends on only a portion of a composite primary key rather than the complete key.

---

### 2. Is a table with a single-column primary key always in 2NF?
> Yes. If a table is in 1NF and has a single-column primary key, partial dependencies are impossible, so it is automatically in 2NF.

---

# 🧠 Quick Revision

```text
1NF Table (Composite Key: A + B)
       ↓
Check: Does non-key column C depend on ONLY A?
       ↓ (If Yes → Partial Dependency Violation!)
Decompose Table
       ↓
2NF Table (Full Functional Dependency)
```

> **Memory Trick:** `2NF = 1NF + NO Partial Dependencies`
