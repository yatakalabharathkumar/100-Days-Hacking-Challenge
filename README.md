## 🗓️ Day 43/100 – JavaScript Static Analysis

**Focus:** Analyzing client-side code to find logic flaws, hidden endpoints, and secrets.

### 📜 Why Analyze JavaScript?
Modern Single Page Applications (SPAs) push massive amounts of logic to the client. This code contains the blueprint of the application's API and functionality.

### 🕵️‍♂️ Analysis Workflow

**1. Secret Hunting**
*   **Technique:** Grepping for keywords like `api_key`, `token`, `secret`, `password`.
*   **Tools:** JSLinkFinder, SecretFinder.
*   **Risk:** Exposure of third-party credentials allowing lateral movement.

**2. Endpoint Discovery**
*   **Technique:** Extracting URLs and paths from the code to find "shadow APIs" (admin endpoints or beta features not linked in the UI).
*   **Regex:** `/[a-zA-Z0-9\-\_\/]+\.php/` or `/api\/v[0-9]\/[a-z]+/`

**3. Logic Flaws**
*   **Scenario:** Found a variable `isPremiumUser = false`.
*   **Exploit:** Used Console to set `isPremiumUser = true` to unlock features.
*   **Lesson:** Client-side state is untrusted.

### 🛠️ Tools Used
*   **Chrome DevTools:** Sources Tab (Pretty Print).
*   **Burp Suite:** "JS Miner" extension.
*   **Source Maps:** Reverting minified code to original source structure.

**Day 43 Takeaway:** Minification is not encryption. Client-side code is open-source to the attacker.
