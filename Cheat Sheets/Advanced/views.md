# Views in Oracle SQL 🪞

A **view** is a **virtual table** based on the result of a query.  
It does **not store data physically** but provides a way to simplify complex queries, enhance security, and present data in a specific format.

---

## 1. Creating a Basic View

**Syntax:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Example:**

```sql
CREATE VIEW emp_sales AS
SELECT employee_id, first_name, last_name, department_id, salary
FROM employees
WHERE department_id = 10;
```

* Creates a view of employees in the Sales department.

---

## 2. Querying a View

**Syntax:**

```sql
SELECT *
FROM view_name;
```

**Example:**

```sql
SELECT *
FROM emp_sales;
```

---

## 3. Updating a View

* Views **can be updatable** if they reference a **single table** and do not contain **aggregates, joins, or DISTINCT**.

**Syntax:**

```sql
UPDATE view_name
SET column_name = value
WHERE condition;
```

**Example:**

```sql
UPDATE emp_sales
SET salary = salary * 1.1
WHERE employee_id = 101;
```

---

## 4. Creating a View with Joins

**Syntax:**

```sql
CREATE VIEW view_name AS
SELECT t1.column1, t2.column2, ...
FROM table1 t1
JOIN table2 t2 ON t1.id = t2.id
WHERE condition;
```

**Example:**

```sql
CREATE VIEW emp_dept AS
SELECT e.employee_id, e.first_name, e.last_name, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id;
```

---

## 5. Creating a Materialized View

* Stores **data physically** and can be **refreshed periodically**.
* Useful for **performance optimization** on large datasets.

**Syntax:**

```sql
CREATE MATERIALIZED VIEW mv_name
REFRESH FAST ON COMMIT
AS
SELECT column1, column2
FROM table_name;
```

**Example:**

```sql
CREATE MATERIALIZED VIEW mv_emp_sales
REFRESH FAST ON COMMIT
AS
SELECT employee_id, first_name, last_name, salary
FROM employees
WHERE department_id = 10;
```

---

## 6. Dropping a View

**Syntax:**

```sql
DROP VIEW view_name;
```

**Example:**

```sql
DROP VIEW emp_sales;
```

---

## 7. Quick Tips ✅

* Views simplify **complex queries** and improve **readability**.
* Use views to **restrict access** to sensitive columns.
* Materialized views **improve performance** but require storage and maintenance.
* Always **name views clearly** to indicate their purpose.