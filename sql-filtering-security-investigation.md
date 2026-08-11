# SQL Filtering for Security Investigations

I investigated suspicious login attempts and employee machine records using SQL filters. The data came from two tables: `log_in_attempts` and `employees`. These queries reduce raw records to the rows needed for a security review.

## Data

The `log_in_attempts` table stored login date, login time, login success, and country. The `employees` table stored department and office location.

## Failed logins after business hours

```sql
SELECT *
FROM log_in_attempts
WHERE success = 0
  AND login_time > '18:00';
```

This query pulls failed login attempts made after 18:00. `success = 0` marks a failed login. `login_time > '18:00'` removes daytime rows. `AND` forces both conditions to be true, so the result contains only after-hours failures.

## Login attempts on two suspicious dates

```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09'
   OR login_date = '2022-05-08';
```

The event occurred on 2022-05-09, and the prior day needed review too. `OR` keeps records from either date. The result covers the full two-day window.

## Login attempts outside Mexico

```sql
SELECT *
FROM log_in_attempts
WHERE country NOT LIKE 'MEX%';
```

The team ruled out activity originating in Mexico, but the country field stored both `MEX` and `MEXICO`. `LIKE 'MEX%'` matches both values because `%` stands for any characters after `MEX`. `NOT LIKE` removes those rows, leaving attempts from other countries.

For case-sensitive databases, use:

```sql
SELECT *
FROM log_in_attempts
WHERE UPPER(country) NOT LIKE 'MEX%';
```

## Marketing employees in the East building

```sql
SELECT *
FROM employees
WHERE department = 'Marketing'
  AND office LIKE 'East%';
```

Security updates needed a specific employee group. `department = 'Marketing'` selects the department. `office LIKE 'East%'` matches East-170, East-320, and other East offices. `AND` joins the two filters, so only Marketing staff in the East building appear.

## Sales or Finance employees

```sql
SELECT *
FROM employees
WHERE department = 'Sales'
   OR department = 'Finance';
```

A separate update applied to Sales and Finance. `OR` accepts either department, so the result includes both groups.

## Employees outside Information Technology

```sql
SELECT *
FROM employees
WHERE NOT (department = 'Information Technology');
```

Information Technology already received the update. `NOT` excludes that department. The result lists employees in every other department.

## Summary

These filters turned raw login and employee tables into targeted investigation sets. The queries separated after-hours failures, two suspicious dates, non-Mexico logins, and employee groups that needed action. The next step for a real incident would be to correlate these rows with ticket history, endpoint data, and account ownership.
````
