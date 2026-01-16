## 🗓️ Day 20/100 – HTML Forms & Input Elements

**Focus:** Complete form implementation and user input collection.

### 📋 Form Elements Mastered

**1. Basic Inputs**
```html
<input type="text" name="username" placeholder="Enter username">
<input type="email" name="email" required>
<input type="password" name="pass">

2. Selection Controls<!-- Radio (single choice) -->
<input type="radio" name="plan" value="basic"> Basic Plan
<input type="radio" name="plan" value="pro"> Pro Plan

<!-- Checkbox (multiple) -->
<input type="checkbox" name="skills" value="html"> HTML
<input type="checkbox" name="skills" value="css"> CSS

<!-- Dropdown -->
<select name="country">
  <option value="IN">India</option>
  <option value="US">USA</option>
</select>

3. Advanced Inputs<textarea name="message" rows="5" cols="30" placeholder="Your message..."></textarea>
<input type="file" name="resume" accept=".pdf,.doc">
4. Complete Form Example<form action="/submit" method="POST" enctype="multipart/form-data">
  <input type="email" name="email" required>
  <input type="file" name="document">
  <button type="submit">Submit Application</button>
</form>
🔍 Security Testing Context
Attack Surfaces Identified:Input sanitization gaps (XSS, SQLi)
File upload validation (RCE, stored XSS)
Business logic manipulation (checkbox/radio tampering)
CSRF exposure (missing tokens)
Hidden fields inspection

Day 20 Takeaway: Forms are where user-controlled data enters the system. Every field is a potential vulnerability entry point.
