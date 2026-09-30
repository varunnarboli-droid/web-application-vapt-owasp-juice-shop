# Web Application VAPT & OWASP Top 10 Assessment

## Project Overview

This project demonstrates a practical Vulnerability Assessment and Penetration Testing (VAPT) assessment of the OWASP Juice Shop intentionally vulnerable web application.

The assessment was performed in a controlled local lab environment using Kali Linux, Burp Suite Community Edition, Docker, and OWASP testing methodologies.

## Objectives

- Identify common web application vulnerabilities
- Analyze HTTP requests and responses
- Perform manual security testing using Burp Suite
- Validate vulnerabilities with controlled test cases
- Document security findings and evidence
- Provide remediation recommendations

## Lab Environment

| Component | Details |
|---|---|
| Operating System | Kali Linux |
| Target Application | OWASP Juice Shop |
| Deployment | Docker |
| Proxy / Testing Tool | Burp Suite Community Edition |
| Target URL | http://127.0.0.1:3000 |
| Testing Methodology | OWASP Top 10 |

## Tools Used

- Burp Suite Community Edition
- Docker
- Kali Linux
- cURL
- Browser Developer/Network Tools

## Security Testing Performed

### 1. SQL Injection – Authentication Bypass

**Endpoint:**

`POST /rest/user/login`

A controlled SQL injection test demonstrated that improperly handled input could alter the authentication query and result in an authenticated administrator session.

**Impact:**
- Authentication bypass
- Unauthorized administrative access
- Potential exposure of application data

**OWASP Category:** A03 – Injection

---

### 2. SQL Error / Information Disclosure

**Endpoint:**

`GET /rest/products/search?q=`

Special-character input caused a SQLite database error to be returned by the application.

**Impact:**
- Database technology disclosure
- SQL query/error information exposure
- Useful information for further attack development

---

### 3. Unauthenticated Application Configuration Disclosure

**Endpoint:**

`GET /rest/admin/application-configuration`

The endpoint returned application configuration information without requiring authentication.

**Impact:**
- Application information disclosure
- Increased reconnaissance capability for attackers

---

### 4. Application Version Disclosure

**Endpoint:**

`GET /rest/admin/application-version`

The endpoint returned the application version without authentication.

**Impact:**
- Helps identify the deployed application version
- Can assist version-specific vulnerability research

---

### 5. Exposed FTP Directory and Files

**Endpoint:**

`GET /ftp/`

The application exposed a directory listing containing multiple files.

An accessible Markdown file was also tested:

`GET /ftp/acquisitions.md`

**Impact:**
- Sensitive information disclosure
- Unauthorized access to application files
- Increased reconnaissance capability

---

### 6. Missing Content-Security-Policy Header

The application's response did not include a `Content-Security-Policy` header during the tested response-header review.

**Potential Impact:**
A CSP can provide an additional browser-side defense against certain client-side attacks.

---

## Security Controls Tested

The following tests were also performed without confirming a vulnerability:

- Unauthenticated basket access → `401 Unauthorized`
- Invalid login credentials → `401 Unauthorized`
- XSS/HTML input test → XSS not confirmed
- `/rest/user/whoami` → no user information disclosed
- `.bak` file access → `403 Forbidden`

## Methodology

1. Reconnaissance
2. HTTP traffic analysis
3. Endpoint identification
4. Input validation testing
5. Authentication testing
6. Authorization testing
7. Injection testing
8. Information disclosure testing
9. Security-header review
10. Evidence collection
11. Security finding documentation

## Evidence

Screenshots and supporting evidence are stored in the `Evidence/` directory.

Sensitive information such as authentication tokens, passwords, and session data should be removed or redacted before publication.

## Remediation

Recommended security improvements include:

- Use parameterized queries / prepared statements
- Implement robust server-side input validation
- Avoid exposing database errors to users
- Enforce authentication and authorization on administrative endpoints
- Restrict access to sensitive files and directories
- Remove unnecessary version/configuration disclosures
- Implement an appropriate Content-Security-Policy
- Apply secure error handling
- Conduct regular security testing

## Disclaimer

This assessment was performed exclusively against an intentionally vulnerable OWASP Juice Shop instance running locally in a controlled lab environment.

No real-world systems or third-party applications were tested.

## Author

Shivanand Mallikarjun

Cyber Security / VAPT | Security Testing | SIEM | Vulnerability Assessment
