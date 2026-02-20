## 🗓️ Day 55/100 – Linux Privilege Escalation Basics

**Focus:** What to do after getting a low-privilege shell on a Linux system.

### 🔍 Step 1: Enumeration

Questions to answer:

- System:
  - OS and kernel version
  - Installed packages and services
- Users & Privileges:
  - Who am I? What groups am I in?
  - Who can use sudo, and for what commands?
- Files & Permissions:
  - World-writable files and directories
  - SUID/SGID binaries
- Automation & Tasks:
  - Cron jobs and timers, who owns them, and what they run
- Secrets:
  - Config files, history files, keys, and stored credentials

Tools that help:
- `LinPEAS`, `LinEnum`, and manual one-liner enumeration. 

### ⚙️ Common Privesc Paths Reviewed

- **Sudo Misconfigurations**
  - Users allowed to run certain programs as root.
  - If those programs can be escaped to a shell (GTFOBins), that often means root.

- **SUID Binaries**
  - Binaries with the SUID bit set run with the owner’s privileges.
  - Abusing poorly chosen or custom SUID programs can lead to escalation.

- **Cron Jobs**
  - Privileged cron tasks that call scripts in writable locations.
  - Editing those scripts to execute a shell with elevated privileges.

- **Weak Permissions & Stored Secrets**
  - World-readable config files containing passwords or keys.
  - SSH keys or database credentials left on disk.

### 🧠 Mindset

- Privilege escalation is a process:
  1. Enumerate.
  2. Identify misconfigurations.
  3. Select a safe, reliable path.
  4. Exploit and confirm.

**Day 55 Summary:**
Getting a shell is only half the story—Linux privilege escalation is about turning that foothold into meaningful control by systematically hunting for weak links.
