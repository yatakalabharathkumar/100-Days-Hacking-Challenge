## 🗓️ Day 62/100 – Wireshark Analysis of Auth Flows

**Focus:** Using Wireshark to visualize how different authentication and session mechanisms look on the wire.

### 🔍 Scenarios Analyzed

1. HTTP Basic Auth (Insecure)
   - Accessed a password-protected page over HTTP.
   - Observed:
     - Initial 401 response requesting authentication.
     - Follow-up request containing an `Authorization: Basic <base64>` header with credentials.
   - In Wireshark, following the TCP stream showed the username and password in cleartext once decoded from Base64.

2. Cookie-Based Sessions
   - Logged into a web app using a form-based login.
   - Observed:
     - `Set-Cookie` header in the server's response containing a session token.
     - Subsequent requests including `Cookie: sessionToken=...` headers.
   - This illustrated how session hijacking works if an attacker can capture this traffic on an unencrypted connection.

3. HTTPS-Protected Auth
   - Repeated similar login flows over HTTPS.
   - Observed:
     - TLS handshake (ClientHello, ServerHello, etc.).
     - HTTP data carried inside encrypted TLS records, making credentials and cookies unreadable without decryption keys.

### 🧠 Takeaways

- Plain HTTP:
  - Credentials (Basic auth) and session cookies are fully visible to anyone on path.
- HTTPS:
  - Properly configured TLS prevents direct inspection of auth data.
- Wireshark:
  - Great for demonstrating:
    - Why legacy/insecure auth methods are dangerous.
    - How cookies and session tokens move between client and server.
    - The real impact of enabling (or not enabling) encryption.

**Day 62 Summary:**
Seeing authentication and session flows in Wireshark turns “use HTTPS and protect cookies” from best-practice advice into a very tangible security requirement.
