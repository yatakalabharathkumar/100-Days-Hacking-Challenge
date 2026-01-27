## 🗓️ Day 31/100 – Directory Brute-Forcing (Content Discovery)

**Focus:** Identifying hidden files, directories, and misconfigurations using enumeration tools.

### 🔍 What is Directory Brute-Forcing?
It is the process of sending HTTP requests for common file and directory names (from a wordlist) to see if the server responds with a 200 OK or 403 Forbidden, revealing resources that are not linked in the web application.

### 🛠️ Tools Used
*   **Gobuster:** Fast, Go-based directory scanner.
*   **Dirb:** Classic content scanner.
*   **FFuF:** Fast web fuzzer.

### 🚩 Discoveries (Common Misconfigurations)
1.  **Hidden Admin Portals:**
    *   Paths like `/admin`, `/login`, `/manager` often bypassed frontend navigation but remained accessible.
2.  **Sensitive Configuration Files:**
    *   Found `.env` (environment variables) containing API keys and DB credentials.
    *   Found `.git/HEAD` exposing version control history.
3.  **Backup Files:**
    *   Developers often leave `backup.zip` or `index.php.bak` in the web root, allowing source code download.

### 🛡️ Remediation
*   **WAF Rules:** Block excessive 404 requests (scanning signatures).
*   **Clean Web Root:** Remove all non-essential files (backups, configs).
*   **Access Control:** Use IP allow-listing for admin panels.

**Day 31 Takeaway:** If a file exists on a public server, it *will* be found. Obscurity is not security.
