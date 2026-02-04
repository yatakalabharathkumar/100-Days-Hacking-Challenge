## 🗓️ Day 39/100 – Client-Side vs. Server-Side Security

**Focus:** Understanding execution environments to identify security gaps.

### 🌐 The Two Environments

**1. Client-Side (JavaScript)**
*   **Location:** User's Browser.
*   **Purpose:** Interactivity, UI updates, basic validation (UX).
*   **Security Reality:**
    *   **Trust Level:** Zero.
    *   **Bypass:** Easy. Attackers can modify scripts, disable validation, or send direct HTTP requests via proxies.
    *   **Risks:** Cross-Site Scripting (XSS), Sensitive data storage in LocalStorage.

**2. Server-Side (PHP/Node/Python)**
*   **Location:** Web Server / Backend.
*   **Purpose:** Business logic, database access, authentication.
*   **Security Reality:**
    *   **Trust Level:** High (if coded correctly).
    *   **Bypass:** Difficult. Requires finding logic flaws or injection vulnerabilities.
    *   **Risks:** SQL Injection, Command Injection, Insecure Deserialization.

### ⚔️ Attack Scenario: Bypass Validation
*   **Scenario:** A form uses JS to check if `age > 18`.
*   **Attack:**
    1.  Turn off JavaScript in browser settings.
    2.  Submit `age = 12`.
    3.  If the server (PHP) doesn't check again, the invalid data is accepted.

### 🛡️ Core Principle
**"Never Trust the Client."** Always replicate validation logic on the server-side to ensure data integrity and security.
