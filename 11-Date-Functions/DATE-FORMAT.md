# 🎨 DATE_FORMAT & STR_TO_DATE Functions

## 📌 Definition

The **`DATE_FORMAT()`** function formats a date/datetime value into a customized readable string, while **`STR_TO_DATE()`** parses a formatted string into a standard SQL date data type.

---

## 🔑 Key Format Specifiers (MySQL)

| Specifier | Description | Output Example |
| :--- | :--- | :--- |
| **`%Y`** | 4-digit Year | `2025` |
| **`%y`** | 2-digit Year | `25` |
| **`%m`** | 2-digit Month (01 to 12) | `06` |
| **`%M`** | Full Month Name | `June` |
| **`%b`** | Abbreviated Month Name | `Jun` |
| **`%d`** | 2-digit Day of Month (01 to 31) | `15` |
| **`%W`** | Full Weekday Name | `Wednesday` |

---

## 💻 Syntax & Examples (MySQL)

### 1. Formatting Dates into Custom String Formats
```sql
SELECT 
    order_date,
    DATE_FORMAT(order_date, '%d-%m-%Y') AS format_dd_mm_yyyy, -- '15-06-2025'
    DATE_FORMAT(order_date, '%M %d, %Y') AS format_readable   -- 'June 15, 2025'
FROM orders;
```

### 2. Parsing Custom String into SQL Date (`STR_TO_DATE`)
```sql
SELECT STR_TO_DATE('15/06/2025', '%d/%m/%Y') AS parsed_date;
-- Returns SQL Date: '2025-06-15'
```

---

## ⚖️ Dialect Comparisons

| Database | Date Formatting Function |
| :--- | :--- |
| **MySQL** | `DATE_FORMAT(date, '%Y-%m-%d')` |
| **PostgreSQL / Oracle** | `TO_CHAR(date, 'YYYY-MM-DD')` |
| **SQL Server** | `FORMAT(date, 'yyyy-MM-dd')` |

---

# 🎯 Most Asked Interview Questions

### 1. How do you format a date as `'DD-MM-YYYY'` in MySQL?
> Use `DATE_FORMAT(date_column, '%d-%m-%Y')`.

---

### 2. How do you convert a string like `'31-12-2024'` into a valid SQL Date in MySQL?
> Use `STR_TO_DATE('31-12-2024', '%d-%m-%Y')`.

---

# 🧠 Quick Revision

```text
Date Formatting Pipeline
 ├── DATE_FORMAT(date, '%d/%m/%Y') → Converts Date to Formatted String
 └── STR_TO_DATE('15/06/2025', '%d/%m/%Y') → Converts String to Date
```

> **Memory Trick:** `%Y = 4-digit year | %m = Month | %d = Day`
