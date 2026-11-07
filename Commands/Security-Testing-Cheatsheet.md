# Web Application Security – Testing Cheatsheet

## 1. Environment Setup

### Check PHP version
```bash
php -v
```

### Check Apache status
```bash
sudo systemctl status apache2
```

### Start Apache
```bash
sudo systemctl start apache2
```

### Check DVWA locally
```text
http://localhost/DVWA/
```

## 2. Python HTTP Server

Used to host the local CSRF demonstration page.

### Create a directory
```bash
mkdir -p ~/csrf-demo
```

### Navigate to directory
```bash
cd ~/csrf-demo
```

### Create HTML file
```bash
nano csrf.html
```

### Start local HTTP server
```bash
python3 -m http.server 8000
```

### Access the test page
```text
http://127.0.0.1:8000/csrf.html
```

## 3. Burp Suite Configuration

**Proxy listener:**
```text
127.0.0.1:8080
```

**Firefox proxy settings:**
- HTTP Proxy: 127.0.0.1
- Port: 8080
- Enable proxy for HTTPS when required.

**Testing procedure:**
1. Launch Burp Suite.
2. Start a temporary project.
3. Use Burp defaults.
4. Verify the proxy listener.
5. Configure Firefox to use the proxy.
6. Enable interception.
7. Generate a request from the browser.
8. Inspect captured HTTP request and response details.

## 4. Browser Developer Tools

Open Developer Tools:
```text
Ctrl + Shift + I
```

Useful tabs:
- Network: Inspect HTTP requests and responses.
- Console: Observe JavaScript errors.
- Elements: Inspect webpage HTML.
- Storage: Examine cookies and browser storage.

## 5. HTTP Security Headers

Inspect the following response headers:

```text
Content-Security-Policy
X-Content-Type-Options
X-Frame-Options
Strict-Transport-Security
Referrer-Policy
```

## 6. Important Security Concepts

| Vulnerability | Main Protection |
|---|---|
| SQL Injection | Prepared statements |
| Reflected XSS | Output encoding |
| Stored XSS | Input sanitization and output encoding |
| CSRF | Anti-CSRF tokens |
| File Inclusion | File allowlisting |
| Insecure HTTP | HTTPS and secure headers |

## 7. Useful References

- DVWA: https://github.com/digininja/DVWA
- Burp Suite: https://portswigger.net/burp
- OWASP Top 10: https://owasp.org/www-project-top-ten/
- OWASP Cheat Sheet Series: https://cheatsheetseries.owasp.org/

## Disclaimer

All commands and testing activities documented here are intended for authorized security testing in controlled lab environments.
