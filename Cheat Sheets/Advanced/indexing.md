# Indexing in Oracle SQL 📂

Indexes are database objects that **improve the speed of data retrieval** from tables.  
They can significantly enhance query performance, especially on large tables.

---

## 1. Why Use Indexes?
- Reduce query response time by avoiding full table scans.  
- Useful for **WHERE clauses, JOIN conditions, and ORDER BY clauses**.  
- Can improve **performance of searches** but may slightly slow down **INSERT, UPDATE, DELETE** operations.

---

## 2. Basic Index

**Syntax:**
```sql
CREATE INDEX index_name
ON table_name (column1, column2, ...);
```

**Example:**

```sql
CREATE INDEX idx_emp_lastname
ON employees (last_name);
```

* Creates an index on the `last_name` column of `employees` table.

---

## 3. Unique Index

Ensures that the indexed column(s) contain **unique values**.

**Syntax:**

```sql
CREATE UNIQUE INDEX index_name
ON table_name (column1, column2, ...);
```

**Example:**

```sql
CREATE UNIQUE INDEX idx_emp_email
ON employees (email);
```

* Ensures no duplicate emails exist in the `employees` table.

---

## 4. Composite (Multi-column) Index

Indexes **multiple columns** together. Useful when queries filter on more than one column.

**Syntax:**

```sql
CREATE INDEX index_name
ON table_name (column1, column2);
```

**Example:**

```sql
CREATE INDEX idx_emp_dept_salary
ON employees (department_id, salary);
```

* Optimizes queries filtering on both `department_id` and `salary`.

---

## 5. Bitmap Index

Efficient for **columns with low cardinality** (few distinct values).

* Ideal for **gender, status, or category columns**.

**Syntax:**

```sql
CREATE BITMAP INDEX index_name
ON table_name (column_name);
```

**Example:**

```sql
CREATE BITMAP INDEX idx_emp_gender
ON employees (gender);
```

---

## 6. Function-based Index

Indexes the **result of a function** applied to a column.

**Syntax:**

```sql
CREATE INDEX index_name
ON table_name (UPPER(column_name));
```

**Example:**

```sql
CREATE INDEX idx_emp_upper_lastname
ON employees (UPPER(last_name));
```

* Optimizes queries like `WHERE UPPER(last_name) = 'SMITH'`.

---

## 7. Dropping an Index

**Syntax:**

```sql
DROP INDEX index_name;
```

**Example:**

```sql
DROP INDEX idx_emp_lastname;
```

---

## 8. Quick Tips ✅

* Indexes **speed up SELECT queries** but **slow down DML operations**.
* Avoid excessive indexing; use **indexes on frequently queried columns**.
* Use **EXPLAIN PLAN** to check if indexes are being utilized.
* Combine **function-based or composite indexes** for complex queries.