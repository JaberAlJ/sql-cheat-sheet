# GRANT Statement 🛡️

The `GRANT` statement is used in SQL to **give privileges** to users or roles.  
Privileges control what operations a user can perform on database objects.

---

## 1. Grant System Privileges

**Syntax:**

```sql
GRANT privilege_name
TO user_or_role
[WITH ADMIN OPTION];
```

* `privilege_name`: The system privilege to grant (e.g., `CREATE TABLE`, `ALTER USER`).
* `user_or_role`: The user or role receiving the privilege.
* `WITH ADMIN OPTION` (optional): Allows the user to **grant the same privilege to others**.

**Example:**

```sql
GRANT CREATE TABLE TO hr_user;
GRANT CREATE SESSION TO hr_user WITH ADMIN OPTION;
```

---

## 2. Grant Object Privileges

**Syntax:**

```sql
GRANT privilege_name
ON object_name
TO user_or_role
[WITH GRANT OPTION];
```

* `privilege_name`: The object privilege (e.g., `SELECT`, `INSERT`, `UPDATE`, `DELETE`).
* `object_name`: The table, view, sequence, or other object.
* `WITH GRANT OPTION` (optional): Allows the user to **grant the privilege on this object to others**.

**Example:**

```sql
GRANT SELECT, INSERT ON employees TO hr_user;
GRANT UPDATE ON employees TO hr_user WITH GRANT OPTION;
```

---

## 3. Quick Tips

* Use **roles** to group privileges and simplify management.
* Always follow the **principle of least privilege**: give only the privileges needed.
* `WITH GRANT OPTION` should be used **carefully** to avoid privilege abuse.