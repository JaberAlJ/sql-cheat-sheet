# Data Definition Language (DDL) Cheat Sheet 🏗️

This folder contains **SQL DDL statements** for creating, modifying, and removing database objects.  
It is designed as a **quick reference guide** with examples.

---

## What You’ll Find Here

1. **[CREATE](create.md) 🏗️**  
- Define and create database objects
- Examples: `CREATE TABLE`, `CREATE VIEW`, `CREATE SEQUENCE`, `CREATE INDEX`, `CREATE USER`

2. **[ALTER](alter.md) 🔧**  
- Modify existing objects
- Examples: `ALTER TABLE`, `ALTER SEQUENCE`, `ALTER USER`, `CREATE OR REPLACE VIEW`

3. **[DROP](drop.md) ❌**  
- Permanently remove objects
- Examples: `DROP TABLE`, `DROP VIEW`, `DROP SEQUENCE`, `DROP INDEX`, `DROP USER`

4. **[TRUNCATE](truncate.md) 🗑️**  
- Quickly remove all rows from a table
- Faster than `DELETE`
- Examples: `TRUNCATE TABLE employees`, `TRUNCATE TABLE departments CASCADE`

---

**Quick Tips:**
- Always **back up data** before using DROP or TRUNCATE.
- Use `ALTER` carefully; dropping columns or constraints may result in data loss.
- Use sequences for auto-generated IDs.
- For views, use `CREATE OR REPLACE` instead of ALTER.

---

This folder serves as a **quick reference** for developers and students working with SQL.