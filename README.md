## 🗓️ Day 15/100 – Web Development Basics for Hackers

**Focus:** Understanding website structure before testing its security.  
**Topics:** HTML, CSS, JavaScript

### 🌐 What I Studied
1. **HTML (Structure):**
   - Defines the skeleton of a webpage (headings, paragraphs, forms, buttons).
   - Helps locate input fields and parameters that may become injection points.[web:8]

2. **CSS (Styling):**
   - Controls layout, colors, fonts, and responsive design across devices.
   - While not a direct attack surface in most cases, misconfigurations in linked resources or imports can reveal internal paths.[web:8]

3. **JavaScript (Client-Side Logic):**
   - Handles input validation, DOM manipulation, and API requests.
   - Critical for security testing: DOM-based XSS, insecure client-side validation, and exposed API endpoints.[web:6][web:8]

### 🔍 Why This Matters for Ethical Hacking
- You cannot effectively test a web app without understanding how the frontend talks to the backend.
- Knowing where data is generated, transformed, and sent is key to finding vulnerabilities like XSS, CSRF, and injection.

### 📎 Notes
This day was about strengthening fundamentals rather than running tools. The better I understand how developers think, the better I can model realistic attack paths.
