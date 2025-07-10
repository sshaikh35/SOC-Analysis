# 📧 Email Header Analysis - SOC Hands-On Case

🔐 **File:** `Challenge+Mail.zip`  
📁 **Location:** `C:\Users\LetsDefend\Desktop\Files\Challenge+Mail.zip`  
🗝️ **Password:** `infected`  
📅 **Date of Analysis:** July 8, 2025

---

## 🧠 Objective

This task was part of a hands-on SOC analyst training simulation focused on understanding and analyzing email headers to detect potential phishing or malicious activity.

---

## 🔍 Tasks & Answers

| Task | Answer | Result |
|------|--------|--------|
| What is the **recipient address** if you reply to the email? | `info@letsdefend.io` | ✅ Correct |
| What **year** was the email sent? | `2022` | ✅ Correct |
| What is the **Message-ID** of the email? | `74bda5edf824cea8aad36e707.675c34a61f.20220321204512.a02caaccf3.a268ce5a@mail41.suw13.rsgsv.net` | ✅ Correct |

---

## 📚 Skills Practiced

- ✅ Email Header Analysis (`.eml` format)
- ✅ Identifying spoofed sender behavior
- ✅ Extracting key header metadata (Message-ID, From, To, Date)
- ✅ Building situational awareness of email-based threats

---

## 🔎 Learnings

- **Email headers** are essential in analyzing the trustworthiness and routing of an email.
- A well-crafted phishing email can appear legitimate at first glance — header analysis helps uncover hidden details.
- **Message-ID** is a unique fingerprint for each email and can be used to trace and correlate email traffic.
- Tools like `Notepad++`, `Outlook`, and `Gmail` can be used to extract header data from `.eml` files.

---

## 🧩 Future Enhancements

- Integrate VirusTotal or MISP to check embedded links or attachments.
- Build an automated parser for `.eml` headers using Python.
- Cross-reference sender IP with threat intel sources.

---

## 📌 Use Case

This experience simulates the initial phase of an **email threat investigation** as a Level 1 SOC Analyst and helps build confidence in log analysis and detection workflows.

---

## 🏷️ Tags

`SOC Analyst` `Email Security` `Phishing` `Header Analysis` `LetsDefend` `Cybersecurity Lab` `Blue Team`
