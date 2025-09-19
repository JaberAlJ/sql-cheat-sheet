# Analytic Functions in Oracle SQL 📊

Analytic functions compute **aggregate or ranking values** over a **set of rows** related to the current row.  
Unlike regular aggregate functions, **analytic functions do not collapse rows**.

---

## 1. ROW_NUMBER()
Assigns a **unique sequential number** to each row within a partition.

**Syntax:**
```sql
ROW_NUMBER() OVER (
    PARTITION BY column1
    ORDER BY column2 [ASC|DESC]
) AS row_num
```

**Example:**

```sql
SELECT employee_id, department_id, salary,
       ROW_NUMBER() OVER (PARTITION BY department_id ORDER BY salary DESC) AS row_num
FROM employees;
```

* Gives the **highest salary in each department a row number of 1**.

---

## 2. RANK()

Assigns a **rank** to each row within a partition with **ties getting the same rank**.

* Skips ranks for ties.

**Syntax:**

```sql
RANK() OVER (
    PARTITION BY column1
    ORDER BY column2 [ASC|DESC]
) AS rank_num
```

**Example:**

```sql
SELECT employee_id, department_id, salary,
       RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rank_num
FROM employees;
```

* If two employees have the same salary, they get the **same rank**, and the next rank is skipped.

---

## 3. DENSE\_RANK()

Similar to `RANK()`, but **does not skip ranks** for ties.

**Syntax:**

```sql
DENSE_RANK() OVER (
    PARTITION BY column1
    ORDER BY column2 [ASC|DESC]
) AS dense_rank_num
```

**Example:**

```sql
SELECT employee_id, department_id, salary,
       DENSE_RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS dense_rank_num
FROM employees;
```

* Tied salaries get the same rank, but the **next rank is consecutive**.

---

## 4. NTILE(n)

Divides the result set into **n approximately equal groups** and assigns a group number.

**Syntax:**

```sql
NTILE(n) OVER (
    PARTITION BY column1
    ORDER BY column2 [ASC|DESC]
) AS group_num
```

**Example:**

```sql
SELECT employee_id, department_id, salary,
       NTILE(4) OVER (PARTITION BY department_id ORDER BY salary DESC) AS quartile
FROM employees;
```

* Divides employees into **quartiles** based on salary within each department.

---

## 5. LAG() and LEAD()

Access **previous or next row values** in the partition.

**Syntax:**

```sql
LAG(column, offset, default) OVER (PARTITION BY col1 ORDER BY col2) AS prev_val
LEAD(column, offset, default) OVER (PARTITION BY col1 ORDER BY col2) AS next_val
```

**Example:**

```sql
SELECT employee_id, department_id, salary,
       LAG(salary, 1, 0) OVER (PARTITION BY department_id ORDER BY salary) AS prev_salary,
       LEAD(salary, 1, 0) OVER (PARTITION BY department_id ORDER BY salary) AS next_salary
FROM employees;
```

* `LAG` fetches the **previous row’s salary**, `LEAD` fetches the **next row’s salary**.

---

## 6. Quick Tips ✅

* Always use `ORDER BY` inside the `OVER()` clause to define the sequence.
* `PARTITION BY` is optional; without it, the function applies to the **entire result set**.
* Analytic functions **do not reduce the number of rows**, unlike aggregate functions.
* Useful for **reporting, ranking, and trend analysis** in SQL.