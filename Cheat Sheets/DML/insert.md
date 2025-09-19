# INSERT Statement ➕

The `INSERT` statement is used to **add new rows** into a table in a database.

---

## 1. Insert a Single Row

**Syntax:**

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

**Example:**

```sql
INSERT INTO employees (first_name, last_name, email, hire_date, job_id)
VALUES ('John', 'Doe', 'jdoe@example.com', TO_DATE('2025-09-19', 'YYYY-MM-DD'), 'IT_PROG');
```

---

## 2. Insert Multiple Rows

**Syntax:**

```sql
INSERT ALL
  INTO table_name (column1, column2, ...) VALUES (value1, value2, ...)
  INTO table_name (column1, column2, ...) VALUES (value1, value2, ...)
SELECT * FROM dual;
```

**Example:**

```sql
INSERT ALL
  INTO employees (first_name, last_name, email, hire_date, job_id) VALUES ('Alice', 'Smith', 'asmith@example.com', TO_DATE('2025-09-19','YYYY-MM-DD'), 'HR_REP')
  INTO employees (first_name, last_name, email, hire_date, job_id) VALUES ('Bob', 'Brown', 'bbrown@example.com', TO_DATE('2025-09-19','YYYY-MM-DD'), 'IT_PROG')
SELECT * FROM dual;
```

---

## 3. Insert Using SELECT Statement

**Syntax:**

```sql
INSERT INTO table_name (column1, column2, ...)
SELECT column1, column2, ...
FROM another_table
WHERE condition;
```

**Example:**

```sql
INSERT INTO employees_backup (first_name, last_name, email, hire_date, job_id)
SELECT first_name, last_name, email, hire_date, job_id
FROM employees
WHERE department_id = 10;
```

---

## 4. Insert Default Values

**Syntax:**

```sql
INSERT INTO table_name
DEFAULT VALUES;
```

**Example:**

```sql
INSERT INTO departments
DEFAULT VALUES;
```

> Note: Some Oracle versions may require you to provide at least one column with a value if `DEFAULT VALUES` is not supported.

---

This cheat sheet provides **syntax and examples** for common `INSERT` statements in SQL.