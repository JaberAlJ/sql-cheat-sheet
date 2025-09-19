# INNER JOIN 🧩

The `INNER JOIN` keyword selects records that have **matching values** in both tables. It is the most common type of join used in SQL.

---

## Syntax

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```

* `table1`, `table2` → Names of the tables to join.
* `column_name` → Column used to match rows between tables.

---

## Example

### 1. Joining two tables

Assume we have the following tables:

**employees**

| emp\_id | name  | dept\_id |
| ------- | ----- | -------- |
| 1       | John  | 10       |
| 2       | Alice | 20       |
| 3       | Bob   | 10       |

**departments**

| dept\_id | dept\_name |
| -------- | ---------- |
| 10       | HR         |
| 20       | IT         |
| 30       | Finance    |

```sql
SELECT e.name, d.dept_name
FROM employees e
INNER JOIN departments d
ON e.dept_id = d.dept_id;
```

**Result:**

| name  | dept\_name |
| ----- | ---------- |
| John  | HR         |
| Alice | IT         |
| Bob   | HR         |

---

## Quick Tips

* Only rows with **matching keys** in both tables are returned.
* Rows without a match are **excluded**.
* Can join **multiple tables** using multiple `INNER JOIN` statements.

```sql
SELECT a.col1, b.col2, c.col3
FROM table1 a
INNER JOIN table2 b ON a.id = b.id
INNER JOIN table3 c ON b.id = c.id;
```