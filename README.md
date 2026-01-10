## 🗓️ Day 14: Network Reconnaissance & Topology Mapping

**Topic:** Network Scanning, Enumeration, and Topology  
**Tools:** `Zenmap`, `Nmap`

### 🚀 Overview
Today, I focused on **Information Gathering**, specifically analyzing how much data can be extracted from a single "Intense Scan" using **Zenmap** (the Nmap GUI). The goal was to understand the attacker's perspective: *mapping before attacking*.

### 🔍 Key Learnings
1.  **The Path Matters:** It’s not just about the target; it’s about the journey. The scan revealed every intermediate hop (routers/gateways) between my machine and `example.com`.
2.  **Attack Surface:** A vulnerable intermediate node can be an entry point, even if the final target is hardened.
3.  **Data Extracted:**
    *   Open Ports & Protocols
    *   Service Versions (crucial for finding CVEs)
    *   OS Fingerprinting
    *   Network Topology Visualization

### 💻 Command/Technique
Running an "Intense Scan" usually correlates to the following Nmap arguments:
```bash
nmap -T4 -A -v <target_domain>
