## 🗓️ Day 44/100 – API Security Testing

*Focus:* Testing REST APIs for Broken Authentication and Authorization (OWASP API Top 10).

### 🔗 What is API Security?
Unlike traditional web apps, APIs expose logic and data directly. Security relies heavily on proper implementation of AuthN (Who are you?) and AuthZ (What can you do?).

### ⚔️ Vulnerabilities Tested

*1. BOLA (Broken Object Level Authorization)*
*   Also known as IDOR (Insecure Direct Object Reference).
*   *Request:* GET /api/v1/messages/500
*   *Attack:* Changed ID to 501.
*   *Result:* Server returned message 501 belonging to another user.
*   *Fix:* Check if (resource.owner == current_user) on every access.

*2. Broken Authentication*
*   *Attack:* Accessed /api/v1/admin/dashboard without an Authorization: Bearer header.
*   *Result:* 200 OK. The developer assumed only the Admin UI would call this endpoint.

*3. Mass Assignment*
*   *Request:* POST /api/profile
*   *Payload:*
    json
    {
      "username": "hacker",
      "email": "hacker@test.com",
      "role": "admin"  <-- Injected Field
    }
    
*   *Result:* Account created with Admin privileges because the backend bound all input fields directly to the User model.

### 🛠️ Tools Used
*   *Postman:* For crafting and organizing API requests.
*   *Burp Suite:* For intercepting traffic and fuzzing IDs.

*Day 44 Takeaway:* APIs often trust the client too much. Authorization must be enforced at the object level, not just the URL level.
