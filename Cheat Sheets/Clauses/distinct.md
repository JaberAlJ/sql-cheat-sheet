# DISTINCT Clause ✨

The `DISTINCT` clause in SQL is used to **remove duplicate rows** from the result set.  
It ensures that the values returned are **unique**.

---

## Syntax

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name
WHERE condition;
```

---

## Examples

### 1. Retrieve unique departments

```sql
SELECT DISTINCT department_id
FROM employees;
```

**Explanation:** Returns a list of **unique department IDs** from the `employees` table.

---

### 2. Unique combinations of columns

```sql
SELECT DISTINCT department_id, job_id
FROM employees;
```

**Explanation:** Returns unique **department and job combinations**, removing duplicates.

---

### 3. Using DISTINCT with WHERE

```sql
SELECT DISTINCT job_id
FROM employees
WHERE salary > 5000;
```

**Explanation:** Returns unique `job_id`s of employees whose salary is greater than 5000.

---

### Quick Tips

* `DISTINCT` applies to **all columns in the SELECT list**.
* Using `DISTINCT` on multiple columns considers the **entire row combination**.
* Can be combined with **ORDER BY** to get sorted unique results.