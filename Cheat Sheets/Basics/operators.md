# SQL Operators ⚙️

Operators in Oracle SQL are special symbols or keywords used to perform operations on values, columns, and expressions.  
They are categorized into:

- **Arithmetic Operators**
- **Comparison Operators**
- **Logical Operators**
- **Other Useful Operators**
- **Wildcard Patterns for LIKE**
- **Operator Precedence**

---

## 1. Arithmetic Operators ➕➖✖️➗

| Operator | Description            | Example              | Result |
|----------|------------------------|----------------------|--------|
| `+`      | Addition               | `5 + 3`              | `8`    |
| `-`      | Subtraction            | `10 - 4`             | `6`    |
| `*`      | Multiplication         | `7 * 2`              | `14`   |
| `/`      | Division               | `20 / 5`             | `4`    |
| `**`     | Exponentiation (power) | `2 ** 3`             | `8`    |

---

## 2. Comparison Operators 🔍

Used to compare two values and return `TRUE`, `FALSE`, or `UNKNOWN`.

| Operator       | Description                                | Example                 |
|----------------|--------------------------------------------|-------------------------|
| `=`            | Equal to                                   | `salary = 5000`         |
| `!=` or `<>`   | Not equal to                               | `dept_id <> 10`         |
| `>`            | Greater than                               | `marks > 50`            |
| `<`            | Less than                                  | `age < 30`              |
| `>=`           | Greater than or equal to                   | `hire_date >= '01-JAN-25'` |
| `<=`           | Less than or equal to                      | `salary <= 10000`       |
| `BETWEEN`      | Between two values (inclusive)             | `salary BETWEEN 5000 AND 8000` |
| `IN`           | Matches any value in a list                | `dept_id IN (10, 20, 30)` |
| `LIKE`         | Pattern matching with wildcards (`%` , `_`)| `name LIKE 'J%'` → starts with J |
| `IS NULL`      | Checks if value is `NULL`                  | `commission IS NULL`    |

---

## 3. Logical Operators 🔗

Used to combine conditions in `WHERE` or `HAVING` clauses.

| Operator | Description                                   | Example                                |
|----------|-----------------------------------------------|----------------------------------------|
| `AND`    | Both conditions must be true                  | `salary > 5000 AND dept_id = 10`       |
| `OR`     | At least one condition must be true           | `dept_id = 10 OR dept_id = 20`         |
| `NOT`    | Negates the condition                         | `NOT (salary < 3000)`                  |

---

## 4. Other Useful Operators 🛠️

| Operator          | Description                                      | Example                                  |
|-------------------|--------------------------------------------------|------------------------------------------|
| `||` (Concatenation) | Joins two strings                              | `'Hello ' || 'World'` → `Hello World`    |
| `DISTINCT`        | Removes duplicate values in result set           | `SELECT DISTINCT dept_id FROM employees;` |
| `ALL`             | Compares a value to **all values** in a subquery | `salary > ALL (SELECT salary FROM interns)` |
| `ANY` / `SOME`    | Compares a value to **any value** in a subquery  | `salary > ANY (SELECT salary FROM interns)` |
| `EXISTS`          | Returns true if subquery returns any rows        | `EXISTS (SELECT 1 FROM employees WHERE dept_id = 10)` |

---

## 5. Wildcard Patterns for LIKE 🔎

The `LIKE` operator is used for **pattern matching** in string comparisons.  

| Wildcard | Description                                            | Example                       | Matches                   |
|----------|--------------------------------------------------------|-------------------------------|---------------------------|
| `%`      | Represents zero or more characters                     | `name LIKE 'S%'`              | `Sam`, `Smith`, `SQL`     |
| `_`      | Represents a single character                          | `name LIKE '_a%'`             | `Sam`, `Max`, `Jack`      |
| `ESCAPE` | Defines an escape character for literals in the pattern| `name LIKE '50\%%' ESCAPE '\'`| `50% off`                 |

---

## 6. Operator Precedence 🧮

When multiple operators are used in an expression, Oracle SQL follows a **precedence order** (priority).  

From **highest to lowest**:

1. **Exponentiation** (`**`)
2. **Unary +, -** (e.g., `-5`)
3. **Multiplication, Division** (`*`, `/`)
4. **Addition, Subtraction** (`+`, `-`)
5. **Comparison Operators** (`=`, `!=`, `<`, `>`, `<=`, `>=`, `BETWEEN`, `IN`, `LIKE`, `IS NULL`)
6. **NOT**
7. **AND**
8. **OR**

---

## 🔑 Key Notes
- Use **parentheses `()`** to control precedence in complex expressions.
- `AND` has higher precedence than `OR`.
- Always check for `NULL` using `IS NULL` or `IS NOT NULL`, not `= NULL`.
- Use `%` and `_` carefully in `LIKE` patterns to avoid unexpected matches.
- Always use **parentheses `()`** for clarity in complex conditions.

---

✅ This cheat sheet provides a **quick lookup** for the most common Oracle SQL operators.
