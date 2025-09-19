# OUTER JOIN 🌐

An `OUTER JOIN` returns rows that **have matching values** in one table and **also includes unmatched rows** from one or both tables.  
There are three types: **LEFT OUTER JOIN**, **RIGHT OUTER JOIN**, and **FULL OUTER JOIN**.

---

## 1. LEFT OUTER JOIN

Returns all rows from the **left table** and matched rows from the right table.  
If there is no match, `NULL` is returned for columns from the right table.

### Syntax

```sql
SELECT columns
FROM table1
LEFT OUTER JOIN table2
ON table1.column_name = table2.column_name;
```

### Example

```sql
SELECT e.name, d.dept_name
FROM employees e
LEFT OUTER JOIN departments d
ON e.dept_id = d.dept_id;
```

**Result:**

| name  | dept\_name |                                |
| ----- | ---------- | ------------------------------ |
| John  | HR         |                                |
| Alice | IT         |                                |
| Bob   | HR         |                                |
| Eve   | NULL       | -- employee with no department |

---

## 2. RIGHT OUTER JOIN

Returns all rows from the **right table** and matched rows from the left table.
If there is no match, `NULL` is returned for columns from the left table.

### Syntax

```sql
SELECT columns
FROM table1
RIGHT OUTER JOIN table2
ON table1.column_name = table2.column_name;
```

### Example

```sql
SELECT e.name, d.dept_name
FROM employees e
RIGHT OUTER JOIN departments d
ON e.dept_id = d.dept_id;
```

**Result:**

| name  | dept\_name |                                |
| ----- | ---------- | ------------------------------ |
| John  | HR         |                                |
| Alice | IT         |                                |
| Bob   | HR         |                                |
| NULL  | Finance    | -- department with no employee |

---

## 3. FULL OUTER JOIN

Returns all rows when there is a match in **either table**.
Unmatched rows from both tables will have `NULL` in the missing columns.

### Syntax

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name;
```

### Example

```sql
SELECT e.name, d.dept_name
FROM employees e
FULL OUTER JOIN departments d
ON e.dept_id = d.dept_id;
```

**Result:**

| name  | dept\_name |
| ----- | ---------- |
| John  | HR         |
| Alice | IT         |
| Bob   | HR         |
| Eve   | NULL       |
| NULL  | Finance    |

---

## Quick Tips

* Use `LEFT OUTER JOIN` when you want **all rows from the left table**.
* Use `RIGHT OUTER JOIN` when you want **all rows from the right table**.
* Use `FULL OUTER JOIN` when you want **all rows from both tables**.
* `OUTER` keyword is optional in Oracle: `LEFT JOIN` works the same as `LEFT OUTER JOIN`.