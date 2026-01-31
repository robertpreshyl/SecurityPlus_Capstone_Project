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
| **Confidentiality** | High | Customer telemetry data includes facility layouts, operational patterns, energy usage - competitive intelligence risk if breached | Medium | Yes - No DLP, partial SIEM |
| **Integrity** | Critical | Cooling decisions based on sensor data; false data could cause equipment failure, downtime, or safety incidents at client sites | High | Minor gap - No FIM on IoT gateways |
| **Availability** | Critical | 24/7 SLA commitments to customers; platform downtime = client data center cooling failures = potential multi-million € liability | High | Minor gap - DR not regularly tested |

**Impact Analysis:**
```
Confidentiality Breach: 
- Customer operational data exposed to competitors
- GDPR violations (€20M or 4% revenue fine)
- Contract terminations, reputational damage

Integrity Failure:
- False temperature readings cause incorrect cooling adjustments
- Client equipment overheating → downtime → SLA penalties
- Safety incidents if critical systems fail

Availability Outage:
- Customers lose real-time monitoring capability
- Cannot adjust cooling = energy waste or equipment risk
- SLA breach penalties (~€5K-50K per hour per client)
- 47 client sites affected simultaneously
```

### B.1.2 Cooling Hardware Manufacturing

| Attribute | Requirement Level | Justification | Current State | Gap? |
|-----------|------------------|---------------|---------------|------|
| **Confidentiality** | Medium | Manufacturing process details and supplier information moderately sensitive but not core IP | Medium | No - Adequate physical/network controls |
| **Integrity** | High | Quality control data must be accurate; incorrect specs = faulty products = safety risk and warranty claims | Medium | Yes - No automated QA verification |
| **Availability** | Medium | Manufacturing downtime impacts revenue but not immediately critical; can reschedule production | Medium | No - Acceptable downtime tolerance |

### B.1.3 Customer Support Operations

| Attribute | Requirement Level | Justification | Current State | Gap? |
|-----------|------------------|---------------|---------------|------|
| **Confidentiality** | High | Access to customer credentials, site access codes, network diagrams for troubleshooting | Medium | Yes - No DLP on support systems |
| **Integrity** | High | Support ticket records create audit trail; false entries = liability in disputes | Medium | Yes - No logging of ticket modifications |
| **Availability** | High | 24/7 support for critical clients; extended outages = SLA violations | Medium | Yes - Kigali expansion introduces timezone coverage gaps |

### B.1.4 Sales & CRM

| Attribute | Requirement Level | Justification | Current State | Gap? |
|-----------|------------------|---------------|---------------|------|
| **Confidentiality** | High | Customer contacts, pricing negotiations, pipeline data = competitive intelligence; GDPR-protected PII | High | Minor - Salesforce encryption enabled |
| **Integrity** | High | Revenue forecasting depends on accurate pipeline data; contract terms must be exact | High | No - Salesforce audit logs active |
| **Availability** | Medium | Sales can work offline temporarily; not immediately business-critical | High | No - Salesforce 99.9% SLA acceptable |

### B.1.5 Research & Development

| Attribute | Requirement Level | Justification | Current State | Gap? |
|-----------|------------------|---------------|---------------|------|
| **Confidentiality** | Critical | Cooling algorithm IP is company crown jewel; nation-state actors target cleantech; loss = loss of competitive advantage worth €15M+ Series B valuation | Medium | YES - Air-gapped system exists but no formal IP protection program |
| **Integrity** | Critical | Algorithm accuracy directly impacts product performance; tampering could sabotage products in field | Medium | Yes - No code signing, limited version control audit |
| **Availability** | Medium | R&D can tolerate short outages; affects innovation speed but not immediate operations | Medium | No - Acceptable for R&D workflow |

### B.1.6 Finance & Accounting

| Attribute | Requirement Level | Justification | Current State | Gap? |
|-----------|------------------|---------------|---------------|------|
| **Confidentiality** | Critical | Financial records = investor information, M&A data, bank details; regulatory requirement (Bookkeeping Act) | High | Minor - NetSuite encryption, access controls |
| **Integrity** | Critical | Financial data accuracy legally mandated; errors = audit failures, investor loss of confidence, potential fraud liability | High | No - Strong controls in NetSuite |
| **Availability** | High | Month-end close, payroll, invoicing time-sensitive; regulatory reporting deadlines | High | No - NetSuite 99.5% SLA acceptable |

### B.1.7 Human Resources

| Attribute | Requirement Level | Justification | Current State | Gap? |
|-----------|------------------|---------------|---------------|------|
| **Confidentiality** | Critical | GDPR Article 9 special category data (health); employment contracts; salary data = legal requirement + employee trust | High | Minor - Workday encryption enabled |
| **Integrity** | High | Payroll accuracy critical; benefit enrollment errors = financial/legal liability | High | No - Workday controls adequate |
| **Availability** | Medium | Payroll disruption serious but can be processed manually/delayed if needed | High | No - Workday SLA acceptable |

---

# SECTION C: DATA ASSET CIA REQUIREMENTS

## C.1 Data Classification to CIA Mapping

Reference the Data Classification from Company Profile and map to CIA:

| Data Category | Classification | C Level | I Level | A Level | Justification |
|---------------|---------------|---------|---------|---------|---------------|
| Cooling Algorithm IP | RESTRICTED | Critical | Critical | Medium | Core competitive advantage; tampering detection critical; R&D can tolerate brief outages |
| Source Code | RESTRICTED | Critical | Critical | Medium | IP protection; build integrity critical; dev workflow accepts some downtime |
| Customer Contact Info | REGULATED | Critical | High | Medium | GDPR mandates; data accuracy important; sales can work offline briefly |
| Employee PII | REGULATED | Critical | High | Medium | GDPR Article 9 special category; payroll accuracy critical; HR tolerates limited downtime |
| IoT Telemetry Data | CONFIDENTIAL | High | Critical | Critical | Customer competitive data; sensor accuracy = safety; 24/7 monitoring SLA |
| Financial Records | CONFIDENTIAL | Critical | Critical | High | Regulatory requirement; audit trail integrity; quarterly reporting deadlines |
| Customer Contracts | CONFIDENTIAL | High | Critical | Medium | Business-sensitive; contract terms must be exact; can retrieve from backups if needed |
| Security Logs | CONFIDENTIAL | High | Critical | High | Incident investigation; tamper-proof logging required; investigation delays acceptable |
| Marketing Content | PUBLIC/INTERNAL | Low | Medium | Medium | Public-facing data; accuracy matters for brand; website downtime tolerable |
| R&D Documentation | RESTRICTED | Critical | High | Medium | Trade secrets; design accuracy important; R&D process tolerates delays |

## C.2 Data Location and Protection Analysis

| Data Asset | Primary Location | Backup Location | Encryption at Rest | Encryption in Transit | Access Controls |
|------------|-----------------|-----------------|-------------------|----------------------|-----------------|
| Cooling Algorithm IP | Air-gapped system | Encrypted tape in safe | AES-256 (assumed) | N/A (air-gapped) | Physical + badge + PIN |
| Source Code | GitHub Enterprise | AWS S3 (encrypted) | AES-256 (GitHub) | TLS 1.3 | MFA + branch protection |
| Customer Data | Salesforce | Salesforce backup | AES-256 (Salesforce) | TLS 1.2 | SSO + Conditional Access |
| IoT Telemetry | AWS Timestream/S3 | S3 cross-region replication | AES-256 (KMS) | TLS 1.3 + MQTT TLS | IAM + device certificates |
| Financial Records | NetSuite | NetSuite backup | AES-256 (NetSuite) | TLS 1.2 | Role-based, dual approval |
| Employee PII | Workday | Workday backup | AES-256 (Workday) | TLS 1.2 | RBAC + HR/Manager access only |

---

# SECTION D: SYSTEM CIA REQUIREMENTS

## D.1 Critical Systems Analysis

### On-Premises Systems

| System | Asset ID | C Level | I Level | A Level | RTO | RPO | Current Controls |
|--------|----------|---------|---------|---------|-----|-----|------------------|
| Primary DC | SRV-001 | Critical | High | Critical | 1 hour | 15 min | HA failover, badge+PIN, encrypted |
| Secondary DC | SRV-002 | Critical | High | Critical | 1 hour | 15 min | HA failover, badge+PIN, encrypted |
| File Server | SRV-003 | High | High | High | 4 hours | 1 hour | RAID, Veeam backup, ACLs |
| Database Server | SRV-004 | Critical | Critical | Critical | 1 hour | 15 min | SQL HA, TDE, backup, audit logs |
| SIEM Server | SRV-010 | High | Critical | High | 8 hours | 4 hours | Wazuh, log integrity, limited deploy |

### Cloud Systems

| System | Platform | C Level | I Level | A Level | RTO | RPO | Current Controls |
|--------|----------|---------|---------|---------|-----|-----|------------------|
| Production Apps | AWS eu-north-1 | High | High | Critical | 2 hours | 30 min | KMS encryption, Multi-AZ, ELB, IAM |
| IoT Platform | AWS IoT Core | High | Critical | Critical | 1 hour | 15 min | Device certs, TLS, Timestream, CloudWatch |
| DR Environment | AWS eu-west-1 | High | High | High | 4 hours | 1 hour | Cross-region replication, S3 versioning |
| Corporate Services | Azure/M365 | High | High | High | 4 hours | N/A | Azure AD, Conditional Access, M365 encryption |

### IoT/OT Systems

| System | Quantity | C Level | I Level | A Level | Special Considerations |
|--------|----------|---------|---------|---------|----------------------|
| Temperature Sensors | 280 | Medium | Critical | Critical | Integrity = safety; false readings = equipment damage; 24/7 monitoring SLA |
| Cooling Controllers | 45 | Medium | Critical | Critical | SAFETY CRITICAL - controls physical HVAC; tampering = life safety risk at data centers |
| Gateway Devices | 52 | High | High | Critical | Entry point to customer networks; compromise = pivot point; customer trust impact |

---

# SECTION E: GLOBAL EXPANSION CIA CONSIDERATIONS

## E.1 Regional Office Requirements

Consider how CIA requirements differ across regions:

| Region | Office | Special Confidentiality Needs | Special Integrity Needs | Special Availability Needs |
|--------|--------|------------------------------|------------------------|---------------------------|
| Finland | Turku HQ | Core IP remains in Finland; data sovereignty for Finnish clients; GDPR compliant | Financial reporting to Finnish authorities; EU regulatory compliance | Mission-critical HQ; all systems must remain available |
| Netherlands | Amsterdam | GDPR + Dutch DPA requirements; Schrems II considerations for US data transfers | Dutch commercial law; contract integrity | EU timezone business hours critical; no 24/7 requirement |
| USA | Austin | CCPA applies to California customers; potential state breach notification laws | SOC 2 audit requirements for US enterprise clients | US timezone coverage; 9-5 CST minimum |
| Rwanda | Kigali | Rwanda Data Protection Act; lower threat profile but insider risk in shared facilities | Call center QA; support ticket accuracy | Internet reliability concerns; backup satellite link may be needed |

## E.2 Cross-Border Data Transfer

| Data Type | Transfer Path | Confidentiality Requirement | Legal Mechanism Needed |
|-----------|---------------|----------------------------|----------------------|
| Employee PII | Turku ↔ Amsterdam | Critical | EU adequacy decision applies; GDPR Article 88 employment data rules |
| Customer Data | Turku ↔ Austin | Critical | Standard Contractual Clauses (SCCs) + supplementary measures; Schrems II compliant |
| Support Data | All regions ↔ Kigali | High | Rwanda-EU data transfer assessment needed; may require SCCs |
| IoT Telemetry | Client sites → AWS Stockholm | High | GDPR Article 44 applies; AWS GDPR DPA covers this; customer contracts must specify EU-only storage |

---

# SECTION F: CIA REQUIREMENTS SUMMARY MATRIX

## F.1 Overall Requirements Matrix

Create a heat map of CIA requirements:

| Asset/Function | Confidentiality | Integrity | Availability | Overall Criticality |
|----------------|-----------------|-----------|--------------|---------------------|
| Cooling Algorithm IP | C | C | M | **CRITICAL** |
| IoT Monitoring Platform | H | C | C | **CRITICAL** |
| Customer Database | H | H | M | **HIGH** |
| Financial Systems | C | C | H | **CRITICAL** |
| HR Systems | C | H | M | **HIGH** |
| R&D Systems | C | C | M | **CRITICAL** |
| Email System | H | M | H | **HIGH** |
| Website/Marketing | L | M | M | **MEDIUM** |

**Legend:** C = Critical | H = High | M = Medium | L = Low

---

# SECTION G: GAP ANALYSIS & RECOMMENDATIONS

## G.1 Confidentiality Gaps

| Gap | Current State | Required State | Risk | Recommendation |
|-----|---------------|----------------|------|----------------|
| No DLP solution | Data can leave via email, USB, cloud without detection | Prevent/detect data exfiltration of RESTRICTED/REGULATED data | High - IP theft, GDPR breach | Implement DLP (endpoints, email, cloud) - Priority 1 |
| Inconsistent MFA | Only M365 has MFA; VPN, AWS, GitHub use passwords only | MFA on all systems accessing CONFIDENTIAL+ data | High - Account compromise | Universal MFA deployment - Priority 1 |
| No IP protection program | Cooling algorithm on air-gapped system but no formal protection | Documented IP handling, NDAs, compartmentalization | High - Loss of competitive advantage | Create IP Protection Policy - Priority 2 |

## G.2 Integrity Gaps

| Gap | Current State | Required State | Risk | Recommendation |
|-----|---------------|----------------|------|----------------|
| No FIM on IoT gateways | File changes on NS-GW-1000 devices unmonitored | Real-time file integrity monitoring on all gateways | Critical - Malware could alter sensor data | Deploy Wazuh FIM module - Priority 1 |
| No code signing | Software updates to IoT devices not cryptographically verified | Digital signatures on all firmware/software | High - Supply chain attack, malware | Implement code signing infrastructure - Priority 2 |
| Support ticket audit gaps | Ticket modifications not logged in detail | Immutable audit trail of all ticket changes | Medium - Dispute liability | Enable comprehensive Jira audit logging - Priority 3 |

## G.3 Availability Gaps

| Gap | Current State | Required State | Risk | Recommendation |
|-----|---------------|----------------|------|----------------|
| DR not regularly tested | DR environment exists but last test unknown | Quarterly DR failover tests with documented results | High - DR may not work when needed | Establish DR testing schedule - Priority 1 |
| Single AWS region for prod | All production in eu-north-1 | Multi-region active-active or hot standby | High - Region outage = total platform failure | Design multi-region architecture - Priority 2 |
| No formal BCP | Disaster recovery focuses on IT; no business process continuity | Business Continuity Plan covering all critical functions | Medium - Uncoordinated recovery efforts | Develop BCP document - Priority 3 |

---

# SECTION H: CONTROLS TO SUPPORT CIA

## H.1 Recommended Controls by CIA Objective

### Confidentiality Controls

| Control | Purpose | Priority | Estimated Effort |
|---------|---------|----------|------------------|
| DLP Solution (Endpoint, Email, Cloud) | Prevent exfiltration of RESTRICTED/REGULATED data; detect anomalous data transfers | **Priority 1** | 3-4 months (vendor selection, deployment, tuning) |
| Universal MFA Deployment | Extend MFA to VPN, AWS, Azure, GitHub, Jira - protect against credential compromise | **Priority 1** | 1-2 months (Duo integration, user enrollment) |
| Data Classification Labels | Tag emails and documents with PUBLIC/INTERNAL/CONFIDENTIAL/RESTRICTED labels | **Priority 2** | 2-3 months (tool deployment, user training) |
| Endpoint Encryption (100%) | Extend BitLocker/FileVault to remaining 10% of endpoints | **Priority 2** | 1 month (rollout, compliance tracking) |
| Quarterly Access Reviews | Review all privileged access (AD, AWS, GitHub) and revoke unnecessary permissions | **Priority 2** | Ongoing (4-6 hours per quarter) |
| IP Protection Policy | Formal policy on CRITICAL IP handling, NDAs, compartmentalization, need-to-know | **Priority 2** | 2 months (policy development, legal review) |

### Integrity Controls

| Control | Purpose | Priority | Estimated Effort |
|---------|---------|----------|------------------|
| File Integrity Monitoring (FIM) | Deploy Wazuh FIM to IoT gateways and critical servers; detect unauthorized file changes | **Priority 1** | 2-3 months (agent deployment, baseline, alerting) |
| Code Signing Infrastructure | PKI for signing all firmware/software updates; prevent tampering | **Priority 1** | 3-4 months (CA setup, signing process, validation) |
| Change Management Process | Formal CAB, approval workflow, rollback plans for production changes | **Priority 2** | 2 months (process documentation, tool integration) |
| Database Activity Monitoring | Real-time monitoring of schema/data changes in PostgreSQL databases | **Priority 2** | 2-3 months (tool deployment, rule tuning) |
| Version Control Enforcement | Mandatory GitHub pull requests, code reviews, branch protection | **Priority 2** | 1 month (GitHub policies, developer training) |
| Immutable Backups | Convert Veeam backups to write-once mode to prevent ransomware encryption | **Priority 3** | 1-2 months (configuration change, testing) |

### Availability Controls

| Control | Purpose | Priority | Estimated Effort |
|---------|---------|----------|------------------|
| DR Testing Program | Quarterly failover tests with documented runbooks; validate recovery capability | **Priority 1** | Ongoing (8-16 hours per quarter) |
| Multi-Region Architecture | Deploy hot standby or active-active in eu-west-1; eliminate single region failure | **Priority 1** | 4-6 months (architecture design, deployment, testing) |
| Capacity Monitoring | Alerts at 70%/85% thresholds for compute, storage, bandwidth | **Priority 2** | 1-2 months (monitoring tool configuration) |
| Business Continuity Plan | Document non-IT recovery processes; coordinate IT and business continuity efforts | **Priority 2** | 2-3 months (BIA, plan development, training) |
| DDoS Protection (AWS Shield + WAF) | Protect public-facing services from volumetric and application-layer attacks | **Priority 2** | 1-2 months (Shield deployment, WAF rules) |
| N+1 Redundancy | Eliminate single points of failure in firewalls, switches, database servers | **Priority 3** | 3-6 months (hardware procurement, deployment) |

---

# SECTION I: EXECUTIVE SUMMARY

# SECTION I: EXECUTIVE SUMMARY

NordicShield Technologies Oy's CIA requirements analysis reveals a **mature but uneven security posture** with critical gaps in data protection and resilience. Four assets have been classified as **CRITICAL**: the proprietary Cooling Algorithm IP, IoT Monitoring Platform, Financial Systems, and R&D Systems, each requiring the highest levels of confidentiality and integrity protection. The platform's availability is business-critical, with SLA penalties of €5,000-€50,000 per hour for downtime.

**Most Critical Requirements:**
- **Integrity** is paramount for IoT sensor data - compromised temperature readings could cause physical damage to client facilities
- **Confidentiality** of the Cooling Algorithm IP (source of competitive advantage) and customer PII (GDPR compliance)
- **Availability** of the IoT platform with maximum 1-hour RTO and 15-minute RPO

**Biggest Gaps:**
1. No Data Loss Prevention (DLP) solution - RESTRICTED data can leave the organization undetected
2. Inconsistent MFA deployment - only M365 protected, leaving VPN, AWS, and GitHub vulnerable
3. Single AWS region for production - region outage would cause total platform failure
4. No File Integrity Monitoring on IoT gateways - malware could alter sensor data undetected

**Global Expansion Impact:** Planned offices in Rwanda and USA introduce cross-border data transfer complexity (GDPR, Schrems II, data localization). Priority 1 controls (DLP, universal MFA, FIM, DR testing, multi-region architecture) must be implemented by Q2-Q3 2026 to support growth while maintaining regulatory compliance.

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 1.2 - CIA Requirements Document |
| **Phase** | 1 - General Security Concepts |
| **Exam Objective** | 1.2 - Summarize fundamental security concepts |
| **Status** | ✅ Complete |
| **Completed By** | Robert Preshyl |
| **Completion Date** | January 31, 2026 |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
