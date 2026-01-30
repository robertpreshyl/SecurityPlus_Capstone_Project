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
| TC-007 | Wireless Security | Technical | Preventive | NET-009 to NET-012 | [YOUR INPUT] | WPA3-Enterprise |
| TC-008 | VPN Remote Access | Technical | Preventive | NET-013 | [YOUR INPUT] | FortiGate SSL VPN |
| TC-009 | Encryption at Rest | Technical | Preventive | AWS KMS, Azure Key Vault | [YOUR INPUT] | Cloud data encrypted |
| TC-010 | Encryption in Transit | Technical | Preventive | All public services | [YOUR INPUT] | TLS 1.2/1.3 |
| TC-011 | SIEM/Log Management | Technical | Detective | SRV-010 | [YOUR INPUT] | Wazuh - partially deployed |
| TC-012 | Vulnerability Scanner | Technical | Detective | Security Team tools | [YOUR INPUT] | Nessus - quarterly only |
| TC-013 | Load Balancer | Technical | Preventive (availability) | NET-014 | [YOUR INPUT] | F5 BIG-IP |
| TC-014 | DNS Filtering | Technical | Preventive | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| TC-015 | Data Loss Prevention | Technical | Preventive, Detective | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Your Analysis - Technical Controls

**Strengths Identified:**
```
[YOUR INPUT - List 3-5 strengths of current technical controls]

Example:
1. Strong endpoint protection with CrowdStrike provides advanced threat detection
2. ...
```

**Gaps Identified:**
```
[YOUR INPUT - List 3-5 gaps in technical controls]

Example:
1. MFA not enforced universally - only M365 users protected
2. ...
```

---

## A.2 Managerial Controls

| Control ID | Control Name | Category | Type(s) | Document/Location | Maturity (1-5) | Notes |
|------------|--------------|----------|---------|-------------------|----------------|-------|
| MC-001 | Information Security Policy | Managerial | Directive | [YOUR INPUT] | 1 | Does not exist |
| MC-002 | Risk Assessment | Managerial | Preventive, Detective | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| MC-003 | Security Awareness Program | Managerial | Preventive, Directive | KnowBe4 | 2 | Annual training only |
| MC-004 | Vendor Risk Management | Managerial | Preventive | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| MC-005 | Incident Response Plan | Managerial | Corrective, Directive | [YOUR INPUT] | 1 | Does not exist |
| MC-006 | Business Continuity Plan | Managerial | Corrective | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| MC-007 | Change Management Policy | Managerial | Preventive, Directive | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| MC-008 | Data Classification Policy | Managerial | Directive | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| MC-009 | Acceptable Use Policy | Managerial | Directive, Deterrent | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| MC-010 | Access Control Policy | Managerial | Directive | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Your Analysis - Managerial Controls

**Current State Assessment:**
```
[YOUR INPUT - Describe the overall state of managerial controls at NordicShield]

Consider:
- Are policies documented?
- When were they last reviewed?
- Are they communicated to employees?
- How does this impact ISO 27001 readiness?
```

---

## A.3 Operational Controls

| Control ID | Control Name | Category | Type(s) | Frequency | Owner | Maturity (1-5) | Notes |
|------------|--------------|----------|---------|-----------|-------|----------------|-------|
| OC-001 | Patch Management | Operational | Preventive, Corrective | [YOUR INPUT] | IT | 2 | Manual, ad-hoc |
| OC-002 | Backup Verification | Operational | Detective | [YOUR INPUT] | IT | [YOUR INPUT] | [YOUR INPUT] |
| OC-003 | Log Review | Operational | Detective | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| OC-004 | User Access Reviews | Operational | Detective, Corrective | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| OC-005 | Security Monitoring | Operational | Detective | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| OC-006 | Incident Handling | Operational | Corrective | [YOUR INPUT] | [YOUR INPUT] | 1 | No formal process |
| OC-007 | Vulnerability Scanning | Operational | Detective | Quarterly | Security | 2 | Nessus |
| OC-008 | Penetration Testing | Operational | Detective | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| OC-009 | Configuration Management | Operational | Preventive | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | Ansible/Terraform |
| OC-010 | Employee Onboarding/Offboarding | Operational | Preventive | [YOUR INPUT] | HR/IT | [YOUR INPUT] | [YOUR INPUT] |

### Your Analysis - Operational Controls

**Process Maturity Assessment:**
```
[YOUR INPUT - Evaluate the maturity of operational processes]

Consider:
- Are processes documented?
- Are they consistently followed?
- Are there metrics/KPIs?
- What automation exists?
```

---

## A.4 Physical Controls

| Control ID | Control Name | Category | Type(s) | Asset Reference | Location | Maturity (1-5) | Notes |
|------------|--------------|----------|---------|-----------------|----------|----------------|-------|
| PC-001 | Badge Access - Building | Physical | Preventive, Detective | SEC-001 | Turku HQ Entrance | [YOUR INPUT] | HID iCLASS SE |
| PC-002 | Badge + PIN Access - DC | Physical | Preventive, Detective | SEC-002 | Data Center | [YOUR INPUT] | Dual factor |
| PC-003 | CCTV Surveillance | Physical | Detective, Deterrent | SEC-004, SEC-005 | Building-wide | [YOUR INPUT] | 24 cameras, Milestone NVR |
| PC-004 | Intrusion Detection System | Physical | Detective | SEC-006 | Building perimeter | [YOUR INPUT] | Bosch B9512G |
| PC-005 | Secure Document Storage | Physical | Preventive | SEC-007 | Finance Office | [YOUR INPUT] | Chubb safe |
| PC-006 | Document Destruction | Physical | Preventive | SEC-008 | Each floor | [YOUR INPUT] | Shredders |
| PC-007 | Environmental Controls | Physical | Preventive | ENV-001, ENV-002, ENV-003 | Data Center | [YOUR INPUT] | HVAC, fire suppression |
| PC-008 | Power Protection | Physical | Preventive | PWR-001 to PWR-004 | Data Center | [YOUR INPUT] | UPS, generator, PDUs |
| PC-009 | Visitor Management | Physical | Preventive, Detective | [YOUR INPUT] | Reception | [YOUR INPUT] | [YOUR INPUT] |
| PC-010 | Security Lighting | Physical | Deterrent | [YOUR INPUT] | Exterior | [YOUR INPUT] | [YOUR INPUT] |

### Your Analysis - Physical Controls

**Physical Security Assessment:**
```
[YOUR INPUT - Evaluate physical security posture]

Consider:
- Is defense-in-depth implemented?
- Are there gaps in coverage?
- How do physical controls support data center security?
- What about the new global offices (Amsterdam, Austin, Kigali)?
```

---

# SECTION B: CONTROL GAP ANALYSIS

## B.1 Critical Gaps (High Risk)

| Gap ID | Missing Control | Category | Type | Risk if Not Addressed | Recommended Priority |
|--------|-----------------|----------|------|----------------------|---------------------|
| GAP-001 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| GAP-002 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| GAP-003 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| GAP-004 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| GAP-005 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## B.2 Compensating Controls

For gaps that cannot be immediately addressed, identify compensating controls:

| Gap ID | Compensating Control | Effectiveness | Duration Until Remediation |
|--------|---------------------|---------------|---------------------------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION C: CONTROL MAPPING

## C.1 Control by Security Objective

Map existing controls to security objectives:

| Objective | Controls Supporting | Gaps |
|-----------|--------------------|----- |
| **Confidentiality** | [YOUR INPUT] | [YOUR INPUT] |
| **Integrity** | [YOUR INPUT] | [YOUR INPUT] |
| **Availability** | [YOUR INPUT] | [YOUR INPUT] |
| **Non-Repudiation** | [YOUR INPUT] | [YOUR INPUT] |
| **Authentication** | [YOUR INPUT] | [YOUR INPUT] |

## C.2 Control Coverage by Asset Category

| Asset Category | Preventive | Detective | Corrective | Deterrent | Coverage Score |
|----------------|------------|-----------|------------|-----------|----------------|
| Servers | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT]/5 |
| Network Devices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT]/5 |
| End-User Devices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT]/5 |
| Cloud Resources | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT]/5 |
| IoT Devices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT]/5 |
| Data | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT]/5 |
| Personnel | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT]/5 |

---

# SECTION D: RECOMMENDATIONS

## D.1 Immediate Actions (0-30 days)

| Priority | Recommendation | Control Type | Estimated Effort | Business Justification |
|----------|---------------|--------------|------------------|----------------------|
| 1 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 2 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 3 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## D.2 Short-Term Actions (30-90 days)

| Priority | Recommendation | Control Type | Estimated Effort | Business Justification |
|----------|---------------|--------------|------------------|----------------------|
| 1 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 2 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 3 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## D.3 Long-Term Actions (90+ days)

| Priority | Recommendation | Control Type | Estimated Effort | Business Justification |
|----------|---------------|--------------|------------------|----------------------|
| 1 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 2 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 3 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION E: EXECUTIVE SUMMARY

```
[YOUR INPUT - Write a 150-250 word executive summary for the CISO]

Include:
- Overall control posture rating (1-5)
- Key strengths
- Critical gaps requiring immediate attention
- Impact on ISO 27001 certification goals
- Top 3 recommendations
```

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 1.1 - Security Controls Matrix |
| **Phase** | 1 - General Security Concepts |
| **Exam Objective** | 1.1 - Compare and contrast various types of security controls |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
