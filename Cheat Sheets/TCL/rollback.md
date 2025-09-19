# ROLLBACK Statement 🔄

The `ROLLBACK` statement is used to **undo changes made in the current transaction**. Any changes that have not been committed can be reverted.

---

## Syntax

```sql
ROLLBACK;
```

You can also rollback to a specific **savepoint**:

```sql
ROLLBACK TO savepoint_name;
```

---

## Key Points

* Undoes all changes in the current transaction **since the last COMMIT or SAVEPOINT**.
* Does **not** affect changes that have already been committed.
* Useful to **maintain data integrity** in case of errors or unexpected issues during a transaction.

---

## Example

### 1. Rolling back all changes

```sql
UPDATE employees
SET salary = salary * 1.1
WHERE department_id = 10;

-- Oops, mistake detected
ROLLBACK;
```

### 2. Rolling back to a savepoint

```sql
INSERT INTO employees (employee_id, first_name, last_name)
VALUES (110, 'Alice', 'Smith');

SAVEPOINT before_update;

UPDATE employees
SET salary = salary + 500
WHERE employee_id = 110;

-- Mistake detected in the update
ROLLBACK TO before_update;

-- The insert remains, the update is undone
```

---

## Quick Tip 💡

* Use `ROLLBACK` to **recover from errors** without affecting previously committed data.
* Combine with `SAVEPOINT` for more **granular control** within a transaction.