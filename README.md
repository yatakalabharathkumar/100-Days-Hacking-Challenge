## 🗓️ Day 22/100 – PHP Fundamentals: Deep Dive into Backend Logic

**Focus:** Server-side execution flow, syntax analysis, and security implications of basic PHP constructs.

### 🐘 Deep Technical Breakdown

**1. Server-Side Execution (The "Black Box")**
*   **Mechanism:** When a browser requests a `.php` file, the web server (Apache/Nginx) passes it to the PHP Interpreter. The interpreter executes the logic, talks to the database, and generates an HTML response.
*   **Hacking Context:** Because the code executes *before* the response is sent, the source code is invisible to the user.
    *   *Attack Vector:* We use **Fuzzing** (sending malformed data) to trigger errors. Detailed PHP errors (Stack Traces) reveal paths, file names, and logic snippets that the server *should* have kept hidden.

**2. Variables & Data Handling (`$variable`)**
*   **Syntax:** All variables start with `$`. PHP is dynamically typed (no need to declare `int` or `string`).
*   **Mechanism:** Variables like `$_GET`, `$_POST`, and `$_COOKIE` are "Superglobals" – they automatically capture user input.
*   **Hacking Context:** These Superglobals are the **primary entry points** for attacks.
    *   If `$user = $_GET['user'];` is used directly in a query -> **SQL Injection**.
    *   If `echo $_GET['msg'];` is used directly in output -> **Cross-Site Scripting (XSS)**.

**3. Comments & Information Leakage**
*   **Syntax:** `//` for single line, `/* ... */` for blocks.
*   **Hacking Context:** While comments are usually stripped from execution, they persist in:
    *   Backup files (`index.php.bak`, `config.php.old`).
    *   Misconfigured servers serving raw text.
    *   **Insight:** Comments like `// TODO: Implement CSRF token here` act as a neon sign pointing hackers to a vulnerability.

**4. PHP Tags (`<?php ?>`)**
*   **Mechanism:** Directs the server to process instructions.
*   **Hacking Context:** In **File Upload** attacks, if an attacker uploads a file named `image.php.jpg` and the server allows it, embedding `<?php system($_GET['cmd']); ?>` inside the image data can lead to **Remote Code Execution (RCE)**.

### 🧠 The Shift: Visuals vs. Logic
Moving from HTML/CSS to PHP means moving from *Presentation* to *Processing*. Security flaws in HTML ruin the look; security flaws in PHP compromise the entire server.

**Day 22 Takeaway:** Mastery of PHP syntax allows you to trace the "invisible" path of user data, predicting where validation might fail.
