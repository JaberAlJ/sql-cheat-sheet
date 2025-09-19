# SELF JOIN 🔄

A `SELF JOIN` is a join in which a table is joined **with itself**.  
It is useful when you want to compare rows **within the same table**.

---

## Syntax

```sql
SELECT a.column1, b.column2
FROM table_name a
JOIN table_name b
ON a.common_column = b.common_column;
```

* `a` and `b` are **aliases** for the same table.
* Helps distinguish between the two instances of the table.

---

## Example

Assume we have an **employees** table with a `manager_id` column:

| emp\_id | name  | manager\_id |
| ------- | ----- | ----------- |
| 1       | John  | NULL        |
| 2       | Alice | 1           |
| 3       | Bob   | 1           |
| 4       | Carol | 2           |

We want to list each employee with their manager’s name:

```sql
SELECT e.name AS employee, m.name AS manager
FROM employees e
LEFT JOIN employees m
ON e.manager_id = m.emp_id;
```

**Result:**

| employee | manager |
| -------- | ------- |
| John     | NULL    |
| Alice    | John    |
| Bob      | John    |
| Carol    | Alice   |

---

## Quick Tips

* Always use **table aliases** to differentiate between the same table.
* Can be used with `INNER JOIN`, `LEFT JOIN`, etc., depending on whether you want unmatched rows.
* Useful for **hierarchical data**, e.g., employees and managers, categories and subcategories.