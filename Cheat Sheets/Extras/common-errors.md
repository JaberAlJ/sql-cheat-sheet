# Common SQL Errors ❌

Understanding common SQL errors helps **debug faster** and write more reliable queries. Here are some frequent mistakes and how to avoid them:

---

## 1. Syntax Errors
- **Cause:** Typos, missing commas, brackets, or keywords.
- **Example:**
```sql
-- Incorrect
SELEC first_name FROM employees;

-- Correct
SELECT first_name FROM employees;
```

* **Tip:** Always double-check SQL keywords and punctuation.

---

## 2. Missing or Invalid Table/Column Names

* **Cause:** Referencing a table or column that does not exist or is misspelled.
* **Example:**

```sql
SELECT salary FROM employes; -- typo in table name
```

* **Tip:** Use `DESC table_name` to verify column names.

---

## 3. Ambiguous Column Names

* **Cause:** Multiple tables in a query have columns with the same name.
* **Example:**

```sql
SELECT id FROM employees e
JOIN departments d ON e.department_id = d.department_id;

-- Fix with table alias
SELECT e.id, d.id
FROM employees e
JOIN departments d ON e.department_id = d.department_id;
```

---

## 4. Constraint Violations

* **Primary Key Violation:** Attempting to insert duplicate values.
* **Foreign Key Violation:** Inserting a value that does not exist in the parent table.
* **Check Constraint Violation:** Inserting values that break the rules.

---

## 5. Data Type Mismatches

* **Cause:** Comparing or inserting values of incompatible types.
* **Example:**

```sql
-- Incorrect: number vs string
WHERE employee_id = '101';

-- Correct
WHERE employee_id = 101;
```

---

## 6. Null Handling Errors

* **Cause:** Not accounting for `NULL` in conditions or calculations.
* **Example:**

```sql
-- Will not return rows where commission_pct is NULL
WHERE commission_pct <> 0;

-- Correct
WHERE NVL(commission_pct, 0) <> 0;
```

---

## 7. Logical Errors

* **Cause:** Query runs but returns unexpected results due to incorrect logic.
* **Tip:** Double-check join conditions, `WHERE` clauses, and aggregate functions.

---

## 8. Performance Pitfalls

* Using `SELECT *` unnecessarily.
* Functions on indexed columns preventing index usage.
* Cartesian products due to missing join conditions.

---

## Quick Tips

* Always test queries on a small dataset before applying to production.
* Use aliases to avoid ambiguity.
* Check execution plans for potential performance issues.
* Keep an eye on constraints and data types when inserting or updating data.