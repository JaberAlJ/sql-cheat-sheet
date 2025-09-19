# CROSS JOIN ✖️

A `CROSS JOIN` returns the **Cartesian product** of two tables.  
Every row from the first table is combined with every row from the second table.

---

## Syntax

```sql
SELECT columns
FROM table1
CROSS JOIN table2;
```

* Produces **all possible combinations** of rows.
* No `ON` clause is used.

---

## Example

Assume we have two tables:

**colors**

| color\_id | color\_name |
| --------- | ----------- |
| 1         | Red         |
| 2         | Blue        |

**sizes**

| size\_id | size\_name |
| -------- | ---------- |
| 1        | Small      |
| 2        | Large      |

```sql
SELECT c.color_name, s.size_name
FROM colors c
CROSS JOIN sizes s;
```

**Result:**

| color\_name | size\_name |
| ----------- | ---------- |
| Red         | Small      |
| Red         | Large      |
| Blue        | Small      |
| Blue        | Large      |

---

## Quick Tips

* Use `CROSS JOIN` when you need **all combinations** of two sets.
* Can result in **large datasets**; use with caution.
* Equivalent to listing multiple tables in the `FROM` clause without a join condition:

```sql
SELECT c.color_name, s.size_name
FROM colors c, sizes s;
```