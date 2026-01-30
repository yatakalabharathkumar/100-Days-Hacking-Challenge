## 🗓️ Day 34/100 – Cross-Site Request Forgery (CSRF)

**Focus:** Exploiting browser trust to perform unauthorized actions on behalf of a user.

### 🎭 What is CSRF?
CSRF is an attack that forces an end user to execute unwanted actions on a web application in which they are currently authenticated. It inherits the identity and privileges of the victim.

### ⚔️ Attack Workflow
1.  **Victim Status:** Logged into a vulnerable application (e.g., `bank.com`). Session cookies are active.
2.  **Attacker Action:** Hosts a malicious site with hidden code:
    ```html
    <form action="http://bank.com/transfer" method="POST">
      <input type="hidden" name="to" value="hacker">
      <input type="hidden" name="amount" value="1000">
    </form>
    <script>document.forms.submit();</script>
    ```
3.  **Execution:** Victim visits attacker's site. The browser executes the script, sending the request to `bank.com` *with* the victim's cookies.
4.  **Result:** The bank processes the transfer, believing the victim initiated it.

### 🛡️ Defense Mechanisms
*   **Anti-CSRF Tokens:** A hidden field with a random value that must match the server's record.
*   **SameSite Cookies:** `Set-Cookie: SessionId=xyz; SameSite=Strict`
*   **Re-Authentication:** Require password entry for sensitive actions (e.g., changing email/password).

**Day 34 Takeaway:** Authentication is not enough. Applications must verify the *intent* of the request, not just the identity.
