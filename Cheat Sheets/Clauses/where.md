# WHERE Clause 📍

The `WHERE` clause in SQL is used to **filter records** based on a specified condition.  
It is commonly used with `SELECT`, `UPDATE`, and `DELETE` statements.

---

## Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

---

## Examples

### 1. Filter by a single condition

```sql
SELECT first_name, last_name, salary
FROM employees
WHERE salary > 5000;
```

**Explanation:** Retrieves employees with a salary greater than 5000.

---

### 2. Filter using `AND`

```sql
SELECT first_name, last_name, department_id
FROM employees
WHERE department_id = 10 AND salary > 4000;
```

**Explanation:** Retrieves employees in department 10 with a salary over 4000.

---

### 3. Filter using `OR`

```sql
SELECT first_name, last_name, department_id
FROM employees
WHERE department_id = 10 OR department_id = 20;
```

**Explanation:** Retrieves employees in department 10 **or** 20.

---

### 4. Filter using `NOT`

```sql
SELECT first_name, last_name
FROM employees
WHERE NOT department_id = 30;
```

**Explanation:** Retrieves employees **not** in department 30.

---

### 5. Filter with comparison operators

```sql
SELECT first_name, last_name, hire_date
FROM employees
WHERE hire_date >= TO_DATE('2020-01-01', 'YYYY-MM-DD');
```

---

### 6. Filter with pattern matching (`LIKE`)

```sql
SELECT first_name, last_name
FROM employees
WHERE first_name LIKE 'J%';
```

**Explanation:** Retrieves employees whose first name starts with 'J'.

---

### Quick Tips

* Always check **data types** when filtering (e.g., use `TO_DATE` for dates).
* Combine conditions with `AND`/`OR` for more complex filters.
* Use parentheses `()` to group conditions and control precedence.