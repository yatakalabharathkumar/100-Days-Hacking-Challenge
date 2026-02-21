## 🗓️ Day 56/100 – Windows Privilege Escalation Basics

**Focus:** Understanding how to escalate from a low-privileged user to Administrator / SYSTEM on Windows.

### 🔍 Step 1: Enumeration

Questions to answer:

- Who am I?
  - Current user, groups, token privileges.
- What is the system?
  - Windows version, patches, installed software.
- What is running?
  - Services, scheduled tasks, startup items.
- What can I touch?
  - File/registry permissions, writable directories, service binaries.
- Any secrets?
  - Saved credentials, config files, PowerShell history, registry hives.

Helpful tools:
- `WinPEAS` (broad automated enumeration)
- `PowerUp` (service/task misconfig checks)
- `Seatbelt` (situational awareness)

### ⚙️ Common Windows Privesc Ideas

- **Service Misconfigurations**
  - Services running as SYSTEM but with weak file or registry ACLs.
  - If you can change the service binary/path and restart the service, you can execute code as SYSTEM.

- **Scheduled Tasks**
  - Tasks running with high privileges but referencing scripts/binaries in writable locations.
  - Editing those files to run a payload.

- **Weak Permissions & Credentials**
  - World-readable config files holding passwords or API keys.
  - Credentials stored in scripts, registry, or command histories that can be reused.

### 🧠 Mindset

- Enumerate thoroughly, then:
  1. Identify misconfigurations and secrets.
  2. Map them to known escalation techniques.
  3. Exploit safely and verify elevation (Administrator / SYSTEM).

**Day 56 Summary:**
On Windows, privilege escalation is about understanding how services, tasks, permissions, and credentials fit together—and exploiting the one place where that model breaks.
