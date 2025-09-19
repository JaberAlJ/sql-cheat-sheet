# SQL Best Practices ✅

Following best practices in SQL ensures **efficient, maintainable, and error-free** database operations. Here are some key guidelines:

---

## 1. Writing Clean SQL
- **Use Meaningful Names:** Tables, columns, indexes, and constraints should have descriptive names.
- **Consistent Formatting:** Capitalize SQL keywords and align clauses for readability.
- **Comment Your Code:** Explain complex queries or business logic.

**Example:**
```sql
-- Fetch employees from the Sales department
SELECT first_name, last_name, salary
FROM employees
WHERE department_id = 50;
```

---

## 2. Query Optimization

* **Select Only Required Columns:** Avoid `SELECT *`.
* **Filter Early:** Use `WHERE` conditions to reduce data before processing.
* **Use Joins Wisely:** Prefer `INNER JOIN` when possible and avoid unnecessary joins.

---

## 3. Indexing and Keys

* **Primary and Foreign Keys:** Always define to enforce data integrity.
* **Use Indexes for Frequently Queried Columns:** But avoid excessive indexing.
* **Check Index Usage:** Ensure queries actually benefit from indexes.

---

## 4. Transactions and Data Safety

* **Use Transactions:** Group related DML operations using `COMMIT` and `ROLLBACK`.
* **Savepoints:** Use `SAVEPOINT` for partial rollbacks in complex transactions.
* **Avoid Auto-commit for Critical Operations** to prevent accidental data loss.

---

## 5. Naming Conventions

* **Tables:** Singular nouns, e.g., `employee`, `order`.
* **Columns:** Use lowercase with underscores or camelCase consistently.
* **Constraints:** Use prefixes like `pk_`, `fk_`, `uq_` for easy identification.

---

## 6. Security Best Practices

* **Grant Minimal Privileges:** Follow principle of least privilege.
* **Avoid Hardcoding Sensitive Data:** Use bind variables or secure storage.
* **Use Views for Sensitive Data:** Restrict direct table access.

---

## 7. Maintainability

* **Break Complex Queries:** Use CTEs (`WITH` clause) for clarity.
* **Version Control SQL Scripts:** Keep track of changes for deployment and rollback.
* **Regularly Review Queries:** Refactor inefficient queries and remove deprecated code.

---

## Quick Tips

* Keep consistent naming and formatting across the database.
* Use comments liberally to describe complex joins or business rules.
* Regularly analyze execution plans and optimize slow queries.