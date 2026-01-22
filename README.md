## 🗓️ Day 26/100 – Brute Force & Rate Limiting

**Focus:** Simulating authentication attacks to understand the importance of account lockout policies.

### ⚔️ Attack Simulation
Building on previous concepts, today involved practical testing of authentication endpoints.
*   **Technique:** Automated submission of username/password pairs (Brute Force & Dictionary Attacks).
*   **Tools Used:** Burp Suite Intruder / Hydra.

### 🚩 Vulnerabilities Identified
1.  **Weak Password Policies:** Accounts with simple passwords (e.g., `admin123`) were compromised almost instantly.
2.  **Missing Rate Limiting:** The target application allowed thousands of requests per minute without triggering a block or CAPTCHA.
3.  **No Account Lockout:** The system failed to lock the account after multiple failed attempts, allowing indefinite guessing.

### 🛡️ Defensive Learnings
*   **Throttling:** Implement exponential backoff for failed logins.
*   **Lockout Policies:** Temporarily disable accounts after 3-5 failed attempts.
*   **MFA:** Multi-Factor Authentication effectively neutralizes simple brute force attacks.
