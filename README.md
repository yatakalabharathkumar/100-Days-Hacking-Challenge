## 🗓️ Day 54/100 – File Upload Vulnerabilities

**Focus:** Understanding how insecure file upload functionality can be abused and how to secure it.

### ⚠️ What Can Go Wrong?

- Unrestricted file upload:
  - Any file type is accepted (scripts, executables, archives).
  - Files are stored in web-accessible locations where they might be executed.
- Attacker goals:
  - Upload a web shell to get remote command execution.
  - Host phishing pages or malware.
  - Overwrite or plant files in sensitive paths (if path controls are weak).

### 🧪 Techniques I Read About / Practiced

- Extension and MIME/type bypass:
  - Using names like `shell.php.jpg` or `shell.asp;.jpg`.
  - Sending inconsistent `Content-Type` headers to fool basic checks.
- Path-related tricks:
  - Uploading via endpoints that allow path traversal to escape the intended directory.
- Triggering execution:
  - Accessing the uploaded script via direct URL if the directory is executable.
  - Abusing server/parsing misconfigurations.

### 🛡️ Basic Hardening Ideas

- Allowlist only specific, safe file types (e.g., certain image formats).
- Validate:
  - File extension
  - MIME type
  - Magic bytes / content where possible
- Store uploads:
  - Outside the webroot or in non-executable locations.
  - With randomized, server-side generated filenames.
- Apply:
  - Size limits
  - Malware scanning where appropriate
  - Extra checks before serving files back to users

**Day 54 Summary:**
File uploads are powerful, but if you don’t treat every upload as hostile by default, you’re effectively offering attackers a write primitive on your server.
