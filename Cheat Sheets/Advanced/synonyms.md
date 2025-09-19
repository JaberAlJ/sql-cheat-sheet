# Synonyms in Oracle SQL 🔗

A **synonym** is an **alias** for a database object (table, view, sequence, etc.).  
Synonyms simplify object references and improve code readability, especially when accessing objects in **other schemas**.

---

## 1. Types of Synonyms
1. **Private Synonym** – Available only to the user who creates it.  
2. **Public Synonym** – Available to **all users** in the database.

---

## 2. Creating a Private Synonym

**Syntax:**
```sql
CREATE SYNONYM synonym_name FOR object_name;
```

**Example:**

```sql
CREATE SYNONYM emp_syn FOR hr.employees;
```

* Allows the current user to reference `hr.employees` simply as `emp_syn`.

---

## 3. Creating a Public Synonym

**Syntax:**

```sql
CREATE PUBLIC SYNONYM synonym_name FOR object_name;
```

**Example:**

```sql
CREATE PUBLIC SYNONYM emp_syn FOR hr.employees;
```

* Now all users can reference `hr.employees` using `emp_syn`.

---

## 4. Dropping a Synonym

### a) Private Synonym

```sql
DROP SYNONYM synonym_name;
```

**Example:**

```sql
DROP SYNONYM emp_syn;
```

### b) Public Synonym

```sql
DROP PUBLIC SYNONYM synonym_name;
```

**Example:**

```sql
DROP PUBLIC SYNONYM emp_syn;
```

---

## 5. Quick Tips ✅

* Synonyms **hide schema names** for easier SQL writing.
* Public synonyms **avoid the need for fully qualified object names** for multiple users.
* They are **read-only references**; cannot change the underlying object.
* Useful in **large applications** to simplify object references across schemas.