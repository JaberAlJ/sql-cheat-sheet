Here’s a structured `savepoint.md` for your **TCL (Transaction Control Language)** folder:

# SAVEPOINT Statement 📍

The `SAVEPOINT` statement is used to **set a point within a transaction** to which you can later roll back if needed. It allows **partial rollback** of a transaction instead of undoing all changes.

---

## Syntax

```sql
SAVEPOINT savepoint_name;
```

You can later rollback to this savepoint:

```sql
ROLLBACK TO savepoint_name;
```

---

## Key Points

* Creates a **marker** within a transaction.
* Allows **partial rollback** to a specific point.
* Must be used **before a COMMIT**, otherwise rollback is not possible.
* Helps in **controlling complex transactions** step by step.

---

## Example

### 1. Using savepoints in a transaction

```sql
INSERT INTO employees (employee_id, first_name, last_name)
VALUES (201, 'Emma', 'Brown');

SAVEPOINT sp1;

UPDATE employees
SET salary = salary + 1000
WHERE employee_id = 201;

SAVEPOINT sp2;

DELETE FROM employees
WHERE employee_id = 202;

-- Mistake detected in the delete
ROLLBACK TO sp2;

COMMIT;
```

**Explanation:**

* `sp1` and `sp2` are savepoints.
* Rollback to `sp2` undoes changes after `sp2` but keeps earlier changes intact.
* COMMIT finalizes all remaining changes.

---

## Quick Tip 💡

* Savepoints are useful in **large transactions** where you want to **test intermediate steps** before final commit.
* Naming savepoints clearly (e.g., `before_update`, `after_insert`) helps **track transaction progress**.