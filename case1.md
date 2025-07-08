 CVE-2024-49138 Exploitation Detection - SOC Case Report

 Alert Overview

**Date:** January 22, 2025
**Severity:** Medium
**Analyst:** Sameer (SOC L1)
**Alert Type:** Privilege Escalation
**Rule Triggered:** SOC335 - CVE-2024-49138 Exploitation Detected

---

## 🔎 Alert Details

| Field              | Value                                                              |
| ------------------ | ------------------------------------------------------------------ |
| **Event ID**       | 313                                                                |
| **Hostname**       | Victor                                                             |
| **IP Address**     | 172.16.17.207                                                      |
| **Process Name**   | svohost.exe                                                        |
| **Process Path**   | `C:\temp\service_installer\svohost.exe`                            |
| **Parent Process** | `powershell.exe`                                                   |
| **Command Line**   | `\??\C:\Windows\system32\conhost.exe 0xffffffff -ForceV1`          |
| **File Hash**      | `b432dcf4a0f0b601b1d79848467137a5e25cab5a0b7b1224be9d3b6540122db9` |
| **User**           | EC2AMAZ-ILGVOIN\LetsDefend                                         |
| **Device Action**  | Allowed                                                            |

---

## 🔬 Investigation Summary

* The alert was triggered for execution of a suspicious file (`svohost.exe`) from the temp directory, a known technique in privilege escalation.
* The file hash matched known **malicious** entries in threat intel feeds.
* The executable was spawned by **PowerShell**, commonly used in exploitation.
* **C2 Access** was confirmed in the logs, but incorrectly answered as "Not Accessed" during playbook steps.
* Malware was **not quarantined**, leaving the host potentially vulnerable.

---

## 📘 Playbook Execution Summary

| Playbook Step           | Your Answer     | Correct Answer  | Notes                         |
| ----------------------- | --------------- | --------------- | ----------------------------- |
| Check C2 Access         | Not Accessed    | Accessed        | ❌ Missed C2 callback evidence |
| Analyze Malware         | Malicious       | Malicious       | ✅ Correct                     |
| Check Quarantine Status | Not Quarantined | Not Quarantined | ✅ Correct                     |

---

## 🔖 Extracted IOCs

| Type     | Value                                                              | Comment        |
| -------- | ------------------------------------------------------------------ | -------------- |
| MD5 Hash | `b432dcf4a0f0b601b1d79848467137a5e25cab5a0b7b1224be9d3b6540122db9` | Malicious hash |

---

## 📚 Final Verdict

> **True Positive** ✔️
> Privilege escalation attempt confirmed using CVE-2024-49138. The file is malicious and remained unquarantined. C2 access was initiated by the malware, confirming compromise.

**Next Actions Suggested:**

* Manually isolate the host via EDR.
* Perform an IOC sweep across networked endpoints.
* Add hash to blocklist.
* Initiate deeper forensic review.

---

## 🔎 Areas of Improvement

### ❌ Missed C2 Communication Detection

You marked the C2 check as "Not Accessed" while the logs clearly showed consistent API requests, confirming the malware was beaconing.

> **Fix:** Always cross-reference endpoint logs and check if the malware contacted a C2 domain or IP. Look for recurring intervals or external traffic patterns.

### 🖉 Empty Analyst Note

> **Fix:** Always document your justification for closing an alert. A short note like: *"Hash confirmed malicious, C2 reached, no quarantine action observed. Marking as TP"* would be ideal.

---

## 👍 Great Work

* speed: 12 mins resolution!
* Correctly identified malicious hash.
* Used threat intel effectively.


