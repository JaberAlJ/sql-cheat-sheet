# CREATE Statements in SQL 🏗️

The `CREATE` statement is used to define and create database objects such as tables, views, sequences, indexes, and more.

---

## 1. Create Table

Create a new table in the database.

```sql
CREATE TABLE table_name (
    column1 datatype [CONSTRAINT],
    column2 datatype [CONSTRAINT],
    ...
    [table_constraints]
);
```

**Example:**

```sql
CREATE TABLE employees (
    employee_id NUMBER(5) PRIMARY KEY,
    first_name VARCHAR2(50),
    last_name VARCHAR2(50) NOT NULL,
    hire_date DATE DEFAULT SYSDATE,
    salary NUMBER(8,2),
    department_id NUMBER(3),
    CONSTRAINT fk_department FOREIGN KEY (department_id)
        REFERENCES departments(department_id)
);
```

---

## 2. Create View

A view is a virtual table based on a query.

```sql
CREATE [OR REPLACE] VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Example:**

```sql
CREATE OR REPLACE VIEW emp_salary_view AS
SELECT first_name, last_name, salary
FROM employees
WHERE salary > 5000;
```

---

## 3. Create Sequence

Sequences are used to generate unique numeric values.

```sql
CREATE SEQUENCE sequence_name
    START WITH 1
    INCREMENT BY 1
    [MINVALUE value]
    [MAXVALUE value]
    [CYCLE | NOCYCLE]
    [CACHE value | NOCACHE];
```

**Example:**

```sql
CREATE SEQUENCE emp_seq
    START WITH 1001
    INCREMENT BY 1
    NOCACHE
    NOCYCLE;
```

---

## 4. Create Index

Indexes improve query performance.

```sql
CREATE [UNIQUE] INDEX index_name
ON table_name (column1, column2, ...);
```

**Example:**

```sql
CREATE UNIQUE INDEX emp_lastname_idx
ON employees(last_name);
```

---

## 5. Create Synonym

A synonym is an alias for another database object.

```sql
CREATE [PUBLIC] SYNONYM synonym_name FOR object_name;
```

**Example:**

```sql
CREATE PUBLIC SYNONYM emp FOR employees;
```

---

## 6. Create User (Optional)

Create a new database user.

```sql
CREATE USER username IDENTIFIED BY password
[DEFAULT TABLESPACE tablespace_name]
[TEMPORARY TABLESPACE temp_tablespace];
```

**Example:**

```sql
CREATE USER hr_user IDENTIFIED BY hr123
DEFAULT TABLESPACE users
TEMPORARY TABLESPACE temp;
```

---

### Notes

* Use `CREATE OR REPLACE` for views and procedures to avoid errors if the object exists.
* Always define **primary keys**, **foreign keys**, and **constraints** for data integrity.
* Use sequences for generating unique identifiers, especially for primary keys.