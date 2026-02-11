## 🗓️ Day 46/100 – Open Redirects & Phishing  

**Focus:** Understanding open redirect vulnerabilities and their role in phishing attacks.

### 🔁 What is an Open Redirect?

An open redirect happens when an application:

1. Takes a user‑controlled input that looks like  
   `?next=/login` or `?redirect=https://foo.com`.
2. Uses that input directly in a redirect response without validation or allow‑listing.

Example patterns:
```http
GET /login?next=https://realbank.com/dashboard
302 Location: https://realbank.com/dashboard

If the next parameter is not validated, an attacker can set:GET /login?next=https://phish-site.com
302 Location: https://phish-site.com🪤 How Attackers Abuse Open RedirectsAttackers combine open redirects with social engineering:Phishing via Trusted DomainsEmail: "Click here to check your balance: https://realbank.com/login?next=https://fake-login.com"User only sees realbank.com in the link and browser bar before being silently redirected to the malicious site.Chain with Cloned Login PagesRedirect target is a fake login / OTP page that looks exactly like the original.Credentials and MFA codes are captured.OAuth‑Like FlowsUse open‑redirect in flows that look like consent prompts, leading the user to a fake authorization page.🛡️ Mitigation StrategiesPrefer allow‑lists of allowed paths/domains for redirects.Avoid using full user‑supplied URLs; instead use:Small fixed codes mapped server‑side (e.g., ?redirect_id=1).Relative paths instead of absolute URLs where safe.If redirecting externally, show a confirmation screen explaining that the user is leaving the current site.🧠 Day 46 TakeawayOpen redirects are often treated as low‑severity UX quirks, but in the wild, they significantly boost phishing success. A well‑scoped redirect policy is a simple but powerful defensive layer.
