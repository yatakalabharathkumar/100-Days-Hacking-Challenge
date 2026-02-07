## 🗓️ Day 42/100 – CSP Bypass Techniques

**Focus:** Analyzing weak Content Security Policy (CSP) headers to execute XSS payloads.

### 🛡️ What is CSP?
Content Security Policy is an HTTP header (`Content-Security-Policy`) that allows site administrators to declare approved sources of content that browsers are allowed to load.

### ⚔️ Common Bypasses Demonstrated

**1. 'unsafe-inline'**
*   **Policy:** `script-src 'self' 'unsafe-inline'`
*   **Weakness:** Allows `<script>alert(1)</script>` to run directly in the HTML.
*   **Fix:** Use Nonces (random tokens) or Hashes.

**2. CDN Whitelist Abuse (Script Gadgets)**
*   **Policy:** `script-src 'self' https://cdnjs.cloudflare.com`
*   **Weakness:** The attacker doesn't host the script; they load a vulnerable library (like old AngularJS) *from* the trusted CDN and use it to execute code.
*   **Technique:** "JSONP Hijacking" or "AngularJS Sandbox Escape".

**3. Wildcards**
*   **Policy:** `script-src 'self' https:`
*   **Weakness:** Allows scripts from ANY site with HTTPS (including the attacker's site).

### 🔍 Analysis Tool
*   **Google CSP Evaluator:** Used to visualize policy gaps and potential bypasses.

**Day 42 Takeaway:** CSP is powerful, but configuration is difficult. A bypassed CSP is often worse than no CSP because it leads to complacency.
