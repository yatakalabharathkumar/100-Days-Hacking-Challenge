## Day 4: Subdomain Enumeration & Attack Surface

**Focus:** Reconnaissance, Asset Discovery, and Attack Surface Management

I learned that a secure main domain does not guarantee a secure infrastructure. Attackers look for the "low-hanging fruit" in subdomains.

**Key Learnings:**
- **Enumeration:** The process of listing all valid subdomains for a target (e.g., `admin.site.com`, `dev.site.com`).
- **Hidden Risks:** How developers often leave test environments or old admin panels exposed on public subdomains.
- **Entry Points:** Why these forgotten assets are often less monitored and easier to exploit than the main application.
- **Defense:** The importance of knowing your full inventory/attack surface.

**Concept:** "Security through obscurity" fails when hackers can simply enumerate your hidden sites.
