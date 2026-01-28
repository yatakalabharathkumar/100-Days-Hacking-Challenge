## 🗓️ Day 32/100 – OWASP ZAP (Automated Scanning)

**Focus:** Using automated tools to map attack surfaces and detect common vulnerabilities.

### ⚡ What is OWASP ZAP?
The Zed Attack Proxy (ZAP) is a free, open-source penetration testing tool maintained by OWASP. It acts as a "Man-in-the-Middle" proxy (similar to Burp Suite) but specializes in automated scanning.

### 🛠️ Workflow Executed
1.  **Spidering (Crawling):**
    *   ZAP automatically navigated the application to discover all accessible URLs, including those not visible in the navigation menu.
    *   *Result:* Complete site map generated in <2 minutes.

2.  **Active Scanning:**
    *   ZAP injected malicious payloads (SQLi, XSS, CRLF) into every identified parameter.
    *   *Result:* Detected 15+ alerts ranging from "Missing Security Headers" (Low) to "Reflected XSS" (High).

3.  **Passive Scanning:**
    *   Analyzed traffic without sending attacks to find issues like sensitive cookies without `HttpOnly` or missing `CSP` headers.

### 🧠 Learning Outcome
Automation is a double-edged sword. It helps defenders find holes quickly, but it also allows script kiddies to launch sophisticated scans with zero knowledge. A robust security program must include regular automated scans.
