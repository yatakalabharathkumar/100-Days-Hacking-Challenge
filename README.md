## 🗓️ Day 48/100 – CTF-Style Pentest as Incident Response Drill

**Focus:** Using a CTF lab not just to hack, but to simulate a real incident from attack to response.

### 🎯 Objective

Treat a CTF environment like:
- A small production network that just got breached.
- A place to practice both **offense (red)** and **defense (blue)**.

### 🟥 Red Team Phase (Attacker View)

- Recon: Port scans, service fingerprinting, basic enumeration.
- Initial access: Exploiting a web or service vuln to gain a foothold.
- Privilege escalation: Local privesc on the compromised host.
- Lateral movement: Pivoting to another machine or service inside the lab.

Each step, I noted:
- Commands used.
- Indicators left behind (logs, processes, new files, suspicious connections).

### 🟦 Blue Team Phase (Defender View)

Switched to “incident responder” mode:
- Reviewed system and application logs for:
  - Failed logins, strange user agents, odd process launches.
- Looked at network traces for:
  - Suspicious outbound connections, repeated scans, lateral movement.
- Tried to answer:
  - When did the compromise start?
  - Which host was patient zero?
  - What data or systems were touched?

### 🧠 Takeaways

- CTFs can be more than puzzles; they are **great sandboxes for IR practice**.
- Thinking like a SOC analyst changes how you attack:
  - You start noticing what traces your tools and payloads leave behind.
- Incident response is a loop:
  - Detect → Analyze → Contain → Eradicate → Recover → Document.

**Day 48 Summary:**  
Today’s “game” wasn’t just about capturing flags, it was about telling the full breach story.
