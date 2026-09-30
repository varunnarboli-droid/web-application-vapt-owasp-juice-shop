# Web Application VAPT Report

## 1. Target

OWASP Juice Shop – Local Lab

Target:
http://127.0.0.1:3000

## 2. Testing Methodology

Testing was performed using:

- Burp Suite Community Edition
- OWASP Juice Shop
- Kali Linux
- Burp Repeater
- Manual HTTP request analysis

## 3. Vulnerability Identified

### SQL Injection – Authentication Bypass

Endpoint:

POST /rest/user/login

The login endpoint was tested with SQL injection input in the email parameter.

The application returned an authenticated administrator session, demonstrating an authentication bypass.

### Severity

High

### Impact

An attacker may be able to bypass authentication and obtain unauthorized access to an administrator account.

### Recommendation

- Use parameterized SQL queries.
- Use prepared statements.
- Validate and sanitize user input.
- Never concatenate user-controlled input into SQL queries.
- Implement secure authentication error handling.

## 4. Evidence

Evidence:

`Evidence/01-sqli-login-bypass.md`

## 5. Tools Used

- Burp Suite
- OWASP Juice Shop
- Kali Linux
- Docker

## 6. Conclusion

The assessment identified a SQL injection vulnerability in the authentication mechanism of the intentionally vulnerable OWASP Juice Shop application.

Testing was performed only against the local lab environment.
