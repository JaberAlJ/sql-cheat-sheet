# Grouping Data with GROUP BY & HAVING 📊

The `GROUP BY` clause in SQL is used to **group rows that have the same values** in specified columns, often used with **aggregate functions**. The `HAVING` clause is used to **filter groups** based on a condition.

---

## 1. Basic Syntax

```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1;
```

* `aggregate_function` — Examples: `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()`.

**Example:**

```sql
SELECT department_id, COUNT(*) AS num_employees
FROM employees
GROUP BY department_id;
```

This returns the **number of employees in each department**.

---

## 2. Using Multiple Columns in GROUP BY

```sql
SELECT department_id, job_id, COUNT(*) AS num_employees
FROM employees
GROUP BY department_id, job_id;
```

* Groups rows first by `department_id` and then by `job_id`.
* Useful for **nested aggregation**.

---

## 3. Using Aggregate Functions

Common aggregate functions:

| Function | Description                    | Example                    |
| -------- | ------------------------------ | -------------------------- |
| COUNT()  | Counts rows or non-NULL values | COUNT(\*) or COUNT(salary) |
| SUM()    | Sum of numeric values          | SUM(salary)                |
| AVG()    | Average of numeric values      | AVG(salary)                |
| MIN()    | Minimum value                  | MIN(salary)                |
| MAX()    | Maximum value                  | MAX(salary)                |

**Example:**

```sql
SELECT department_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY department_id;
```

---

## 4. Filtering Groups with HAVING

Unlike `WHERE` (filters individual rows), `HAVING` filters **groups after aggregation**:

```sql
SELECT department_id, COUNT(*) AS num_employees
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 5;
```

* Returns only departments with **more than 5 employees**.

**Example with multiple conditions:**

```sql
SELECT department_id, SUM(salary) AS total_salary
FROM employees
GROUP BY department_id
HAVING SUM(salary) > 50000;
```

---

## 5. Combining GROUP BY with ORDER BY

You can sort grouped results:

```sql
SELECT department_id, COUNT(*) AS num_employees
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 5
ORDER BY num_employees DESC;
```

---

This file provides a **quick reference for grouping and filtering aggregated data** in SQL.