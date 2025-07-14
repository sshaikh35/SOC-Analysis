# 🛡️ SOC Case 3: SQL Injection + XSS + LFI Attempt

## 📅 Date: Mar 07, 2024
## 📌 Severity: High
## 🎯 Type: Web Application Attack

### 🔍 Summary
An alert was triggered for a suspicious GET request involving SQL Injection patterns, cross-site scripting (XSS), and command execution attempts targeting `WebServer1000`.

### 🌐 Source
- IP: `118.194.247.28`
- Reputation: **Malicious** (China Unicom Beijing - flagged in VirusTotal)

### 🧪 Request Pattern
The payload contained:
- SQL Injection (`AND 1=1`, `UNION ALL SELECT`)
- XSS payload (`<script>alert("XSS")</script>`)
- Command execution (`xp_cmdshell`)
- File access (`cat /etc/passwd`)

### 🛠️ Actions Taken
- Marked as **True Positive**
- Verified IP via threat intel
- Confirmed not a test
- Flagged device action as **Allowed** (requires remediation)
- **Recommended blocking** source IP and creating WAF rule for pattern

### 📌 Learnings
- Always verify “Planned Test” using threat intel or internal test IPs
- Never leave Alert Notes empty
- Suggest containment even if automation doesn’t act

---

> Investigation Time: 8 mins  
> Playbook Success Rate: 33%  
> Case Score: 50%
