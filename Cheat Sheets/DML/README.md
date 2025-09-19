# Data Manipulation Language (DML) 🛠️

This folder contains cheat sheets for **Oracle SQL DML statements**, which are used to **manipulate data** in database tables.  

The cheat sheets include **syntax and examples** for easy reference.

---

## What You’ll Find Here

1. **[SELECT](select.md) 📋**  
   - Retrieve data from one or more tables.  
   - Use clauses like `WHERE`, `ORDER BY`, `DISTINCT`, and `GROUP BY`.  
   - Supports joins and subqueries for advanced queries.

2. **[INSERT](insert.md) ➕**  
   - Add new rows to a table.  
   - Insert single or multiple rows.  
   - Insert data using `SELECT` statements or default values.

3. **[UPDATE](update.md) ✏️**  
   - Modify existing rows in a table.  
   - Update single or multiple columns.  
   - Use subqueries for conditional updates.  

4. **[DELETE](delete.md) 🗑️**  
   - Remove rows from a table.  
   - Delete specific rows using conditions or all rows.  
   - Supports deletion using subqueries.

5. **[MERGE](merge.md) 🔄**  
   - Insert or update rows based on a source table.  
   - Perform "upsert" operations efficiently.  
   - Supports conditional updates and inserts in a single statement.

---

## Quick Tips

- Always use `WHERE` clauses in `UPDATE` and `DELETE` to avoid affecting all rows.
- Use `MERGE` for efficient **upsert operations** (update if exists, insert if not).
- Use `DISTINCT`, `ORDER BY`, and aggregate functions to refine `SELECT` queries.
- Combine DML statements with subqueries and joins for more advanced data manipulation.

---

This folder serves as a **quick reference** for developers and students working with SQL.