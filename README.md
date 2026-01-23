## 🗓️ Day 27/100 – Burp Suite: HTTP Request Manipulation

**Focus:** Intercepting, modifying, and replaying web traffic.

### 🕵️‍♂️ Burp Suite Workflow

**1. Proxy Setup**Browser → Burp Proxy (127.0.0.1:8080) → Target Application- Installed Burp CA Certificate for HTTPS interception
- Configured Firefox proxy settings

**2. Traffic Interception**GET /login.php?user=admin&pass=test HTTP/1.1
Host: target.com
Cookie: session=abc123- **Capability:** Pause, inspect, and modify requests before they reach the server

**3. Request Tampering Examples**Originalamount=100.00Modified (Negative Value)amount=-100.00Modified (String Injection)amount=100; DROP TABLE users;
**4. Attack Scenarios Tested**
- **Parameter Tampering:** Price manipulation, IDOR
- **Authorization Bypass:** Role escalation, privilege changes
- **Business Logic Abuse:** Race conditions, quantity overflows

### 🎯 Key Takeaways
1. **Everything is HTTP** – Every interaction is just structured text you can control
2. **Client-side validation is meaningless** – Burp bypasses JavaScript entirely
3. **Attack surface = every parameter** – Headers, body, cookies, all testable

**Burp Suite transforms passive observation into active manipulation.**
