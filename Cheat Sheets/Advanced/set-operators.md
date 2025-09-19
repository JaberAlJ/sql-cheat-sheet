# Set Operators in Oracle SQL ⚡

**Set operators** combine the results of two or more queries into a single result set.  
Oracle SQL supports `UNION`, `UNION ALL`, `INTERSECT`, and `MINUS`.

---

## 1. UNION
Combines the results of **two queries** and **removes duplicates**.  
- Columns must be **same number and compatible data types**.  

**Syntax:**
```sql
SELECT column1, column2
FROM table1
UNION
SELECT column1, column2
FROM table2;
```

**Example:**

```sql
SELECT first_name, last_name
FROM employees
WHERE department_id = 10
UNION
SELECT first_name, last_name
FROM employees
WHERE department_id = 20;
```

---

## 2. UNION ALL

Combines the results of **two queries** but **includes duplicates**.

**Syntax:**

```sql
SELECT column1, column2
FROM table1
UNION ALL
SELECT column1, column2
FROM table2;
```

**Example:**

```sql
SELECT first_name, last_name
FROM employees
WHERE department_id = 10
UNION ALL
SELECT first_name, last_name
FROM employees
WHERE department_id = 20;
```

---

## 3. INTERSECT

Returns **only rows that appear in both queries**.

* Duplicates are automatically removed.

**Syntax:**

```sql
SELECT column1, column2
FROM table1
INTERSECT
SELECT column1, column2
FROM table2;
```

**Example:**

```sql
SELECT first_name, last_name
FROM employees
WHERE department_id = 10
INTERSECT
SELECT first_name, last_name
FROM employees
WHERE salary > 5000;
```

---

## 4. MINUS

Returns **rows from the first query that are not in the second query**.

* Also removes duplicates automatically.

**Syntax:**

```sql
SELECT column1, column2
FROM table1
MINUS
SELECT column1, column2
FROM table2;
```

**Example:**

```sql
SELECT first_name, last_name
FROM employees
WHERE department_id = 10
MINUS
SELECT first_name, last_name
FROM employees
WHERE salary > 5000;
```

---

## 5. Quick Tips ✅

* **Order of columns matters**; data types must match.
* Use `UNION ALL` instead of `UNION` for better performance when duplicates are not a concern.
* Set operators can be **chained**: `query1 UNION query2 MINUS query3`.
* Always use `ORDER BY` at the **end of the final query**, not inside individual queries.