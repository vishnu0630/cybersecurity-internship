# Task 3 - Web Application Security Testing

## Objective
The objective of this task is to identify, exploit, and analyze common web application vulnerabilities using Damn Vulnerable Web Application (DVWA). The testing was performed in a controlled lab environment to understand how these vulnerabilities work and how they can be mitigated.

---

## Lab Environment

- Operating System: Kali Linux
- Target Application: Damn Vulnerable Web Application (DVWA)
- Web Server: Apache2
- Database: MySQL
- PHP Version: 8.4.22
- Browser: Firefox
- Proxy Tool: Burp Suite Community Edition

---

## Vulnerabilities Tested

### 1. SQL Injection (SQLi)
**Description:**
Tested SQL Injection by manipulating the User ID parameter.

**Result:**
Successfully bypassed the intended query and retrieved multiple database records.

**Mitigation:**
- Use Prepared Statements (Parameterized Queries)
- Validate user input
- Apply least privilege to database accounts

---

### 2. Reflected Cross-Site Scripting (XSS)

**Description:**
Injected JavaScript into user input.

**Payload Used:**
```html
<img src=x onerror=alert(1)>
```

**Result:**
JavaScript executed successfully.

**Mitigation:**
- Output Encoding
- Input Validation
- Content Security Policy (CSP)

---

### 3. Stored Cross-Site Scripting (Stored XSS)

**Description:**
Stored malicious JavaScript inside the application database.

**Result:**
Payload executed whenever the stored content was viewed.

**Mitigation:**
- Sanitize user input
- Encode output
- Implement CSP

---

### 4. Cross-Site Request Forgery (CSRF)

**Description:**
Tested whether an authenticated user's password could be changed through a crafted request.

**Result:**
Password was successfully changed without proper CSRF protection.

**Mitigation:**
- CSRF Tokens
- SameSite Cookies
- Verify Origin and Referer headers

---

### 5. Local File Inclusion (LFI)

**Description:**
Performed Directory Traversal to access sensitive system files.

**Payload Used:**
```
../../../../../../etc/passwd
```

**Result:**
Successfully displayed the Linux `/etc/passwd` file.

**Mitigation:**
- Whitelist allowed files
- Prevent directory traversal
- Validate file paths

---

### 6. Unrestricted File Upload

**Description:**
Uploaded a PHP web shell to the server.

**Result:**
Successfully executed the uploaded PHP file (`phpinfo()`).

**Mitigation:**
- Restrict allowed file types
- Validate MIME types
- Store uploads outside the web root
- Disable script execution in upload directories

---

## Burp Suite Testing

Burp Suite Community Edition was used to:

- Intercept HTTP Requests
- Analyze HTTP Responses
- Capture Login Requests
- Configure Burp Intruder
- Perform Manual Security Testing

---

## Screenshots Included

- SQL Injection
- Reflected XSS
- Stored XSS
- CSRF Password Change
- Local File Inclusion
- File Upload Success
- Uploaded PHP Execution
- Burp Intruder Configuration
- HTTP Request and Response Analysis

---

## Files Included

```
Task-3-Web-Application-Security/
│
├── README.md
├── Security_Testing_Report.pdf
└── Screenshots/
```

---

## Learning Outcomes

Through this task, I learned:

- SQL Injection testing
- Cross-Site Scripting attacks
- Cross-Site Request Forgery exploitation
- Local File Inclusion attacks
- Unrestricted File Upload exploitation
- HTTP request and response analysis
- Burp Suite interception and request modification
- Common web application security best practices

---

## Disclaimer

This project was performed only in a controlled laboratory environment (DVWA) for educational and cybersecurity training purposes. No unauthorized systems were targeted.
