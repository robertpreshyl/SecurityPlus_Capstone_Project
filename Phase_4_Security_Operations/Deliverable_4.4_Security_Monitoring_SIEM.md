# Deliverable 4.4: Security Monitoring & SIEM Operations
## NordicShield Technologies Oy

---

```
╔══════════════════════════════════════════════════════════════════╗
║          SECURITY MONITORING & SIEM OPERATIONS                    ║
║                                                                    ║
║  Document ID: SIEM-NS-2026-001                                    ║
║  Version: 1.0                                                     ║
║  Author: [YOUR NAME]                                              ║
║  Classification: Confidential                                     ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Document Purpose

This document establishes NordicShield's security monitoring strategy and SIEM operations, defining log collection, correlation rules, alerting procedures, and SOC workflows. Effective monitoring is the foundation of detecting and responding to security threats.

---

## Instructions

1. Design the monitoring architecture and log sources
2. Create detection use cases and correlation rules
3. Define alerting and triage procedures
4. Complete all `[YOUR INPUT]` sections
5. Consider 24/7 coverage requirements for NordicShield SOC

---

# SECTION A: MONITORING STRATEGY

## A.1 Monitoring Objectives

```
[YOUR INPUT - Define monitoring objectives]

NORDICSHIELD SECURITY MONITORING OBJECTIVES
==========================================

1. DETECT: [YOUR INPUT - Identify security threats and anomalies]
   - Known attack patterns (signature-based)
   - Behavioral anomalies (analytics)
   - Policy violations

2. RESPOND: [YOUR INPUT - Enable rapid incident response]
   - Alert SOC analysts
   - Provide context for investigation
   - Support forensic analysis

3. COMPLY: [YOUR INPUT - Meet regulatory monitoring requirements]
   - GDPR access logging
   - Audit trail requirements
   - Evidence preservation

4. IMPROVE: [YOUR INPUT - Continuous security improvement]
   - Trend analysis
   - Attack surface visibility
   - Security posture metrics
```

## A.2 Monitoring Architecture

```
[YOUR INPUT - Design the monitoring architecture]

┌─────────────────────────────────────────────────────────────────────────┐
│               NORDICSHIELD SECURITY MONITORING ARCHITECTURE              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  DATA SOURCES              COLLECTION             PROCESSING             │
│  ═══════════════════════════════════════════════════════════════════    │
│                                                                          │
│  ┌──────────────┐         ┌──────────────┐       ┌──────────────────┐   │
│  │ Firewalls    │────────►│              │       │                  │   │
│  │ IDS/IPS      │         │    LOG       │       │                  │   │
│  │ WAF          │         │  COLLECTORS  │       │       SIEM       │   │
│  └──────────────┘         │              │       │                  │   │
│  ┌──────────────┐         │  [YOUR INPUT │──────►│  [YOUR INPUT -   │   │
│  │ Servers      │────────►│   - Syslog   │       │   Splunk/        │   │
│  │ Windows/Linux│         │   - Agents   │       │   Sentinel]      │   │
│  │ Containers   │         │   - APIs]    │       │                  │   │
│  └──────────────┘         │              │       │  • Parsing       │   │
│  ┌──────────────┐         └──────────────┘       │  • Normalization │   │
│  │ Endpoints    │                │               │  • Correlation   │   │
│  │ EDR          │────────────────┘               │  • Alerting      │   │
│  │ AV           │                                │                  │   │
│  └──────────────┘                                └────────┬─────────┘   │
│  ┌──────────────┐                                         │             │
│  │ Cloud        │                                         │             │
│  │ AWS/Azure    │─────────────────────────────────────────┘             │
│  │ GCP          │                                         │             │
│  └──────────────┘                                         │             │
│  ┌──────────────┐                                         ▼             │
│  │ Identity     │                                ┌──────────────────┐   │
│  │ AD/Azure AD  │────────────────────────────────│     SOC          │   │
│  │ RADIUS       │                                │  OPERATIONS      │   │
│  └──────────────┘                                │                  │   │
│  ┌──────────────┐                                │  • Alert Triage  │   │
│  │ Network      │                                │  • Investigation │   │
│  │ Flows/PCAP   │────────────────────────────────│  • Response      │   │
│  │ DNS          │                                │  • Hunting       │   │
│  └──────────────┘                                └──────────────────┘   │
│  ┌──────────────┐                                                       │
│  │ Applications │                                                       │
│  │ Custom apps  │────────────────────────────────────────────────────   │
│  │ SaaS         │                                                       │
│  └──────────────┘                                                       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

## A.3 SIEM Platform Selection

| Criteria | Weight | Option 1: [YOUR INPUT - Splunk] | Option 2: [YOUR INPUT - Microsoft Sentinel] | Option 3: [YOUR INPUT - Elastic] |
|----------|--------|--------------------------------|---------------------------------------------|----------------------------------|
| Log Volume Handling | [YOUR INPUT - 20%] | [YOUR INPUT - Score 1-5] | [YOUR INPUT] | [YOUR INPUT] |
| Cloud Integration | [YOUR INPUT - 15%] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Correlation Capabilities | [YOUR INPUT - 20%] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Threat Intelligence | [YOUR INPUT - 10%] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| SOAR Integration | [YOUR INPUT - 10%] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Ease of Use | [YOUR INPUT - 10%] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Total Cost | [YOUR INPUT - 15%] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Total Score** | 100% | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Recommendation** | | [YOUR INPUT - Explain choice] | | |

---

# SECTION B: LOG SOURCES & COLLECTION

## B.1 Critical Log Sources

### Network Infrastructure Logs

| Source | Log Type | Collection Method | Retention | Priority |
|--------|----------|-------------------|-----------|----------|
| Firewall (Palo Alto) | [YOUR INPUT - Traffic, threat, URL filtering] | [YOUR INPUT - Syslog CEF] | [YOUR INPUT - 90 days hot, 1 year cold] | [YOUR INPUT - Critical] |
| IDS/IPS (Suricata) | [YOUR INPUT - Alerts, flow records] | [YOUR INPUT - Syslog] | [YOUR INPUT - 90 days] | [YOUR INPUT - Critical] |
| Web Proxy | [YOUR INPUT - Access logs, blocks] | [YOUR INPUT - Syslog/API] | [YOUR INPUT - 90 days] | [YOUR INPUT - High] |
| DNS Server | [YOUR INPUT - Query logs] | [YOUR INPUT - Syslog/File] | [YOUR INPUT - 30 days] | [YOUR INPUT - High] |
| DHCP Server | [YOUR INPUT - Lease logs] | [YOUR INPUT - Syslog] | [YOUR INPUT - 90 days] | [YOUR INPUT - Medium] |
| VPN Gateway | [YOUR INPUT - Connection logs] | [YOUR INPUT - Syslog] | [YOUR INPUT - 1 year] | [YOUR INPUT - Critical] |
| Network Switches | [YOUR INPUT - Auth, port status] | [YOUR INPUT - Syslog] | [YOUR INPUT - 30 days] | [YOUR INPUT - Medium] |
| Wireless Controller | [YOUR INPUT - Client connections, rogue AP] | [YOUR INPUT - Syslog/API] | [YOUR INPUT - 90 days] | [YOUR INPUT - High] |
| Load Balancer | [YOUR INPUT - Access logs] | [YOUR INPUT - Syslog] | [YOUR INPUT - 30 days] | [YOUR INPUT - Medium] |

### Server & Endpoint Logs

| Source | Log Type | Collection Method | Retention | Priority |
|--------|----------|-------------------|-----------|----------|
| Windows Servers | [YOUR INPUT - Security, System, Application, PowerShell] | [YOUR INPUT - WEF/Agent] | [YOUR INPUT - 90 days] | [YOUR INPUT - Critical] |
| Linux Servers | [YOUR INPUT - Auth, syslog, audit] | [YOUR INPUT - rsyslog/Agent] | [YOUR INPUT - 90 days] | [YOUR INPUT - Critical] |
| Active Directory | [YOUR INPUT - Security events, replication] | [YOUR INPUT - WEF] | [YOUR INPUT - 1 year] | [YOUR INPUT - Critical] |
| DNS Server (AD) | [YOUR INPUT - Analytic, Zone changes] | [YOUR INPUT - WEF] | [YOUR INPUT - 90 days] | [YOUR INPUT - High] |
| Certificate Authority | [YOUR INPUT - Issuance, revocation] | [YOUR INPUT - WEF] | [YOUR INPUT - 7 years] | [YOUR INPUT - High] |
| Windows Workstations | [YOUR INPUT - Security, Defender, AppLocker] | [YOUR INPUT - Agent] | [YOUR INPUT - 30 days] | [YOUR INPUT - High] |
| EDR (CrowdStrike) | [YOUR INPUT - Detections, telemetry] | [YOUR INPUT - API] | [YOUR INPUT - 90 days in SIEM] | [YOUR INPUT - Critical] |
| Antivirus | [YOUR INPUT - Detections, updates] | [YOUR INPUT - Syslog/API] | [YOUR INPUT - 90 days] | [YOUR INPUT - High] |

### Cloud Logs

| Source | Log Type | Collection Method | Retention | Priority |
|--------|----------|-------------------|-----------|----------|
| AWS CloudTrail | [YOUR INPUT - API activity] | [YOUR INPUT - S3 + EventBridge] | [YOUR INPUT - 1 year] | [YOUR INPUT - Critical] |
| AWS VPC Flow Logs | [YOUR INPUT - Network flow] | [YOUR INPUT - CloudWatch/S3] | [YOUR INPUT - 90 days] | [YOUR INPUT - High] |
| AWS GuardDuty | [YOUR INPUT - Threat findings] | [YOUR INPUT - EventBridge] | [YOUR INPUT - 90 days] | [YOUR INPUT - Critical] |
| Azure Activity Log | [YOUR INPUT - Subscription activity] | [YOUR INPUT - Diagnostic Settings] | [YOUR INPUT - 1 year] | [YOUR INPUT - Critical] |
| Azure AD Sign-in Logs | [YOUR INPUT - Authentication events] | [YOUR INPUT - Diagnostic Settings] | [YOUR INPUT - 1 year] | [YOUR INPUT - Critical] |
| Azure AD Audit Logs | [YOUR INPUT - Directory changes] | [YOUR INPUT - Diagnostic Settings] | [YOUR INPUT - 1 year] | [YOUR INPUT - Critical] |
| Microsoft 365 | [YOUR INPUT - Audit, DLP, mail flow] | [YOUR INPUT - Office Management API] | [YOUR INPUT - 1 year] | [YOUR INPUT - High] |
| Azure Defender | [YOUR INPUT - Security alerts] | [YOUR INPUT - API/Sentinel native] | [YOUR INPUT - 90 days] | [YOUR INPUT - Critical] |

### Application Logs

| Source | Log Type | Collection Method | Retention | Priority |
|--------|----------|-------------------|-----------|----------|
| Web Applications | [YOUR INPUT - Access, error, security events] | [YOUR INPUT - Agent/File shipping] | [YOUR INPUT - 90 days] | [YOUR INPUT - High] |
| Database (SQL, Postgres) | [YOUR INPUT - Connections, queries, errors] | [YOUR INPUT - Native logging] | [YOUR INPUT - 90 days] | [YOUR INPUT - High] |
| Email Gateway | [YOUR INPUT - Mail flow, spam, threats] | [YOUR INPUT - Syslog/API] | [YOUR INPUT - 90 days] | [YOUR INPUT - High] |
| DLP | [YOUR INPUT - Policy violations] | [YOUR INPUT - API] | [YOUR INPUT - 1 year] | [YOUR INPUT - High] |
| PAM Solution | [YOUR INPUT - Privileged session, password checkouts] | [YOUR INPUT - API] | [YOUR INPUT - 1 year] | [YOUR INPUT - Critical] |
| Custom Applications | [YOUR INPUT - Business-specific security events] | [YOUR INPUT - Agent/API] | [YOUR INPUT - Per app requirement] | [YOUR INPUT - Varies] |

### Identity & Access Logs

| Source | Log Type | Collection Method | Retention | Priority |
|--------|----------|-------------------|-----------|----------|
| Azure AD | [YOUR INPUT - Sign-ins, provisioning, risk events] | [YOUR INPUT - Graph API/Diagnostic] | [YOUR INPUT - 1 year] | [YOUR INPUT - Critical] |
| On-prem AD | [YOUR INPUT - Logon, account management, GPO] | [YOUR INPUT - WEF] | [YOUR INPUT - 1 year] | [YOUR INPUT - Critical] |
| RADIUS/NPS | [YOUR INPUT - Network authentication] | [YOUR INPUT - WEF/Syslog] | [YOUR INPUT - 1 year] | [YOUR INPUT - High] |
| SSO (Okta/Ping) | [YOUR INPUT - Auth, MFA, provisioning] | [YOUR INPUT - API] | [YOUR INPUT - 1 year] | [YOUR INPUT - Critical] |
| MFA Provider | [YOUR INPUT - Challenge, success, failure] | [YOUR INPUT - API] | [YOUR INPUT - 1 year] | [YOUR INPUT - Critical] |
| VPN | [YOUR INPUT - Connection, disconnection, failures] | [YOUR INPUT - Syslog] | [YOUR INPUT - 1 year] | [YOUR INPUT - Critical] |

## B.2 Windows Event IDs to Collect

| Event ID | Description | Category | Priority |
|----------|-------------|----------|----------|
| 4624 | [YOUR INPUT - Successful logon] | [YOUR INPUT - Logon] | [YOUR INPUT - High] |
| 4625 | [YOUR INPUT - Failed logon] | [YOUR INPUT - Logon] | [YOUR INPUT - Critical] |
| 4648 | [YOUR INPUT - Explicit credential logon] | [YOUR INPUT - Logon] | [YOUR INPUT - High] |
| 4672 | [YOUR INPUT - Special privileges assigned] | [YOUR INPUT - Privilege] | [YOUR INPUT - High] |
| 4688 | [YOUR INPUT - Process creation] | [YOUR INPUT - Process] | [YOUR INPUT - Critical] |
| 4689 | [YOUR INPUT - Process termination] | [YOUR INPUT - Process] | [YOUR INPUT - Medium] |
| 4698 | [YOUR INPUT - Scheduled task created] | [YOUR INPUT - Persistence] | [YOUR INPUT - Critical] |
| 4720 | [YOUR INPUT - User account created] | [YOUR INPUT - Account Management] | [YOUR INPUT - Critical] |
| 4722 | [YOUR INPUT - User account enabled] | [YOUR INPUT - Account Management] | [YOUR INPUT - High] |
| 4724 | [YOUR INPUT - Password reset attempt] | [YOUR INPUT - Account Management] | [YOUR INPUT - High] |
| 4728 | [YOUR INPUT - Member added to security group] | [YOUR INPUT - Group Management] | [YOUR INPUT - Critical] |
| 4732 | [YOUR INPUT - Member added to local group] | [YOUR INPUT - Group Management] | [YOUR INPUT - High] |
| 4768 | [YOUR INPUT - Kerberos TGT requested] | [YOUR INPUT - Kerberos] | [YOUR INPUT - Medium] |
| 4769 | [YOUR INPUT - Kerberos service ticket requested] | [YOUR INPUT - Kerberos] | [YOUR INPUT - Medium] |
| 4771 | [YOUR INPUT - Kerberos pre-auth failed] | [YOUR INPUT - Kerberos] | [YOUR INPUT - High] |
| 4776 | [YOUR INPUT - NTLM authentication] | [YOUR INPUT - NTLM] | [YOUR INPUT - High] |
| 4946 | [YOUR INPUT - Firewall rule added] | [YOUR INPUT - Firewall] | [YOUR INPUT - High] |
| 5140 | [YOUR INPUT - Network share accessed] | [YOUR INPUT - Object Access] | [YOUR INPUT - High] |
| 5156 | [YOUR INPUT - Network connection allowed] | [YOUR INPUT - Network] | [YOUR INPUT - Medium] |
| 7045 | [YOUR INPUT - Service installed] | [YOUR INPUT - Service] | [YOUR INPUT - Critical] |

## B.3 Log Collection Health Monitoring

| Metric | Threshold | Alert Condition | Response |
|--------|-----------|-----------------|----------|
| Source Heartbeat | [YOUR INPUT - Every 5 minutes] | [YOUR INPUT - Missing >15 minutes] | [YOUR INPUT - Investigate connectivity] |
| Event Rate Anomaly | [YOUR INPUT - ±50% of baseline] | [YOUR INPUT - Sudden drop or spike] | [YOUR INPUT - Check source health] |
| Parse Errors | [YOUR INPUT - <1% of events] | [YOUR INPUT - >5% parse failures] | [YOUR INPUT - Review parser] |
| Log Latency | [YOUR INPUT - <5 minutes] | [YOUR INPUT - >15 minute delay] | [YOUR INPUT - Check collection pipeline] |
| Storage Utilization | [YOUR INPUT - <80%] | [YOUR INPUT - >85%] | [YOUR INPUT - Expand storage or adjust retention] |

---

# SECTION C: DETECTION USE CASES

## C.1 Use Case Categories

### Authentication & Access

| Use Case ID | Name | Description | MITRE ATT&CK | Priority |
|-------------|------|-------------|--------------|----------|
| AUTH-001 | [YOUR INPUT - Brute Force Detection] | [YOUR INPUT - Multiple failed logins followed by success] | [YOUR INPUT - T1110] | [YOUR INPUT - High] |
| AUTH-002 | [YOUR INPUT - Impossible Travel] | [YOUR INPUT - Login from geographically distant locations in short time] | [YOUR INPUT - T1078] | [YOUR INPUT - High] |
| AUTH-003 | [YOUR INPUT - After-Hours Login] | [YOUR INPUT - Authentication outside business hours] | [YOUR INPUT - T1078] | [YOUR INPUT - Medium] |
| AUTH-004 | [YOUR INPUT - Credential Stuffing] | [YOUR INPUT - High-volume failed logins across accounts] | [YOUR INPUT - T1110.004] | [YOUR INPUT - Critical] |
| AUTH-005 | [YOUR INPUT - MFA Bypass Attempt] | [YOUR INPUT - Successful login without expected MFA] | [YOUR INPUT - T1556] | [YOUR INPUT - Critical] |
| AUTH-006 | [YOUR INPUT - Password Spray] | [YOUR INPUT - Same password tried across many accounts] | [YOUR INPUT - T1110.003] | [YOUR INPUT - Critical] |
| AUTH-007 | [YOUR INPUT - Account Lockout Surge] | [YOUR INPUT - Multiple accounts locked in short period] | [YOUR INPUT - T1110] | [YOUR INPUT - High] |
| AUTH-008 | [YOUR INPUT - Service Account Interactive Login] | [YOUR INPUT - Service account used for interactive session] | [YOUR INPUT - T1078] | [YOUR INPUT - Critical] |

### Privilege Escalation

| Use Case ID | Name | Description | MITRE ATT&CK | Priority |
|-------------|------|-------------|--------------|----------|
| PRIV-001 | [YOUR INPUT - New Admin Account] | [YOUR INPUT - New account added to privileged group] | [YOUR INPUT - T1136] | [YOUR INPUT - Critical] |
| PRIV-002 | [YOUR INPUT - Privileged Group Change] | [YOUR INPUT - Membership change in Domain Admins, etc.] | [YOUR INPUT - T1098] | [YOUR INPUT - Critical] |
| PRIV-003 | [YOUR INPUT - UAC Bypass] | [YOUR INPUT - Process elevation without UAC prompt] | [YOUR INPUT - T1548.002] | [YOUR INPUT - High] |
| PRIV-004 | [YOUR INPUT - Sudo to Root] | [YOUR INPUT - Non-admin user becomes root on Linux] | [YOUR INPUT - T1548.003] | [YOUR INPUT - High] |
| PRIV-005 | [YOUR INPUT - DCSync Attack] | [YOUR INPUT - Non-DC requesting replication] | [YOUR INPUT - T1003.006] | [YOUR INPUT - Critical] |

### Lateral Movement

| Use Case ID | Name | Description | MITRE ATT&CK | Priority |
|-------------|------|-------------|--------------|----------|
| LAT-001 | [YOUR INPUT - RDP from Unusual Source] | [YOUR INPUT - RDP connection from unexpected host] | [YOUR INPUT - T1021.001] | [YOUR INPUT - High] |
| LAT-002 | [YOUR INPUT - PsExec Usage] | [YOUR INPUT - PsExec or similar remote execution tool] | [YOUR INPUT - T1570] | [YOUR INPUT - High] |
| LAT-003 | [YOUR INPUT - WMI Remote Execution] | [YOUR INPUT - WMI used for remote command execution] | [YOUR INPUT - T1047] | [YOUR INPUT - High] |
| LAT-004 | [YOUR INPUT - Pass-the-Hash] | [YOUR INPUT - NTLM auth without corresponding Kerberos] | [YOUR INPUT - T1550.002] | [YOUR INPUT - Critical] |
| LAT-005 | [YOUR INPUT - SMB Lateral Movement] | [YOUR INPUT - Admin shares accessed between workstations] | [YOUR INPUT - T1021.002] | [YOUR INPUT - High] |

### Malware & Execution

| Use Case ID | Name | Description | MITRE ATT&CK | Priority |
|-------------|------|-------------|--------------|----------|
| MAL-001 | [YOUR INPUT - Suspicious PowerShell] | [YOUR INPUT - Encoded, obfuscated, or download commands] | [YOUR INPUT - T1059.001] | [YOUR INPUT - Critical] |
| MAL-002 | [YOUR INPUT - Script from Temp/Downloads] | [YOUR INPUT - Script execution from temporary folders] | [YOUR INPUT - T1059] | [YOUR INPUT - High] |
| MAL-003 | [YOUR INPUT - Living-off-the-Land] | [YOUR INPUT - Suspicious use of LOLBins] | [YOUR INPUT - T1218] | [YOUR INPUT - High] |
| MAL-004 | [YOUR INPUT - Ransomware Indicators] | [YOUR INPUT - Mass file modification, shadow copy deletion] | [YOUR INPUT - T1486] | [YOUR INPUT - Critical] |
| MAL-005 | [YOUR INPUT - Webshell Detection] | [YOUR INPUT - Suspicious process spawned by web server] | [YOUR INPUT - T1505.003] | [YOUR INPUT - Critical] |
| MAL-006 | [YOUR INPUT - EDR Alert] | [YOUR INPUT - CrowdStrike/Defender detection] | [YOUR INPUT - Various] | [YOUR INPUT - Varies] |

### Data Exfiltration

| Use Case ID | Name | Description | MITRE ATT&CK | Priority |
|-------------|------|-------------|--------------|----------|
| EXFIL-001 | [YOUR INPUT - Large Data Transfer] | [YOUR INPUT - Unusual volume upload to external] | [YOUR INPUT - T1041] | [YOUR INPUT - High] |
| EXFIL-002 | [YOUR INPUT - DNS Tunneling] | [YOUR INPUT - High volume/unusual DNS queries] | [YOUR INPUT - T1048.003] | [YOUR INPUT - High] |
| EXFIL-003 | [YOUR INPUT - Cloud Storage Upload] | [YOUR INPUT - Data uploaded to personal cloud services] | [YOUR INPUT - T1567.002] | [YOUR INPUT - High] |
| EXFIL-004 | [YOUR INPUT - Email Attachment Exfil] | [YOUR INPUT - Large attachments to external recipients] | [YOUR INPUT - T1048.003] | [YOUR INPUT - Medium] |
| EXFIL-005 | [YOUR INPUT - USB Data Copy] | [YOUR INPUT - Large file copy to removable media] | [YOUR INPUT - T1052.001] | [YOUR INPUT - High] |

### Cloud Security

| Use Case ID | Name | Description | MITRE ATT&CK | Priority |
|-------------|------|-------------|--------------|----------|
| CLOUD-001 | [YOUR INPUT - Root/Global Admin Login] | [YOUR INPUT - AWS root or Azure Global Admin used] | [YOUR INPUT - T1078.004] | [YOUR INPUT - Critical] |
| CLOUD-002 | [YOUR INPUT - Security Group Modification] | [YOUR INPUT - Firewall rules opening 0.0.0.0/0] | [YOUR INPUT - T1562.007] | [YOUR INPUT - Critical] |
| CLOUD-003 | [YOUR INPUT - S3 Bucket Made Public] | [YOUR INPUT - Bucket ACL or policy allows public access] | [YOUR INPUT - T1530] | [YOUR INPUT - Critical] |
| CLOUD-004 | [YOUR INPUT - IAM Policy Change] | [YOUR INPUT - Permissions boundary removed or elevated] | [YOUR INPUT - T1098] | [YOUR INPUT - High] |
| CLOUD-005 | [YOUR INPUT - Unusual API Activity] | [YOUR INPUT - Reconnaissance APIs like List*, Describe*] | [YOUR INPUT - T1580] | [YOUR INPUT - Medium] |
| CLOUD-006 | [YOUR INPUT - CloudTrail Disabled] | [YOUR INPUT - Logging disabled in any region] | [YOUR INPUT - T1562.008] | [YOUR INPUT - Critical] |

## C.2 Use Case Template

```
[YOUR INPUT - Complete use case documentation template]

USE CASE DOCUMENTATION
======================

USE CASE ID: [e.g., AUTH-001]
NAME: [Descriptive name]
VERSION: [1.0]
LAST UPDATED: [DATE]
AUTHOR: [YOUR NAME]

DESCRIPTION:
[Detailed description of what this use case detects]

BUSINESS JUSTIFICATION:
[Why is this detection important for NordicShield?]

MITRE ATT&CK MAPPING:
- Tactic: [YOUR INPUT]
- Technique: [YOUR INPUT]
- Sub-technique: [YOUR INPUT]

DATA SOURCES REQUIRED:
- [YOUR INPUT - Log source 1]
- [YOUR INPUT - Log source 2]

DETECTION LOGIC:
[YOUR INPUT - Pseudocode or query logic]

Example query (SPL/KQL):
```
[YOUR INPUT - Actual query]
```

THRESHOLDS:
- [YOUR INPUT - e.g., >5 failed logins in 5 minutes]
- [YOUR INPUT - Configurable parameters]

FALSE POSITIVE SCENARIOS:
1. [YOUR INPUT - Known benign scenario]
2. [YOUR INPUT - How to distinguish]

TUNING RECOMMENDATIONS:
- [YOUR INPUT - Whitelist criteria]
- [YOUR INPUT - Threshold adjustments]

ALERT SEVERITY: [Critical/High/Medium/Low]

RESPONSE ACTIONS:
1. [YOUR INPUT - First response step]
2. [YOUR INPUT - Escalation criteria]
3. [YOUR INPUT - Related playbook reference]

TESTING PROCEDURE:
[YOUR INPUT - How to validate the detection works]

REFERENCES:
- [YOUR INPUT - Related documentation]
```

## C.3 Correlation Rules

### Sample Correlation Rules

| Rule Name | Logic | Sources | Alert Priority |
|-----------|-------|---------|----------------|
| Brute Force Success | [YOUR INPUT - >5 failed logins + 1 success within 10 min, same source] | [YOUR INPUT - AD Security Log, VPN] | [YOUR INPUT - Critical] |
| Ransomware Behavior | [YOUR INPUT - Shadow copy deletion + mass file rename within 5 min] | [YOUR INPUT - Windows Security, Sysmon] | [YOUR INPUT - Critical] |
| Lateral Movement Chain | [YOUR INPUT - RDP/SMB to 3+ new hosts within 30 min from same user] | [YOUR INPUT - Windows Security, Network] | [YOUR INPUT - High] |
| Data Exfil Prep | [YOUR INPUT - Archive creation + large outbound transfer] | [YOUR INPUT - Process, Network] | [YOUR INPUT - High] |
| Persistence Established | [YOUR INPUT - New service + scheduled task on same host, same session] | [YOUR INPUT - Windows Security] | [YOUR INPUT - Critical] |

---

# SECTION D: ALERTING & TRIAGE

## D.1 Alert Severity Classification

| Severity | Definition | Response Time | Escalation |
|----------|------------|---------------|------------|
| Critical | [YOUR INPUT - Active threat, immediate risk to business] | [YOUR INPUT - 15 minutes] | [YOUR INPUT - Immediate to SOC Lead, CISO within 1 hour] |
| High | [YOUR INPUT - Significant threat indicator, requires investigation] | [YOUR INPUT - 1 hour] | [YOUR INPUT - SOC Lead within 4 hours if unresolved] |
| Medium | [YOUR INPUT - Potential threat, may be false positive] | [YOUR INPUT - 4 hours] | [YOUR INPUT - Review in daily triage] |
| Low | [YOUR INPUT - Informational, policy violation, minor anomaly] | [YOUR INPUT - 24 hours] | [YOUR INPUT - Include in weekly review] |
| Informational | [YOUR INPUT - FYI, trending, no immediate action] | [YOUR INPUT - Weekly review] | [YOUR INPUT - No escalation needed] |

## D.2 Alert Triage Workflow

```
[YOUR INPUT - Define triage workflow]

ALERT TRIAGE WORKFLOW
=====================

┌─────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│   ┌────────────────┐                                                    │
│   │  ALERT FIRES   │                                                    │
│   └───────┬────────┘                                                    │
│           │                                                              │
│           ▼                                                              │
│   ┌────────────────┐                                                    │
│   │ INITIAL TRIAGE │◄──── Tier 1 SOC Analyst (SLA: [YOUR INPUT])       │
│   │ (<5 minutes)   │                                                    │
│   └───────┬────────┘                                                    │
│           │                                                              │
│     ┌─────┴─────┐                                                       │
│     │           │                                                       │
│     ▼           ▼                                                       │
│ ┌─────────┐ ┌─────────┐                                                │
│ │  TRUE   │ │  FALSE  │──► [YOUR INPUT - Close, tune rule]            │
│ │POSITIVE │ │POSITIVE │                                                │
│ └────┬────┘ └─────────┘                                                │
│      │                                                                  │
│      ▼                                                                  │
│ ┌────────────────┐                                                     │
│ │  ENRICHMENT    │◄──── [YOUR INPUT - Add context from CMDB, TI, etc.]│
│ │  (5-15 min)    │                                                     │
│ └───────┬────────┘                                                     │
│         │                                                               │
│   ┌─────┴─────┐                                                        │
│   │           │                                                        │
│   ▼           ▼                                                        │
│ ┌─────────┐ ┌─────────┐                                                │
│ │ T1 CAN  │ │ESCALATE │──► Tier 2 Analyst                             │
│ │ RESOLVE │ │ TO T2   │                                                │
│ └────┬────┘ └────┬────┘                                                │
│      │           │                                                      │
│      ▼           ▼                                                      │
│ ┌────────────────────────────┐                                         │
│ │     INVESTIGATION          │◄──── [YOUR INPUT - Detailed analysis]  │
│ │  (T1: 30 min / T2: 2 hr)   │                                         │
│ └────────────┬───────────────┘                                         │
│              │                                                          │
│        ┌─────┴─────┐                                                   │
│        │           │                                                   │
│        ▼           ▼                                                   │
│   ┌─────────┐ ┌─────────────┐                                         │
│   │ BENIGN  │ │  INCIDENT   │──► Incident Response Process            │
│   │         │ │  CONFIRMED  │                                         │
│   └────┬────┘ └─────────────┘                                         │
│        │                                                               │
│        ▼                                                               │
│   ┌─────────────┐                                                     │
│   │ DOCUMENT &  │                                                     │
│   │    CLOSE    │                                                     │
│   └─────────────┘                                                     │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

## D.3 Triage Checklist

```
[YOUR INPUT - Create triage checklist]

ALERT TRIAGE CHECKLIST
======================

□ 1. INITIAL ASSESSMENT
  □ Review alert details and severity
  □ Identify affected asset(s)
  □ Check asset criticality in CMDB
  □ Note time of event vs. current time

□ 2. CONTEXT GATHERING
  □ What triggered the alert?
  □ Is this a known user/system?
  □ Check for related alerts (±30 minutes, same host/user)
  □ Review recent changes (change management)
  □ Check threat intelligence for IOCs

□ 3. VALIDATE ALERT
  □ Review raw log data
  □ Check if behavior is expected for this user/system
  □ Verify alert logic/threshold makes sense
  □ Is this a known false positive pattern?

□ 4. ENRICHMENT
  □ Asset information (owner, criticality, data sensitivity)
  □ User information (role, recent activity)
  □ Network context (where is this host?)
  □ Threat intelligence match?

□ 5. DETERMINATION
  □ True Positive - Investigate or escalate
  □ True Positive - No action needed (already mitigated)
  □ False Positive - Document and tune
  □ Benign True Positive - Whitelist consideration

□ 6. DOCUMENTATION
  □ Document all findings in ticket
  □ Note time spent on investigation
  □ Record indicators discovered
  □ Reference related tickets if any
```

## D.4 False Positive Management

| Category | Example | Action | Tuning Method |
|----------|---------|--------|---------------|
| Known Business Activity | [YOUR INPUT - Backup job triggering large transfer alert] | [YOUR INPUT - Whitelist specific source/destination] | [YOUR INPUT - Add to exception list] |
| Maintenance Window | [YOUR INPUT - Patching causing unusual service restarts] | [YOUR INPUT - Schedule suppression during maintenance] | [YOUR INPUT - Suppress alert during window] |
| Vendor Activity | [YOUR INPUT - Managed service provider remote access] | [YOUR INPUT - Whitelist known vendor IPs/accounts] | [YOUR INPUT - Conditional whitelist] |
| Threshold Too Low | [YOUR INPUT - 3 failed logins triggering alert] | [YOUR INPUT - Raise threshold] | [YOUR INPUT - Adjust detection logic] |
| Misconfigured Source | [YOUR INPUT - Test system generating alerts] | [YOUR INPUT - Exclude source or fix logging] | [YOUR INPUT - Source-level filtering] |

---

# SECTION E: SOC OPERATIONS

## E.1 SOC Operating Model

```
[YOUR INPUT - Define SOC structure]

NORDICSHIELD SOC OPERATING MODEL
================================

COVERAGE: 24/7 (Follow-the-Sun + On-Call)

TIER STRUCTURE:
═══════════════

TIER 1 - ALERT HANDLING
├── Headcount: [YOUR INPUT - 4 FTE]
├── Schedule: [YOUR INPUT - 2 analysts per shift, 12-hour shifts]
├── Responsibilities:
│   ├── [YOUR INPUT - Initial alert triage]
│   ├── [YOUR INPUT - False positive identification]
│   ├── [YOUR INPUT - Basic incident handling]
│   └── [YOUR INPUT - Escalation to Tier 2]
└── SLA: [YOUR INPUT - 15 min response to critical]

TIER 2 - INVESTIGATION
├── Headcount: [YOUR INPUT - 2 FTE]
├── Schedule: [YOUR INPUT - Business hours + on-call]
├── Responsibilities:
│   ├── [YOUR INPUT - Deep-dive investigations]
│   ├── [YOUR INPUT - Incident response coordination]
│   ├── [YOUR INPUT - Threat hunting]
│   └── [YOUR INPUT - Detection engineering support]
└── SLA: [YOUR INPUT - 4-hour investigation completion]

TIER 3 - ENGINEERING & THREAT INTEL
├── Headcount: [YOUR INPUT - 2 FTE]
├── Schedule: [YOUR INPUT - Business hours]
├── Responsibilities:
│   ├── [YOUR INPUT - Detection development]
│   ├── [YOUR INPUT - SIEM administration]
│   ├── [YOUR INPUT - Threat intelligence analysis]
│   └── [YOUR INPUT - Advanced incident support]
└── SLA: [YOUR INPUT - 48-hour new detection development]

SOC MANAGER
├── Headcount: [YOUR INPUT - 1 FTE]
├── Responsibilities:
│   ├── [YOUR INPUT - Team management]
│   ├── [YOUR INPUT - Metrics and reporting]
│   ├── [YOUR INPUT - Process improvement]
│   └── [YOUR INPUT - Stakeholder communication]
```

## E.2 Shift Handover Procedure

```
[YOUR INPUT - Create handover template]

SOC SHIFT HANDOVER TEMPLATE
===========================

Date: _______________
Outgoing Shift: _______________
Incoming Shift: _______________

OPEN INCIDENTS:
| Ticket ID | Description | Status | Priority | Action Needed |
|-----------|-------------|--------|----------|---------------|
| [YOUR INPUT] | | | | |
| [YOUR INPUT] | | | | |

ONGOING INVESTIGATIONS:
| Ticket ID | Summary | Analyst | Next Steps |
|-----------|---------|---------|------------|
| [YOUR INPUT] | | | |

NOTABLE EVENTS THIS SHIFT:
1. [YOUR INPUT]
2. [YOUR INPUT]

SYSTEM/TOOL ISSUES:
[ ] All systems operational
[ ] Issues: [YOUR INPUT - List any problems]

MAINTENANCE WINDOWS (Next 12 hours):
- [YOUR INPUT]

INTELLIGENCE UPDATES:
- [YOUR INPUT - Any new threats, IOCs, or advisories]

ESCALATIONS/VIP SITUATIONS:
- [YOUR INPUT - Any executive involvement or special situations]

HANDOVER CONFIRMATION:
Outgoing Analyst: _________________ Time: _______
Incoming Analyst: _________________ Time: _______
```

## E.3 SOC KPIs

| Metric | Definition | Target | Current | Status |
|--------|------------|--------|---------|--------|
| Mean Time to Detect (MTTD) | [YOUR INPUT - Time from event to alert] | [YOUR INPUT - <15 min] | [YOUR INPUT] | [YOUR INPUT] |
| Mean Time to Acknowledge (MTTA) | [YOUR INPUT - Time from alert to analyst pickup] | [YOUR INPUT - <15 min Critical, <1 hr High] | [YOUR INPUT] | [YOUR INPUT] |
| Mean Time to Respond (MTTR) | [YOUR INPUT - Time from alert to resolution] | [YOUR INPUT - <4 hr Critical, <24 hr High] | [YOUR INPUT] | [YOUR INPUT] |
| Alert Volume | [YOUR INPUT - Total alerts per day/week] | [YOUR INPUT - Trend monitoring] | [YOUR INPUT] | [YOUR INPUT] |
| True Positive Rate | [YOUR INPUT - True positives / total alerts] | [YOUR INPUT - >70%] | [YOUR INPUT] | [YOUR INPUT] |
| Escalation Rate | [YOUR INPUT - T1 to T2 escalations / total] | [YOUR INPUT - <20%] | [YOUR INPUT] | [YOUR INPUT] |
| Incidents Detected | [YOUR INPUT - Confirmed security incidents] | [YOUR INPUT - All detected] | [YOUR INPUT] | [YOUR INPUT] |
| Analyst Utilization | [YOUR INPUT - Time on productive work] | [YOUR INPUT - >70%] | [YOUR INPUT] | [YOUR INPUT] |
| Ticket Backlog | [YOUR INPUT - Open tickets >24 hours] | [YOUR INPUT - <10] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION F: MONITORING SCENARIOS

## F.1 Scenario: Alert Storm

```
[YOUR INPUT - Complete this scenario]

SCENARIO: ALERT STORM DURING MAINTENANCE
========================================

SITUATION:
At 2:00 AM, the SOC begins receiving hundreds of alerts per minute. 
The on-call Tier 1 analyst is overwhelmed. Initial review shows:
- 800+ "New Service Installed" alerts across Windows servers
- 200+ "Suspicious PowerShell" alerts
- 150+ "Unauthorized Software" alerts
- All alerts started at 2:00 AM

CONTEXT:
- Change management shows a scheduled patching window 2:00-6:00 AM
- SCCM is pushing updates to 150 Windows servers
- Alert volume has completely swamped the SIEM dashboard

RESPONSE TASKS:

1. IMMEDIATE STABILIZATION:
   [YOUR INPUT - How do you handle the alert volume?]
   - Suppression approach: [YOUR INPUT]
   - Prioritization: [YOUR INPUT]

2. VALIDATION:
   [YOUR INPUT - How do you verify this is legitimate patching?]
   - Cross-reference with: [YOUR INPUT]
   - What would indicate it's NOT legitimate?

3. HIDDEN THREAT CONCERN:
   [YOUR INPUT - Could an attacker be hiding in this noise?]
   - What would you look for?
   - Sampling strategy?

4. PROCESS IMPROVEMENT:
   [YOUR INPUT - What should be done to prevent this?]
   - Change management integration: [YOUR INPUT]
   - Maintenance window handling: [YOUR INPUT]

5. DOCUMENTATION:
   [YOUR INPUT - What needs to be documented?]
```

## F.2 Scenario: Potential Insider Threat

```
[YOUR INPUT - Complete this scenario]

SCENARIO: DEPARTING EMPLOYEE DATA ACCESS
=========================================

SITUATION:
Your SIEM generates a medium-priority alert: "Unusual Data Access 
Pattern." Investigation reveals:

- User: maria.korhonen@nordicshield.fi
- Role: Senior Product Engineer
- Behavior: Accessed 47 SharePoint folders in last 2 hours
- Folders contain: Product designs, customer lists, pricing
- Time: 11:30 PM (unusual for this user)
- Method: VPN from home IP address

HR CONTEXT (obtained carefully):
- Maria submitted resignation 3 days ago
- Last day is in 2 weeks
- Departure is voluntary
- She joined a competitor

INVESTIGATION TASKS:

1. INITIAL ASSESSMENT:
   [YOUR INPUT - What's your initial risk assessment?]
   Likelihood of malicious intent: [YOUR INPUT]
   Potential impact: [YOUR INPUT]

2. ADDITIONAL DATA GATHERING:
   [YOUR INPUT - What other logs/information do you need?]
   - Check for: [YOUR INPUT]
   - DLP logs: [YOUR INPUT]
   - Previous behavior: [YOUR INPUT]

3. STAKEHOLDER NOTIFICATION:
   [YOUR INPUT - Who needs to know?]
   - HR: [YOUR INPUT]
   - Legal: [YOUR INPUT]
   - Management: [YOUR INPUT]
   - When in investigation to notify?

4. CONTAINMENT OPTIONS:
   [YOUR INPUT - What actions are appropriate?]
   - Access restriction: [YOUR INPUT]
   - Monitoring increase: [YOUR INPUT]
   - Preservation: [YOUR INPUT]

5. PRIVACY CONSIDERATIONS:
   [YOUR INPUT - GDPR and privacy factors]
   - Employee privacy rights: [YOUR INPUT]
   - Investigation documentation: [YOUR INPUT]
```

## F.3 Scenario: Building a New Detection

```
[YOUR INPUT - Build a detection use case]

SCENARIO: DETECTION ENGINEERING REQUEST
=======================================

REQUEST:
The threat intelligence team reports that a new attack technique 
is being used against Finnish technology companies. Attackers are 
using Azure AD "Consent Grant" attacks where malicious apps 
request excessive permissions.

ATTACK PATTERN:
1. User receives phishing email with link to malicious app
2. App requests OAuth consent for Mail.Read, Files.ReadWrite, etc.
3. User grants consent (often without realizing implications)
4. Attacker uses app to access emails and files

YOUR TASK - BUILD THE DETECTION:

1. DATA SOURCE IDENTIFICATION:
   [YOUR INPUT - What logs are needed?]
   - Source 1: [YOUR INPUT]
   - Source 2: [YOUR INPUT]
   - Are these logs currently collected?

2. DETECTION LOGIC:
   [YOUR INPUT - What pattern indicates this attack?]
   - Baseline behavior: [YOUR INPUT]
   - Anomalous behavior: [YOUR INPUT]
   - Query pseudocode: [YOUR INPUT]

3. THRESHOLD DETERMINATION:
   [YOUR INPUT - How sensitive should the alert be?]
   - Initial threshold: [YOUR INPUT]
   - Tuning approach: [YOUR INPUT]

4. FALSE POSITIVE ANALYSIS:
   [YOUR INPUT - What legitimate activity might trigger this?]
   - FP scenario 1: [YOUR INPUT]
   - FP scenario 2: [YOUR INPUT]
   - Mitigation: [YOUR INPUT]

5. RESPONSE PLAYBOOK:
   [YOUR INPUT - What should analyst do when this fires?]
   - Step 1: [YOUR INPUT]
   - Step 2: [YOUR INPUT]
   - Step 3: [YOUR INPUT]

6. TESTING PLAN:
   [YOUR INPUT - How will you validate the detection?]
```

---

# SECTION G: DASHBOARDS & REPORTING

## G.1 SOC Dashboard Components

| Dashboard | Audience | Key Widgets | Refresh Rate |
|-----------|----------|-------------|--------------|
| Real-Time Operations | [YOUR INPUT - SOC Analysts] | [YOUR INPUT - Alert queue, active incidents, system health] | [YOUR INPUT - Real-time] |
| Threat Overview | [YOUR INPUT - SOC Lead/Manager] | [YOUR INPUT - Alert trends, MITRE heat map, top sources] | [YOUR INPUT - 5 minutes] |
| Asset Risk | [YOUR INPUT - Security Team] | [YOUR INPUT - High-risk assets, vulnerability overlap] | [YOUR INPUT - Hourly] |
| Executive Summary | [YOUR INPUT - CISO/Leadership] | [YOUR INPUT - Incident counts, SLA compliance, risk posture] | [YOUR INPUT - Daily] |
| Investigation Support | [YOUR INPUT - Analysts] | [YOUR INPUT - IOC search, timeline, entity context] | [YOUR INPUT - On-demand] |

## G.2 Sample Dashboard Layout

```
[YOUR INPUT - Design SOC operations dashboard]

┌─────────────────────────────────────────────────────────────────────────┐
│                    NORDICSHIELD SOC OPERATIONS DASHBOARD                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌─────────────────────────┐  ┌─────────────────────────┐              │
│  │  ALERTS BY SEVERITY     │  │  ALERTS - LAST 24 HRS   │              │
│  │  ──────────────────     │  │  ────────────────────   │              │
│  │  🔴 Critical: [XX]      │  │         [CHART]         │              │
│  │  🟠 High: [XX]          │  │       Alert Volume      │              │
│  │  🟡 Medium: [XX]        │  │        Over Time        │              │
│  │  🟢 Low: [XX]           │  │                         │              │
│  └─────────────────────────┘  └─────────────────────────┘              │
│                                                                          │
│  ┌───────────────────────────────────────────────────────────────────┐  │
│  │  ALERT QUEUE                                           [FILTERS]  │  │
│  │  ─────────────────────────────────────────────────────────────    │  │
│  │  ID     │ Time  │ Alert Name          │ Asset     │ Sev │ Status │  │
│  │  ───────┼───────┼─────────────────────┼───────────┼─────┼────────│  │
│  │  12345  │ 10:32 │ Brute Force Success │ MAIL-01   │ 🔴  │ New    │  │
│  │  12344  │ 10:28 │ Suspicious PS       │ WKS-042   │ 🟠  │ Triage │  │
│  │  12343  │ 10:15 │ After Hours Login   │ SRV-WEB01 │ 🟡  │ Invest │  │
│  │  [YOUR INPUT - More rows]                                         │  │
│  └───────────────────────────────────────────────────────────────────┘  │
│                                                                          │
│  ┌─────────────────────────┐  ┌─────────────────────────┐              │
│  │  TOP ALERT SOURCES      │  │  SOC METRICS            │              │
│  │  ──────────────────     │  │  ────────────           │              │
│  │  1. [ASSET] - XX alerts │  │  MTTA: [XX min]         │              │
│  │  2. [ASSET] - XX alerts │  │  MTTR: [XX hr]          │              │
│  │  3. [ASSET] - XX alerts │  │  FP Rate: [XX%]         │              │
│  │  [YOUR INPUT]           │  │  Backlog: [XX]          │              │
│  └─────────────────────────┘  └─────────────────────────┘              │
│                                                                          │
│  ┌─────────────────────────┐  ┌─────────────────────────┐              │
│  │  SYSTEM HEALTH          │  │  ACTIVE INCIDENTS       │              │
│  │  ──────────────         │  │  ────────────────       │              │
│  │  SIEM: 🟢               │  │  INC-001: Ransomware    │              │
│  │  Log Collectors: 🟢     │  │  Status: Contain        │              │
│  │  EDR: 🟢                │  │  Lead: [Analyst]        │              │
│  │  Threat Intel: 🟢       │  │  [YOUR INPUT]           │              │
│  └─────────────────────────┘  └─────────────────────────┘              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

## G.3 Executive Reporting Template

```
[YOUR INPUT - Create executive report]

MONTHLY SOC EXECUTIVE REPORT
============================

PERIOD: [MONTH YEAR]
CLASSIFICATION: Confidential

EXECUTIVE SUMMARY:
[YOUR INPUT - 3-4 sentences summarizing security posture]

KEY METRICS:
┌────────────────────────────────────────────────────────────┐
│  Total Alerts:      [XXXX]    (↑/↓ XX% vs last month)     │
│  Confirmed Incidents: [XX]    (↑/↓ XX% vs last month)     │
│  MTTA (Critical):   [XX min]  (Target: 15 min)            │
│  MTTR (Critical):   [XX hr]   (Target: 4 hr)              │
│  SLA Compliance:    [XX%]     (Target: 95%)               │
└────────────────────────────────────────────────────────────┘

SIGNIFICANT INCIDENTS:
1. [YOUR INPUT - Brief description, impact, resolution]
2. [YOUR INPUT]

THREAT LANDSCAPE:
- [YOUR INPUT - Notable threats observed]
- [YOUR INPUT - Industry intelligence relevant]

TOP DETECTION CATEGORIES:
1. [YOUR INPUT - Category] - XX alerts
2. [YOUR INPUT] - XX alerts
3. [YOUR INPUT] - XX alerts

IMPROVEMENTS MADE:
- [YOUR INPUT - New detections, tuning, process improvements]

RECOMMENDATIONS:
1. [YOUR INPUT]
2. [YOUR INPUT]

NEXT MONTH FOCUS:
- [YOUR INPUT]
```

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 4.4 - Security Monitoring & SIEM Operations |
| **Phase** | 4 - Security Operations |
| **Exam Objectives** | 4.4 - Security alerting and monitoring concepts |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
