# 🧠 SOC Analyst Case Report — Case 4

## 🛡️ Alert Details

- **Alert Name:** SOC144 - New Scheduled Task Created  
- **Severity:** Critical  
- **Date:** May 14, 2021 – 03:22 PM  
- **Event ID:** 91  
- **Alert Type:** Malware  
- **Source Hostname:** Helena  
- **Source IP:** 172.16.17.36  
- **Device Action:** Allowed

---

## 🚨 Summary

A scheduled task was created on host `Helena`. Upon analysis, the task was found to execute a **malicious Python file**, identified by its hash `65d880c7f474720dafb84c1e93c51e11`, which is linked to Trojan activity. The file beaconed to the known **Command & Control (C2) IP address** `92.27.116.104`.

---

## 🧩 Investigation Flow

| Step | Action Taken | Result |
|------|--------------|--------|
| 1. Check for C2 communication | Investigated traffic | ✅ **Accessed** |
| 2. Analyze the binary hash | VirusTotal and Threat Intel | ✅ **Malicious** |
| 3. Check malware status | Verified in EDR | ❌ **Not Quarantined** |

---

## 🧠 Analyst Notes

- **Hash Detected**: `65d880c7f474720dafb84c1e93c51e11`
- **C2 IP Contacted**: `92.27.116.104`
- **Technique Used**: Scheduled Task for persistence
- **Threat Type**: Trojan / Backdoor
- **Alert Verdict**: ✅ **True Positive**

---

## 🧰 Recommended Mitigation

- 🔒 **Isolate** the host (`Helena`) from the network
- 🗑️ **Remove** scheduled task and the malicious Python script
- 🔥 **Block C2 IP** `92.27.116.104` at the firewall
- 🔍 **Perform IOC sweep** across endpoints for hash/IP traces
- 🧑‍🏫 **Educate user** on executing unverified scripts

---

## 📁 Artifacts

| Type | Value | Comment |
|------|-------|---------|
| MD5 Hash | `65d880c7f474720dafb84c1e93c51e11` | Malicious Trojan |
| IP Address | `92.27.116.104` | C2 Server |

---

## 📊 Case Stats

- **Score**: 100%
- **Playbook Success Rate**: 100%
- **Investigation Time**: 18 minutes

---

## 📌 Learning Outcome

This case highlighted how attackers use **scheduled tasks** to maintain persistence. Quick detection and full playbook execution helped identify the threat early. Ensuring quarantine and adding IOC hunting are key follow-up steps for containment.

