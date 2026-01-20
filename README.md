## 🗓️ Day 24/100 – Modern Web Hacking with OWASP Juice Shop

**Focus:** Identifying logic flaws and validation errors in modern Single Page Applications (SPAs).

### 🧃 Lab Environment: OWASP Juice Shop
Unlike Mutillidae (legacy PHP), Juice Shop is built with a modern stack (Node.js, Express, Angular). It represents the security challenges of today's e-commerce sites.

### 🛡️ Vulnerabilities Explored
**1. Business Logic Flaws**
*   *Concept:* Manipulating the workflow of the application rather than just the code.
*   *Example:* Modifying request parameters to bypass payment gates or alter order pricing.

**2. Insecure Authentication**
*   *Concept:* Weaknesses in how the app handles user identity.
*   *Example:* Testing for weak password policies, lack of MFA, or session token mishandling.

**3. Improper Input Validation**
*   *Concept:* Trusting client-side checks without backend verification.
*   *Example:* Sending malicious payloads that the frontend UI blocks, but the backend API accepts via direct requests (using Burp Suite).

### 🧠 Key Takeaway
Modern frameworks solve many old problems (like some basic XSS), but they introduce new risks around **API security** and **business logic**. Security is not just about code; it's about the integrity of the entire process.
