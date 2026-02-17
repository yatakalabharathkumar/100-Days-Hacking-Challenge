## 🗓️ Day 52/100 – SQL Injection Basics

**Focus:** Understanding how SQL injection works and why unsafe query building is dangerous.

### 🔍 What is SQL Injection?

SQL Injection happens when:
- An application builds SQL queries by concatenating user input directly into the query string.
- The database cannot distinguish between the intended command and injected data.

Example vulnerable pattern:

```sql
SELECT * FROM users
WHERE username = '`<user_input>`'
AND password = '`<user_input>`';
If user input is:

username: admin

password: ' OR 1=1--

The final query becomes:

sql
SELECT * FROM users
WHERE username = 'admin'
AND password = '' OR 1=1--';
1=1 is always true, so the authentication check is effectively bypassed.

🧪 What I Practiced
Recognizing places where applications build queries using:

String concatenation

Unsafely interpolated parameters

Understanding basic SQLi goals:

Authentication bypass

Extracting data from tables

Modifying or deleting data, depending on privileges

Reading about more advanced SQLi paths (time-based, error-based, UNION-based).

🛡️ Basic Defenses (Preview)
Use parameterized queries / prepared statements.

Avoid building SQL with string concatenation.

Enforce least privilege on database accounts.

Hide detailed SQL error messages from users.
