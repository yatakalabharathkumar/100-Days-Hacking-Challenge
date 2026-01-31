## 🗓️ Day 35/100 – File Systems Across Platforms

**Focus:** Understanding OS-specific file structures for malware analysis and incident response.

### 💾 Windows (NTFS) - Critical PathsC:\Windows\System32\  ← Malware DLLs, drivers
C:\Users$$user]\AppData\Roaming\  ← Persistence, config files
C:\ProgramData\  ← System-wide malware
%TEMP%\  ← Temporary payloads
HKCU\Software\Microsoft\Windows\CurrentVersion\Run  ← Registry persistence
### 🐧 Linux/Unix - Key Locations/etc/passwd  ← User enumeration
/var/log/auth.log  ← Failed login attempts
/tmp/  ← Temporary exploits, scripts
/home/[user]/.ssh/  ← Key theft target
/etc/crontab  ← Scheduled task persistence
/proc/[pid]/  ← Live process inspection
### 📱 Android - Mobile File System/data/data/[package]/  ← App private data
/sdcard/Android/data/  ← External app storage
/sdcard/Download/  ← User downloads (malware entry)
/system/app/  ← System applications
### 🔍 Malware Analysis Applications
1. **Persistence Detection:** Check startup folders, scheduled tasks, service registrations.
2. **Artifact Collection:** Gather memory dumps, registry hives, log files.
3. **Lateral Movement:** Identify shared directories, writable system paths.

### 🛡️ Defensive Takeaways
*   Monitor file creation in sensitive directories
*   Implement application whitelisting
*   Regularly audit scheduled tasks and startup programs
*   Use file integrity monitoring (OSSEC, Tripwire)
