# VAPT Web Application Project

## Project Overview
This project demonstrates Vulnerability Assessment and Penetration Testing (VAPT) on a vulnerable web application in a controlled lab environment.

The testing was performed using Kali Linux as an attacker machine and Metasploitable2 with DVWA (Damn Vulnerable Web Application) as the target environment.

---

## Objective
The objective of this project is to identify and analyze common web application vulnerabilities, understand their impact, and study possible mitigation techniques.

---

## Lab Environment

### Attacker Machine
- Kali Linux

### Target Machine
- Metasploitable2

### Web Application
- DVWA (Damn Vulnerable Web Application)

### Target IP
192.168.74.128

### Security Level
Low

---

# Tools Used

- Kali Linux
- Metasploitable2
- DVWA
- Nmap
- Browser

---

# Testing Methodology

The following steps were performed:

1. Network connectivity testing
2. Service enumeration
3. Web application vulnerability testing
4. Documentation of findings
5. Risk analysis and mitigation

---

# Vulnerability Assessment

## 1. Ping Test

### Command
ping 192.168.74.128

### Result
The target machine was reachable and network connectivity was confirmed.

---

# 2. Nmap Scan

### Command
nmap -sV 192.168.74.128

### Result
Open ports and running services were identified on the target machine.

---

# 3. SQL Injection

## Description
SQL Injection occurs when an application fails to properly validate user input, allowing malicious SQL queries to be executed.

## Testing

Normal Input:
1

Result:
Single user record displayed.

Payload:
1' OR '1'='1

Result:
Multiple user records were displayed, confirming SQL Injection vulnerability.

## Impact
An attacker may access unauthorized database information.

## Mitigation
- Use prepared statements.
- Validate user input.
- Apply proper database security controls.

---

# 4. Reflected XSS

## Description
Reflected Cross-Site Scripting occurs when user input is immediately reflected in the web page without proper sanitization.

## Payload
alert('XSS')

## Result
A browser alert box was displayed, confirming JavaScript execution.

## Impact
Attackers may execute malicious scripts in a victim's browser.

## Mitigation
- Validate user input.
- Encode output.
- Implement Content Security Policy (CSP).

---

# 5. Stored XSS

## Description
Stored XSS occurs when malicious input is stored permanently by the application and executed when users access the page.

## Payload

alert('Stored XSS')

## Result
The payload was stored successfully and executed when the page was opened again.

## Impact
Stored XSS can affect multiple users visiting the vulnerable page.

## Mitigation
- Sanitize user input.
- Encode output.
- Use secure coding practices.

---

# 6. Command Injection

## Description
Command Injection occurs when an application executes system commands using unsanitized user input.

## Input
127.0.0.1 && whoami

## Result
The additional command was executed along with the ping request.

## Impact
An attacker may execute unauthorized system commands.

## Mitigation
- Avoid passing user input directly to system commands.
- Use secure APIs.
- Implement strict input validation.

---

# 7. File Upload

## Description
File Upload vulnerability occurs when an application allows users to upload files without proper validation.

## Testing
A test image file was uploaded through DVWA File Upload functionality.

File:
test.jpg

## Result
File uploaded successfully:
../../hackable/uploads/test.jpg

## Impact
Attackers may upload malicious files if proper restrictions are not implemented.

## Mitigation
- Validate file extensions.
- Check MIME types.
- Restrict executable uploads.
- Store uploaded files securely.

---

# 8. Brute Force

## Description
Brute Force vulnerability occurs when an application allows repeated login attempts without protection.

## Testing

Credentials tested:

Username:
admin

Password:
password

## Result
Successful login achieved.

Message displayed:
Welcome to the password protected area admin

## Impact
Attackers may gain unauthorized access through password guessing attacks.

## Mitigation
- Implement account lockout.
- Use strong passwords.
- Add CAPTCHA.
- Enable multi-factor authentication.

---

# Screenshots

Screenshots of vulnerability testing are available in the Screenshots folder.

Included:
- Network connectivity
- Nmap Scan
- DVWA Security Level
- SQL Injection
- XSS Reflected
- XSS Stored
- Command Injection
- File Upload
- Brute Force

---

# Conclusion

This project demonstrates practical VAPT techniques on a vulnerable web application in a controlled lab environment.

Multiple vulnerabilities were identified, tested, and documented along with their risks and mitigation methods.
