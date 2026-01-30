# Deliverable 4.7: Incident Response Plan & Playbooks
## NordicShield Technologies Oy

---

```
╔══════════════════════════════════════════════════════════════════╗
║            INCIDENT RESPONSE PLAN & PLAYBOOKS                     ║
║                                                                    ║
║  Document ID: IR-NS-2026-001                                      ║
║  Version: 1.0                                                     ║
║  Author: [YOUR NAME]                                              ║
║  Classification: Confidential                                     ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Document Purpose

This document establishes NordicShield's Incident Response (IR) capability, including the IR plan, team structure, procedures, and specific playbooks for common incident types. Effective incident response minimizes damage, reduces recovery time, and preserves evidence for investigation.

**Framework Reference:** NIST SP 800-61 Rev. 2 - Computer Security Incident Handling Guide

---

## Instructions

1. Establish the incident response framework and governance
2. Define team roles and escalation procedures  
3. Create incident-specific playbooks
4. Complete all `[YOUR INPUT]` sections
5. Ensure alignment with legal and regulatory requirements

---

# SECTION A: INCIDENT RESPONSE FRAMEWORK

## A.1 Incident Response Philosophy

```
[YOUR INPUT - Define IR principles]

NORDICSHIELD INCIDENT RESPONSE PRINCIPLES
=========================================

MOTTO: "Prepare, Detect, Respond, Recover, Learn"

CORE PRINCIPLES:

1. PREPARATION IS EVERYTHING
   [YOUR INPUT - The best incident is one you're ready for]
   - Documented procedures before they're needed
   - Trained and exercised team
   - Tools and access ready

2. SPEED MATTERS
   [YOUR INPUT - Every minute counts in limiting damage]
   - Pre-authorized actions for common scenarios
   - Clear escalation paths
   - No bureaucratic delays during incidents

3. EVIDENCE PRESERVATION
   [YOUR INPUT - Protect the ability to investigate]
   - Forensic-first mindset
   - Chain of custody from moment one
   - Document everything

4. COMMUNICATION
   [YOUR INPUT - Right information to right people at right time]
   - Stakeholders informed appropriately
   - External communications coordinated
   - No surprises

5. CONTINUOUS IMPROVEMENT
   [YOUR INPUT - Every incident is a learning opportunity]
   - Blameless post-mortems
   - Actionable improvements
   - Track improvements to completion
```

## A.2 Incident Response Lifecycle

```
[YOUR INPUT - Describe each phase]

NIST SP 800-61 INCIDENT RESPONSE LIFECYCLE
==========================================

┌─────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                    1. PREPARATION                                │    │
│  │  [YOUR INPUT - Activities before incidents occur]               │    │
│  │  • IR plan development and maintenance                          │    │
│  │  • Team training and exercises                                  │    │
│  │  • Tool deployment (forensic, containment)                      │    │
│  │  • Playbook development                                         │    │
│  │  • Contact lists and communication templates                    │    │
│  └───────────────────────────────┬─────────────────────────────────┘    │
│                                  │                                       │
│                                  ▼                                       │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │            2. DETECTION & ANALYSIS                              │    │
│  │  [YOUR INPUT - Identifying and validating incidents]            │    │
│  │  • Alert monitoring (SIEM, EDR, users)                          │    │
│  │  • Triage and initial analysis                                  │    │
│  │  • Incident classification and severity                         │    │
│  │  • Scope determination                                          │    │
│  │  • Documentation initiation                                     │    │
│  └───────────────────────────────┬─────────────────────────────────┘    │
│                                  │                                       │
│                                  ▼                                       │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │            3. CONTAINMENT, ERADICATION, RECOVERY                │    │
│  │  [YOUR INPUT - Stop damage, remove threat, restore]             │    │
│  │                                                                  │    │
│  │  CONTAINMENT                                                    │    │
│  │  • Short-term: Stop immediate damage                            │    │
│  │  • Long-term: Prevent recurrence while investigating            │    │
│  │                                                                  │    │
│  │  ERADICATION                                                    │    │
│  │  • Remove threat artifacts                                      │    │
│  │  • Patch vulnerabilities exploited                              │    │
│  │  • Reset compromised credentials                                │    │
│  │                                                                  │    │
│  │  RECOVERY                                                       │    │
│  │  • Restore systems to normal operation                          │    │
│  │  • Validate system integrity                                    │    │
│  │  • Monitor for recurrence                                       │    │
│  └───────────────────────────────┬─────────────────────────────────┘    │
│                                  │                                       │
│                                  ▼                                       │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │            4. POST-INCIDENT ACTIVITY                            │    │
│  │  [YOUR INPUT - Learn and improve]                               │    │
│  │  • Incident timeline documentation                              │    │
│  │  • Root cause analysis                                          │    │
│  │  • Lessons learned meeting                                      │    │
│  │  • Improvement recommendations                                  │    │
│  │  • Update playbooks and procedures                              │    │
│  │  • Metrics and reporting                                        │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

# SECTION B: INCIDENT RESPONSE TEAM

## B.1 CSIRT Structure

| Role | Responsibilities | Primary | Backup |
|------|------------------|---------|--------|
| Incident Commander | [YOUR INPUT - Overall incident leadership, decisions, communication] | [YOUR INPUT - CISO] | [YOUR INPUT - Security Manager] |
| IR Lead | [YOUR INPUT - Technical leadership, coordinate responders, track actions] | [YOUR INPUT - SOC Manager] | [YOUR INPUT - Senior Analyst] |
| Security Analysts | [YOUR INPUT - Detection, analysis, containment actions] | [YOUR INPUT - SOC Team] | [YOUR INPUT - Rotational] |
| Forensic Investigator | [YOUR INPUT - Evidence collection, analysis, chain of custody] | [YOUR INPUT - Security Engineer] | [YOUR INPUT - MSSP] |
| IT Operations | [YOUR INPUT - System access, restoration, infrastructure changes] | [YOUR INPUT - IT Manager] | [YOUR INPUT - Senior SysAdmin] |
| Legal Counsel | [YOUR INPUT - Legal guidance, regulatory notification, law enforcement] | [YOUR INPUT - General Counsel] | [YOUR INPUT - Outside Counsel] |
| Communications | [YOUR INPUT - Internal/external communications, media] | [YOUR INPUT - PR Manager] | [YOUR INPUT - Corp Comm] |
| HR Representative | [YOUR INPUT - Employee matters, insider threats, terminations] | [YOUR INPUT - HR Manager] | [YOUR INPUT - HR Director] |
| Business Unit Liaison | [YOUR INPUT - Business impact assessment, process decisions] | [YOUR INPUT - Affected BU Manager] | [YOUR INPUT - VP Operations] |

## B.2 Contact Roster

```
[YOUR INPUT - Complete contact information]

INCIDENT RESPONSE CONTACT ROSTER
================================

INTERNAL CONTACTS

┌───────────────────────────────────────────────────────────────────────────┐
│ Role                  │ Name        │ Phone          │ Email              │
├───────────────────────┼─────────────┼────────────────┼────────────────────┤
│ CISO                  │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ Security Manager      │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ SOC Manager          │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ IT Director          │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ General Counsel      │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ PR/Communications    │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ CEO                  │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ CFO                  │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
└───────────────────────────────────────────────────────────────────────────┘

EXTERNAL CONTACTS

┌───────────────────────────────────────────────────────────────────────────┐
│ Entity                │ Contact     │ Phone          │ When to Engage     │
├───────────────────────┼─────────────┼────────────────┼────────────────────┤
│ IR Retainer (MSSP)   │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ Cyber Insurance      │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ Outside Legal Counsel│ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ Law Enforcement (FBI)│ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ Law Enforcement (FI) │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ DPA (Finland)        │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ CERT-FI              │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
│ Forensic Partner     │ [YOUR INPUT]│ [YOUR INPUT]   │ [YOUR INPUT]       │
└───────────────────────────────────────────────────────────────────────────┘

ON-CALL SCHEDULE
- Primary On-Call: [YOUR INPUT - Weekly rotation schedule]
- Escalation: [YOUR INPUT - If no response in 15 minutes, contact...]
- War Room: [YOUR INPUT - Physical and virtual locations]
```

## B.3 IR Authority Matrix

| Action | SOC Analyst | SOC Lead | Security Manager | CISO | CEO |
|--------|-------------|----------|------------------|------|-----|
| Isolate single endpoint | [YOUR INPUT - ✅] | ✅ | ✅ | ✅ | ✅ |
| Isolate server | [YOUR INPUT - ⬜] | ✅ | ✅ | ✅ | ✅ |
| Isolate network segment | [YOUR INPUT - ⬜] | ⬜ | ✅ | ✅ | ✅ |
| Disable user account | [YOUR INPUT - ⬜] | ✅ | ✅ | ✅ | ✅ |
| Block IP/domain at perimeter | [YOUR INPUT - ✅] | ✅ | ✅ | ✅ | ✅ |
| Shut down critical system | [YOUR INPUT - ⬜] | ⬜ | ⬜ | ✅ | ✅ |
| Engage external IR firm | [YOUR INPUT - ⬜] | ⬜ | ✅ | ✅ | ✅ |
| Notify law enforcement | [YOUR INPUT - ⬜] | ⬜ | ⬜ | ✅ | ✅ |
| Public communication | [YOUR INPUT - ⬜] | ⬜ | ⬜ | ⬜ | ✅ |
| Regulatory notification (GDPR) | [YOUR INPUT - ⬜] | ⬜ | ⬜ | ✅ | ✅ |
| Authorize ransom payment | [YOUR INPUT - ⬜] | ⬜ | ⬜ | ⬜ | ✅ (+ Board) |

---

# SECTION C: INCIDENT CLASSIFICATION

## C.1 Incident Categories

| Category | Definition | Examples |
|----------|------------|----------|
| Malware | [YOUR INPUT - Malicious software infection] | [YOUR INPUT - Virus, ransomware, trojan, cryptominer] |
| Unauthorized Access | [YOUR INPUT - Access without permission] | [YOUR INPUT - Compromised credentials, brute force, privilege escalation] |
| Denial of Service | [YOUR INPUT - Disruption of service availability] | [YOUR INPUT - DDoS, resource exhaustion] |
| Data Breach | [YOUR INPUT - Unauthorized data access/exfiltration] | [YOUR INPUT - Data theft, exposure, leakage] |
| Insider Threat | [YOUR INPUT - Malicious or negligent insider action] | [YOUR INPUT - Data theft by employee, sabotage] |
| Social Engineering | [YOUR INPUT - Human manipulation] | [YOUR INPUT - Phishing, BEC, pretexting] |
| Physical Security | [YOUR INPUT - Physical security breach] | [YOUR INPUT - Unauthorized building access, theft] |
| Web Attack | [YOUR INPUT - Web application attacks] | [YOUR INPUT - SQL injection, XSS, defacement] |
| Policy Violation | [YOUR INPUT - Violation of security policy] | [YOUR INPUT - Unauthorized software, data handling] |

## C.2 Severity Levels

| Severity | Impact | Examples | Response Time | Notification |
|----------|--------|----------|---------------|--------------|
| Critical (P1) | [YOUR INPUT - Business-threatening, widespread, high-value asset compromise] | [YOUR INPUT - Active ransomware, confirmed data breach, critical system compromise] | [YOUR INPUT - Immediate, 24/7] | [YOUR INPUT - CISO, CEO, Legal within 30 min] |
| High (P2) | [YOUR INPUT - Significant impact to operations or data risk] | [YOUR INPUT - Confirmed malware, single system compromise, credential theft] | [YOUR INPUT - 1 hour response] | [YOUR INPUT - Security Manager within 1 hour] |
| Medium (P3) | [YOUR INPUT - Limited impact, no confirmed compromise] | [YOUR INPUT - Suspicious activity, policy violation, phishing attempt] | [YOUR INPUT - 4 hours response] | [YOUR INPUT - SOC Manager] |
| Low (P4) | [YOUR INPUT - Minimal impact, informational] | [YOUR INPUT - Failed attacks, scan detection, minor policy issues] | [YOUR INPUT - Next business day] | [YOUR INPUT - Ticket tracking only] |

## C.3 Incident Declaration

```
[YOUR INPUT - Define when an incident is declared]

INCIDENT DECLARATION CRITERIA
=============================

AUTOMATIC DECLARATION (No judgment required):
- [YOUR INPUT - Confirmed ransomware execution]
- [YOUR INPUT - Confirmed data exfiltration]
- [YOUR INPUT - Confirmed unauthorized access to critical system]
- [YOUR INPUT - Multiple systems showing same malware]
- [YOUR INPUT - DDoS affecting production services]

ANALYST JUDGMENT (Escalate if uncertain):
- [YOUR INPUT - Suspicious activity that may indicate compromise]
- [YOUR INPUT - Single malware detection with unclear impact]
- [YOUR INPUT - Anomalous user behavior]

DECLARATION AUTHORITY:
- Any SOC Analyst can declare P3/P4 incidents
- SOC Lead or higher can declare P2 incidents
- Security Manager or CISO must declare P1 incidents

WHEN IN DOUBT: Escalate and declare. Better to over-declare 
and close than miss an active incident.
```

---

# SECTION D: INCIDENT RESPONSE PROCEDURES

## D.1 Initial Response Procedure

```
[YOUR INPUT - Complete initial response steps]

INITIAL INCIDENT RESPONSE CHECKLIST
===================================

When an incident is detected or reported, the responder should:

□ STEP 1: INITIAL ASSESSMENT (5 minutes)
  - [YOUR INPUT - Gather initial information]
  - What was detected/reported?
  - When did it occur?
  - What systems/users are affected?
  - Is it ongoing or historical?

□ STEP 2: CLASSIFY SEVERITY
  - [YOUR INPUT - Apply severity matrix]
  - Document initial classification
  - May be adjusted as more info available

□ STEP 3: CREATE INCIDENT RECORD
  - [YOUR INPUT - Open incident ticket]
  - Assign incident ID: INC-YYYY-NNNN
  - Include all known information
  - Start incident timeline

□ STEP 4: NOTIFY APPROPRIATE PARTIES
  - [YOUR INPUT - Based on severity, notify per escalation matrix]
  - P1: Immediate call to on-call + management chain
  - P2: Contact SOC Lead within 1 hour
  - P3/P4: Standard ticket routing

□ STEP 5: PRESERVE EVIDENCE
  - [YOUR INPUT - Before taking any action, consider evidence]
  - Take screenshots
  - Note volatile data that may be lost
  - Do not reboot unless absolutely necessary

□ STEP 6: INITIAL CONTAINMENT ASSESSMENT
  - [YOUR INPUT - Can immediate action prevent further damage?]
  - If yes and within authority, contain
  - If uncertain, escalate first

□ STEP 7: BEGIN DOCUMENTATION
  - [YOUR INPUT - Start detailed timeline]
  - Record all observations and actions
  - Use UTC timestamps
```

## D.2 Evidence Handling & Chain of Custody

```
[YOUR INPUT - Define evidence procedures]

EVIDENCE HANDLING PROCEDURES
============================

TYPES OF EVIDENCE:

1. VOLATILE EVIDENCE (Collected First - Lost when power off)
   - [YOUR INPUT - Running processes]
   - [YOUR INPUT - Network connections]
   - [YOUR INPUT - Logged-in users]
   - [YOUR INPUT - Memory contents (RAM)]
   - [YOUR INPUT - Clipboard contents]

2. NON-VOLATILE EVIDENCE
   - [YOUR INPUT - Hard drive contents]
   - [YOUR INPUT - Log files]
   - [YOUR INPUT - Configuration files]
   - [YOUR INPUT - User files]

EVIDENCE COLLECTION ORDER:
[YOUR INPUT - Order of volatility (RFC 3227)]
1. Registers, CPU cache
2. Memory (RAM)
3. Network state, routing tables
4. Running processes
5. Disk (file system)
6. Backups, archives

COLLECTION PROCEDURES:

Memory Acquisition:
- [YOUR INPUT - Use approved forensic tool (e.g., FTK Imager, Magnet RAM Capture)]
- [YOUR INPUT - Document system state before acquisition]
- [YOUR INPUT - Calculate hash of memory dump]

Disk Imaging:
- [YOUR INPUT - Use write blocker if possible]
- [YOUR INPUT - Create forensic image (bit-for-bit)]
- [YOUR INPUT - Calculate and record hash (SHA-256)]
- [YOUR INPUT - Verify hash after imaging]

Log Collection:
- [YOUR INPUT - Export logs to secure location]
- [YOUR INPUT - Include SIEM, EDR, system logs]
- [YOUR INPUT - Preserve original timestamps]

CHAIN OF CUSTODY:
Every piece of evidence must have documented:
- What: [YOUR INPUT - Description of evidence]
- When: [YOUR INPUT - Date/time collected]
- Who: [YOUR INPUT - Collector name and signature]
- Where: [YOUR INPUT - Location collected and stored]
- How: [YOUR INPUT - Method of collection]
- Hash: [YOUR INPUT - Cryptographic hash value]
```

### Chain of Custody Form

```
[YOUR INPUT - Complete chain of custody template]

CHAIN OF CUSTODY FORM
=====================

INCIDENT ID: [YOUR INPUT]
EVIDENCE ID: [YOUR INPUT - E-YYYY-NNNN]

EVIDENCE DESCRIPTION:
Item: [YOUR INPUT - e.g., "Memory dump from WKSTN-FIN-042"]
Type: [YOUR INPUT - Physical/Digital]
Collection Date: [YOUR INPUT]
Collection Location: [YOUR INPUT]
Collector: [YOUR INPUT - Name, Title]
Hash (SHA-256): [YOUR INPUT]

TRANSFER LOG:

| Date/Time | Released By | Received By | Purpose | Signature |
|-----------|------------|-------------|---------|-----------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| | | | | |
| | | | | |

STORAGE LOCATION:
Current Location: [YOUR INPUT]
Access Restrictions: [YOUR INPUT]

NOTES:
[YOUR INPUT]
```

## D.3 Communication Templates

### Internal Notification Template

```
[YOUR INPUT - Create internal notification template]

SECURITY INCIDENT NOTIFICATION
==============================

TO: [Distribution List]
FROM: Security Operations Center
DATE: [DATE TIME UTC]
SUBJECT: [SEVERITY] Security Incident - INC-YYYY-NNNN

INCIDENT SUMMARY
----------------
Incident ID: [INC-YYYY-NNNN]
Severity: [CRITICAL/HIGH/MEDIUM/LOW]
Status: [ACTIVE / CONTAINED / RESOLVED]
Time Detected: [DATE TIME UTC]

WHAT HAPPENED:
[YOUR INPUT - Brief, factual description]

IMPACT:
- Systems Affected: [YOUR INPUT]
- Users Affected: [YOUR INPUT]
- Data Affected: [YOUR INPUT]
- Business Impact: [YOUR INPUT]

CURRENT ACTIONS:
[YOUR INPUT - What is being done now]

REQUIRED ACTIONS FROM YOU:
[YOUR INPUT - What recipients need to do, if anything]

NEXT UPDATE:
Expected: [DATE TIME]

INCIDENT COMMANDER: [Name]
CONTACT: [Email/Phone for questions]

---
CONFIDENTIAL - Do not forward outside authorized recipients
```

### Executive Briefing Template

```
[YOUR INPUT - Create executive briefing template]

EXECUTIVE INCIDENT BRIEFING
===========================

INCIDENT: [INC-YYYY-NNNN]
BRIEFING #: [X]
DATE: [DATE TIME]

SITUATION OVERVIEW
------------------
[YOUR INPUT - 2-3 sentence summary for executives]

TIMELINE
--------
[YOUR INPUT - Key milestones only]
- [TIME]: Incident detected
- [TIME]: Containment initiated
- [TIME]: Current status

BUSINESS IMPACT
---------------
Financial: [YOUR INPUT - Known/estimated]
Operational: [YOUR INPUT - Systems/processes affected]
Reputational: [YOUR INPUT - Customer/public impact]
Regulatory: [YOUR INPUT - Notification requirements]

DECISIONS REQUIRED
------------------
[YOUR INPUT - List any decisions needed from leadership]

NEXT STEPS
----------
[YOUR INPUT - Immediate planned actions]

QUESTIONS?
Contact: [Incident Commander]
```

---

# SECTION E: INCIDENT PLAYBOOKS

## E.1 Playbook: Ransomware Response

```
[YOUR INPUT - Complete ransomware playbook]

PLAYBOOK: RANSOMWARE INCIDENT RESPONSE
======================================

PLAYBOOK ID: IR-PB-001
SEVERITY: CRITICAL (P1)
LAST UPDATED: [DATE]

INDICATORS:
- [YOUR INPUT - Ransom note files appearing]
- [YOUR INPUT - Mass file encryption (.encrypted, .locked extensions)]
- [YOUR INPUT - EDR detection of ransomware behavior]
- [YOUR INPUT - Users reporting inability to access files]

IMMEDIATE ACTIONS (First 15 minutes):
=====================================

□ 1. ISOLATE AFFECTED SYSTEMS
   - [YOUR INPUT - Network isolation via EDR]
   - [YOUR INPUT - Physically disconnect if EDR unavailable]
   - [YOUR INPUT - Do NOT power off (preserve memory)]
   
   CRITICAL: Speed is essential - ransomware spreads rapidly

□ 2. IDENTIFY SCOPE
   - [YOUR INPUT - How many systems showing indicators?]
   - [YOUR INPUT - Is encryption still active or complete?]
   - [YOUR INPUT - Which network segments affected?]

□ 3. PRESERVE RANSOM NOTE
   - [YOUR INPUT - Screenshot ransom demands]
   - [YOUR INPUT - Save ransom note file]
   - [YOUR INPUT - Note any IOCs (email, bitcoin address)]

□ 4. ACTIVATE INCIDENT RESPONSE TEAM
   - [YOUR INPUT - Notify per P1 escalation]
   - [YOUR INPUT - Stand up war room]
   - [YOUR INPUT - Consider engaging IR retainer]

CONTAINMENT (First 2 hours):
============================

□ 5. PREVENT FURTHER SPREAD
   - [YOUR INPUT - Identify patient zero]
   - [YOUR INPUT - Block lateral movement paths]
   - [YOUR INPUT - Disable compromised accounts]
   - [YOUR INPUT - Consider network segmentation]

□ 6. PROTECT BACKUPS
   - [YOUR INPUT - Verify backup systems not affected]
   - [YOUR INPUT - Isolate backup infrastructure]
   - [YOUR INPUT - Validate backup integrity]

□ 7. IDENTIFY RANSOMWARE VARIANT
   - [YOUR INPUT - Upload sample to ID Ransomware]
   - [YOUR INPUT - Check No More Ransom project]
   - [YOUR INPUT - Identify if decryptor available]

INVESTIGATION:
==============

□ 8. DETERMINE INITIAL ACCESS
   - [YOUR INPUT - How did ransomware enter?]
   - Common vectors:
     [YOUR INPUT - Phishing email]
     [YOUR INPUT - Exposed RDP]
     [YOUR INPUT - Exploited vulnerability]
     [YOUR INPUT - Supply chain compromise]

□ 9. ASSESS DATA EXFILTRATION
   - [YOUR INPUT - Many ransomware groups steal before encrypting]
   - [YOUR INPUT - Review network egress logs]
   - [YOUR INPUT - Check for data staging]

□ 10. TIMELINE RECONSTRUCTION
    - [YOUR INPUT - Build attack timeline]
    - [YOUR INPUT - Identify all affected systems]
    - [YOUR INPUT - Determine attacker dwell time]

RECOVERY DECISIONS:
===================

OPTION A: RESTORE FROM BACKUP
- [YOUR INPUT - Preferred option if backups viable]
- Verify backups are clean (pre-date compromise)
- Test restoration process
- Plan for extended recovery time

OPTION B: DECRYPTOR AVAILABLE
- [YOUR INPUT - Verify decryptor legitimacy]
- Test on non-critical system first
- May still need to address root cause

OPTION C: NEGOTIATE/PAY RANSOM*** 
- [YOUR INPUT - LAST RESORT ONLY]
- REQUIRES: Executive/Board approval
- CONSULT: Legal, law enforcement, insurance
- RISKS: No guarantee of decryption, funding criminals

***NordicShield Policy: [YOUR INPUT - Define company position on ransom]

NOTIFICATIONS:
==============
- [YOUR INPUT - Law enforcement if required/desired]
- [YOUR INPUT - Cyber insurance carrier]
- [YOUR INPUT - Regulatory bodies if data breach]
- [YOUR INPUT - Affected customers per policy]

POST-INCIDENT:
==============
- [YOUR INPUT - Complete eradication of threat]
- [YOUR INPUT - Implement additional controls]
- [YOUR INPUT - Full lessons learned review]
- [YOUR INPUT - Report to board]
```

## E.2 Playbook: Business Email Compromise (BEC)

```
[YOUR INPUT - Complete BEC playbook]

PLAYBOOK: BUSINESS EMAIL COMPROMISE RESPONSE
============================================

PLAYBOOK ID: IR-PB-002
SEVERITY: HIGH to CRITICAL
LAST UPDATED: [DATE]

INDICATORS:
- [YOUR INPUT - Request for wire transfer with urgency]
- [YOUR INPUT - Email from executive with unusual request]
- [YOUR INPUT - Vendor notification of banking change]
- [YOUR INPUT - Suspicious mailbox rules]
- [YOUR INPUT - Impossible travel or unusual sign-in]

IMMEDIATE ACTIONS:
==================

□ 1. STOP FINANCIAL TRANSACTIONS
   - [YOUR INPUT - If fraud in progress, contact bank IMMEDIATELY]
   - [YOUR INPUT - Request wire recall]
   - [YOUR INPUT - Notify finance to halt pending transfers]
   
   Time is critical: Wire recalls have limited windows

□ 2. SECURE COMPROMISED ACCOUNT
   - [YOUR INPUT - Revoke all sessions]
   - [YOUR INPUT - Reset password]
   - [YOUR INPUT - Reset MFA]
   - [YOUR INPUT - Block sign-in temporarily]

□ 3. PRESERVE EVIDENCE
   - [YOUR INPUT - Export mailbox before changes]
   - [YOUR INPUT - Export sign-in logs]
   - [YOUR INPUT - Screenshot suspicious emails/rules]

INVESTIGATION:
==============

□ 4. DETERMINE COMPROMISE SCOPE
   - [YOUR INPUT - When was account compromised?]
   - [YOUR INPUT - How was access gained?]
     - Phishing?
     - Password spray?
     - Token theft?
   - [YOUR INPUT - What data was accessed?]

□ 5. CHECK FOR MAILBOX RULES
   - [YOUR INPUT - Forwarding rules?]
   - [YOUR INPUT - Delete rules (hiding sent items)?]
   - [YOUR INPUT - Move rules?]

□ 6. IDENTIFY ALL COMMUNICATIONS
   - [YOUR INPUT - What emails did attacker send?]
   - [YOUR INPUT - Who received fraudulent requests?]
   - [YOUR INPUT - Any vendor/partner communications?]

□ 7. ASSESS LATERAL MOVEMENT
   - [YOUR INPUT - Did attacker access other accounts?]
   - [YOUR INPUT - OAuth application consent?]
   - [YOUR INPUT - eDiscovery or admin actions?]

CONTAINMENT:
============

□ 8. NEUTRALIZE ATTACKER ACCESS
   - [YOUR INPUT - Remove malicious mailbox rules]
   - [YOUR INPUT - Revoke OAuth consents]
   - [YOUR INPUT - Block attacker IPs (if identified)]

□ 9. NOTIFY AFFECTED PARTIES
   - [YOUR INPUT - Internal recipients of fake emails]
   - [YOUR INPUT - External partners/vendors contacted]
   - [YOUR INPUT - Warn about fraudulent communications]

FINANCIAL RECOVERY:
===================

□ 10. BANK NOTIFICATION
    - [YOUR INPUT - Contact bank fraud department]
    - [YOUR INPUT - Provide incident details]
    - [YOUR INPUT - File for wire recall]
    - Time limits:
      - [YOUR INPUT - Domestic wire: 24-48 hours]
      - [YOUR INPUT - International: Often too late after 24 hours]

□ 11. LAW ENFORCEMENT
    - [YOUR INPUT - File IC3 complaint (FBI)]
    - [YOUR INPUT - Local law enforcement report]
    - [YOUR INPUT - May be required for insurance claim]

□ 12. INSURANCE CLAIM
    - [YOUR INPUT - Notify cyber insurance of loss]
    - [YOUR INPUT - Provide required documentation]

POST-INCIDENT:
==============
- [YOUR INPUT - User security awareness reinforcement]
- [YOUR INPUT - Implement additional BEC controls]
- [YOUR INPUT - Financial process review (dual approval)]
- [YOUR INPUT - Invoice/banking change verification process]
```

## E.3 Playbook: Data Breach Response

```
[YOUR INPUT - Complete data breach playbook]

PLAYBOOK: DATA BREACH RESPONSE
==============================

PLAYBOOK ID: IR-PB-003
SEVERITY: CRITICAL (P1)
LAST UPDATED: [DATE]

INDICATORS:
- [YOUR INPUT - Unauthorized database access detected]
- [YOUR INPUT - Large data export/download]
- [YOUR INPUT - Data found on external site/dark web]
- [YOUR INPUT - Customer/employee data compromise reported]
- [YOUR INPUT - Ransomware with data exfiltration]

IMMEDIATE ACTIONS:
==================

□ 1. CONFIRM BREACH OCCURRED
   - [YOUR INPUT - Validate the detection]
   - [YOUR INPUT - Distinguish breach from attempted access]
   - [YOUR INPUT - Document initial findings]

□ 2. ACTIVATE BREACH RESPONSE TEAM
   - [YOUR INPUT - Core IR team]
   - [YOUR INPUT - Legal counsel (MANDATORY)]
   - [YOUR INPUT - Privacy/DPO]
   - [YOUR INPUT - Communications/PR]

□ 3. PRESERVE EVIDENCE
   - [YOUR INPUT - System logs, access logs, network traffic]
   - [YOUR INPUT - Follow chain of custody]

INVESTIGATION:
==============

□ 4. DETERMINE WHAT DATA WAS ACCESSED
   - [YOUR INPUT - Which systems/databases?]
   - [YOUR INPUT - What data elements?]
     - Personal data (names, addresses)?
     - Financial data (payment cards)?
     - Health data?
     - Credentials?
   - [YOUR INPUT - How many records?]

□ 5. IDENTIFY AFFECTED INDIVIDUALS
   - [YOUR INPUT - Employees, customers, partners?]
   - [YOUR INPUT - EU residents (GDPR)?]
   - [YOUR INPUT - Other jurisdictions?]

□ 6. DETERMINE DATA CLASSIFICATION
   - [YOUR INPUT - Public, Internal, Confidential, Restricted?]
   - [YOUR INPUT - Regulatory category (PII, PHI, PCI)?]

□ 7. ASSESS HARM POTENTIAL
   - [YOUR INPUT - Risk of identity theft?]
   - [YOUR INPUT - Financial harm?]
   - [YOUR INPUT - Physical safety concerns?]

REGULATORY NOTIFICATION ASSESSMENT:
===================================

GDPR (EU Data Subjects):
□ [YOUR INPUT - 72-hour notification to DPA if risk to rights/freedoms]
□ [YOUR INPUT - Individual notification if high risk]
□ [YOUR INPUT - Document reasoning if not notifying]

Other Regulations:
□ [YOUR INPUT - Check applicable state/country laws]
□ [YOUR INPUT - PCI-DSS if payment card data]
□ [YOUR INPUT - HIPAA if health data (US)]
□ [YOUR INPUT - Industry-specific requirements]

NOTIFICATION PREPARATION:
=========================

DPA NOTIFICATION (if required):
- What: [YOUR INPUT - Description of breach]
- When: [YOUR INPUT - Estimated timeline]
- Impact: [YOUR INPUT - Number and type of data subjects]
- Measures: [YOUR INPUT - Actions taken]
- Contact: [YOUR INPUT - DPO contact information]

INDIVIDUAL NOTIFICATION (if required):
- What happened: [YOUR INPUT - Clear, plain language]
- What data: [YOUR INPUT - Specific data types affected]
- What we're doing: [YOUR INPUT - Remediation steps]
- What you should do: [YOUR INPUT - Protective actions]
- How to contact us: [YOUR INPUT - Dedicated support line]

REMEDIATION:
============
- [YOUR INPUT - Close access vector]
- [YOUR INPUT - Reset affected credentials]
- [YOUR INPUT - Offer credit monitoring if appropriate]
- [YOUR INPUT - Implement additional controls]
```

## E.4 Playbook: Insider Threat Response

```
[YOUR INPUT - Complete insider threat playbook]

PLAYBOOK: INSIDER THREAT RESPONSE
=================================

PLAYBOOK ID: IR-PB-004
SEVERITY: VARIES
LAST UPDATED: [DATE]

INDICATORS:
- [YOUR INPUT - Unusual data access patterns]
- [YOUR INPUT - Large downloads before resignation]
- [YOUR INPUT - After-hours access to sensitive systems]
- [YOUR INPUT - DLP alerts on sensitive data movement]
- [YOUR INPUT - Report from colleague of suspicious behavior]

CRITICAL CONSIDERATIONS:
========================
⚠️ INVOLVE HR AND LEGAL FROM THE START
⚠️ MAINTAIN CONFIDENTIALITY - Need to know only
⚠️ DO NOT TIP OFF THE SUBJECT
⚠️ DOCUMENT EVERYTHING

INVESTIGATION PHASE:
====================

□ 1. CONFIRM SUSPICIOUS ACTIVITY
   - [YOUR INPUT - Review alerts/reports objectively]
   - [YOUR INPUT - Could there be an innocent explanation?]
   - [YOUR INPUT - Document initial concerns]

□ 2. FORM INVESTIGATION TEAM
   - [YOUR INPUT - Security lead]
   - [YOUR INPUT - HR representative]
   - [YOUR INPUT - Legal counsel]
   - [YOUR INPUT - Direct chain ONLY if necessary]

□ 3. COVERT MONITORING (if approved)
   - [YOUR INPUT - Enhanced logging]
   - [YOUR INPUT - DLP policy tightening]
   - [YOUR INPUT - Network traffic analysis]
   - NOTE: Must be within legal/policy bounds

□ 4. DATA ACCESS ANALYSIS
   - [YOUR INPUT - What has the individual accessed?]
   - [YOUR INPUT - Compared to normal job function?]
   - [YOUR INPUT - Any data exfiltration indicators?]

□ 5. BUILD TIMELINE
   - [YOUR INPUT - When did suspicious activity start?]
   - [YOUR INPUT - Correlate with any events (resignation, review, etc.)?]

RESPONSE OPTIONS:
=================

OPTION A: INSUFFICIENT EVIDENCE
- [YOUR INPUT - Close investigation]
- [YOUR INPUT - Continue normal monitoring]
- [YOUR INPUT - Document findings]

OPTION B: POLICY VIOLATION (Non-Malicious)
- [YOUR INPUT - HR-led counseling/warning]
- [YOUR INPUT - Additional training]
- [YOUR INPUT - Enhanced monitoring period]

OPTION C: CONFIRMED MALICIOUS ACTIVITY
- [YOUR INPUT - Coordinate with HR for termination]
- [YOUR INPUT - Preserve all evidence]
- [YOUR INPUT - Plan access revocation timing]
- [YOUR INPUT - Consider law enforcement]

TERMINATION PROCEDURE (if applicable):
=====================================
- [YOUR INPUT - Coordinate timing with HR]
- [YOUR INPUT - Prepare access revocation (DO NOT execute early)]
- [YOUR INPUT - Execute access removal simultaneously with notification]
- [YOUR INPUT - Collect company property]
- [YOUR INPUT - Forensic preservation of systems]
- [YOUR INPUT - Monitor for post-departure activity]
```

---

# SECTION F: POST-INCIDENT ACTIVITIES

## F.1 Lessons Learned Process

```
[YOUR INPUT - Define lessons learned process]

POST-INCIDENT REVIEW PROCESS
============================

TIMING:
- Initial debrief: [YOUR INPUT - Within 24 hours of resolution]
- Full lessons learned: [YOUR INPUT - Within 2 weeks]
- Follow-up on actions: [YOUR INPUT - Monthly until closed]

PARTICIPANTS:
- [YOUR INPUT - All incident responders]
- [YOUR INPUT - Affected business units]
- [YOUR INPUT - IT operations]
- [YOUR INPUT - Management as appropriate]

AGENDA:

1. INCIDENT TIMELINE REVIEW
   [YOUR INPUT - Walk through what happened chronologically]

2. WHAT WORKED WELL
   [YOUR INPUT - Identify effective responses to repeat]

3. WHAT COULD BE IMPROVED
   [YOUR INPUT - Gaps, delays, challenges]

4. ROOT CAUSE ANALYSIS
   [YOUR INPUT - Why did this happen? What enabled the attack?]

5. IMPROVEMENT RECOMMENDATIONS
   [YOUR INPUT - Specific, actionable items with owners]

6. FOLLOW-UP TRACKING
   [YOUR INPUT - Assign tickets, due dates, accountability]

KEY QUESTIONS TO ASK:
- [YOUR INPUT - How was the incident detected?]
- [YOUR INPUT - Could we have detected it earlier?]
- [YOUR INPUT - Was our response timely?]
- [YOUR INPUT - Did we have the right tools?]
- [YOUR INPUT - Did our playbooks work?]
- [YOUR INPUT - What would we do differently?]
```

## F.2 Lessons Learned Report Template

```
[YOUR INPUT - Complete lessons learned template]

INCIDENT LESSONS LEARNED REPORT
===============================

INCIDENT ID: [INC-YYYY-NNNN]
INCIDENT TYPE: [YOUR INPUT]
DATE RANGE: [YOUR INPUT - Detection to closure]
REPORT DATE: [DATE]
AUTHOR: [YOUR NAME]

EXECUTIVE SUMMARY
-----------------
[YOUR INPUT - 3-5 sentence summary of incident and key takeaways]

INCIDENT OVERVIEW
-----------------
Detection: [YOUR INPUT - How was incident detected?]
Classification: [YOUR INPUT - Type and severity]
Scope: [YOUR INPUT - Systems, users, data affected]
Duration: [YOUR INPUT - Time from detection to containment to resolution]
Business Impact: [YOUR INPUT - Downtime, financial, reputational]

TIMELINE
--------
[YOUR INPUT - Key events with timestamps]
| Time (UTC) | Event |
|------------|-------|
| | |

ROOT CAUSE ANALYSIS
-------------------
Primary Cause: [YOUR INPUT]
Contributing Factors:
- [YOUR INPUT]
- [YOUR INPUT]

Could This Have Been Prevented?: [YOUR INPUT]
Could This Have Been Detected Earlier?: [YOUR INPUT]

RESPONSE EVALUATION
-------------------
What Worked Well:
1. [YOUR INPUT]
2. [YOUR INPUT]

What Needs Improvement:
1. [YOUR INPUT]
2. [YOUR INPUT]

IMPROVEMENT RECOMMENDATIONS
---------------------------
| # | Recommendation | Priority | Owner | Due Date |
|---|----------------|----------|-------|----------|
| 1 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 2 | | | | |
| 3 | | | | |

METRICS
-------
- Time to detect: [YOUR INPUT]
- Time to contain: [YOUR INPUT]
- Time to resolve: [YOUR INPUT]
- [Compare to targets/previous incidents]

APPENDICES
----------
A. Detailed timeline
B. Evidence inventory
C. Communication log
```

---

# SECTION G: FORENSICS FUNDAMENTALS

## G.1 Digital Forensics Process

```
[YOUR INPUT - Outline forensic process]

DIGITAL FORENSICS PROCESS
=========================

┌─────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│  1. IDENTIFICATION                                                       │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ [YOUR INPUT - Identify sources of potential evidence]            │   │
│  │ • What systems are involved?                                     │   │
│  │ • What data sources exist?                                       │   │
│  │ • What is the scope of collection needed?                        │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                 │                                        │
│                                 ▼                                        │
│  2. COLLECTION                                                           │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ [YOUR INPUT - Acquire evidence following proper procedures]      │   │
│  │ • Follow order of volatility                                     │   │
│  │ • Use forensically sound methods                                 │   │
│  │ • Document everything                                            │   │
│  │ • Maintain chain of custody                                      │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                 │                                        │
│                                 ▼                                        │
│  3. EXAMINATION                                                          │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ [YOUR INPUT - Process and examine collected data]                │   │
│  │ • Work on forensic copies only                                   │   │
│  │ • Extract relevant data                                          │   │
│  │ • Recover deleted data if possible                               │   │
│  │ • Correlate data from multiple sources                           │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                 │                                        │
│                                 ▼                                        │
│  4. ANALYSIS                                                             │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ [YOUR INPUT - Interpret findings to answer questions]            │   │
│  │ • Build timeline of events                                       │   │
│  │ • Identify attacker tools, techniques, procedures                │   │
│  │ • Determine scope and impact                                     │   │
│  │ • Draw conclusions based on evidence                             │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                 │                                        │
│                                 ▼                                        │
│  5. REPORTING                                                            │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ [YOUR INPUT - Document findings and conclusions]                 │   │
│  │ • Detailed technical report                                      │   │
│  │ • Executive summary                                              │   │
│  │ • Evidence appendices                                            │   │
│  │ • Testify if needed (legal proceedings)                          │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

## G.2 Forensic Artifacts by OS

| Artifact | Windows | Linux | Value |
|----------|---------|-------|-------|
| Process List | [YOUR INPUT - tasklist, Get-Process] | [YOUR INPUT - ps aux, /proc] | [YOUR INPUT - Running malware, suspicious processes] |
| Network Connections | [YOUR INPUT - netstat, Get-NetTCPConnection] | [YOUR INPUT - netstat, ss, /proc/net] | [YOUR INPUT - C2 connections, lateral movement] |
| Login History | [YOUR INPUT - Event logs 4624/4625] | [YOUR INPUT - /var/log/auth.log, wtmp, lastlog] | [YOUR INPUT - User activity, unauthorized access] |
| Command History | [YOUR INPUT - PowerShell history, CMD history] | [YOUR INPUT - .bash_history, .zsh_history] | [YOUR INPUT - Attacker commands] |
| Scheduled Tasks | [YOUR INPUT - Task Scheduler, at jobs] | [YOUR INPUT - cron, at, systemd timers] | [YOUR INPUT - Persistence mechanisms] |
| Startup Programs | [YOUR INPUT - Registry Run keys, Startup folder] | [YOUR INPUT - rc.local, init.d, systemd] | [YOUR INPUT - Persistence] |
| Installed Software | [YOUR INPUT - Programs and Features, WMI] | [YOUR INPUT - dpkg, rpm, /opt] | [YOUR INPUT - Malicious software] |
| User Accounts | [YOUR INPUT - SAM, AD users] | [YOUR INPUT - /etc/passwd, /etc/shadow] | [YOUR INPUT - Rogue accounts] |
| Registry | [YOUR INPUT - Registry hives (SYSTEM, SOFTWARE, NTUSER)] | [YOUR INPUT - N/A] | [YOUR INPUT - Configuration, persistence, artifacts] |
| Prefetch/Amcache | [YOUR INPUT - C:\Windows\Prefetch, Amcache.hve] | [YOUR INPUT - N/A] | [YOUR INPUT - Program execution evidence] |
| Browser History | [YOUR INPUT - Chrome, Edge, Firefox data] | [YOUR INPUT - Same browsers in ~/.config] | [YOUR INPUT - User activity, phishing clicks] |

## G.3 Log Sources for Investigation

| Log Source | Location / Method | Key Events |
|------------|------------------|------------|
| Windows Security Log | [YOUR INPUT - Event Viewer, SIEM] | [YOUR INPUT - Logons (4624), Failures (4625), Privilege use, Account changes] |
| Windows System Log | [YOUR INPUT - Event Viewer] | [YOUR INPUT - Service starts/stops, Driver loading, Shutdown] |
| Windows PowerShell | [YOUR INPUT - Microsoft-Windows-PowerShell/Operational] | [YOUR INPUT - Script execution, Commands run] |
| Windows Sysmon | [YOUR INPUT - Microsoft-Windows-Sysmon/Operational] | [YOUR INPUT - Process create, Network connect, File create] |
| Linux Auth Log | [YOUR INPUT - /var/log/auth.log or /var/log/secure] | [YOUR INPUT - SSH logins, sudo usage, authentication] |
| Linux Syslog | [YOUR INPUT - /var/log/syslog or /var/log/messages] | [YOUR INPUT - System events, service status] |
| Firewall Logs | [YOUR INPUT - Firewall management or SIEM] | [YOUR INPUT - Allowed/denied connections, attacks] |
| Proxy Logs | [YOUR INPUT - Proxy management or SIEM] | [YOUR INPUT - Web access, malware downloads, C2] |
| DNS Logs | [YOUR INPUT - DNS server or EDR] | [YOUR INPUT - Domain lookups, C2 communication] |
| Email Logs | [YOUR INPUT - Mail gateway, Exchange/O365] | [YOUR INPUT - Phishing delivery, exfiltration attempts] |
| Cloud Audit Logs | [YOUR INPUT - AWS CloudTrail, Azure Activity, GCP Audit] | [YOUR INPUT - API calls, configuration changes, access] |

---

# SECTION H: IR SCENARIOS

## H.1 Scenario: After-Hours Critical Incident

```
[YOUR INPUT - Complete scenario]

SCENARIO: RANSOMWARE DETECTED AT 2 AM
=====================================

SITUATION:
It's Saturday at 2:15 AM. You're the on-call SOC analyst. 
An EDR alert fires: "Ransomware behavior detected" on 
SRV-FILE-001 (main file server). The automated containment 
attempt shows "Failed - Network isolation error."

ANALYSIS TASKS:

1. IMMEDIATE ASSESSMENT (5 minutes):
   [YOUR INPUT - What do you need to determine immediately?]
   - Is encryption actively occurring?
   - How widespread is the infection?
   - Why did automated containment fail?

2. MANUAL CONTAINMENT:
   [YOUR INPUT - Automated failed, what do you do?]
   - Network switch isolation?
   - Physical disconnect?
   - Other affected systems?

3. ESCALATION DECISION:
   [YOUR INPUT - Who do you call at 2 AM and why?]
   - SOC Lead?
   - CISO?
   - IT Operations?

4. INITIAL RESPONSE ACTIONS:
   [YOUR INPUT - What do you do until help arrives?]
   - Evidence preservation
   - Scope determination
   - Documentation

5. COMMUNICATION:
   [YOUR INPUT - What do you communicate and to whom?]
```

## H.2 Scenario: Suspected Insider Data Theft

```
[YOUR INPUT - Complete scenario]

SCENARIO: DEPARTING EMPLOYEE DATA EXFILTRATION
=============================================

SITUATION:
HR informs you that a senior engineer, Mikko, resigned 
yesterday and his last day is in two weeks. Today, DLP 
alerts show Mikko downloaded 500 engineering documents 
to a USB drive and emailed 50 files to his personal 
email over the past 3 days.

ANALYSIS TASKS:

1. INITIAL RESPONSE:
   [YOUR INPUT - What do you do immediately?]
   - Alert HR? When?
   - Stop the exfiltration?
   - Tip off Mikko or not?

2. INVESTIGATION SCOPE:
   [YOUR INPUT - What do you need to find out?]
   - What data was taken?
   - Is this normal for his role?
   - Any policy violations?

3. LEGAL CONSIDERATIONS:
   [YOUR INPUT - What legal issues must you consider?]
   - Employee privacy
   - Evidence preservation
   - Potential prosecution

4. RESPONSE OPTIONS:
   [YOUR INPUT - What are your options?]
   - Immediate termination?
   - Continue monitoring?
   - Confront Mikko?

5. EVIDENCE HANDLING:
   [YOUR INPUT - How do you preserve evidence?]
   - Email exports
   - USB logs
   - Access logs
```

---

# SECTION I: METRICS & REPORTING

## I.1 IR KPIs

| Metric | Definition | Target | Current |
|--------|------------|--------|---------|
| Mean Time to Detect (MTTD) | [YOUR INPUT - Alert to confirmed incident] | [YOUR INPUT - <4 hours] | [YOUR INPUT] |
| Mean Time to Respond (MTTR) | [YOUR INPUT - Detection to containment] | [YOUR INPUT - <1 hour] | [YOUR INPUT] |
| Mean Time to Recover (MTTRec) | [YOUR INPUT - Containment to normal ops] | [YOUR INPUT - <24 hours] | [YOUR INPUT] |
| Incident Volume | [YOUR INPUT - Total incidents per period] | [YOUR INPUT - Trend tracking] | [YOUR INPUT] |
| Severity Distribution | [YOUR INPUT - % by severity level] | [YOUR INPUT - <5% P1, <15% P2] | [YOUR INPUT] |
| Recurrence Rate | [YOUR INPUT - Same root cause incidents] | [YOUR INPUT - <10%] | [YOUR INPUT] |
| False Positive Rate | [YOUR INPUT - Declared incidents that weren't] | [YOUR INPUT - <15%] | [YOUR INPUT] |
| Lessons Learned Completion | [YOUR INPUT - % of incidents with LL completed] | [YOUR INPUT - 100% for P1/P2] | [YOUR INPUT] |
| Improvement Implementation | [YOUR INPUT - % of LL actions completed] | [YOUR INPUT - >90%] | [YOUR INPUT] |

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 4.7 - Incident Response Plan & Playbooks |
| **Phase** | 4 - Security Operations |
| **Exam Objectives** | 4.8 - Incident response, 4.9 - Digital forensics |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
