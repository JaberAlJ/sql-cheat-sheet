# ALTER Statements Cheat Sheet 🔧

The `ALTER` statement is used to modify existing database objects like tables, views, sequences, or users.

---

## 1. Alter Table

### a) Add Column
```sql
ALTER TABLE table_name
ADD column_name datatype [CONSTRAINT];
```

**Example:**
```sql
ALTER TABLE employees
ADD middle_name VARCHAR2(50);
```
```sql
ALTER TABLE employees
ADD middle_name VARCHAR2(50) UNIQUE;
```

### b) Modify Column

```sql
ALTER TABLE table_name
MODIFY column_name datatype [CONSTRAINT];
```

**Example:**

```sql
ALTER TABLE employees
MODIFY salary NUMBER(10,2) NOT NULL;
```
```sql
ALTER TABLE employees
MODIFY last_name VARCHAR2(100);
```

### c) Drop Column

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

**Example:**

```sql
ALTER TABLE employees
DROP COLUMN middle_name;
```

### d) Add / Drop Constraint

```sql
ALTER TABLE table_name
ADD CONSTRAINT constraint_name constraint_definition;
```
```sql
ALTER TABLE table_name
DROP CONSTRAINT constraint_name;
```

**Example:**

```sql
ALTER TABLE employees
ADD CONSTRAINT chk_salary CHECK (salary > 0);
```
```sql
ALTER TABLE employees
ADD CONSTRAINT fk_dept FOREIGN KEY (department_id)
REFERENCES departments(department_id);
```
```sql
ALTER TABLE employees
DROP CONSTRAINT chk_salary;
```

---

## 2. Alter Sequence

### a) Change Increment

```sql
ALTER SEQUENCE seq_name
INCREMENT BY n;
```

**Example:**

```sql
ALTER SEQUENCE emp_seq
INCREMENT BY 5;
```

### b) Restart Sequence (Oracle 12c+)

```sql
ALTER SEQUENCE seq_name
RESTART START WITH n;
```

**Example:**

```sql
ALTER SEQUENCE emp_seq
RESTART START WITH 1001;
```

---

## 3. Alter User

### a) Change Password

```sql
ALTER USER username IDENTIFIED BY new_password;
```

**Example:**

```sql
ALTER USER admin_user IDENTIFIED BY Admin@2025;
```

### b) Default / Temporary Tablespace

```sql
ALTER USER username
DEFAULT TABLESPACE new_tablespace
TEMPORARY TABLESPACE temp_tablespace;
```

**Example:**

```sql
ALTER USER hr_user
DEFAULT TABLESPACE data
TEMPORARY TABLESPACE temp_data;
```

---

## 4. Alter View

You cannot directly alter a view; instead, use:

```sql
CREATE OR REPLACE VIEW view_name AS
SELECT ... ;
```

**Example:**

```sql
CREATE OR REPLACE VIEW emp_salary_view AS
SELECT first_name, last_name, salary
FROM employees
WHERE salary > 5000;
```

---

**Tips:**

* Use `ALTER TABLE` carefully; dropping columns or constraints may result in data loss.
* For views, always use `CREATE OR REPLACE`.
* Sequences can be modified but not decreased below current value without reset.