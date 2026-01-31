# Deliverable 1.1: Security Controls Matrix
## NordicShield Technologies Oy

---

## Document Purpose

This matrix documents all security controls currently implemented at NordicShield Technologies, categorizes them by type and category, identifies gaps, and recommends improvements to support global expansion and ISO 27001 certification.

---

## Instructions

1. Review each control listed in the "Current Controls" section
2. Fill in the `[YOUR INPUT]` sections with your analysis
3. Add any missing controls you identify from the Company Profile
4. Complete the Gap Analysis section
5. Provide recommendations

---

# SECTION A: CURRENT CONTROLS INVENTORY

## A.1 Technical Controls

| Control ID | Control Name | Category | Type(s) | Asset Reference | Maturity (1-5) | Notes |
|------------|--------------|----------|---------|-----------------|----------------|-------|
| TC-001 | Perimeter Firewall | Technical | Preventive, Detective | NET-007, NET-008 | 4 | FortiGate 200F HA pair |
| TC-002 | Endpoint Detection & Response | Technical | Preventive, Detective, Corrective | All endpoints | 4 | CrowdStrike Falcon |
| TC-003 | Email Security Gateway | Technical | Preventive, Detective | M365 Integration | 3 | Proofpoint |
| TC-004 | Backup System | Technical | Corrective | SRV-008, STO-003, STO-004 | 4 | Veeam + tape |
| TC-005 | Network Segmentation (VLANs) | Technical | Preventive | NET-001 to NET-006 | 2 | Exists but not enforced |
| TC-006 | Multi-Factor Authentication | Technical | Preventive | Azure AD | 2 | M365 only - not universal |
| TC-007 | Wireless Security | Technical | Preventive | NET-009 to NET-012 | 4 | WPA3-Enterprise |
| TC-008 | VPN Remote Access | Technical | Preventive | NET-013 | 3 | FortiGate SSL VPN |
| TC-009 | Encryption at Rest | Technical | Preventive | AWS KMS, Azure Key Vault | 4 | Cloud data encrypted |
| TC-010 | Encryption in Transit | Technical | Preventive | All public services | 4 | TLS 1.2/1.3 |
| TC-011 | SIEM/Log Management | Technical | Detective | SRV-010 | 2 | Wazuh - partially deployed |
| TC-012 | Vulnerability Scanner | Technical | Detective | Security Team tools | 2 | Nessus - quarterly only |
| TC-013 | Load Balancer | Technical | Preventive (availability) | NET-014 | 4 | F5 BIG-IP |
| TC-014 | DNS Filtering | Technical | Preventive | Cloudflare | 3 | External DNS only, no internal filtering |
| TC-015 | Data Loss Prevention | Technical | Preventive, Detective | Not implemented | 1 | No DLP solution in place |

### Your Analysis - Technical Controls

**Strengths Identified:**
```
1. Strong endpoint protection with CrowdStrike Falcon provides advanced threat detection and response capabilities across all endpoints
2. High-availability firewall configuration (FortiGate 200F HA pair) ensures network perimeter resilience
3. Robust backup infrastructure with Veeam and tape storage supporting disaster recovery requirements
4. Modern wireless security using WPA3-Enterprise provides strong authentication and encryption
5. Cloud data encryption implemented with AWS KMS and Azure Key Vault following industry best practices
```

**Gaps Identified:**
```
1. MFA not enforced universally - only M365 users protected, leaving VPN and other systems vulnerable
2. SIEM (Wazuh) only partially deployed - limited visibility into security events across the environment
3. Vulnerability scanning performed quarterly only - insufficient frequency to detect emerging threats
4. No Data Loss Prevention (DLP) solution - sensitive data exfiltration risk is high
5. Network segmentation exists (VLANs) but not properly enforced - lateral movement risk remains
```

---

## A.2 Managerial Controls

| Control ID | Control Name | Category | Type(s) | Document/Location | Maturity (1-5) | Notes |
|------------|--------------|----------|---------|-------------------|----------------|-------|
| MC-001 | Information Security Policy | Managerial | Directive | Does not exist | 1 | Does not exist |
| MC-002 | Risk Assessment | Managerial | Preventive, Detective | No formal register | 1 | Ad-hoc assessments only |
| MC-003 | Security Awareness Program | Managerial | Preventive, Directive | KnowBe4 | 2 | Annual training only |
| MC-004 | Vendor Risk Management | Managerial | Preventive | No formal process | 1 | Critical vendors not assessed |
| MC-005 | Incident Response Plan | Managerial | Corrective, Directive | Does not exist | 1 | Does not exist |
| MC-006 | Business Continuity Plan | Managerial | Corrective | Informal only | 2 | Basic DR exists, no formal BCP |
| MC-007 | Change Management Policy | Managerial | Preventive, Directive | Informal process | 2 | Ad-hoc change approval |
| MC-008 | Data Classification Policy | Managerial | Directive | Scheme exists, not enforced | 2 | Classification defined but not applied |
| MC-009 | Acceptable Use Policy | Managerial | Directive, Deterrent | Does not exist | 1 | No formal AUP documented |
| MC-010 | Access Control Policy | Managerial | Directive | AD groups exist | 2 | Technical controls exist, no policy |

### Your Analysis - Managerial Controls

**Current State Assessment:**
```
NordicShield's managerial controls are significantly underdeveloped, representing the most critical gap in their security program. Key findings:

- Policies Not Documented: Most essential security policies (Information Security Policy, Acceptable Use Policy, Incident Response Plan) do not exist in formal documentation. This creates compliance and liability risks.

- No Formal Review Process: Without documented policies, there is no review cycle. ISO 27001 requires policies to be reviewed at planned intervals.

- Limited Employee Communication: Security expectations are communicated informally. Only annual KnowBe4 training exists, which is insufficient for building security culture.

- ISO 27001 Readiness Impact: This is the most significant barrier to certification. ISO 27001 requires documented policies (A.5), risk assessment processes (A.8), and incident management procedures (A.16). Current maturity is approximately 20% of required state.

- Vendor Risk Exposure: With critical vendors like AWS, Microsoft, Salesforce, and CrowdStrike handling sensitive data, the absence of formal vendor risk management creates significant third-party risk.

Immediate action required: Develop foundational ISMS documentation before ISO 27001 certification can proceed.
```

---

## A.3 Operational Controls

| Control ID | Control Name | Category | Type(s) | Frequency | Owner | Maturity (1-5) | Notes |
|------------|--------------|----------|---------|-----------|-------|----------------|-------|
| OC-001 | Patch Management | Operational | Preventive, Corrective | Ad-hoc | IT | 2 | Manual, ad-hoc |
| OC-002 | Backup Verification | Operational | Detective | Weekly | IT | 3 | Veeam reports reviewed |
| OC-003 | Log Review | Operational | Detective | Rarely | Security Team | 1 | No formal process |
| OC-004 | User Access Reviews | Operational | Detective, Corrective | Annually | HR/IT | 2 | During audit only |
| OC-005 | Security Monitoring | Operational | Detective | 24/7 (limited) | Security Team | 2 | CrowdStrike alerts only |
| OC-006 | Incident Handling | Operational | Corrective | As needed | Security Team | 1 | No formal process |
| OC-007 | Vulnerability Scanning | Operational | Detective | Quarterly | Security | 2 | Nessus |
| OC-008 | Penetration Testing | Operational | Detective | Never performed | External | 1 | Not conducted |
| OC-009 | Configuration Management | Operational | Preventive | As needed | DevOps | 3 | Ansible/Terraform |
| OC-010 | Employee Onboarding/Offboarding | Operational | Preventive | Per event | HR/IT | 3 | Checklist exists |

### Your Analysis - Operational Controls

**Process Maturity Assessment:**
```
NordicShield's operational controls show mixed maturity levels, with some areas functioning well and others critically underdeveloped:

Documentation Status:
- Backup procedures are documented and followed consistently (Veeam)
- Onboarding/offboarding has a checklist but lacks security-specific steps
- Patch management, log review, and incident handling have NO documented procedures

Consistency of Execution:
- Backup verification is consistent (weekly reviews)
- Patch management is entirely reactive - no scheduled maintenance windows
- User access reviews only happen when auditors request them
- Security monitoring is passive (waiting for CrowdStrike alerts)

Metrics and KPIs:
- No security KPIs are tracked
- No mean-time-to-detect (MTTD) or mean-time-to-respond (MTTR) metrics
- Vulnerability scan results are not tracked over time
- No patch compliance percentage measured

Automation Level:
- Configuration management uses Ansible/Terraform (good foundation)
- CI/CD pipeline exists via Azure DevOps
- No automated patch deployment
- No automated security alerting beyond CrowdStrike
- SOAR capabilities not implemented

Priority: Establish documented procedures for incident handling and patch management immediately.
```

---

## A.4 Physical Controls

| Control ID | Control Name | Category | Type(s) | Asset Reference | Location | Maturity (1-5) | Notes |
|------------|--------------|----------|---------|-----------------|----------|----------------|-------|
| PC-001 | Badge Access - Building | Physical | Preventive, Detective | SEC-001 | Turku HQ Entrance | 4 | HID iCLASS SE |
| PC-002 | Badge + PIN Access - DC | Physical | Preventive, Detective | SEC-002 | Data Center | 4 | Dual factor |
| PC-003 | CCTV Surveillance | Physical | Detective, Deterrent | SEC-004, SEC-005 | Building-wide | 4 | 24 cameras, Milestone NVR |
| PC-004 | Intrusion Detection System | Physical | Detective | SEC-006 | Building perimeter | 4 | Bosch B9512G |
| PC-005 | Secure Document Storage | Physical | Preventive | SEC-007 | Finance Office | 3 | Chubb safe |
| PC-006 | Document Destruction | Physical | Preventive | SEC-008 | Each floor | 3 | Shredders |
| PC-007 | Environmental Controls | Physical | Preventive | ENV-001, ENV-002, ENV-003 | Data Center | 4 | HVAC, fire suppression |
| PC-008 | Power Protection | Physical | Preventive | PWR-001 to PWR-004 | Data Center | 4 | UPS, generator, PDUs |
| PC-009 | Visitor Management | Physical | Preventive, Detective | Reception desk | Reception | 2 | Manual sign-in log |
| PC-010 | Security Lighting | Physical | Deterrent | Exterior fixtures | Exterior | 3 | Motion-activated lighting |

### Your Analysis - Physical Controls

**Physical Security Assessment:**
```
NordicShield's physical security at Turku HQ is relatively mature, with good defense-in-depth for the data center. Key findings:

Defense-in-Depth Implementation:
- Layer 1: Building perimeter (intrusion detection, security lighting, CCTV)
- Layer 2: Building entrance (badge access, visitor management)
- Layer 3: Office floors (badge access between zones)
- Layer 4: Data center (badge + PIN dual authentication)
- Layer 5: Server racks (physical locks assumed)

Coverage Gaps Identified:
- Visitor management is manual (no electronic system) - audit trail is weak
- Manufacturing floor (SEC-003) has badge-only access - same as general office
- No mantrap/airlock at data center entrance
- Tailgating prevention not formally addressed

Data Center Security (Strong):
- Dual-factor access control (badge + PIN)
- Environmental monitoring (temperature, humidity via NetBotz)
- FM-200 fire suppression system
- Redundant power (dual UPS, generator backup)
- Dedicated cooling (Schneider InRow)

Global Office Expansion Concerns (Critical):
- Amsterdam, Austin, Kigali offices have NO physical security planning yet
- Co-working spaces (initial plan) present significant physical security risks
- Need consistent physical security standards across all locations
- Remote data handling policies required for satellite offices

Recommendation: Develop Physical Security Standard for global offices before expansion.
```

---

# SECTION B: CONTROL GAP ANALYSIS

## B.1 Critical Gaps (High Risk)

| Gap ID | Missing Control | Category | Type | Risk if Not Addressed | Recommended Priority |
|--------|-----------------|----------|------|----------------------|---------------------|
| GAP-001 | Incident Response Plan | Managerial | Corrective | Unable to respond effectively to breaches; regulatory non-compliance (GDPR 72-hour notification); reputational damage | P1 - Immediate |
| GAP-002 | Universal MFA | Technical | Preventive | Account compromise via phishing; lateral movement; credential stuffing attacks on VPN | P1 - Immediate |
| GAP-003 | Information Security Policy | Managerial | Directive | No governance foundation; ISO 27001 certification impossible; employee behavior unguided | P1 - Immediate |
| GAP-004 | Vendor Risk Management | Managerial | Preventive | Supply chain attacks; third-party data breaches; NIS2 non-compliance | P2 - High |
| GAP-005 | Data Loss Prevention | Technical | Preventive, Detective | IP theft (cooling algorithms); customer data exfiltration; insider threats undetected | P2 - High |

## B.2 Compensating Controls

For gaps that cannot be immediately addressed, identify compensating controls:

| Gap ID | Compensating Control | Effectiveness | Duration Until Remediation |
|--------|---------------------|---------------|---------------------------|
| GAP-001 | CrowdStrike MDR service provides 24/7 monitoring and basic incident support | Medium - reactive only, no internal procedures | 30 days |
| GAP-002 | Conditional Access policies in Azure AD limit risky sign-ins; CrowdStrike monitors endpoint compromise | Medium - reduces but doesn't eliminate risk | 60 days |
| GAP-005 | Proofpoint email security blocks some data exfiltration via email; network egress monitoring via FortiGate | Low - many exfiltration paths unmonitored | 90 days |

---

# SECTION C: CONTROL MAPPING

## C.1 Control by Security Objective

Map existing controls to security objectives:

| Objective | Controls Supporting | Gaps |
|-----------|--------------------|----- |
| **Confidentiality** | TC-001 (Firewall), TC-002 (EDR), TC-006 (MFA-partial), TC-009 (Encryption at Rest), TC-010 (Encryption in Transit), PC-002 (DC Access) | No DLP, Inconsistent MFA, No data classification enforcement |
| **Integrity** | TC-002 (EDR), TC-004 (Backup), TC-009 (Encryption), OC-009 (Config Mgmt) | No file integrity monitoring, No code signing verification |
| **Availability** | TC-004 (Backup), TC-013 (Load Balancer), PC-007 (Environmental), PC-008 (Power), NET-001/002 (Redundant switches) | No formal BCP, DR not tested regularly |
| **Non-Repudiation** | TC-011 (SIEM-partial), PC-003 (CCTV), Azure AD logs | Logging incomplete, No centralized audit trail |
| **Authentication** | TC-006 (MFA-partial), TC-008 (VPN), Azure AD, PC-001/002 (Badge access) | MFA not universal, No privileged access management (PAM) |

## C.2 Control Coverage by Asset Category

| Asset Category | Preventive | Detective | Corrective | Deterrent | Coverage Score |
|----------------|------------|-----------|------------|-----------|----------------|
| Servers | TC-001, TC-005, TC-009 | TC-002, TC-011 | TC-004, OC-001 | None | 3/5 |
| Network Devices | TC-001, TC-005, TC-007 | TC-011 (partial) | OC-001 | None | 3/5 |
| End-User Devices | TC-002, TC-006 (partial) | TC-002, TC-003 | TC-002 | MC-003 | 4/5 |
| Cloud Resources | TC-009, TC-010, Azure AD | TC-002, Qualys | Backup | None | 3/5 |
| IoT Devices | TC-005 (VLAN), Gateway TLS | Limited | OTA updates | None | 2/5 |
| Data | TC-009, TC-010 | TC-003 (email only) | TC-004 | None | 2/5 |
| Personnel | MC-003, OC-010 | OC-004 (annual) | OC-006 (informal) | PC-003, PC-010 | 2/5 |

---

# SECTION D: RECOMMENDATIONS

## D.1 Immediate Actions (0-30 days)

| Priority | Recommendation | Control Type | Estimated Effort | Business Justification |
|----------|---------------|--------------|------------------|----------------------|
| 1 | Deploy universal MFA via Azure AD for all applications including VPN | Technical - Preventive | 40 hours | Blocks 99.9% of account compromise attacks; required for cyber insurance |
| 2 | Create Incident Response Plan with GDPR breach notification procedures | Managerial - Corrective | 60 hours | GDPR requires 72-hour breach notification; current state creates legal liability |
| 3 | Draft Information Security Policy and Acceptable Use Policy | Managerial - Directive | 40 hours | Foundation for ISO 27001; provides legal protection; sets employee expectations |

## D.2 Short-Term Actions (30-90 days)

| Priority | Recommendation | Control Type | Estimated Effort | Business Justification |
|----------|---------------|--------------|------------------|----------------------|
| 1 | Fully deploy Wazuh SIEM with log collection from all critical assets | Technical - Detective | 80 hours | Enables threat detection; required for NIS2 compliance; supports incident investigation |
| 2 | Implement automated patch management with WSUS/Intune for Windows, Ansible for Linux | Operational - Preventive | 60 hours | Reduces vulnerability window; enables compliance reporting; reduces IT workload |
| 3 | Establish Vendor Risk Management program starting with critical vendors | Managerial - Preventive | 50 hours | Addresses supply chain risk; required for ISO 27001 Annex A.15; protects customer data |

## D.3 Long-Term Actions (90+ days)

| Priority | Recommendation | Control Type | Estimated Effort | Business Justification |
|----------|---------------|--------------|------------------|----------------------|
| 1 | Implement Zero Trust Network Architecture with micro-segmentation | Technical - Preventive | 200 hours | Limits lateral movement; supports remote workforce; enables secure global expansion |
| 2 | Deploy Data Loss Prevention across endpoints, email, and cloud | Technical - Preventive, Detective | 120 hours | Protects intellectual property (cooling algorithms); prevents data breaches; enables classification enforcement |
| 3 | Conduct first penetration test and establish annual testing program | Operational - Detective | External vendor + 40 hours | Validates control effectiveness; identifies unknown vulnerabilities; required for SOC 2 |

---

# SECTION E: EXECUTIVE SUMMARY

```
SECURITY CONTROLS ASSESSMENT - EXECUTIVE SUMMARY

Overall Control Posture Rating: 2.4/5 (Developing)

NordicShield Technologies has established foundational technical security controls, 
particularly in endpoint protection (CrowdStrike), perimeter security (FortiGate), 
and backup/recovery (Veeam). These provide a reasonable baseline for a company of 
this size.

Key Strengths:
- Strong endpoint detection and response capability
- Robust physical security at Turku HQ data center
- Modern encryption standards for data at rest and in transit
- Established configuration management with Ansible/Terraform

Critical Gaps Requiring Immediate Attention:
1. No Incident Response Plan - creates GDPR compliance risk
2. Inconsistent MFA deployment - significant account compromise exposure
3. Missing foundational security policies - blocks ISO 27001 certification
4. No vendor risk management - supply chain vulnerability

ISO 27001 Certification Impact:
Current state meets approximately 35% of ISO 27001 requirements. Primary blockers 
are documentation gaps (Annex A.5, A.7, A.8) and operational process immaturity 
(A.12, A.16). Estimated 12-15 months to certification readiness with dedicated effort.

Top 3 Recommendations:
1. IMMEDIATE: Deploy universal MFA and create Incident Response Plan
2. 30-90 DAYS: Complete SIEM deployment and establish policy framework
3. 90+ DAYS: Implement Zero Trust architecture for global expansion

Prepared by: Precious Robert, Security Analyst
Date: January 31, 2026
```

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 1.1 - Security Controls Matrix |
| **Phase** | 1 - General Security Concepts |
| **Exam Objective** | 1.1 - Compare and contrast various types of security controls |
| **Status** | ✅ Complete |
| **Completed By** | Precious Robert |
| **Completion Date** | January 31, 2026 |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
