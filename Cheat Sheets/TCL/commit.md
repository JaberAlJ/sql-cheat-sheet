# COMMIT Statement ✅

The `COMMIT` statement is used to **save all the changes made in the current transaction permanently** to the database. Once committed, the changes **cannot be rolled back**.

---

## Syntax

```sql
COMMIT;
```

You can also use `COMMIT WORK;` (both are equivalent).

---

## Key Points

* Ends the current transaction.
* Makes all changes in the transaction permanent.
* Cannot be undone by `ROLLBACK` after a commit.
* Often used after a series of `INSERT`, `UPDATE`, or `DELETE` statements.

---

## Example

### 1. Committing changes after an insert

```sql
INSERT INTO employees (employee_id, first_name, last_name, hire_date)
VALUES (101, 'John', 'Doe', SYSDATE);

COMMIT;
```

### 2. Committing multiple changes

```sql
UPDATE employees
SET salary = salary * 1.1
WHERE department_id = 10;

DELETE FROM employees
WHERE employee_id = 105;

COMMIT;
```

---

## Quick Tip 💡

* Always commit after a logical unit of work to **ensure data integrity**.
* In some environments, `AUTOCOMMIT` may be enabled, which commits each statement automatically.