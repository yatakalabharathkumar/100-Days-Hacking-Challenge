## 🗓️ Day 28/100 – SQL Injection (SQLi)

**Focus:** Exploiting improper input validation to manipulate database queries.

### 💉 What is SQL Injection?
SQLi is a vulnerability where an application takes user input and inserts it directly into a database query. This allows an attacker to interfere with the queries the application makes to its database.

### ⚔️ Attack Vectors Explored

**1. Authentication Bypass**
*   **Scenario:** Login form vulnerable to SQLi.
*   **Payload:** `' OR 1=1 --`
*   **Result:** The query becomes `SELECT * FROM users WHERE user = '' OR 1=1 --'` which is always TRUE, logging the attacker in as the first user (usually Admin).

**2. UNION-Based SQLi**
*   **Scenario:** Retrieving data from other tables.
*   **Payload:** `' UNION SELECT username, password FROM users --`
*   **Result:** The application displays results from the `users` table mixed with the original query results.

**3. Blind SQLi**
*   **Scenario:** No visible output, but the application behaves differently (e.g., page load delay).
*   **Technique:** Inferring data character by character based on True/False responses.

### 🛡️ Defense Mechanism
*   **Primary Fix:** Use **Prepared Statements (Parameterized Queries)**.
*   **Secondary:** Input Validation (Allow-listing) and Least Privilege Principle for DB accounts.

**Day 28 Takeaway:** SQLi is preventable, yet it remains a leading cause of data breaches due to legacy code and lack of secure coding practices.
