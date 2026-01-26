## 🗓️ Day 30/100 – 1 Month Milestone! 🏆

**Focus:** Specialized WordPress Vulnerability Scanning with WPScan.

### 🎉 Milestone Reflection
**30 Days Complete.**
From basic networking concepts to executing automated attacks against databases and CMS platforms. Consistency is the key differentiator.

### 🕵️‍♂️ Tool: WPScan
WPScan is a black box WordPress vulnerability scanner.

**1. Basic Scan**
```bash
wpscan --url http://target-wordpress-site.com

Identifies core version, active theme, and installed plugins.

2. User Enumeration

bash
wpscan --url http://target.com --enumerate u
Risk: Reveals valid usernames (e.g., admin, editor), reducing brute-force complexity by 50%.

3. Vulnerable Plugin Detection

bash
wpscan --url http://target.com --enumerate p --plugins-detection aggressive
Risk: Matches installed plugin versions against the WPScan Vulnerability Database (WPVDB) to find known exploits.

4. Password Brute Force

bash
wpscan --url http://target.com --passwords /path/to/wordlist.txt --usernames admin
🛡️ Defensive Takeaways
Disable User Enumeration: Block access to /?author=1 endpoints.

Update Everything: Auto-update plugins and themes.

Limit Login Attempts: Install security plugins (Wordfence/Sucuri) to stop brute-force.

Hide Version Info: Remove generator meta tags to slow down reconnaissance.
