# SQL Injection – Authentication Bypass

## Endpoint

POST /rest/user/login

## Description

A controlled SQL injection test was performed against the login endpoint in the local OWASP Juice Shop lab.

The application accepted SQL syntax in the email parameter and returned an authenticated administrator session.

## Test Result

HTTP Status: 200 OK

## Impact

Successful exploitation can allow authentication bypass and unauthorized access to an administrator account.

## Remediation

- Use parameterized queries / prepared statements.
- Never concatenate user-controlled input directly into SQL queries.
- Implement strict server-side input validation.
- Return generic authentication errors.
