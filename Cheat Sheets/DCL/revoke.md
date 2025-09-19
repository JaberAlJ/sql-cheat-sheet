# REVOKE Statement 🛑

The `REVOKE` statement is used in SQL to **remove previously granted privileges** from users or roles.  
This helps maintain security and control over database access.

---

## 1. Revoke System Privileges

**Syntax:**

```sql
REVOKE privilege_name
FROM user_or_role;
```

* `privilege_name`: The system privilege to remove (e.g., `CREATE TABLE`, `ALTER USER`).
* `user_or_role`: The user or role losing the privilege.

**Example:**

```sql
REVOKE CREATE TABLE FROM hr_user;
REVOKE CREATE SESSION FROM hr_user;
```

---

## 2. Revoke Object Privileges

**Syntax:**

```sql
REVOKE privilege_name
ON object_name
FROM user_or_role;
```

* `privilege_name`: The object privilege (e.g., `SELECT`, `INSERT`, `UPDATE`, `DELETE`).
* `object_name`: The table, view, sequence, or other object.
* `user_or_role`: The user or role losing the privilege.

**Example:**

```sql
REVOKE SELECT, INSERT ON employees FROM hr_user;
REVOKE UPDATE ON employees FROM hr_user;
```

---

## 3. Quick Tips

* Revoking a privilege **automatically revokes** any dependent privileges granted with `WITH GRANT OPTION`.
* Regularly review privileges to ensure **users have only necessary access**.
* Use `REVOKE` together with `GRANT` to maintain tight security control.