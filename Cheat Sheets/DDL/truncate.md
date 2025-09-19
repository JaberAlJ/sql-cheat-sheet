# TRUNCATE Statements Cheat Sheet 🗑️

The `TRUNCATE` statement is used to **quickly delete all rows from a table**.  
It is **faster than DELETE** because it does not generate individual row deletions or undo logs.  
**Note:** TRUNCATE cannot be rolled back in most cases.

---

## 1. Truncate Table
```sql
TRUNCATE TABLE table_name;
```

**Examples:**

```sql
TRUNCATE TABLE employees;
```
```sql
-- Truncate a table and reset storage/recycle settings
TRUNCATE TABLE employees DROP STORAGE;
```

---

## 2. Truncate with CASCADE (Dependent Tables)

```sql
TRUNCATE TABLE table_name CASCADE;
```

**Examples:**

```sql
-- Truncate a parent table and all dependent child tables
TRUNCATE TABLE departments CASCADE;
```

---

## 3. Truncate Reset Identity/Sequence (Oracle Specific)

```sql
TRUNCATE TABLE table_name RESTART IDENTITY;
```

**Examples:**

```sql
-- Reset any sequences associated with the table
TRUNCATE TABLE employees RESTART IDENTITY;
```

---

**Tips:**

* TRUNCATE is **faster than DELETE** but cannot be rolled back once executed.
* Does **not fire triggers** in Oracle.
* Use CASCADE carefully; it will affect dependent tables.
* Ideal for clearing large tables during testing or maintenance.