# MERGE Statement 🔄

The `MERGE` statement is used to **insert, update, or delete rows** in a target table based on the results of a join with a source table. It is also called an "upsert" operation.

---

## 1. Basic MERGE Syntax

**Syntax:**

```sql
MERGE INTO target_table t
USING source_table s
ON (t.column_name = s.column_name)
WHEN MATCHED THEN
    UPDATE SET t.column1 = s.column1, t.column2 = s.column2
WHEN NOT MATCHED THEN
    INSERT (t.column1, t.column2, ...)
    VALUES (s.column1, s.column2, ...);
```

**Example:**

```sql
MERGE INTO employees e
USING new_employees n
ON (e.employee_id = n.employee_id)
WHEN MATCHED THEN
    UPDATE SET e.salary = n.salary, e.job_id = n.job_id
WHEN NOT MATCHED THEN
    INSERT (employee_id, first_name, last_name, email, hire_date, job_id, salary)
    VALUES (n.employee_id, n.first_name, n.last_name, n.email, n.hire_date, n.job_id, n.salary);
```

---

## 2. MERGE with Only UPDATE for Matches

**Syntax:**

```sql
MERGE INTO target_table t
USING source_table s
ON (t.column_name = s.column_name)
WHEN MATCHED THEN
    UPDATE SET t.column1 = s.column1;
```

**Example:**

```sql
MERGE INTO employees e
USING salary_updates s
ON (e.employee_id = s.employee_id)
WHEN MATCHED THEN
    UPDATE SET e.salary = s.new_salary;
```

---

## 3. MERGE with Only INSERT for Non-Matches

**Syntax:**

```sql
MERGE INTO target_table t
USING source_table s
ON (t.column_name = s.column_name)
WHEN NOT MATCHED THEN
    INSERT (column1, column2, ...)
    VALUES (s.column1, s.column2, ...);
```

**Example:**

```sql
MERGE INTO employees e
USING new_hires n
ON (e.employee_id = n.employee_id)
WHEN NOT MATCHED THEN
    INSERT (employee_id, first_name, last_name, email, hire_date, job_id, salary)
    VALUES (n.employee_id, n.first_name, n.last_name, n.email, n.hire_date, n.job_id, n.salary);
```

---

This cheat sheet provides **syntax and examples** for using the `MERGE` statement in SQL, enabling **insert/update operations in a single command**.