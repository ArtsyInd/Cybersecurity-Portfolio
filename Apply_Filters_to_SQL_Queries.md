# Apply Filters to SQL Queries

> **Cybersecurity Portfolio Project**  
> **Category:** SQL | Security Analysis | Data Investigation  
> **Skills Demonstrated:** SQL filtering, `WHERE`, `AND`, `OR`, `NOT`, `LIKE`, date/time filtering, security investigation

---

## Project Description

As a security professional at a large organization, I used SQL to investigate potential security issues involving employee accounts and login activity. I queried the `log_in_attempts` and `employees` tables to identify suspicious after-hours activity, investigate login attempts on specific dates and locations, and identify employee groups requiring security updates. The queries demonstrate how SQL filters can be used to retrieve targeted information efficiently during a security investigation.

---

# 1. Retrieve After-Hours Failed Login Attempts

## Objective

A potential security incident occurred after normal business hours. I needed to identify all failed login attempts that occurred after 18:00.

## SQL Query

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00'
  AND success = 0;
```

## Explanation

The query searches the `log_in_attempts` table and returns only records that satisfy **both** conditions:

- `login_time > '18:00'` filters for login attempts after 18:00.
- `success = 0` filters for unsuccessful login attempts.
- `AND` ensures that both conditions must be true for a record to be returned.

This allows the security team to focus specifically on failed login attempts that occurred outside normal business hours.

### Security Relevance

Repeated failed login attempts after business hours can be an indicator of suspicious activity, such as password guessing or brute-force attempts. Filtering the data makes it easier to identify events that require further investigation.

---

# 2. Retrieve Login Attempts on Specific Dates

## Objective

A suspicious event occurred on **2022-05-09**. I needed to review login attempts from both that date and the previous day, **2022-05-08**.

## SQL Query

```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09'
   OR login_date = '2022-05-08';
```

## Explanation

The query retrieves login attempts from either of the two specified dates.

- `login_date = '2022-05-09'` selects attempts from May 9, 2022.
- `login_date = '2022-05-08'` selects attempts from May 8, 2022.
- `OR` allows a record to match either condition.

This provides the security team with login activity immediately before and during the suspected security event.

### Security Relevance

Reviewing activity across adjacent dates provides additional context around a suspicious event and can help identify patterns that may not be visible when examining only one date.

---

# 3. Retrieve Login Attempts Outside Mexico

## Objective

The security team determined that the suspicious activity did not originate in Mexico. I therefore needed to identify login attempts originating from locations outside Mexico.

The `country` column contains both `MEX` and `MEXICO`, so a pattern match is required.

## SQL Query

```sql
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

## Explanation

The query uses `LIKE` with the `%` wildcard to identify country values beginning with `MEX`.

- `LIKE 'MEX%'` matches values such as `MEX` and `MEXICO`.
- `%` represents any sequence of characters following `MEX`.
- `NOT` reverses the condition and returns records whose country does not match the Mexico pattern.

This ensures that both `MEX` and `MEXICO` are excluded from the results.

### Security Relevance

Filtering login activity by geographic origin can help analysts investigate suspicious authentication attempts and determine whether activity originated from an expected location.

---

# 4. Retrieve Employees in Marketing

## Objective

The security team needed to perform security updates on machines assigned to employees in the Marketing department who work in offices located in the East building.

## SQL Query

```sql
SELECT *
FROM employees
WHERE department LIKE 'Marketing%'
  AND office LIKE 'East%';
```

## Explanation

The query filters the `employees` table using two conditions:

- `department LIKE 'Marketing%'` identifies employees whose department value begins with `Marketing`.
- `office LIKE 'East%'` identifies offices whose names begin with `East`.
- `AND` ensures that employees must satisfy both conditions.

The `%` wildcard is useful because the office values may contain additional characters, such as `East-170` or `East-320`.

### Security Relevance

This query allows the security team to identify the specific employee machines that require the planned security update without modifying unrelated systems.

---

# 5. Retrieve Employees in Finance or Sales

## Objective

The security team needed to identify employees in either the Sales or Finance departments for another security update.

## SQL Query

```sql
SELECT *
FROM employees
WHERE department = 'Sales'
   OR department = 'Finance';
```

## Explanation

The query returns employees who belong to either department.

- `department = 'Sales'` identifies Sales employees.
- `department = 'Finance'` identifies Finance employees.
- `OR` allows either condition to be true.

Using `OR` is appropriate because an employee only needs to belong to one of the two departments to be included in the results.

### Security Relevance

The filtered results provide the security team with a targeted list of employees whose machines require the additional update.

---

# 6. Retrieve All Employees Not in IT

## Objective

Employees in the Information Technology department have already received the security update. I therefore needed to identify employees in all other departments.

## SQL Query

```sql
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```

## Explanation

The query uses `NOT` to exclude employees whose department is Information Technology.

- `department = 'Information Technology'` identifies IT employees.
- `NOT` reverses this condition.
- The resulting records represent employees who are not in the IT department.

An equivalent form would be:

```sql
SELECT *
FROM employees
WHERE department != 'Information Technology';
```

The `NOT` version demonstrates explicitly how the `NOT` operator can be used in a SQL filter.

### Security Relevance

This query helps ensure that security updates are applied to employees who have not already received them while avoiding unnecessary changes to machines belonging to the IT department.

---

# SQL Concepts Demonstrated

## `WHERE`

The `WHERE` clause filters records based on specified conditions.

Example:

```sql
SELECT *
FROM employees
WHERE department = 'Finance';
```

Only records satisfying the condition are returned.

---

## `AND`

`AND` requires multiple conditions to be true.

Example:

```sql
WHERE login_time > '18:00'
  AND success = 0;
```

Both conditions must be satisfied.

---

## `OR`

`OR` returns records when at least one of the specified conditions is true.

Example:

```sql
WHERE department = 'Sales'
   OR department = 'Finance';
```

An employee can belong to either department and still be included.

---

## `NOT`

`NOT` reverses a condition.

Example:

```sql
WHERE NOT department = 'Information Technology';
```

This excludes employees whose department is Information Technology.

---

## `LIKE` and `%`

`LIKE` is used for pattern matching.

The `%` wildcard represents zero or more characters.

Example:

```sql
WHERE country LIKE 'MEX%';
```

This can match:

```text
MEX
MEXICO
```

Similarly:

```sql
WHERE office LIKE 'East%';
```

can match values such as:

```text
East-170
East-320
East-434
```

Using pattern matching is useful when database values contain variations or additional characters.

---

# Security Investigation Workflow

The queries in this activity demonstrate a basic SQL-driven security investigation workflow:

```text
Potential Security Issue
          |
          v
Identify Relevant Dataset
          |
          v
Apply SQL Filters
          |
          v
Narrow Down Relevant Records
          |
          v
Investigate Results
          |
          v
Determine Appropriate Security Action
```

The `log_in_attempts` table was used to investigate authentication activity, while the `employees` table was used to identify employee groups and machines requiring security updates.

---

# Query Summary

| Investigation | SQL Concepts Used | Purpose |
|---|---|---|
| After-hours failed logins | `AND`, time filtering | Identify failed attempts after 18:00 |
| Specific login dates | `OR`, date filtering | Investigate May 8 and May 9, 2022 |
| Login attempts outside Mexico | `NOT`, `LIKE`, `%` | Exclude Mexico-based activity |
| Marketing employees in East offices | `AND`, `LIKE`, `%` | Identify targeted employee machines |
| Finance or Sales employees | `OR` | Identify two specific departments |
| Employees outside IT | `NOT` | Exclude employees who already received the update |

---

# Key Skills Demonstrated

- SQL querying
- Security data investigation
- Authentication log analysis
- Date and time filtering
- Pattern matching with `LIKE`
- Wildcard filtering with `%`
- Combining conditions with `AND`
- Combining alternatives with `OR`
- Excluding records with `NOT`
- Targeted employee data retrieval
- Applying SQL to cybersecurity investigations

---

# Summary

In this activity, I used SQL filters to investigate login activity and identify employee groups relevant to security operations. I analyzed failed after-hours login attempts, investigated activity surrounding a specific security event, excluded login attempts from Mexico, and identified employees based on department and office location. These queries demonstrate how SQL can be used by security professionals to efficiently investigate authentication data, narrow large datasets, and support targeted security actions.
