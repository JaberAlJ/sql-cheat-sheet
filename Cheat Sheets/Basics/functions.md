# Oracle SQL Single-Row and Multi-Row Functions 🛠️

Single-row functions operate on **one row at a time** and return **one result per row**.  
Multi-row (aggregate) functions operate on **multiple rows** and return **a single summarized result**.  

Categories:
- **Character Functions**
- **Number Functions**
- **Date/Time Functions**
- **Conversion Functions**
- **General Functions**
- **Aggregate (Multi-Row) Functions**

---

## 1. Character Functions ✍️

### Case Conversion
| Function | Description                | Example                           | Result        |
|----------|----------------------------|-----------------------------------|---------------|
| `UPPER(x)` | Converts to uppercase     | `UPPER('oracle')`                 | `ORACLE`      |
| `LOWER(x)` | Converts to lowercase     | `LOWER('SQL')`                    | `sql`         |
| `INITCAP(x)` | Capitalizes first letter of each word | `INITCAP('oracle sql')` | `Oracle Sql` |

### Character Manipulation
| Function       | Description                                       | Example                               | Result        |
|----------------|---------------------------------------------------|---------------------------------------|---------------|
| `CONCAT(a,b)`  | Joins two strings (same as `a || b`)              | `CONCAT('Hello','World')`             | `HelloWorld`  |
| `SUBSTR(x,m,n)`| Extracts substring from position `m`, length `n`  | `SUBSTR('Database',2,3)`              | `ata`         |
| `LENGTH(x)`    | Returns string length                             | `LENGTH('Oracle')`                    | `6`           |
| `INSTR(x,y)`   | Finds position of substring `y` in string `x`     | `INSTR('Oracle SQL','SQL')`           | `8`           |
| `LPAD(x,n,p)`  | Pads left side with `p` until length `n`          | `LPAD('123',5,'0')`                   | `00123`       |
| `RPAD(x,n,p)`  | Pads right side with `p` until length `n`         | `RPAD('123',5,'*')`                   | `123**`       |
| `TRIM(x)`      | Removes leading/trailing spaces (or chars)        | `TRIM('  Oracle  ')`                  | `Oracle`      |
| `REPLACE(x,y,z)` | Replaces substring `y` with `z` in string `x`   | `REPLACE('2025-09-19','-','/')`       | `2025/09/19`  |

---

## 2. Number Functions 🔢

| Function           | Description                                | Example               | Result  |
|--------------------|--------------------------------------------|-----------------------|---------|
| `ROUND(x,n)`       | Rounds to `n` decimal places               | `ROUND(123.456,2)`    | `123.46`|
| `TRUNC(x,n)`       | Truncates without rounding                 | `TRUNC(123.456,2)`    | `123.45`|
| `MOD(m,n)`         | Returns remainder of `m/n`                 | `MOD(10,3)`           | `1`     |
| `POWER(x,y)`       | Returns `x` raised to the power `y`        | `POWER(2,3)`          | `8`     |
| `SQRT(x)`          | Square root                                | `SQRT(25)`            | `5`     |
| `ABS(x)`           | Absolute value                             | `ABS(-15)`            | `15`    |
| `SIGN(x)`          | Returns -1, 0, or 1 depending on sign      | `SIGN(-20)`           | `-1`    |
| `FLOOR(x)`         | Largest integer ≤ `x`                      | `FLOOR(15.9)`         | `15`    |
| `CEIL(x)`          | Smallest integer ≥ `x`                     | `CEIL(15.1)`          | `16`    |

---

## 3. Date/Time Functions ⏰

| Function                      | Description                                     | Example                                      | Result                  |
|-------------------------------|-------------------------------------------------|----------------------------------------------|-------------------------|
| `SYSDATE`                     | Current database date and time                  | `SYSDATE`                                    | `19-SEP-25`             |
| `CURRENT_DATE`                | Current date in session time zone               | `CURRENT_DATE`                               | `19-SEP-25`             |
| `CURRENT_TIMESTAMP`           | Current timestamp with fractional seconds & TZ  | `CURRENT_TIMESTAMP`                          | `19-SEP-25 13:45:30`    |
| `ADD_MONTHS(d,n)`             | Adds `n` months to date `d`                     | `ADD_MONTHS(SYSDATE,2)`                      | Two months later        |
| `MONTHS_BETWEEN(d1,d2)`       | Months between two dates                        | `MONTHS_BETWEEN('01-JUL-25','01-JAN-25')`    | `6`                     |
| `NEXT_DAY(d,'day')`           | Next occurrence of given weekday after date     | `NEXT_DAY(SYSDATE,'FRIDAY')`                 | Next Friday             |
| `LAST_DAY(d)`                 | Last day of the month for given date            | `LAST_DAY(SYSDATE)`                          | `30-SEP-25` (if Sept)   |
| `ROUND(d, fmt)`               | Rounds date to nearest unit (e.g., month, year) | `ROUND(SYSDATE,'MONTH')`                     | First day of next month |
| `TRUNC(d, fmt)`               | Truncates date to given unit                    | `TRUNC(SYSDATE,'YEAR')`                      | First day of year       |

---

## 4. Conversion Functions 🔄

| Function                        | Description                                      | Example                                | Result           |
|---------------------------------|--------------------------------------------------|----------------------------------------|------------------|
| `TO_CHAR(x, fmt)`               | Converts number/date to string                   | `TO_CHAR(SYSDATE,'DD-MON-YYYY')`       | `19-SEP-2025`    |
| `TO_DATE(x, fmt)`               | Converts string to date                          | `TO_DATE('19-09-2025','DD-MM-YYYY')`   | `19-SEP-25`      |
| `TO_NUMBER(x, fmt)`             | Converts string to number                        | `TO_NUMBER('12345')`                   | `12345`          |
| `CAST(x AS datatype)`           | Converts a value to specified datatype           | `CAST('2025-09-19' AS DATE)`           | `19-SEP-25`      |

---

## 5. General Functions ⚙️

| Function            | Description                                    | Example                                    | Result      |
|---------------------|------------------------------------------------|--------------------------------------------|-------------|
| `NVL(x,y)`          | Replaces `NULL` with value `y`                 | `NVL(commission,0)`                        | `0` if NULL |
| `NVL2(x,y,z)`       | Returns `y` if `x` not null, else `z`          | `NVL2(commission,'Yes','No')`              | `Yes` / `No`|
| `NULLIF(x,y)`       | Returns `NULL` if `x = y`, else `x`            | `NULLIF(100,100)`                          | `NULL`      |
| `COALESCE(x1,x2,…)` | Returns first non-null value                   | `COALESCE(NULL,NULL,'Oracle')`             | `Oracle`    |
| `DECODE(expr, s1,r1, s2,r2,…, default)` | IF-THEN-ELSE logic         | `DECODE(grade,'A','Excellent','B','Good','C','Average','Poor')` | Result based on grade |
| `CASE`              | More flexible conditional logic                | `CASE WHEN salary>10000 THEN 'High' ELSE 'Low' END` | `High` / `Low` |

---

## 6. Aggregate (Multi-Row) Functions 📊

| Function           | Description                                | Example                                 | Result                     |
|--------------------|--------------------------------------------|-----------------------------------------|----------------------------|
| `COUNT(column)`    | Counts non-null values in a column         | `COUNT(salary)`                         | Number of salaries         |
| `COUNT(*)`         | Counts all rows                             | `COUNT(*)`                              | Total rows                 |
| `SUM(column)`      | Returns sum of values                        | `SUM(salary)`                           | Total salary               |
| `AVG(column)`      | Returns average of values                    | `AVG(salary)`                           | Average salary             |
| `MIN(column)`      | Returns minimum value                        | `MIN(salary)`                           | Lowest salary              |
| `MAX(column)`      | Returns maximum value                        | `MAX(salary)`                           | Highest salary             |
| `STDDEV(column)`   | Standard deviation of numeric values        | `STDDEV(salary)`                        | Std deviation              |
| `VARIANCE(column)` | Variance of numeric values                   | `VARIANCE(salary)`                       | Variance                   |

> **Note:** Aggregate functions are often used with `GROUP BY` and `HAVING` clauses.

---

## 🔑 Key Notes
- Single-row functions return **one value per row**; aggregate functions summarize **multiple rows**.  
- Functions can be **nested**, e.g., `ROUND(AVG(salary),2)`.  
- Always handle `NULL` values using `NVL`, `COALESCE`, or `CASE`.  

---

✅ This cheat sheet provides a **quick reference** for Oracle’s single-row and multi-row (aggregate) functions.
