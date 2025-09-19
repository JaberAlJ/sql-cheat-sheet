# GROUP BY Clause 📊

The `GROUP BY` clause in SQL is used to **group rows that have the same values** in specified columns.  
It is often used with **aggregate functions** like `COUNT`, `SUM`, `AVG`, `MIN`, and `MAX`.

---

## Syntax

```sql
SELECT column1, aggregate_function(column2)
FROM table_name
WHERE condition
GROUP BY column1;
```

---

## Examples

### 1. Count employees in each department

```sql
SELECT department_id, COUNT(*) AS total_employees
FROM employees
GROUP BY department_id;
```

**Explanation:** Groups employees by `department_id` and counts how many employees are in each department.

---

### 2. Sum of salaries by department

```sql
SELECT department_id, SUM(salary) AS total_salary
FROM employees
GROUP BY department_id;
```

**Explanation:** Groups employees by `department_id` and calculates the total salary per department.

---

### 3. Average salary by job

```sql
SELECT job_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY job_id;
```

**Explanation:** Groups employees by `job_id` and calculates the average salary for each job.

---

### 4. With `WHERE` clause

```sql
SELECT department_id, COUNT(*) AS total_employees
FROM employees
WHERE salary > 4000
GROUP BY department_id;
```

**Explanation:** Groups only employees with salary > 4000 by department.

---

### Quick Tips

* Always include **aggregate functions** when using `GROUP BY`.
* Columns in `SELECT` that are **not aggregated** must be included in `GROUP BY`.
* Combine with `HAVING` to filter groups after aggregation.