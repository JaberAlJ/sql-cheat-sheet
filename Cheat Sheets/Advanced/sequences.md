# Sequences in Oracle SQL 🔢

A **sequence** is a database object that generates a **unique numeric value**, often used for **primary keys**.  
Sequences are independent of tables and can be incremented automatically.

---

## 1. Creating a Sequence

**Syntax:**
```sql
CREATE SEQUENCE sequence_name
START WITH initial_value
INCREMENT BY increment_value
[MINVALUE min_value | NOMINVALUE]
[MAXVALUE max_value | NOMAXVALUE]
[CYCLE | NOCYCLE]
[CACHE n | NOCACHE];
```

**Example:**

```sql
CREATE SEQUENCE emp_seq
START WITH 1
INCREMENT BY 1
NOCYCLE
CACHE 20;
```

* `START WITH 1` → sequence starts at 1
* `INCREMENT BY 1` → increments by 1
* `NOCYCLE` → stops at the maximum value
* `CACHE 20` → preallocates 20 sequence numbers for faster access

---

## 2. Using a Sequence

### a) Get the Next Value

```sql
sequence_name.NEXTVAL
```

**Example:**

```sql
INSERT INTO employees (employee_id, first_name, last_name)
VALUES (emp_seq.NEXTVAL, 'John', 'Doe');
```

### b) Get the Current Value

```sql
sequence_name.CURRVAL
```

* Can be used **after NEXTVAL has been called** in the session.

**Example:**

```sql
SELECT emp_seq.CURRVAL
FROM dual;
```

---

## 3. Altering a Sequence

**Syntax:**

```sql
ALTER SEQUENCE sequence_name
INCREMENT BY new_increment
MINVALUE new_min
MAXVALUE new_max
[CYCLE | NOCYCLE]
[CACHE n | NOCACHE];
```

**Example:**

```sql
ALTER SEQUENCE emp_seq
INCREMENT BY 5;
```

---

## 4. Dropping a Sequence

**Syntax:**

```sql
DROP SEQUENCE sequence_name;
```

**Example:**

```sql
DROP SEQUENCE emp_seq;
```

---

## 5. Quick Tips ✅

* Sequences are ideal for **generating unique IDs**.
* Use `CACHE` to improve performance for frequently used sequences.
* `NOCYCLE` prevents repeated values; `CYCLE` allows reuse after reaching max.
* Sequences are **independent of transactions**; generated numbers are not rolled back.