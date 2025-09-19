# DELETE Statement 🗑️

The `DELETE` statement is used to **remove rows** from a table in a database.

---

## 1. Delete Specific Rows

**Syntax:**

```sql
DELETE FROM table_name
WHERE condition;
```

**Example:**

```sql
DELETE FROM employees
WHERE employee_id = 101;
```

> ⚠️ Always include a `WHERE` clause to avoid deleting all rows unintentionally.

---

## 2. Delete Multiple Rows Using Condition

**Syntax:**

```sql
DELETE FROM table_name
WHERE column_name IN (value1, value2, ...);
```

**Example:**

```sql
DELETE FROM employees
WHERE department_id IN (10, 20);
```

---

## 3. Delete All Rows

**Syntax:**

```sql
DELETE FROM table_name;
```

**Example:**

```sql
DELETE FROM employees;
```

> ⚠️ This deletes **all rows** but keeps the table structure intact.

---

## 4. Delete Using Subquery

**Syntax:**

```sql
DELETE FROM table_name
WHERE column_name = (SELECT column_name FROM another_table WHERE condition);
```

**Example:**

```sql
DELETE FROM employees
WHERE department_id = (
    SELECT department_id
    FROM departments
    WHERE department_name = 'Temporary'
);
```

---

This cheat sheet provides **syntax and examples** for common `DELETE` statements in SQL.