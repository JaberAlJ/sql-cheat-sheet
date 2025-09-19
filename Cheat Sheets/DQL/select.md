# SELECT Statement 📋

The `SELECT` statement is used to **retrieve data** from one or more tables in a database. It is one of the most commonly used SQL statements.

---

## 1. Basic SELECT

**Syntax:**

```sql
SELECT column1, column2, ...
FROM table_name;
```

**Example:**

```sql
SELECT first_name, last_name, salary
FROM employees;
```

**Select all columns:**

```sql
SELECT * FROM employees;
```

---

## 2. SELECT with WHERE Clause

**Syntax:**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Example:**

```sql
SELECT first_name, last_name, salary
FROM employees
WHERE salary > 5000;
```

**Using IN and LIKE:**

```sql
SELECT first_name, last_name
FROM employees
WHERE department_id IN (10, 20, 30)
AND first_name LIKE 'J%';
```

---

## 3. SELECT with ORDER BY

**Syntax:**

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column_name [ASC|DESC];
```

**Example:**

```sql
SELECT first_name, last_name, salary
FROM employees
ORDER BY salary DESC;
```

---

## 4. SELECT with DISTINCT

**Syntax:**

```sql
SELECT DISTINCT column_name
FROM table_name;
```

**Example:**

```sql
SELECT DISTINCT department_id
FROM employees;
```

---

## 5. SELECT with Aggregate Functions

**Syntax:**

```sql
SELECT aggregate_function(column_name)
FROM table_name
[WHERE condition]
[GROUP BY column_name];
```

**Example:**

```sql
SELECT department_id, COUNT(*) AS total_employees, AVG(salary) AS avg_salary
FROM employees
GROUP BY department_id;
```

**Common Aggregate Functions:**

* `COUNT()` – number of rows
* `SUM()` – total of numeric values
* `AVG()` – average
* `MIN()` – minimum value
* `MAX()` – maximum value

---

## 6. SELECT with JOINs

**Syntax (INNER JOIN):**

```sql
SELECT table1.column1, table2.column2, ...
FROM table1
INNER JOIN table2
ON table1.common_column = table2.common_column;
```

**Example:**

```sql
SELECT e.first_name, e.last_name, d.department_name
FROM employees e
INNER JOIN departments d
ON e.department_id = d.department_id;
```

**Syntax (LEFT JOIN):**

```sql
SELECT table1.column1, table2.column2, ...
FROM table1
LEFT JOIN table2
ON table1.common_column = table2.common_column;
```

**Example:**

```sql
SELECT e.first_name, e.last_name, d.department_name
FROM employees e
LEFT JOIN departments d
ON e.department_id = d.department_id;
```

---

## 7. SELECT with Subquery

**Syntax:**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name = (SELECT column_name FROM table_name WHERE condition);
```

**Example:**

```sql
SELECT first_name, last_name
FROM employees
WHERE department_id = (
    SELECT department_id
    FROM departments
    WHERE department_name = 'Sales'
);
```

---

## 8. Limiting Rows (Top N Records)

**Syntax:**

```sql
SELECT column1, column2, ...
FROM table_name
FETCH FIRST n ROWS ONLY;
```

**Example:**

```sql
SELECT *
FROM employees
FETCH FIRST 5 ROWS ONLY;
```

---

This cheat sheet provides **syntax and examples** for common `SELECT` queries in SQL.