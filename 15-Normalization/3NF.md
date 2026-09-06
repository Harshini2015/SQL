# 3️⃣ Third Normal Form (3NF)

## 📌 Definition

A table is in **Third Normal Form (3NF)** if:
1. It is already in **Second Normal Form (2NF)**.
2. It has **NO Transitive Dependencies** (no non-key attribute depends on another non-key attribute).

---

## 🔑 Key Concepts

* **Transitive Dependency:** Occurs when attribute $A$ determines non-key attribute $B$, and $B$ determines non-key attribute $C$ ($A \rightarrow B \rightarrow C$). Therefore, $C$ transitively depends on $A$.
* **3NF Rule Quote:** *"Every non-key attribute must depend on the key, the whole key, and nothing but the key."*

---

## 📝 Example: Converting 2NF to 3NF

### ❌ 2NF Table (Has Transitive Dependency)

Primary Key = `emp_id`

| emp_id | name  | dept_id | dept_name |
| -----: | :---- | ------: | :-------- |
|    101 | Rahul |      10 | IT        |
|    102 | Priya |      20 | HR        |

* `emp_id` $\rightarrow$ `dept_id`
* `dept_id` $\rightarrow$ `dept_name` (Non-key `dept_name` depends on non-key `dept_id`!)

---

### ✅ 3NF Solution (Decomposed into 2 Tables)

#### 1. `employees` Table (`emp_id` PK, `dept_id` FK)
| emp_id | name  | dept_id |
| -----: | :---- | ------: |
|    101 | Rahul |      10 |
|    102 | Priya |      20 |

#### 2. `departments` Table (`dept_id` PK)
| dept_id | dept_name |
| ------: | :-------- |
|      10 | IT        |
|      20 | HR        |

---

# 🎯 Most Asked Interview Questions

### 1. What is a transitive dependency in database normalization?
> A transitive dependency occurs when an attribute depends on a non-key attribute, which in turn depends on the primary key ($A \rightarrow B \rightarrow C$).

---

### 2. Explain the famous sentence describing 3NF.
> *"All attributes must depend on the key (1NF), the whole key (2NF), and nothing but the key (3NF)."*

---

# 🧠 Quick Revision

```text
2NF Table
 ↓
Check: Does non-key column C depend on non-key column B?
 ↓ (If Yes → Transitive Dependency Violation!)
Decompose into separate entity table
 ↓
3NF Table (NO Transitive Dependencies)
```

> **Memory Trick:** `3NF = 2NF + NO Transitive Dependencies (Non-key → Non-key)`
