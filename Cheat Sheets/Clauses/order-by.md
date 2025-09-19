# ORDER BY Clause ⬆️⬇️

The `ORDER BY` clause in SQL is used to **sort the result set** by one or more columns.  
By default, it sorts in **ascending order**. You can also sort in **descending order**.

---

## Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC];
```

* `ASC` → Ascending order (default)
* `DESC` → Descending order

---

## Examples

### 1. Sort employees by salary ascending

```sql
SELECT first_name, last_name, salary
FROM employees
ORDER BY salary;
```

**Explanation:** Retrieves all employees sorted by `salary` from lowest to highest.

---

### 2. Sort employees by salary descending

```sql
SELECT first_name, last_name, salary
FROM employees
ORDER BY salary DESC;
```

**Explanation:** Retrieves all employees sorted by `salary` from highest to lowest.

---

### 3. Sort by multiple columns

```sql
SELECT department_id, first_name, last_name, salary
FROM employees
ORDER BY department_id ASC, salary DESC;
```

**Explanation:**

* First, sorts employees by `department_id` ascending.
* Within each department, sorts by `salary` descending.

---

### 4. Using `ORDER BY` with `WHERE`

```sql
SELECT first_name, last_name, hire_date
FROM employees
WHERE hire_date >= TO_DATE('2020-01-01', 'YYYY-MM-DD')
ORDER BY hire_date ASC;
```

**Explanation:** Retrieves employees hired after Jan 1, 2020, sorted by hire date.

---

### Quick Tips

* `ORDER BY` is usually placed **at the end** of the query.
* Can sort **alphabetically, numerically, or by date**.
* Use multiple columns to control sorting priority.