# Transaction Control Language (TCL) 📝

This folder contains cheat sheets for **SQL Transaction Control Language (TCL) statements**, which are used to **manage transactions** in a database.

TCL statements help ensure **data integrity and consistency** by controlling when changes are **saved or undone**.

---

## What You’ll Find Here

1. **[COMMIT](commit.md) ✅**  
   Save all changes made in the current transaction permanently.

2. **[ROLLBACK](rollback.md) 🔄**  
   Undo changes in the current transaction that have not been committed yet.

3. **[SAVEPOINT](savepoint.md) 📍**  
   Set a point within a transaction to roll back to later if needed.

---

## Quick Tips 💡

- Always **commit** after completing a logical unit of work to ensure changes are permanent.  
- Use **rollback** to recover from mistakes without affecting previously committed data.  
- Use **savepoints** to manage complex transactions and allow partial rollbacks.  

---

> TCL statements work **together with DML operations** (`INSERT`, `UPDATE`, `DELETE`) to ensure safe and controlled changes to your database.
