# BETWEEN, IN, and LIKE Clauses 🔍

These clauses are used to **filter data** in SQL with specific conditions.  
They are often used in the `WHERE` clause to simplify queries.

---

## 1. BETWEEN … AND …  

The `BETWEEN` clause is used to filter values **within a range** (inclusive).

### Syntax
```sql
SELECT column1, column2
FROM table_name
WHERE column1 BETWEEN value1 AND value2;
```

### Example

```sql
SELECT first_name, last_name, salary
FROM employees
WHERE salary BETWEEN 3000 AND 6000;
```

**Explanation:** Retrieves employees whose salary is between 3000 and 6000 (inclusive).

---

## 2. IN (…)

The `IN` clause is used to filter values **matching any value in a list**.

### Syntax

```sql
SELECT column1, column2
FROM table_name
WHERE column1 IN (value1, value2, ...);
```

### Example

```sql
SELECT first_name, last_name, department_id
FROM employees
WHERE department_id IN (10, 20, 30);
```

**Explanation:** Retrieves employees in department 10, 20, or 30.

---

## 3. LIKE

The `LIKE` clause is used for **pattern matching** with strings.

### Wildcards

* `%` → matches **zero or more characters**
* `_` → matches **exactly one character**

### Syntax

```sql
SELECT column1, column2
FROM table_name
WHERE column1 LIKE 'pattern';
```

### Examples

**a) Starts with J**

```sql
SELECT first_name, last_name
FROM employees
WHERE first_name LIKE 'J%';
```

**b) Ends with n**

```sql
SELECT first_name, last_name
FROM employees
WHERE first_name LIKE '%n';
```

**c) Contains "ar"**

```sql
SELECT first_name, last_name
FROM employees
WHERE first_name LIKE '%ar%';
```

**d) Second letter is "a"**

```sql
SELECT first_name, last_name
FROM employees
WHERE first_name LIKE '_a%';
```

---

### Quick Tips

* `BETWEEN` works with **numbers, dates, and text**.
* `IN` is cleaner than multiple `OR` conditions.
* `LIKE` is **case-insensitive** in some databases (e.g., Oracle by default).
* Combine with `NOT` to exclude values: `NOT BETWEEN`, `NOT IN`, `NOT LIKE`.