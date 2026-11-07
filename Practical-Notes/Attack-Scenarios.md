# Web Application Security – Attack Scenarios

## 1. SQL Injection (SQLi)

**Objective:** Understand how attackers can manipulate SQL queries through unsanitized user input.

**Methodology:**
- Accessed the SQL Injection module in DVWA.
- Tested user input fields with SQL injection payloads.
- Observed how input handling affected database queries.

**Security Impact:**
- Unauthorized access to database information.
- Authentication bypass.
- Potential modification or deletion of database records.

**Mitigation:**
- Use prepared statements and parameterized queries.
- Validate and sanitize user input.
- Apply least-privilege database permissions.

## 2. Reflected Cross-Site Scripting (XSS)

**Objective:** Demonstrate how malicious scripts can execute through reflected user input.

**Methodology:**
- Accessed the Reflected XSS module in DVWA.
- Submitted a JavaScript test payload.
- Observed the browser's response.

**Security Impact:**
- Session theft.
- Unauthorized actions in a victim's browser.
- Manipulation of webpage content.

**Mitigation:**
- Apply context-aware output encoding.
- Validate user input.
- Implement Content Security Policy (CSP).

## 3. Stored Cross-Site Scripting (XSS)

**Objective:** Understand persistent XSS attacks through stored user input.

**Methodology:**
- Accessed the DVWA guestbook.
- Submitted a test message containing a JavaScript payload.
- Observed the script execution when the stored entry was displayed.

**Observation:** The JavaScript alert was successfully triggered, demonstrating stored XSS.

**Security Impact:**
- Persistent script execution for users viewing the affected page.
- Session compromise and malicious content injection.

**Mitigation:**
- Encode output before displaying user-generated content.
- Sanitize HTML input.
- Implement a suitable Content Security Policy.

## 4. Cross-Site Request Forgery (CSRF)

**Objective:** Understand how an attacker can trick an authenticated user into submitting an unintended request.

**Methodology:**
- Accessed the DVWA CSRF module.
- Performed a normal password-change operation.
- Created a local HTML test page containing a form that submitted a password-change request.
- Hosted the test page using Python's HTTP server.
- Submitted the test form and observed the browser redirect to DVWA.

**Observation:** The test request was submitted. Successful password modification through the forged request was not independently verified.

**Security Impact:**
- Unauthorized account changes.
- Unintended actions performed using an authenticated session.

**Mitigation:**
- Implement anti-CSRF tokens.
- Validate request origin.
- Configure appropriate SameSite cookie attributes.

## 5. File Inclusion

**Objective:** Understand local and remote file inclusion vulnerabilities.

**Environment Observation:**
- Accessed the DVWA File Inclusion module.
- The environment used PHP 8.4.27.
- The application indicated that `allow_url_include` was disabled.

**Result:** Remote file inclusion could not be demonstrated because of the PHP configuration. The practical was skipped.

**Security Impact:**
- Unauthorized access to local files.
- Potential execution of malicious included files.

**Mitigation:**
- Avoid including files directly from untrusted user input.
- Use predefined file allowlists.
- Disable unnecessary remote inclusion functionality.
- Apply proper server permissions.

## 6. Burp Suite – HTTP Request Interception

**Objective:** Learn how to intercept and inspect HTTP requests using Burp Suite.

**Methodology:**
- Launched Burp Suite Community Edition.
- Configured a temporary project using Burp defaults.
- Verified the proxy listener at `127.0.0.1:8080`.
- Configured Firefox to use the local proxy.
- Attempted to intercept requests generated while accessing DVWA.

**Observation:** The proxy listener was running and browser access to DVWA was established. Successful request interception was not independently confirmed.

**Security Relevance:**
- Helps identify insecure request handling.
- Allows inspection of HTTP parameters and headers.
- Supports security testing of web applications.

## 7. HTTP Security Headers

**Objective:** Understand the role of HTTP response security headers.

**Testing:** Inspected the local DVWA application as part of the security-header testing exercise.

**Security Headers to Examine:**
- Content-Security-Policy
- X-Content-Type-Options
- X-Frame-Options
- Strict-Transport-Security
- Referrer-Policy

**Security Importance:**
- Helps mitigate cross-site scripting.
- Reduces clickjacking risks.
- Prevents MIME-type sniffing.
- Improves browser-side security.

**Mitigation:** Configure appropriate security headers at the web server or application level.

---

## Conclusion

This practical exercise provided hands-on exposure to common web application security vulnerabilities using DVWA in a controlled local environment. It improved understanding of vulnerability identification, testing methodologies, security risks, and mitigation techniques.

All testing was performed for educational purposes in an authorized local lab environment.
