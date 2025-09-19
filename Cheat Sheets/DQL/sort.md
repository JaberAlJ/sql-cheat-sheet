# Sorting Data with ORDER BY 🔀

The `ORDER BY` clause in SQL is used to **sort the result set** of a query by one or more columns. Sorting can be done in **ascending (ASC)** or **descending (DESC)** order.

---

## 1. Basic Syntax

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column [ASC|DESC];
```

* `ASC` — Sorts in ascending order (default).
* `DESC` — Sorts in descending order.

**Example:**

```sql
SELECT first_name, last_name, salary
FROM employees
ORDER BY salary DESC;
```

> This retrieves employees sorted from **highest to lowest salary**.

---

## 2. Sorting by Multiple Columns

You can sort by more than one column:

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC], ...;
```

**Example:**

```sql
SELECT first_name, last_name, department_id, salary
FROM employees
ORDER BY department_id ASC, salary DESC;
```

* First, results are sorted by `department_id` in ascending order.
* Then, within each department, results are sorted by `salary` in descending order.

---

## 3. Using Column Positions

You can use the **column position** in the `SELECT` statement to sort:

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column_index [ASC|DESC];
```

**Example:**

```sql
SELECT first_name, last_name, salary
FROM employees
ORDER BY 3 DESC;  -- Sort by the 3rd column (salary)
```

> Note: Using column positions can make queries less readable and harder to maintain.

---

## 4. Sorting with Expressions

You can sort by expressions or calculated columns:

```sql
SELECT first_name, last_name, salary, salary * 1.1 AS adjusted_salary
FROM employees
ORDER BY adjusted_salary DESC;
```

---

## 5. Sorting with NULLs

By default, Oracle SQL sorts `NULL` values **last** in ascending order. You can explicitly control this:

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1 NULL [FIRST | LAST];
```

**Example:**

```sql
SELECT first_name, commission_pct
FROM employees
ORDER BY commission_pct NULLS FIRST;  -- Puts NULLs at the beginning
```
```sql
SELECT first_name, commission_pct
FROM employees
ORDER BY commission_pct NULLS LAST;   -- Puts NULLs at the end (default)
```

---

This file provides a **quick reference for sorting query results** in SQL using `ORDER BY`.