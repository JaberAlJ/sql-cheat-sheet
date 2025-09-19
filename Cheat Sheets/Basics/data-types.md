# SQL Data Types 📊

Oracle provides a rich set of **data types** to define the kind of values a column, variable, or expression can hold.  
These can broadly be categorized into:

- **Character Data Types**
- **Numeric Data Types**
- **Date/Time Data Types**
- **Large Object (LOB) Data Types**
- **Other Specialized Data Types**

---

## 1. Character Data Types ✍️

| Data Type      | Description                                                                 | Example                |
|----------------|-----------------------------------------------------------------------------|------------------------|
| `CHAR(n)`      | Fixed-length character string. Pads with spaces to n bytes. (1–2000)        | `CHAR(10)` → `'SQL     '` |
| `VARCHAR2(n)`  | Variable-length character string. More space-efficient. (1–4000)            | `VARCHAR2(20)` → `'Oracle SQL'` |
| `NCHAR(n)`     | Fixed-length national character set string.                                 | `NCHAR(10)`            |
| `NVARCHAR2(n)` | Variable-length national character set string.                              | `NVARCHAR2(50)`        |

---

## 2. Numeric Data Types 🔢

| Data Type      | Description                                                                 | Example                |
|----------------|-----------------------------------------------------------------------------|------------------------|
| `NUMBER(p,s)`  | Number with precision `p` (digits) and scale `s` (decimal places).          | `NUMBER(8,2)` → `12345.67` |
| `INTEGER`      | Equivalent to `NUMBER(38,0)`. Whole numbers only.                          | `42`                   |
| `FLOAT(p)`     | Approximate floating-point number with binary precision `p`.                | `FLOAT(126)`           |
| `BINARY_FLOAT` | 32-bit, single-precision floating-point number.                             | `1.234E+02`            |
| `BINARY_DOUBLE`| 64-bit, double-precision floating-point number.                             | `1.23456789012345E+02` |

---

## 3. Date/Time Data Types ⏰

| Data Type       | Description                                                                | Example                |
|-----------------|----------------------------------------------------------------------------|------------------------|
| `DATE`          | Stores date and time (DD-MON-YY, HH:MI:SS).                                | `DATE '2025-09-19'`    |
| `TIMESTAMP`     | Date + fractional seconds.                                                 | `TIMESTAMP '2025-09-19 13:45:30.123'` |
| `TIMESTAMP WITH TIME ZONE` | Adds time zone information.                                     | `TIMESTAMP '2025-09-19 13:45:30 -05:00'` |
| `TIMESTAMP WITH LOCAL TIME ZONE` | Normalized to DB time zone, shown in user’s session zone. |                        |
| `INTERVAL YEAR TO MONTH`  | Stores differences in years and months.                          | `INTERVAL '2-6' YEAR TO MONTH` |
| `INTERVAL DAY TO SECOND`  | Stores differences in days, hours, minutes, seconds.             | `INTERVAL '10 12:30:45' DAY TO SECOND` |

---

## 4. Large Object (LOB) Data Types 📂

| Data Type  | Description                                                                   |
|------------|-------------------------------------------------------------------------------|
| `CLOB`     | Character large object (up to 4 GB).                                           |
| `NCLOB`    | Unicode character large object (up to 4 GB).                                   |
| `BLOB`     | Binary large object (unstructured binary data up to 4 GB).                     |
| `BFILE`    | Binary file stored outside DB but referenced inside. (Read-only).              |

---

## 5. Other Specialized Data Types ⚙️

| Data Type    | Description                                                                 |
|--------------|-----------------------------------------------------------------------------|
| `RAW(n)`     | Stores binary data in hexadecimal (up to 2000 bytes).                       |
| `LONG`       | Variable-length character data (up to 2 GB). *(Deprecated, use CLOB instead)*|
| `ROWID`      | Physical address of a row in a table.                                       |
| `UROWID`     | Universal rowid for tables (includes non-Oracle storage).                   |

---

## 🔑 Key Notes
- Use `VARCHAR2` instead of `CHAR` for most text to save space.
- Prefer `CLOB`/`BLOB` over deprecated `LONG`.
- Use `TIMESTAMP` for high-precision date/time operations.
- Always define numeric columns with proper precision and scale.

---

✅ This cheat sheet provides a **quick reference** for choosing the right Oracle SQL data type.
