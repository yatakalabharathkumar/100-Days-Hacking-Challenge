## 🗓️ Day 18/100 – HTML Login Page & Buttons

**Focus:** Building a simple login interface in pure HTML.

### 🔐 Login Form Structure

Key elements used:
- `<form>` – wraps the login inputs and defines `action` + `method`.
- `<label>` – associates text with input fields for accessibility.
- `<input type="text">` – captures username or email.
- `<input type="password">` – captures password, masked in the browser.
- `<button type="submit">` – triggers the form submission.[web:22][web:23]

**Example:**

```html
<form action="/login" method="post">
  <h2>Login</h2>

  <label for="username">Username or Email</label>
  <input type="text" id="username" name="username" required>

  <label for="password">Password</label>
  <input type="password" id="password" name="password" required>

  <button type="submit">Login</button>
</form>
