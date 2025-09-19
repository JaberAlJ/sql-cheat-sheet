# Subqueries in Oracle SQL 🔍

A **subquery** is a query nested inside another SQL query. Subqueries are useful for breaking complex queries into simpler parts.

---

## 1. Types of Subqueries

### a) Single-row Subquery
Returns **one row**. Often used with comparison operators (`=`, `<`, `>`, `<=`, `>=`, `!=`).

**Syntax:**
```sql
SELECT column1, column2
FROM table1
WHERE column3 = (SELECT column3
                 FROM table2
                 WHERE condition);
```

**Example:**

```sql
SELECT first_name, last_name
FROM employees
WHERE department_id = (SELECT department_id
                       FROM departments
                       WHERE department_name = 'Sales');
```

---

### b) Multiple-row Subquery

Returns **multiple rows**. Used with `IN`, `ANY`, or `ALL`.

**Syntax:**

```sql
SELECT column1, column2
FROM table1
WHERE column3 IN (SELECT column3
                  FROM table2
                  WHERE condition);
```

**Example:**

```sql
SELECT first_name, last_name
FROM employees
WHERE department_id IN (SELECT department_id
                        FROM departments
                        WHERE location_id = 1700);
```

---

### c) Multiple-column Subquery

Returns **more than one column**. Can be used with tuples (`(col1, col2)`) and comparison operators.

**Syntax:**

```sql
SELECT column1, column2
FROM table1
WHERE (column3, column4) = (SELECT column3, column4
                            FROM table2
                            WHERE condition);
```

**Example:**

```sql
SELECT first_name, last_name
FROM employees
WHERE (department_id, job_id) = (SELECT department_id, job_id
                                 FROM job_history
                                 WHERE employee_id = 101);
```

---

### d) Correlated Subquery

References a column from the **outer query**. Evaluated **row by row**.

**Syntax:**

```sql
SELECT column1, column2
FROM table1 t1
WHERE column3 = (SELECT MAX(column3)
                 FROM table2 t2
                 WHERE t2.column4 = t1.column4);
```

**Example:**

```sql
SELECT employee_id, first_name, salary
FROM employees e
WHERE salary > (SELECT AVG(salary)
                FROM employees
                WHERE department_id = e.department_id);
```

---

### e) Subqueries in `FROM` Clause

Treat a subquery as a **derived table**.

**Syntax:**

```sql
SELECT sub.department_id, sub.avg_salary
FROM (SELECT department_id, AVG(salary) AS avg_salary
      FROM employees
      GROUP BY department_id) sub
WHERE sub.avg_salary > 5000;
```

---

## 2. Quick Tips ✅

* Subqueries can be **nested multiple levels**.
* Use **correlated subqueries** carefully; they can be slower.
* Prefer **JOINs** when performance is critical, but subqueries improve readability.
* Oracle supports **scalar, inline, and table subqueries**.