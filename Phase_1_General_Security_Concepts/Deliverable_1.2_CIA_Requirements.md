# Deliverable 1.2: CIA Requirements Document
## NordicShield Technologies Oy

---

## Document Purpose

This document maps NordicShield's critical business processes, data assets, and systems to Confidentiality, Integrity, and Availability (CIA) requirements. It establishes security baselines and identifies where current controls meet or fall short of requirements.

---

## Instructions

1. Analyze each business function and its CIA requirements
2. Rate requirements as: **Critical** | **High** | **Medium** | **Low**
3. Fill in all `[YOUR INPUT]` sections
4. Justify your ratings based on business impact

---

# SECTION A: CIA TRIAD OVERVIEW

## A.1 Understanding CIA for NordicShield

| Principle | Definition | NordicShield Context |
|-----------|------------|---------------------|
| **Confidentiality** | Ensuring data is accessible only to authorized parties | Protecting trade secrets (cooling algorithms), customer data, employee PII |
| **Integrity** | Ensuring data is accurate, complete, and unaltered | IoT sensor data accuracy, financial records, source code |
| **Availability** | Ensuring systems and data are accessible when needed | 24/7 monitoring platform, customer portal, global operations |

## A.2 Additional Security Principles

| Principle | Definition | Relevance to NordicShield |
|-----------|------------|--------------------------|
| **Non-Repudiation** | Inability to deny an action | Contract signing, audit logs, transaction records |
| **Authentication** | Verifying identity | User access, IoT device identity, API authentication |
| **Authorization** | Granting appropriate access | Role-based access, least privilege |

---

# SECTION B: BUSINESS FUNCTION CIA MAPPING

## B.1 Core Business Functions

### B.1.1 IoT Monitoring Platform (NordicSense)

| Attribute | Requirement Level | Justification | Current State | Gap? |
|-----------|------------------|---------------|---------------|------|
| **Confidentiality** | [YOUR INPUT] | [YOUR INPUT - Why this level? Consider: customer data, competitive advantage] | [YOUR INPUT] | [YOUR INPUT] |
| **Integrity** | [YOUR INPUT] | [YOUR INPUT - Why this level? Consider: sensor data accuracy, business decisions based on data] | [YOUR INPUT] | [YOUR INPUT] |
| **Availability** | [YOUR INPUT] | [YOUR INPUT - Why this level? Consider: 24/7 monitoring, SLA commitments] | [YOUR INPUT] | [YOUR INPUT] |

**Impact Analysis:**
```
[YOUR INPUT - What happens if CIA is compromised for this function?]

Confidentiality Breach: 
Integrity Failure:
Availability Outage:
```

### B.1.2 Cooling Hardware Manufacturing

| Attribute | Requirement Level | Justification | Current State | Gap? |
|-----------|------------------|---------------|---------------|------|
| **Confidentiality** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Integrity** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Availability** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### B.1.3 Customer Support Operations

| Attribute | Requirement Level | Justification | Current State | Gap? |
|-----------|------------------|---------------|---------------|------|
| **Confidentiality** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Integrity** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Availability** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### B.1.4 Sales & CRM

| Attribute | Requirement Level | Justification | Current State | Gap? |
|-----------|------------------|---------------|---------------|------|
| **Confidentiality** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Integrity** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Availability** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### B.1.5 Research & Development

| Attribute | Requirement Level | Justification | Current State | Gap? |
|-----------|------------------|---------------|---------------|------|
| **Confidentiality** | [YOUR INPUT] | [YOUR INPUT - Consider: trade secrets, competitive advantage, IP theft by nation-states] | [YOUR INPUT] | [YOUR INPUT] |
| **Integrity** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Availability** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### B.1.6 Finance & Accounting

| Attribute | Requirement Level | Justification | Current State | Gap? |
|-----------|------------------|---------------|---------------|------|
| **Confidentiality** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Integrity** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Availability** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### B.1.7 Human Resources

| Attribute | Requirement Level | Justification | Current State | Gap? |
|-----------|------------------|---------------|---------------|------|
| **Confidentiality** | [YOUR INPUT] | [YOUR INPUT - Consider: GDPR, employee PII] | [YOUR INPUT] | [YOUR INPUT] |
| **Integrity** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Availability** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION C: DATA ASSET CIA REQUIREMENTS

## C.1 Data Classification to CIA Mapping

Reference the Data Classification from Company Profile and map to CIA:

| Data Category | Classification | C Level | I Level | A Level | Justification |
|---------------|---------------|---------|---------|---------|---------------|
| Cooling Algorithm IP | RESTRICTED | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Source Code | RESTRICTED | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Customer Contact Info | REGULATED | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Employee PII | REGULATED | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Telemetry Data | CONFIDENTIAL | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Financial Records | CONFIDENTIAL | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Customer Contracts | CONFIDENTIAL | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Security Logs | CONFIDENTIAL | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Marketing Content | PUBLIC/INTERNAL | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| R&D Documentation | RESTRICTED | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## C.2 Data Location and Protection Analysis

| Data Asset | Primary Location | Backup Location | Encryption at Rest | Encryption in Transit | Access Controls |
|------------|-----------------|-----------------|-------------------|----------------------|-----------------|
| Cooling Algorithm IP | Air-gapped system | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Source Code | GitHub Enterprise | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Customer Data | Salesforce | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Telemetry | AWS Timestream/S3 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Financial Records | NetSuite | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Employee PII | Workday | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION D: SYSTEM CIA REQUIREMENTS

## D.1 Critical Systems Analysis

### On-Premises Systems

| System | Asset ID | C Level | I Level | A Level | RTO | RPO | Current Controls |
|--------|----------|---------|---------|---------|-----|-----|------------------|
| Primary DC | SRV-001 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Secondary DC | SRV-002 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| File Server | SRV-003 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Database Server | SRV-004 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| SIEM Server | SRV-010 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Cloud Systems

| System | Platform | C Level | I Level | A Level | RTO | RPO | Current Controls |
|--------|----------|---------|---------|---------|-----|-----|------------------|
| Production Apps | AWS eu-north-1 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Platform | AWS IoT Core | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| DR Environment | AWS eu-west-1 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Corporate Services | Azure/M365 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### IoT/OT Systems

| System | Quantity | C Level | I Level | A Level | Special Considerations |
|--------|----------|---------|---------|---------|----------------------|
| Temperature Sensors | 280 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Cooling Controllers | 45 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - Safety critical?] |
| Gateway Devices | 52 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION E: GLOBAL EXPANSION CIA CONSIDERATIONS

## E.1 Regional Office Requirements

Consider how CIA requirements differ across regions:

| Region | Office | Special Confidentiality Needs | Special Integrity Needs | Special Availability Needs |
|--------|--------|------------------------------|------------------------|---------------------------|
| Finland | Turku HQ | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Netherlands | Amsterdam | [YOUR INPUT - GDPR, Dutch DPA] | [YOUR INPUT] | [YOUR INPUT] |
| USA | Austin | [YOUR INPUT - CCPA, state laws] | [YOUR INPUT] | [YOUR INPUT] |
| Rwanda | Kigali | [YOUR INPUT - Data localization] | [YOUR INPUT] | [YOUR INPUT - Internet reliability?] |

## E.2 Cross-Border Data Transfer

| Data Type | Transfer Path | Confidentiality Requirement | Legal Mechanism Needed |
|-----------|---------------|----------------------------|----------------------|
| Employee PII | Turku ↔ Amsterdam | [YOUR INPUT] | [YOUR INPUT - SCCs? Adequacy?] |
| Customer Data | Turku ↔ Austin | [YOUR INPUT] | [YOUR INPUT] |
| Support Data | All regions ↔ Kigali | [YOUR INPUT] | [YOUR INPUT] |
| IoT Telemetry | Client sites → AWS Stockholm | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION F: CIA REQUIREMENTS SUMMARY MATRIX

## F.1 Overall Requirements Matrix

Create a heat map of CIA requirements:

| Asset/Function | Confidentiality | Integrity | Availability | Overall Criticality |
|----------------|-----------------|-----------|--------------|---------------------|
| Cooling Algorithm IP | [C/H/M/L] | [C/H/M/L] | [C/H/M/L] | [YOUR INPUT] |
| IoT Monitoring Platform | [C/H/M/L] | [C/H/M/L] | [C/H/M/L] | [YOUR INPUT] |
| Customer Database | [C/H/M/L] | [C/H/M/L] | [C/H/M/L] | [YOUR INPUT] |
| Financial Systems | [C/H/M/L] | [C/H/M/L] | [C/H/M/L] | [YOUR INPUT] |
| HR Systems | [C/H/M/L] | [C/H/M/L] | [C/H/M/L] | [YOUR INPUT] |
| R&D Systems | [C/H/M/L] | [C/H/M/L] | [C/H/M/L] | [YOUR INPUT] |
| Email System | [C/H/M/L] | [C/H/M/L] | [C/H/M/L] | [YOUR INPUT] |
| Website/Marketing | [C/H/M/L] | [C/H/M/L] | [C/H/M/L] | [YOUR INPUT] |

**Legend:** C = Critical | H = High | M = Medium | L = Low

---

# SECTION G: GAP ANALYSIS & RECOMMENDATIONS

## G.1 Confidentiality Gaps

| Gap | Current State | Required State | Risk | Recommendation |
|-----|---------------|----------------|------|----------------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## G.2 Integrity Gaps

| Gap | Current State | Required State | Risk | Recommendation |
|-----|---------------|----------------|------|----------------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## G.3 Availability Gaps

| Gap | Current State | Required State | Risk | Recommendation |
|-----|---------------|----------------|------|----------------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION H: CONTROLS TO SUPPORT CIA

## H.1 Recommended Controls by CIA Objective

### Confidentiality Controls

| Control | Purpose | Priority | Estimated Effort |
|---------|---------|----------|------------------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Integrity Controls

| Control | Purpose | Priority | Estimated Effort |
|---------|---------|----------|------------------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Availability Controls

| Control | Purpose | Priority | Estimated Effort |
|---------|---------|----------|------------------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION I: EXECUTIVE SUMMARY

```
[YOUR INPUT - Write a 150-250 word executive summary]

Include:
- Overall CIA posture assessment
- Most critical CIA requirements for the business
- Biggest gaps between requirements and current state
- Impact of global expansion on CIA requirements
- Priority recommendations
```

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 1.2 - CIA Requirements Document |
| **Phase** | 1 - General Security Concepts |
| **Exam Objective** | 1.2 - Summarize fundamental security concepts |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
