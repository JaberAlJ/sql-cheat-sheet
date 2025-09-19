# Hierarchical Queries in Oracle SQL 🌳

Hierarchical queries are used to retrieve data that has a **parent-child relationship**, such as organizational charts or bill-of-materials.  
Oracle SQL uses **`CONNECT BY`** and **`START WITH`** clauses for hierarchical queries.

---

## 1. Basic Syntax

```sql
SELECT column1, column2, ...
FROM table_name
START WITH condition_for_root_rows
CONNECT BY PRIOR parent_column = child_column;
```

* **`START WITH`**: Specifies the root (top-level) rows of the hierarchy.
* **`CONNECT BY`**: Defines the relationship between parent and child rows.
* **`PRIOR`**: Refers to the parent row in the hierarchy.

---

## 2. Example: Employee Hierarchy

Assume we have an `employees` table with `employee_id` and `manager_id`.

```sql
SELECT employee_id, manager_id, first_name, last_name, LEVEL
FROM employees
START WITH manager_id IS NULL
CONNECT BY PRIOR employee_id = manager_id;
```

**Explanation:**

* `LEVEL` is a pseudo-column that indicates the depth in the hierarchy.
* Employees without a manager (`manager_id IS NULL`) are the **root nodes**.
* `PRIOR employee_id = manager_id` links each employee to their manager.

---

## 3. Displaying Hierarchical Order

```sql
SELECT LPAD(' ', 2*(LEVEL-1)) || first_name AS employee_name, employee_id, manager_id
FROM employees
START WITH manager_id IS NULL
CONNECT BY PRIOR employee_id = manager_id;
```

* `LPAD` indents names according to their **hierarchy level**.
* Makes the hierarchy visually clear in query results.

---

## 4. Finding Subordinates of a Manager

```sql
SELECT employee_id, first_name, last_name, LEVEL
FROM employees
START WITH employee_id = 101
CONNECT BY PRIOR employee_id = manager_id;
```

* Retrieves all employees under the manager with `employee_id = 101`.
* Includes multiple levels of subordinates.

---

## 5. Using `CONNECT_BY_ISLEAF`

```sql
SELECT employee_id, first_name, CONNECT_BY_ISLEAF AS is_leaf
FROM employees
START WITH manager_id IS NULL
CONNECT BY PRIOR employee_id = manager_id;
```

* `CONNECT_BY_ISLEAF` returns **1 for leaf nodes** (no subordinates) and **0 for non-leaf nodes**.

---

## 6. Quick Tips ✅

* Use `LEVEL` to **determine hierarchy depth**.
* Use `PRIOR` to **refer to the parent row**.
* Combine with `ORDER SIBLINGS BY` to **sort siblings** in hierarchy order.
* Hierarchical queries are ideal for **reporting organizational or nested structures**.