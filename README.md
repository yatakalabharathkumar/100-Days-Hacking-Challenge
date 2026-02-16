## 🗓️ Day 51/100 – JavaScript Attacks & Client-Side Vulnerabilities

**Focus:** Understanding how JavaScript-based attacks abuse client-side weaknesses to impact overall web security.

### 🔍 Attacks Studied

- Cross-Site Scripting (XSS)
  - Injecting malicious JavaScript into pages rendered for other users.
  - Variants: reflected, stored, DOM-based.
  - Impact: session theft, keylogging, CSRF via script, UI manipulation.

- DOM-Based Attacks
  - Vulnerabilities in client-side code using dangerous sinks
    (innerHTML, document.write, location, etc.).
  - The exploit can occur entirely in the browser without a modified HTTP response.

- Cross-Site Request Forgery (CSRF)
  - Forcing a logged-in user’s browser to send unintended state-changing requests.
  - Relies on existing cookies and trust in the browser’s authenticated session.

- Session Hijacking
  - Stealing or abusing session identifiers (often via XSS, insecure cookies, or injected scripts).
  - Can lead to full account takeover.

- Clickjacking
  - Embedding a legitimate site in a hidden/transparent iframe.
  - Tricking users into clicking on UI elements they don’t actually see.

- Malicious Script Injections
  - Injecting or swapping JavaScript through vulnerable inputs, third-party scripts, or compromised assets.

### 🧠 Key Understanding

- Browsers happily execute JavaScript that reaches the page, whether it came from:
  - Unsanitized user input.
  - Insecure DOM manipulation.
  - Compromised or untrusted external scripts.

- Without strong validation, encoding, and client-side-aware defenses, these attacks can:
  - Steal data and sessions.
  - Perform actions on behalf of users.
  - Tamper with what users see and trust.

**Day 51 Summary:**
Client-side vulnerabilities are not just “frontend bugs” — they are a direct path to serious compromise when JavaScript is abused.
