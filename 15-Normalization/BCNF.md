# 🏅 Boyce-Codd Normal Form (BCNF / 3.5NF)

## 📌 Definition

**Boyce-Codd Normal Form (BCNF)**, also referred to as **3.5NF**, is a stricter version of 3NF designed to address anomalies in tables with multiple overlapping candidate keys.

---

## 🔑 Key Rule

A table is in **BCNF** if and only if for **every functional dependency $X \rightarrow Y$**, **$X$ is a Super Key** (or Candidate Key).

$$\text{For every } X \rightarrow Y \implies X \text{ MUST be a Super Key}$$

---

## ⚖️ Important Difference: 3NF vs BCNF

| Feature | 3NF | BCNF |
| :--- | :--- | :--- |
| **Strictness** | Slightly relaxed | **Stricter** |
| **Condition for $X \rightarrow Y$** | $X$ is a Super Key **OR** $Y$ is a Prime Attribute | **$X$ MUST be a Super Key** (No exceptions!) |
| **Overlapping Candidate Keys** | May permit anomalies | Eliminates all anomalies from candidate keys |

---

## 📝 Example

### ❌ 3NF Table (Not in BCNF)

Schema: `Student_Advisor(student_id, subject, advisor)`
* Candidate Keys: `(student_id, subject)`
* Functional Dependencies:
  1. `(student_id, subject) -> advisor`
  2. `advisor -> subject`

> **Problem:** In $advisor \rightarrow subject$, $advisor$ determines $subject$, but $advisor$ is **NOT a Super Key**! This table is in 3NF (because $subject$ is a prime attribute), but **violates BCNF**.

---

### ✅ BCNF Solution

Decompose into 2 tables:
1. `Advisor_Subject(advisor, subject)` — `advisor` is PK.
2. `Student_Advisor(student_id, advisor)` — `(student_id, advisor)` is PK.

---

# 🎯 Most Asked Interview Questions

### 1. What is BCNF in database normalization?
> BCNF (Boyce-Codd Normal Form) requires that for every functional dependency $X \rightarrow Y$, the determinant $X$ must be a Super Key.

---

### 2. Is BCNF stricter than 3NF?
> Yes. BCNF removes the 3NF exception where $Y$ could be a prime attribute, making $X$ strictly required to be a Super Key for every functional dependency.

---

# 🧠 Quick Revision

```text
3NF Table
 ↓
Check: For every X → Y, is X a Super Key?
 ↓ (If No → BCNF Violation!)
Decompose Table
 ↓
BCNF (Every determinant X MUST be a Super Key)
```

> **Memory Trick:** `BCNF = For X → Y, X MUST be a Super Key!`
