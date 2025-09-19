# SQL Shortcuts ⌨️

Using shortcuts and quick commands can **speed up development** and make working with Oracle SQL more efficient. Here are some useful tips and shortcuts:

---

## 1. SQL*Plus / SQL Developer Shortcuts

| Shortcut | Action |
|----------|--------|
| `;`      | Execute the current SQL statement |
| `/`      | Execute the last SQL statement again |
| `DESCRIBE table_name` or `DESC table_name` | Show table structure (columns and types) |
| `SHOW USER` | Display current database user |
| `SHOW TABLES` | List all tables (SQL Developer may vary) |
| `!!`     | Execute OS command from SQL*Plus |

---

## 2. Quick SQL Commands

- **Get Current Date and Time**
```sql
SELECT SYSDATE FROM dual;
```

* **Count Rows in a Table**

```sql
SELECT COUNT(*) FROM employees;
```

* **List All Indexes for a Table**

```sql
SELECT index_name, table_name
FROM user_indexes
WHERE table_name = 'EMPLOYEES';
```

---

## 3. Aliases and Abbreviations

* Use **table aliases** to shorten queries:

```sql
SELECT e.first_name, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id;
```

* **Column aliases** for readability:

```sql
SELECT first_name || ' ' || last_name AS full_name
FROM employees;
```

---

## 4. Keyboard Shortcuts in SQL Developer

| Shortcut           | Action                           |
| ------------------ | -------------------------------- |
| `Ctrl + Enter`     | Run statement                    |
| `F5`               | Run script                       |
| `Ctrl + Shift + L` | Show SQL history                 |
| `Ctrl + /`         | Comment/Uncomment selected lines |
| `Ctrl + Space`     | Auto-complete code               |

---

## 5. Reuse Queries Quickly

* **Use `WITH` clause** (CTE) to simplify repeated subqueries:

```sql
WITH dept_avg AS (
    SELECT department_id, AVG(salary) AS avg_salary
    FROM employees
    GROUP BY department_id
)
SELECT e.first_name, e.salary, d.avg_salary
FROM employees e
JOIN dept_avg d ON e.department_id = d.department_id;
```

---

## Quick Tips

* Memorize frequently used commands and aliases.
* Use SQL Developer snippets for repetitive queries.
* Use `DESC` often to check table structures quickly.
* Keep a personal list of favorite shortcuts for faster coding.