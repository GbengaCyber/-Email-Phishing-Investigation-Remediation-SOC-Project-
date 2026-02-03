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

- SignInLogs

  <img width="700" height="300" alt="image" src="https://github.com/user-attachments/assets/a488bc62-df05-4f8d-97a1-6db568dffe1f" />

- CloudAppEvents
  
<img width="700" height="300" alt="image" src="https://github.com/user-attachments/assets/e2420fae-4a6d-4998-83e6-5f82e89f513e" />

---

## 🎯 Threat Intelligence

Source IP addresses were enriched using AbuseIPDB and confirmed to have a malicious reputation related to brute force activity.

**Threat intelligence evidence:**


<img width="600" height="350" alt="Screenshot 2026-01-27 at 4 27 09 PM" src="https://github.com/user-attachments/assets/fe961f60-a078-4972-9709-1c3ef5f75aa4" />

---

## 🎯 Investigation Result

No successful logons were identified.
The brute force attempt did not result in account compromise.

---
## 🎯 Sentinel Rule Configuration

A Microsoft Sentinel analytics rule was created to alert on brute force authentication patterns.


<img width="500" height="250" alt="image" src="https://github.com/user-attachments/assets/643700b0-c3b9-466f-ba59-466049398bd1" />


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
