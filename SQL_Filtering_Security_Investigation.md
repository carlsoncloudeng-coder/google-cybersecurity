# Apply Filters to SQL Queries — Security Investigation Portfolio

> A cybersecurity portfolio project demonstrating the use of SQL filtering operators (`AND`, `OR`, `NOT`, `LIKE`) to investigate potential security incidents in an organization's login and employee data.

---

## Project Description

As a security professional at a large organization, I investigated potential security issues involving login attempts and employee machines. Using SQL filters, I queried the `log_in_attempts` and `employees` tables to retrieve specific records that helped identify suspicious activity, such as after-hours failed logins, login attempts on specific dates, and activity originating outside expected regions. I also identified employee machines requiring security updates based on department and office location.

---

## Scenario

I discovered several potential security incidents:
- Failed login attempts occurring after business hours
- Suspicious login activity on specific dates
- Login attempts that did not originate in Mexico
- Employee machines in specific departments and buildings needing security updates

I used SQL queries with `AND`, `OR`, `NOT`, and `LIKE` operators to filter the data and support the investigation.

---

## Queries & Explanations

### 1. Retrieve After-Hours Failed Login Attempts

**Objective:** Identify all failed login attempts that occurred after 18:00 to investigate a potential security incident outside business hours.

**Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = FALSE;
```

**Explanation:**
- `login_time > '18:00'` filters for attempts made after 6:00 PM.
- `success = FALSE` filters for failed login attempts (the `success` column uses `0` or `FALSE` for failures).
- `AND` ensures **both** conditions must be true — only after-hours **and** failed attempts are returned.

---

### 2. Retrieve Login Attempts on Specific Dates

**Objective:** Investigate a suspicious event on 2022-05-09 by reviewing all login attempts on that day and the day before.

**Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

**Explanation:**
- `login_date = '2022-05-09'` filters for attempts on the suspicious date.
- `login_date = '2022-05-08'` filters for attempts on the preceding day.
- `OR` ensures **either** condition can be true — attempts on **either** date are returned.
- This captures a wider window of activity around the suspicious event.

---

### 3. Retrieve Login Attempts Outside of Mexico

**Objective:** Investigate login attempts that occurred outside Mexico, since suspicious activity was determined not to originate there.

**Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

**Explanation:**
- `LIKE 'MEX%'` matches any country value starting with "MEX" (covers both "MEX" and "MEXICO").
- `NOT` inverts the condition — it excludes any records matching the pattern.
- This returns all login attempts from countries **other than** Mexico.
- Using `LIKE` with `%` (wildcard) is essential here because the country column contains inconsistent values.

---

### 4. Retrieve Employees in Marketing (East Building)

**Objective:** Identify all employees in the Marketing department located in the East building for a targeted security update.

**Query:**
```sql
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East%';
```

**Explanation:**
- `department = 'Marketing'` filters for employees in the Marketing department.
- `office LIKE 'East%'` matches any office value starting with "East" (e.g., East-170, East-320).
- `AND` ensures **both** conditions must be met — only Marketing employees in the East building are returned.
- `LIKE` with `%` is used because office values include room numbers after the building name.

---

### 5. Retrieve Employees in Finance or Sales

**Objective:** Identify all employees in the Finance or Sales departments for a different security update.

**Query:**
```sql
SELECT *
FROM employees
WHERE department = 'Finance' OR department = 'Sales';
```

**Explanation:**
- `department = 'Finance'` filters for Finance employees.
- `department = 'Sales'` filters for Sales employees.
- `OR` ensures **either** condition can be true — employees in **either** department are returned.
- This allows the security team to apply updates to both departments in one query.

---

### 6. Retrieve All Employees Not in IT

**Objective:** Identify all employees who need a security update, excluding those in the Information Technology department (who already received it).

**Query:**
```sql
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```

**Explanation:**
- `NOT` inverts the equality condition.
- Only employees whose department is **not** "Information Technology" are returned.
- This ensures the IT department is excluded while all other departments are included.

---

## SQL Filtering Techniques Explained

### Using `LIKE` to Search for a Pattern
The `LIKE` operator is used for pattern matching in text columns. The `%` wildcard matches any sequence of characters (including empty sequences).

| Pattern | Matches |
|---------|---------|
| `'MEX%'` | MEX, MEXICO, MEXICO-CITY |
| `'East%'` | East-170, East-320, East-Conference |
| `'%Marketing%'` | Any string containing "Marketing" |

`LIKE` is especially useful when data is inconsistent or when you need to match partial values.

### Filtering for Dates and Times
SQL allows direct comparison of date and time values using standard operators (`=`, `>`, `<`, `>=`, `<=`).

```sql
WHERE login_date = '2022-05-09'    -- Exact date match
WHERE login_time > '18:00'         -- After 6 PM
WHERE login_date BETWEEN '2022-05-08' AND '2022-05-09'  -- Date range
```

Dates should be formatted as `YYYY-MM-DD` and times as `HH:MM:SS` for reliable comparison.

### Using `AND` and `OR` to Filter on Multiple Conditions
- **`AND`** — All conditions must be true for a record to be returned. Narrows results.
  ```sql
  WHERE condition1 AND condition2
  ```
- **`OR`** — At least one condition must be true. Broadens results.
  ```sql
  WHERE condition1 OR condition2
  ```
- **Combining `AND` and `OR`** — Use parentheses to control precedence:
  ```sql
  WHERE (dept = 'Sales' OR dept = 'Finance') AND office LIKE 'East%'
  ```

### Using `NOT` in Filters
The `NOT` operator negates a condition, returning records that do **not** match.

```sql
WHERE NOT country LIKE 'MEX%'       -- Exclude Mexico
WHERE NOT department = 'IT'         -- Exclude IT department
WHERE NOT success = TRUE            -- Exclude successful logins
```

`NOT` is powerful for exclusion-based filtering and works with `LIKE`, `=`, `IN`, `BETWEEN`, and other operators.

---

## Summary

In this project, I used SQL filtering operators to investigate multiple security concerns within an organization's data. I applied `AND` to narrow down after-hours failed logins and Marketing employees in the East building, `OR` to broaden searches across specific dates and departments, `NOT` to exclude Mexico and the IT department, and `LIKE` with wildcards to handle inconsistent text data. These techniques enabled precise, efficient data retrieval to support security investigations and targeted system updates.

---

## Skills Demonstrated

- SQL query writing with filtering operators
- Pattern matching with `LIKE` and wildcards (`%`)
- Logical operators: `AND`, `OR`, `NOT`
- Date and time filtering in SQL
- Security incident investigation through data analysis
- Database querying for access control and asset management

---

*Completed as part of Google Cybersecurity Certificate — SQL for Security Analysis*
