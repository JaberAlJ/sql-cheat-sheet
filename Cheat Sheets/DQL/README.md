# Data Query Language (DQL) 📋

This folder contains **cheat sheets for SQL DQL statements**, which are used to **query and retrieve data** from database tables.

These files provide **syntax, examples, and best practices** for quickly referencing common query operations.

---

## 📂 What You’ll Find Here

1. **[select.md](select.md) 📋 — SELECT Statement**
   Retrieve data from one or more tables, use expressions, aliases, and subqueries.

2. **[filter.md](filter.md) 🧹 — Filtering Data (WHERE Clause)**
   Filter rows using conditions, comparison operators, logical operators, pattern matching, and NULL checks.

3. **[sort.md](sort.md) 🔀 — Sorting Data (ORDER BY)**
   Sort query results by one or more columns in ascending or descending order, handle NULLs, and sort by expressions.

4. **[group.md](group.md) 📊 — Grouping Data (GROUP BY & HAVING)**
   Aggregate data using functions like COUNT, SUM, AVG, MIN, MAX and filter grouped data using HAVING.

---

## ⚡ Quick Tips

* **Always use `ORDER BY`** when using `FETCH FIRST N ROWS ONLY` to ensure consistent results.
* **Use `DISTINCT` carefully**; it removes duplicates but can slow down queries on large tables.
* **`WHERE` filters rows before aggregation**, while **`HAVING` filters after aggregation**.
* **NULL values** behave differently in comparisons; use `IS NULL` or `IS NOT NULL`.
* **Combine multiple conditions** with `AND`, `OR`, `NOT` for precise filtering.
* **Aliases (`AS`)** improve readability for calculated columns or renamed outputs.
* **Column positions in ORDER BY** can be used but may reduce query clarity.

---

This cheat sheet collection is designed for **quick reference and learning**, especially for students, developers, and data analysts working with SQL.