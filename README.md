## 🗓️ Day 60/100 – Advanced SSRF Filters & Bypasses

**Focus:** Understanding how SSRF protections are commonly implemented and how attackers bypass them.

### 🚫 Common “Fixes” (and Their Weaknesses)

- Simple blacklists:
  - Block `127.0.0.1`, `localhost`, `169.254.169.254`, etc.
  - Rely on string matches in the URL.

- Basic whitelists:
  - Allow only certain hostnames, but:
    - Do not handle subdomains correctly.
    - Do not defend against open redirects.

### 🧨 Bypass Techniques Reviewed

- Alternate IP Representations
  - Hex, octal, and mixed formats for IP addresses.
  - Alternative loopback forms like `127.1` or crafted domains resolving to loopback.
  - Goal: reach the same internal host while avoiding literal blacklist patterns.

- URL Tricks & Redirects
  - Exploit open redirects on allowed domains.
  - Let the SSRF client follow redirects to the real internal target.
  - Use URL parsing quirks, encoded characters, and user-info sections (`user@host`) to bypass naive parsers.

- DNS Rebinding
  - Use a domain that:
    - Resolves to a benign IP during validation.
    - Then resolves to an internal IP when the actual request is made.
  - Breaks defenses that validate only on the initial DNS resolution step.

- Advanced Payloads
  - Using schemes like `gopher://`, `file://`, or `dict://` in contexts where the HTTP client supports them.
  - Leveraging curated payload lists and cheat sheets for edge cases.

### 🛡️ Defensive Takeaways (High Level)

- Use robust URL parsing and **strict allowlists** for outbound requests.
- Block internal ranges and metadata endpoints at both app and network levels.
- Avoid following redirects blindly, or re-validate after redirection.
- Treat SSRF as a design concern, not just a regex problem.

**Day 60 Summary:**
Today’s focus was on how “patching SSRF” can be fragile when it’s based on simple string filters—and why layered, well-validated controls are needed instead.
