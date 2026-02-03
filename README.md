# -Email-Phishing-Investigation-Remediation-SOC-Project-



# 🛡️ Project Overview
This project documents a realistic SOC Tier 1/2 email phishing investigation, focusing on detection, analysis, containment, remediation, and lessons learned using Microsoft Defender XDR &amp; cloud telemetry.

The phishing attack was intentionally simulated in a controlled lab environment to validate detection capabilities, analyst response, and security controls.


## Incident Summary

Organization: Tech Creatives
Incident Type: Email Phishing / Credential Harvesting
Severity: High
Status: Resolved




---

## 🎯 Attack Simulation (Phishing Scenario)

This incident was intentionally simulated in a controlled lab environment to replicate a common real-world phishing attack and validate SOC detection and response workflows.

---

🎯 Simulation Objective

Test Microsoft Defender XDR phishing detections

Observe user click behavior and cloud sign-in correlation

Practice end-to-end SOC incident response

---

🧪 Simulation Setup

I Created a test user account: test@creatives.onmicrosoft.com in my Azure tenant.

I Used an external Gmail account to simulate an attacker-controlled sender


Delivered a plain-text phishing email containing a malicious URL (credential harvesting style)

Ensured Safe Links policy allowed user click telemetry for detection

<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/6add861e-02e6-4aa8-a75f-edb578566257" />



---

⚔️ Attack Execution

- Phishing email sent from external Gmail address
- User received and opened the email
- User clicked the embedded phishing URL
- Credential harvesting page simulated (no real credentials stored)
- New cloud session generated from an unfamiliar / anonymous IP
- Microsoft Defender XDR generated a High-severity alert


<img width="600" height="248" alt="Screenshot 2026-01-29 at 6 05 34 PM" src="https://github.com/user-attachments/assets/c3596f7d-0048-4002-960d-6ba93844a3ce" />

---

## 🎯 Alert Details

Alert Title: Anonymous IP Address

User Identity: test@creatives.onmicrosoft.com

User Name: Test SOC

Suspicious IP Address: 2a0d:5600:8:94::d593:6202

Alert Generated: Jan 29, 2026 – 8:41 PM


---
## 🎯 Investigation Process (Simulated Attack Response)

- Alert Triage

- Reviewed alert involving uncommon IP sign-in activity

- IP geolocation resolved to United States, not previously associated with the user

- Login pattern did not match known historical sign-in behavior

** Investigation evidence: ** 

- Correlation & Analysis

- Correlated Azure AD Sign-in Logs with Cloud App Events

- Identified suspicious cloud activity following link interaction

- Evidence indicated credential harvesting


- SignInLogs

  <img width="1000" height="300" alt="image" src="https://github.com/user-attachments/assets/a488bc62-df05-4f8d-97a1-6db568dffe1f" />

- KQL Query
 
    <img width="700" height="350" alt="image" src="https://github.com/user-attachments/assets/4c66b310-3317-40b5-93a6-db39e7df3ec4" />



---

## 🎯 Threat Intelligence


- Phishing sender identified:  ** anina300987@gmail.com **

- Malicious URL analyzed using Any.Run: https://theme.goopoobai.network/UHHxsoV!3c0tRVPqto/

- Verdict: Suspicious phishing infrastructure

** Threat Intelligence Evidence **

<img width="800" height="300" alt="image" src="https://github.com/user-attachments/assets/0e15a483-981f-4013-b637-7581643a56eb" />

 
 
---
## 🎯 Incident Response Actions
🔒 Containment

- I Marked user account as Compromised

- Temporarily isolated user access

- Revoked active sessions

 <img width="700" height="200" alt="image" src="https://github.com/user-attachments/assets/764e857c-9955-4c9d-9bd2-aa0caaea76ff" />


---
## 🎯 🏷️ MITRE ATT&CK Mapping

MITRE ATT&CK Mapping
- T1110 – Brute Force
- T1110.003 – Password Spraying
- T1078 – Valid Accounts (conditional)
---
## 🎯 Response Actions

- Block malicious IP addresses (Firewall / NSG)
- Review authentication activity for lateral movement
- Reset or disable targeted accounts if required
- Enforce MFA and account lockout policies
---

## 🎯 Skills Demonstrated

- KQL log analysis
- SOC alert triage
- Threat intelligence enrichment
- MITRE ATT&CK mapping
- Incident response decision-making
