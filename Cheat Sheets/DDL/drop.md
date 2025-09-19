# DROP Statements Cheat Sheet ❌

The `DROP` statement is used to **delete database objects permanently**. Be careful: dropped objects cannot be recovered unless you have a backup.

---

## 1. Drop Table
```sql
DROP TABLE table_name [CASCADE CONSTRAINTS];
```

**Examples:**

```sql
DROP TABLE employees;
```
```sql
-- Drop table along with all dependent constraints
DROP TABLE employees CASCADE CONSTRAINTS;
```

---

## 2. Drop View

```sql
DROP VIEW view_name;
```

**Examples:**

```sql
DROP VIEW emp_salary_view;
```

---

## 3. Drop Sequence

```sql
DROP SEQUENCE sequence_name;
```

**Examples:**

```sql
DROP SEQUENCE emp_seq;
```

---

## 4. Drop Index

```sql
DROP INDEX index_name;
```

**Examples:**

```sql
DROP INDEX emp_lastname_idx;
```

---

## 5. Drop User

```sql
DROP USER username [CASCADE];
```

**Examples:**

```sql
DROP USER hr_user;
```
```sql
-- Drop user and all objects owned by the user
DROP USER hr_user CASCADE;
```

---

**Tips:**

* Use `CASCADE` or `CASCADE CONSTRAINTS` carefully — it will remove all dependent objects or constraints.
* Dropped objects **cannot be recovered** unless a backup exists.
* Always double-check the object name before dropping.