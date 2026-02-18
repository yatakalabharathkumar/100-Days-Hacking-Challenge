## 🗓️ Day 53/100 – Preventing SQL Injection

**Focus:** Moving from understanding SQL injection to hardening applications against it.

### ✅ Parameterized Queries / Prepared Statements

Replaced vulnerable patterns like:

```sql
-- vulnerable
query = "SELECT * FROM users WHERE username = '" + user + "' AND pass = '" + pass + "'";
with parameterized forms:

sql
-- safe pattern
query = "SELECT * FROM users WHERE username = ? AND pass = ?";
setParam(1, user);
setParam(2, pass);
Key points:

SQL and data are sent separately.

The database treats parameters as literal values, not part of the SQL syntax.

This breaks classic payloads such as ' OR 1=1-- because they are no longer interpreted as code.

🧰 ORMs and Query Builders
ORMs (and query builders) help generate parameterized queries by default.

Still important to:

Avoid manual string concatenation.

Use the ORM’s parameter APIs instead of raw interpolated SQL.

🧱 Extra Layers
Validate and/or whitelist input where it makes sense (e.g., IDs must be numeric, enum values restricted).

Use least-privilege database accounts; the app should not connect as a superuser.

Suppress detailed SQL error messages from end users.

🔥 WAF vs. Secure Code
Web Application Firewalls can:

Block known SQLi payloads with signatures.

Use heuristic and behavioral analysis to detect suspicious patterns.

But:

Misconfigurations or novel payloads can bypass WAF rules.

WAFs should be additional protection, not the main fix.
