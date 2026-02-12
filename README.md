## 🗓️ Day 47/100 – Authorization Bypass & Privilege Escalation

**Focus:** How weak or missing authorization checks allow a regular user to become an admin (vertical privilege escalation).

### 🔐 Concepts

- **Authorization vs Authentication**
  - Authentication: "Who are you?"
  - Authorization: "What are you allowed to do?"
- **Vertical Privilege Escalation**
  - Moving from low-privileged roles (user) to high-privileged roles (admin/moderator).  

### 🧪 Test Scenario (Demo)

The app exposes:
- `/user/profile` – normal user endpoint
- `/admin/users` – should be admin-only

Steps:
1. Log in as a normal user.
2. Capture a request using Burp Suite or a proxy.
3. Manually request:
   - `GET /admin/users`
   - Or edit a request body:
     ```json
     {
       "user_id": 123,
       "role": "admin"   // changed from "user"
     }
     ```
4. If the server responds with **200 OK** and applies the change, you have an authorization bypass.

### ⚙️ Common Weak Patterns

- Relying on **hidden buttons/links** instead of backend checks.
- Trusting client-controlled fields like `role`, `is_admin`, or `permissions`.
- Missing middleware or guards on "internal" admin routes.

### 🛡️ Hardening Strategies

- Implement centralized authorization checks for every sensitive route.
- Never trust client-supplied role or privilege fields.
- Use well-defined roles/permissions and enforce them on the server.
- Add logging for access to admin endpoints and review regularly.

**Day 47 Takeaway:**  
Broken access control is often just "missing code" — one forgotten check can turn any user into an admin.
