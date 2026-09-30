# Web Application VAPT – OWASP Juice Shop

## Overview

This project documents a Web Application Vulnerability Assessment and Penetration Testing (VAPT) assessment performed against the intentionally vulnerable OWASP Juice Shop application in a local lab environment.

## Objective

The objective was to identify and document common web application security vulnerabilities using manual testing and Burp Suite.

## Lab Environment

- Kali Linux
- OWASP Juice Shop
- Docker
- Burp Suite Community Edition
- Burp Repeater

## Target

http://127.0.0.1:3000

## Testing Areas

- Authentication testing
- SQL Injection testing
- Authorization testing
- HTTP request/response analysis
- Input validation testing
- Security configuration review

## Vulnerability Identified

### SQL Injection – Authentication Bypass

**Endpoint:**

`POST /rest/user/login`

Testing demonstrated that SQL injection input could bypass the application's authentication mechanism in the intentionally vulnerable lab.

**Severity:** High

**Impact:**

Potential unauthorized access to an administrator account.

**Recommendation:**

- Use parameterized queries.
- Use prepared statements.
- Validate user input server-side.
- Avoid dynamic SQL query construction.
- Implement secure authentication controls.

## Project Structure

```text
web-application-vapt-owasp-juice-shop/
│
├── Evidence/
│   └── 01-sqli-login-bypass.md
│
├── Reports/
│   └── VAPT-Report.md
│
└── README.md
