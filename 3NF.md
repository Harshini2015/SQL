# Third Normal Form (3NF)

## 📌 What is 3NF?

A table is in **Third Normal Form (3NF)** when:

1. It is already in **2NF**.
2. There is **no transitive dependency**.

A non-key attribute should not depend on another non-key attribute.

---

## ❌ Example: Table Not in 3NF

### Employee

| Employee_ID | Employee_Name | Department_ID | Department_Name |
| ----------- | ------------- | ------------- | --------------- |
| 101         | Rahul         | D01           | IT              |
| 102         | Priya         | D02           | HR              |
| 103         | Amit          | D01           | IT              |

### Primary Key

```text
Employee_ID
```

---

## 🔍 Dependencies

```text
Employee_ID → Employee_Name

Employee_ID → Department_ID

Department_ID → Department_Name
```

Therefore:

```text
Employee_ID
     ↓
Department_ID
     ↓
Department_Name
```

`Department_Name` depends on `Department_ID`, which is a non-key attribute.

This is called **transitive dependency**.

Therefore, the table is **NOT in 3NF** ❌.

---

## ✅ Convert to 3NF

We separate the department information.

### 1. Employee

| Employee_ID | Employee_Name | Department_ID |
| ----------- | ------------- | ------------- |
| 101         | Rahul         | D01           |
| 102         | Priya         | D02           |
| 103         | Amit          | D01           |

### 2. Department

| Department_ID | Department_Name |
| ------------- | --------------- |
| D01           | IT              |
| D02           | HR              |

Now the dependencies are:

```text
Employee_ID → Employee_Name

Employee_ID → Department_ID

Department_ID → Department_Name
```

The department information is stored separately.

There is no transitive dependency within the Employee table.

Therefore, the database design satisfies **3NF** ✅.

---

## 🔑 Key Point

> **3NF removes transitive dependency.**

### Easy way to remember

```text
2NF
 ↓
Remove transitive dependency
 ↓
3NF
```

**3NF → Depend on nothing but the key**

---

> "Third Normal Form means the table should already be in 2NF and should not have transitive dependency. A non-key attribute should depend directly on the primary key and not on another non-key attribute."
