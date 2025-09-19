# UPDATE Statement ✏️

The `UPDATE` statement is used to **modify existing rows** in a table.

---

## 1. Update Single Column

**Syntax:**

```sql
UPDATE table_name
SET column1 = value1
WHERE condition;
```

**Example:**

```sql
UPDATE employees
SET salary = 6000
WHERE employee_id = 101;
```

> ⚠️ Always include a `WHERE` clause to avoid updating all rows unintentionally.

---

## 2. Update Multiple Columns

**Syntax:**

```sql
UPDATE table_name
SET column1 = value1,
    column2 = value2,
    ...
WHERE condition;
```

**Example:**

```sql
UPDATE employees
SET salary = 7000,
    job_id = 'IT_PROG'
WHERE employee_id = 102;
```

---

## 3. Update Using a Subquery

**Syntax:**

```sql
UPDATE table_name
SET column1 = (SELECT column2 FROM another_table WHERE condition)
WHERE condition;
```

**Example:**

```sql
UPDATE employees e
SET department_id = (
    SELECT department_id
    FROM departments
    WHERE department_name = 'Sales'
)
WHERE e.employee_id = 103;
```

---

## 4. Update All Rows

**Syntax:**

```sql
UPDATE table_name
SET column1 = value1;
```

**Example:**

```sql
UPDATE employees
SET salary = salary * 1.05;
```

> ⚠️ This will increase **all employees’ salaries by 5%**, so use with caution.

---

This cheat sheet provides **syntax and examples** for common `UPDATE` statements in SQL.