# Deliverable 2.2: Attack Surface Assessment
## NordicShield Technologies Oy

---

```
╔══════════════════════════════════════════════════════════════════╗
║              ATTACK SURFACE ASSESSMENT REPORT                     ║
║                                                                    ║
║  Document ID: ASA-NS-2026-001                                     ║
║  Assessment Date: [YOUR DATE]                                     ║
║  Assessor: [YOUR NAME]                                            ║
║  Scope: Full Enterprise (IT/OT/IoT/Cloud)                        ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Document Purpose

This Attack Surface Assessment systematically identifies and evaluates all potential entry points, attack vectors, and exposure areas across NordicShield's enterprise. The assessment covers physical, digital, human, and supply chain attack surfaces.

---

## Instructions

1. Map all attack vectors using the company profile as reference
2. Assess exposure level and document controls
3. Complete all `[YOUR INPUT]` sections
4. Prioritize attack surface reduction opportunities

---

# SECTION A: EXECUTIVE SUMMARY

## A.1 Attack Surface Overview

```
[YOUR INPUT - Write a 200-word executive summary]

Total Attack Surface Assessment:
- Number of external-facing services:
- Number of user accounts:
- IoT devices deployed:
- Third-party integrations:
- Geographic locations:

Critical Findings:
1.
2.
3.

Priority Reduction Opportunities:
1.
2.
3.
```

## A.2 Attack Surface Heat Map

| Surface Category | Exposure Level | Current Controls | Risk Rating | Priority |
|------------------|---------------|------------------|-------------|----------|
| External Network | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Internal Network | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Cloud Infrastructure | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT/OT Systems | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Web Applications | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Email/Communication | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Human/Social | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Physical | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Supply Chain | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Mobile/BYOD | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

**Rating Scale:** Critical | High | Medium | Low | Minimal

---

# SECTION B: ATTACK VECTOR ANALYSIS

## B.1 Message-Based Attack Vectors

### Email Attack Surface

| Component | Description | Exposure | Current Controls | Gap Assessment |
|-----------|-------------|----------|------------------|----------------|
| Corporate Email (M365) | [YOUR INPUT - User count] | [YOUR INPUT] | [YOUR INPUT - Defender? SPF/DKIM?] | [YOUR INPUT] |
| Email Addresses Exposed | [YOUR INPUT - How many publicly findable?] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Executive Email | [YOUR INPUT - CEO, CFO exposure] | High - BEC target | [YOUR INPUT] | [YOUR INPUT] |
| Distribution Lists | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Service Accounts | [YOUR INPUT - support@, info@] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

#### Email Attack Scenarios

| Attack Vector | Scenario | Likelihood | Impact | Current Defense |
|---------------|----------|------------|--------|-----------------|
| Phishing | [YOUR INPUT - Credential harvesting] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Spear Phishing | [YOUR INPUT - Targeted exec compromise] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Business Email Compromise | [YOUR INPUT - Invoice fraud] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Malicious Attachment | [YOUR INPUT - Malware delivery] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Malicious Link | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Reply-Chain Attack | [YOUR INPUT - Thread hijacking] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### SMS/Voice Attack Surface

| Component | Description | Exposure | Risk |
|-----------|-------------|----------|------|
| Corporate Phone System | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Employee Mobile Numbers | [YOUR INPUT - Published anywhere?] | [YOUR INPUT] | [YOUR INPUT] |
| Executive Direct Lines | [YOUR INPUT] | High - Vishing target | [YOUR INPUT] |
| Support Hotlines | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## B.2 Image-Based & File-Based Attack Vectors

| Vector | Attack Scenario | Entry Point | Risk Level |
|--------|----------------|-------------|------------|
| Malicious Documents | [YOUR INPUT - Office macros, PDF exploits] | [YOUR INPUT] | [YOUR INPUT] |
| Image Files | [YOUR INPUT - Steganography, web bugs] | [YOUR INPUT] | [YOUR INPUT] |
| USB Drives | [YOUR INPUT - Dropped media, supply chain] | [YOUR INPUT] | [YOUR INPUT] |
| ISO/Archive Files | [YOUR INPUT - Bypass Mark-of-the-Web] | [YOUR INPUT] | [YOUR INPUT] |
| QR Codes | [YOUR INPUT - Malicious redirects] | [YOUR INPUT] | [YOUR INPUT] |

---

## B.3 Network-Based Attack Vectors

### External Network Attack Surface

| Asset | IP/Domain | Services Exposed | Vulnerability | Risk |
|-------|-----------|------------------|---------------|------|
| Corporate Website | nordicsense.fi | [YOUR INPUT - 443, 80] | [YOUR INPUT] | [YOUR INPUT] |
| Customer Portal | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT API Gateway | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| VPN Endpoint | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Mail Server (MX) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| DNS Servers | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

#### External Attack Scenarios

| Attack Vector | Target | Method | Impact | Defense |
|---------------|--------|--------|--------|---------|
| Web Application Exploits | [YOUR INPUT] | [YOUR INPUT - SQLi, XSS, etc.] | [YOUR INPUT] | [YOUR INPUT] |
| API Abuse | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| DDoS Attack | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| DNS Attacks | [YOUR INPUT] | [YOUR INPUT - Hijacking, tunneling] | [YOUR INPUT] | [YOUR INPUT] |
| SSL/TLS Vulnerabilities | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Internal Network Attack Surface

| Segment | Assets | Exposure to Other Segments | Risk |
|---------|--------|---------------------------|------|
| Corporate LAN | [YOUR INPUT - Workstations, servers] | [YOUR INPUT] | [YOUR INPUT] |
| Server VLAN | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT/OT VLAN | [YOUR INPUT - 827 devices] | [YOUR INPUT] | [YOUR INPUT] |
| Guest Network | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Development Network | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Management Network | [YOUR INPUT - iLO, iDRAC, switches] | [YOUR INPUT] | [YOUR INPUT] |

#### Lateral Movement Opportunities

| From | To | Method | Risk | Mitigation |
|------|-----|--------|------|------------|
| Workstation | Domain Controller | [YOUR INPUT - Pass-the-hash, Kerberoasting] | [YOUR INPUT] | [YOUR INPUT] |
| Corporate → IoT VLAN | IoT Gateway | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Wireless Attack Surface

| Wireless Network | SSID Broadcast | Authentication | Encryption | Risk |
|------------------|----------------|----------------|------------|------|
| Corporate WiFi | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Guest WiFi | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT WiFi | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

#### Wireless Attack Scenarios

| Attack | Description | Risk Level | Defense |
|--------|-------------|------------|---------|
| Evil Twin | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Deauthentication | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| WPA Cracking | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Rogue AP | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## B.4 Application-Based Attack Vectors

### Web Applications

| Application | URL/Location | Authentication | Known Risks | Testing Date |
|-------------|--------------|----------------|-------------|--------------|
| NordicSense Platform | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Customer Portal | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Employee Self-Service | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Admin Console | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| API Documentation | [YOUR INPUT] | [YOUR INPUT - Publicly accessible?] | [YOUR INPUT] | [YOUR INPUT] |

#### OWASP Top 10 Assessment

| Vulnerability | Application | Present? | Severity | Evidence/Notes |
|---------------|-------------|----------|----------|----------------|
| A01:2021 - Broken Access Control | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| A02:2021 - Cryptographic Failures | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| A03:2021 - Injection | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| A04:2021 - Insecure Design | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| A05:2021 - Security Misconfiguration | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| A06:2021 - Vulnerable Components | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| A07:2021 - Auth Failures | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| A08:2021 - Software/Data Integrity | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| A09:2021 - Logging Failures | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| A10:2021 - SSRF | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### APIs

| API | Purpose | Authentication | Rate Limiting | Input Validation |
|-----|---------|----------------|---------------|------------------|
| IoT Data Ingestion API | [YOUR INPUT] | [YOUR INPUT - How do devices auth?] | [YOUR INPUT] | [YOUR INPUT] |
| Customer Integration API | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Internal Microservices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Mobile App Backend | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## B.5 Cloud Attack Surface

### AWS Infrastructure

| Resource | Service | Public Exposure | IAM Controls | Risk |
|----------|---------|-----------------|--------------|------|
| Production VPC | EC2, RDS, etc. | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| S3 Buckets | [YOUR INPUT - List buckets] | [YOUR INPUT - Public? Private?] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Core | IoT device connection | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Lambda Functions | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| API Gateway | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

#### AWS-Specific Attack Vectors

| Attack Vector | Target | Risk | Detection |
|---------------|--------|------|-----------|
| S3 Bucket Misconfiguration | [YOUR INPUT - Public buckets?] | [YOUR INPUT] | [YOUR INPUT] |
| IAM Privilege Escalation | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IMDS Exploitation | EC2 instances | [YOUR INPUT] | [YOUR INPUT] |
| Lambda Injection | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Cross-Account Access | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### SaaS Attack Surface

| SaaS Application | Data Stored | Admin Access | Integration | Risk |
|------------------|-------------|--------------|-------------|------|
| Microsoft 365 | [YOUR INPUT] | [YOUR INPUT - Who?] | [YOUR INPUT] | [YOUR INPUT] |
| Salesforce | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| GitHub Enterprise | [YOUR INPUT - Source code] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Workday | [YOUR INPUT - HR data] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Slack | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [Other - from profile] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## B.6 IoT/OT Attack Surface

### IoT Device Inventory Attack Surface

| Device Type | Qty | Communication | Authentication | Physical Security | Risk |
|-------------|-----|---------------|----------------|-------------------|------|
| Temperature Sensors | 280 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Flow Sensors | 156 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Power Monitors | 98 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Cooling Controllers | 45 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Environmental Sensors | 196 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Gateways | 52 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### IoT-Specific Attack Vectors

| Attack Vector | Target Devices | Method | Impact | Likelihood |
|---------------|----------------|--------|--------|------------|
| Default Credentials | [YOUR INPUT] | [YOUR INPUT - Shodan, mass scanning] | [YOUR INPUT] | [YOUR INPUT] |
| Firmware Exploitation | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Protocol Vulnerabilities | [YOUR INPUT - MQTT, CoAP, Modbus?] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Physical Tampering | [YOUR INPUT - Customer site devices] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Man-in-the-Middle | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Denial of Service | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Supply Chain Compromise | [YOUR INPUT] | [YOUR INPUT - Backdoored firmware] | [YOUR INPUT] | [YOUR INPUT] |
| Botnet Recruitment | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### OT-Specific Considerations

| Concern | NordicShield Context | Attack Scenario | Safety Impact |
|---------|---------------------|-----------------|---------------|
| Cooling System Manipulation | [YOUR INPUT] | [YOUR INPUT - Data center overheating] | [YOUR INPUT] |
| Sensor Data Manipulation | [YOUR INPUT] | [YOUR INPUT - False readings] | [YOUR INPUT] |
| Process Disruption | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## B.7 Human Attack Surface

### Social Engineering Vectors

| Attack Vector | Target Personnel | Scenario | Risk Level |
|---------------|------------------|----------|------------|
| Pretexting | [YOUR INPUT - Reception, IT helpdesk] | [YOUR INPUT] | [YOUR INPUT] |
| Phishing (Email) | [YOUR INPUT - All employees] | [YOUR INPUT] | [YOUR INPUT] |
| Spear Phishing | [YOUR INPUT - Executives, Finance, IT] | [YOUR INPUT] | [YOUR INPUT] |
| Vishing | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Smishing | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Watering Hole | [YOUR INPUT - Websites employees visit] | [YOUR INPUT] | [YOUR INPUT] |
| Baiting | [YOUR INPUT - USB drops] | [YOUR INPUT] | [YOUR INPUT] |
| Tailgating | [YOUR INPUT - Physical access] | [YOUR INPUT] | [YOUR INPUT] |
| Impersonation | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Employee Risk Assessment

| Employee Group | Size | Access Level | Training Status | Risk Rating |
|----------------|------|--------------|-----------------|-------------|
| Executives | [YOUR INPUT] | Critical systems, finances | [YOUR INPUT] | [YOUR INPUT] |
| Finance Team | [YOUR INPUT] | Financial systems | [YOUR INPUT] | [YOUR INPUT] |
| IT/Security | [YOUR INPUT] | Administrative access | [YOUR INPUT] | [YOUR INPUT] |
| Developers | [YOUR INPUT] | Source code, production | [YOUR INPUT] | [YOUR INPUT] |
| Sales | [YOUR INPUT] | CRM, customer data | [YOUR INPUT] | [YOUR INPUT] |
| Support | [YOUR INPUT] | Customer systems | [YOUR INPUT] | [YOUR INPUT] |
| HR | [YOUR INPUT] | Employee PII | [YOUR INPUT] | [YOUR INPUT] |
| New Hires | [YOUR INPUT] | Varies | [YOUR INPUT - Not yet trained?] | [YOUR INPUT] |
| Contractors | [YOUR INPUT] | Varies | [YOUR INPUT] | [YOUR INPUT] |

### Online Presence Analysis

| Information Type | Where Found | Risk | Mitigation |
|------------------|-------------|------|------------|
| Employee Names/Titles | [YOUR INPUT - LinkedIn, website] | [YOUR INPUT - Targeting data] | [YOUR INPUT] |
| Org Chart | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Technologies Used | [YOUR INPUT - Job postings] | [YOUR INPUT] | [YOUR INPUT] |
| Office Locations | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Partner Information | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Executive Travel | [YOUR INPUT - Social media] | [YOUR INPUT] | [YOUR INPUT] |

---

## B.8 Physical Attack Surface

### Facility Security Assessment

| Location | Physical Controls | Access Control | Surveillance | Risk |
|----------|-------------------|----------------|--------------|------|
| Turku HQ | [YOUR INPUT] | [YOUR INPUT - Badge, PIN?] | [YOUR INPUT] | [YOUR INPUT] |
| Amsterdam (Planned) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Austin (Planned) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Kigali (Planned) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Data Center (Turku) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Physical Attack Scenarios

| Scenario | Target | Method | Impact | Controls |
|----------|--------|--------|--------|----------|
| Unauthorized Entry | [YOUR INPUT] | [YOUR INPUT - Tailgating, social engineering] | [YOUR INPUT] | [YOUR INPUT] |
| Device Theft | [YOUR INPUT - Laptops, servers] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Dumpster Diving | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Network Jack Access | [YOUR INPUT] | [YOUR INPUT - Plug into LAN] | [YOUR INPUT] | [YOUR INPUT] |
| USB Drops | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Visual Eavesdropping | [YOUR INPUT - Screens, whiteboards] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## B.9 Supply Chain Attack Surface

### Vendor Assessment

| Vendor | Service/Product | Access Level | Last Assessment | Risk Rating |
|--------|-----------------|--------------|-----------------|-------------|
| [From company profile] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [Hardware supplier] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [Software vendor] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [Cloud provider] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [MSP/MSSP] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Software Supply Chain

| Component | Source | Verification | Update Process | Risk |
|-----------|--------|--------------|----------------|------|
| Open Source Libraries | [YOUR INPUT - NPM, PyPI] | [YOUR INPUT - SCA?] | [YOUR INPUT] | [YOUR INPUT] |
| Commercial Software | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Firmware Updates | [YOUR INPUT] | [YOUR INPUT - Signed?] | [YOUR INPUT] | [YOUR INPUT] |
| Container Images | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION C: ATTACK SURFACE BY KILL CHAIN PHASE

## C.1 Reconnaissance Surface

What can attackers learn about NordicShield?

| Information | Where Accessible | Sensitivity | Reduction Option |
|-------------|------------------|-------------|------------------|
| Employee names/roles | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Email format | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Technology stack | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IP ranges | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Domain structure | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Partner relationships | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## C.2 Weaponization Surface

What platforms/technologies are attackers likely to target?

| Target | Relevant Exploits | Likelihood | Detection |
|--------|-------------------|------------|-----------|
| Microsoft Office | [YOUR INPUT - Macro malware] | [YOUR INPUT] | [YOUR INPUT] |
| PDF Readers | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Windows OS | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Web Browsers | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Firmware | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## C.3 Delivery Surface

How can attackers deliver payloads?

| Delivery Vector | Exposure | Controls | Effectiveness |
|-----------------|----------|----------|---------------|
| Email | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Web Browsing | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Removable Media | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Direct Network | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Supply Chain | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION D: ATTACK SURFACE REDUCTION RECOMMENDATIONS

## D.1 Priority Reductions

| # | Surface Area | Current State | Recommended Action | Effort | Impact |
|---|--------------|---------------|-------------------|--------|--------|
| 1 | [YOUR INPUT - Highest priority] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 2 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 3 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 4 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 5 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 6 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 7 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 8 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 9 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 10 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## D.2 Reduction by Category

### Network Surface Reduction

| Action | Benefit | Implementation | Timeline |
|--------|---------|----------------|----------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Application Surface Reduction

| Action | Benefit | Implementation | Timeline |
|--------|---------|----------------|----------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Human Surface Reduction

| Action | Benefit | Implementation | Timeline |
|--------|---------|----------------|----------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### IoT Surface Reduction

| Action | Benefit | Implementation | Timeline |
|--------|---------|----------------|----------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION E: ATTACK SURFACE MONITORING

## E.1 Continuous Monitoring Requirements

| Surface Area | Monitoring Tool | Frequency | Owner |
|--------------|-----------------|-----------|-------|
| External Network | [YOUR INPUT - Shodan, censys, external scanner] | [YOUR INPUT] | [YOUR INPUT] |
| Web Applications | [YOUR INPUT - DAST, bug bounty] | [YOUR INPUT] | [YOUR INPUT] |
| Cloud Configuration | [YOUR INPUT - CSPM] | [YOUR INPUT] | [YOUR INPUT] |
| Credentials | [YOUR INPUT - Dark web monitoring] | [YOUR INPUT] | [YOUR INPUT] |
| DNS | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Certificates | [YOUR INPUT - Expiry monitoring] | [YOUR INPUT] | [YOUR INPUT] |

## E.2 Attack Surface Metrics

| Metric | Current | Target | Measurement |
|--------|---------|--------|-------------|
| External Services | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Unused Accounts | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Open Ports | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Shadow IT Applications | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Unpatched Systems | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION F: EXECUTIVE SUMMARY

```
[YOUR INPUT - Write a 250-300 word executive summary]

Include:
- Overall attack surface assessment
- Most critical exposure areas
- Key findings specific to NordicShield (IoT, global expansion)
- Priority recommendations
- Resource requirements for reduction
- Ongoing monitoring needs
```

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 2.2 - Attack Surface Assessment |
| **Phase** | 2 - Threats, Vulnerabilities, and Mitigations |
| **Exam Objective** | 2.2 - Explain common threat vectors and attack surfaces |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
