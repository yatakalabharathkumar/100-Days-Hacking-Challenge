## Day 13: DVWA (Damn Vulnerable Web Application)

**Focus:** Web Vulnerabilities, Practical Exploitation, and Secure Coding

I practiced on DVWA, learning how poor coding practices lead to exploitable vulnerabilities.

**What is DVWA?**
- A deliberately vulnerable PHP/MySQL web application.
- Designed for security professionals to practice exploitation safely.
- Available in difficulty levels (Low, Medium, High).
- Free and open-source.

**Vulnerabilities I Practiced:**

### 1. SQL Injection (SQLi)
**Description:** Inserting malicious SQL code into input fields to manipulate database queries.

**Example Vulnerable Code:**
```php
$query = "SELECT * FROM users WHERE username='" . $_POST['username'] . "'";
