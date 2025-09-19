# HAVING Clause 🛠️

The `HAVING` clause in SQL is used to **filter groups** created by the `GROUP BY` clause.  
It is similar to `WHERE`, but `WHERE` filters rows **before grouping**, while `HAVING` filters **after grouping**.

---

## Syntax

```sql
SELECT column1, aggregate_function(column2)
FROM table_name
WHERE condition
GROUP BY column1
HAVING aggregate_condition;
```

---

## Examples

### 1. Departments with more than 5 employees

```sql
SELECT department_id, COUNT(*) AS total_employees
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 5;
```

**Explanation:** Shows only departments that have more than 5 employees.

---

### 2. Departments with total salary above 20000

```sql
SELECT department_id, SUM(salary) AS total_salary
FROM employees
GROUP BY department_id
HAVING SUM(salary) > 20000;
```

**Explanation:** Displays departments where the total salary exceeds 20000.

---

### 3. Using `HAVING` with `WHERE`

```sql
SELECT department_id, COUNT(*) AS total_employees
FROM employees
WHERE salary > 3000
GROUP BY department_id
HAVING COUNT(*) > 2;
```

**Explanation:**

1. Filters employees with salary > 3000 (`WHERE`).
2. Groups by `department_id` (`GROUP BY`).
3. Shows only groups with more than 2 employees (`HAVING`).

---

### Quick Tips

* `HAVING` is **only used with GROUP BY**.
* You can use multiple conditions with `AND`/`OR`.
* Remember: `WHERE` filters rows **before aggregation**, `HAVING` filters **after aggregation**.