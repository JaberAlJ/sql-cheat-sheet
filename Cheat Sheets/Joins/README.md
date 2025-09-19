# SQL Joins 📌

This folder contains cheat sheets for **SQL Joins**, which are used to combine rows from **two or more tables** based on related columns.  

Joins are essential for querying **related data** efficiently in relational databases.

---

## Types of Joins

1. **[INNER JOIN](inner-join.md) 🧩**  
   Returns only the rows with **matching values** in both tables.

2. **[OUTER JOIN](outer-join.md) 🌐**  
   Returns rows with matches **and also unmatched rows** from one or both tables.  
   Includes:
   - **LEFT OUTER JOIN** – all rows from the left table  
   - **RIGHT OUTER JOIN** – all rows from the right table  
   - **FULL OUTER JOIN** – all rows from both tables

3. **[SELF JOIN](self-join.md) 🔄**  
   A table is joined **with itself** using aliases, useful for hierarchical data.

4. **[CROSS JOIN](cross-join.md) ✖️**  
   Returns the **Cartesian product** of two tables (all possible combinations).

---

## Quick Tips

- Use **table aliases** when joining multiple tables or performing self joins.  
- Choose the type of join depending on whether you want **only matching rows** or **all rows including unmatched**.  
- `INNER JOIN` is the most common; `CROSS JOIN` can produce **very large results** if tables are big.  