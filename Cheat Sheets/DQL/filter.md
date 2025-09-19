# Filtering Data with WHERE Clause 🧹

The `WHERE` clause is used in SQL to **filter records** that meet specific conditions. It is one of the most commonly used clauses in **Data Query Language (DQL)**.

---

## 1. Basic Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Example:**

```sql
SELECT first_name, last_name, salary
FROM employees
WHERE department_id = 10;
```

---

## 2. Comparison Operators

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column [operator] condition;
```

| Operator | Description                 | Example                      |
| -------- | --------------------------- | ---------------------------- |
| =        | Equal to                    | salary = 5000                |
| != or <> | Not equal to                | department\_id <> 20         |
| >        | Greater than                | salary > 3000                |
| <        | Less than                   | salary < 5000                |
| >=       | Greater than or equal to    | salary >= 4000               |
| <=       | Less than or equal to       | salary <= 6000               |
| BETWEEN  | Between a range             | salary BETWEEN 3000 AND 5000 |
| IN       | Matches any value in a list | department\_id IN (10,20,30) |
| LIKE     | Pattern matching            | first\_name LIKE 'J%'        |
| IS NULL  | Checks for NULL values      | commission\_pct IS NULL      |

---

## 3. Using AND, OR, NOT

Combine multiple conditions:

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 [AND | OR | NOT] condition2;
```

**Example:**

```sql
SELECT first_name, last_name, salary
FROM employees
WHERE department_id = 10 AND salary > 4000;
```

* `AND` — All conditions must be true.
* `OR` — At least one condition must be true.
* `NOT` — Negates a condition.

---

## 4. Pattern Matching with LIKE

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column LIKE condition;
```

**Example:**

* `%` — Any sequence of characters
* `_` — Single character

```sql
SELECT first_name
FROM employees
WHERE first_name LIKE 'A%';   -- Names starting with A

SELECT first_name
FROM employees
WHERE first_name LIKE '_a%';  -- Second character is 'a'
```

---

## 5. Checking for NULL Values

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column IS [NULL | NOT NULL];
```

**Example:**

```sql
SELECT first_name, commission_pct
FROM employees
WHERE commission_pct IS NULL;

SELECT first_name, commission_pct
FROM employees
WHERE commission_pct IS NOT NULL;
```

---

## 6. Using Subqueries in WHERE

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

This file gives a **quick reference for filtering rows in SQL** using `WHERE` and related operators.