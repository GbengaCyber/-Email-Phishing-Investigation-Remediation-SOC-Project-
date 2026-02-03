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
## 🎯 Lab Environment

- Microsoft Defender for Endpoint (MDE)
- Microsoft Sentinel
- Log source: `SignInLogs`

<img width="650" height="300" alt="image" src="https://github.com/user-attachments/assets/e8c0fe64-9b9e-49d3-b776-646e87a11d84" />



---


## 🎯 Attack Simulation

After onboarding the VM to MDE, I simulated a brute force attack by attempting multiple failed logins using incorrect passwords from two different external IP addresses.

This activity was designed to generate realistic authentication telemetry for detection and investigation.



---

## 🎯 Attack Simulation (Phishing Scenario)

This incident was intentionally simulated in a controlled lab environment to replicate a common real-world phishing attack and validate SOC detection and response workflows.

🎯 Simulation Objective

Test Microsoft Defender XDR phishing detections

Observe user click behavior and cloud sign-in correlation

Practice end-to-end SOC incident response

🧪 Simulation Setup

Created a test user account: test@creatives.onmicrosoft.com

Used an external Gmail account to simulate an attacker-controlled sender

Delivered a plain-text phishing email containing a malicious URL (credential harvesting style)

Ensured Safe Links policy allowed user click telemetry for detection

<img width="815" height="248" alt="Screenshot 2026-01-29 at 6 05 34 PM" src="https://github.com/user-attachments/assets/c3596f7d-0048-4002-960d-6ba93844a3ce" />



---
## 🎯 Investigation

The following questions were addressed during investigation:
- Were the source IPs internal or external?
- Did any successful logons occur after failures?
- Was a specific account targeted?
  
Authentication logs were reviewed to validate impact.


** Investigation evidence: ** 

<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/fd956234-ac46-4199-acc2-145c5b3279d2" />


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
