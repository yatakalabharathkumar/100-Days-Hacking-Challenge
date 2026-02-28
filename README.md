## 🗓️ Day 63/100 – Path Traversal Basics

**Focus:** Understanding how insecure file‑path handling leads to directory traversal vulnerabilities.

### 🧩 What Is Path Traversal?

Path traversal happens when:

- An application accepts user input that specifies a file path (e.g., `file=profile.jpg`).  
- The server concatenates this input into a server‑side path and then reads or writes that file without proper validation.  
- Attackers inject segments like `../../../../` into the path to escape the intended directory.

Example vulnerable pattern:

```http
GET /view?file=report.pdfIf the server does:path = base_dir + user_input
read_file(path)An attacker can send:GET /view?file=../../../../etc/passwdIf the server does not sanitize this, it may read the system passwd file.🧪 What I Learned PracticallyHow traversal sequences like ../ cause the app to climb out of its target directory.How URL encoding (..%2f, ..%5c) and alternative separators can bypass basic filters.That writing as well as reading paths can be dangerous (e.g., overwriting config files or logs).🛡️ Basic DefensesNever directly concatenate user‑controlled strings into file paths.Validate and encode/sanitize paths to remove or block ../ and ..\.Use allowlists of known‑safe file names or IDs instead of raw paths.Store files in isolated, non‑root directories, limiting what an attacker can reach even if the path check fails.Day 63 Summary:
Today reinforced that even “simple” file‑handling bugs can expose the underlying filesystem when paths are trusted without strict controls.
