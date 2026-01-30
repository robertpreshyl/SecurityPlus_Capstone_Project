# Deliverable 5.5: Third-Party Risk Management Program
## NordicShield Technologies Oy

---

```
╔══════════════════════════════════════════════════════════════════╗
║         THIRD-PARTY RISK MANAGEMENT (TPRM) PROGRAM               ║
║                                                                    ║
║  Document ID: TPRM-NS-2026-001                                    ║
║  Version: 1.0                                                     ║
║  Author: [YOUR NAME]                                              ║
║  Classification: Internal                                         ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Document Purpose

This document establishes NordicShield's Third-Party Risk Management (TPRM) Program, defining how the organization identifies, assesses, monitors, and manages security risks introduced by vendors, suppliers, partners, and other third parties throughout the relationship lifecycle.

---

## Instructions

1. Establish TPRM governance and policy framework
2. Design vendor assessment methodology
3. Create risk tiering criteria
4. Define ongoing monitoring processes
5. Complete all `[YOUR INPUT]` sections

---

# SECTION A: TPRM PROGRAM FRAMEWORK

## A.1 Program Overview

```
[YOUR INPUT - Define TPRM program]

THIRD-PARTY RISK MANAGEMENT PROGRAM
===================================

PROGRAM PURPOSE:
[YOUR INPUT - Ensure that third parties with access to 
NordicShield's data, systems, or facilities do not introduce 
unacceptable security risks to the organization.]

PROGRAM SCOPE:
[YOUR INPUT - All vendors, suppliers, contractors, partners, 
and service providers who:]
• Access NordicShield systems or networks
• Process, store, or transmit NordicShield data
• Provide critical business services
• Have physical access to NordicShield facilities
• Develop software or components for NordicShield

PROGRAM OBJECTIVES:

1. RISK VISIBILITY
   [YOUR INPUT - Maintain awareness of third-party risk exposure]

2. RISK REDUCTION
   [YOUR INPUT - Ensure appropriate controls at third parties]

3. COMPLIANCE
   [YOUR INPUT - Meet regulatory requirements (GDPR, NIS2, etc.)]

4. INCIDENT PREPAREDNESS
   [YOUR INPUT - Rapid response to third-party security events]

5. CONTINUOUS IMPROVEMENT
   [YOUR INPUT - Mature TPRM practices over time]

REGULATORY DRIVERS:

┌─────────────────────────────────────────────────────────────────────────┐
│  GDPR Article 28                                                        │
│  • Use only processors with sufficient guarantees                       │
│  • Written contract with specific security requirements                 │
│  • Right to audit processors                                            │
├─────────────────────────────────────────────────────────────────────────┤
│  NIS2 Directive                                                         │
│  • Supply chain security measures                                       │
│  • Security requirements for direct suppliers                           │
│  • Assess cybersecurity practices of suppliers                          │
├─────────────────────────────────────────────────────────────────────────┤
│  ISO 27001 A.5.19-A.5.23                                               │
│  • Information security in supplier relationships                       │
│  • Managing security within supply chain                               │
│  • Monitoring, review, and change management                           │
├─────────────────────────────────────────────────────────────────────────┤
│  SOC 2 CC9.2                                                            │
│  • Risk assessment and management for vendors                          │
│  • Monitoring vendor compliance                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

## A.2 TPRM Governance

| Role | Responsibility | Name/Title |
|------|---------------|------------|
| Program Sponsor | [YOUR INPUT - Executive oversight, policy approval] | [YOUR INPUT - CISO] |
| Program Owner | [YOUR INPUT - Program strategy, methodology, reporting] | [YOUR INPUT - GRC Manager] |
| TPRM Analysts | [YOUR INPUT - Conduct assessments, track issues] | [YOUR INPUT - GRC Team] |
| Legal/Procurement | [YOUR INPUT - Contract requirements, terms] | [YOUR INPUT - Legal Counsel, Procurement Manager] |
| Business Owners | [YOUR INPUT - Own vendor relationships, risk acceptance] | [YOUR INPUT - Department heads] |
| IT Security | [YOUR INPUT - Technical assessment, integration review] | [YOUR INPUT - Security Architects] |
| Privacy/DPO | [YOUR INPUT - Data processing assessments, DPAs] | [YOUR INPUT - Data Protection Officer] |

## A.3 Vendor Inventory

```
[YOUR INPUT - Design vendor inventory]

THIRD-PARTY INVENTORY REQUIREMENTS
==================================

All third parties with access to NordicShield data or systems 
MUST be registered in the vendor inventory.

INVENTORY FIELDS:

┌─────────────────────────────────────────────────────────────────────────┐
│  VENDOR IDENTIFICATION                                                  │
│  • Vendor Name                                                          │
│  • Vendor ID (unique identifier)                                        │
│  • Parent Company (if applicable)                                       │
│  • Headquarters Location                                                │
│  • Service Locations                                                    │
├─────────────────────────────────────────────────────────────────────────┤
│  RELATIONSHIP DETAILS                                                   │
│  • Business Owner                                                       │
│  • Service Description                                                  │
│  • Contract Start Date                                                  │
│  • Contract End Date                                                    │
│  • Contract Value (annual)                                              │
│  • Business Criticality (Critical/High/Medium/Low)                     │
├─────────────────────────────────────────────────────────────────────────┤
│  DATA & ACCESS                                                          │
│  • Data Types Accessed (PII, Confidential, etc.)                       │
│  • Data Volume                                                          │
│  • System Access (which systems)                                        │
│  • Network Access (VPN, direct, none)                                  │
│  • Physical Access (facilities)                                         │
├─────────────────────────────────────────────────────────────────────────┤
│  RISK & COMPLIANCE                                                      │
│  • Risk Tier (Critical/High/Medium/Low)                                │
│  • Last Assessment Date                                                 │
│  • Assessment Result (Pass/Conditional/Fail)                           │
│  • Open Issues                                                          │
│  • Certifications (ISO 27001, SOC 2, etc.)                            │
│  • DPA/BAA in place (Yes/No)                                           │
├─────────────────────────────────────────────────────────────────────────┤
│  CONTACTS                                                               │
│  • Primary Vendor Contact                                               │
│  • Security Contact                                                     │
│  • Privacy Contact                                                      │
│  • Emergency Contact                                                    │
└─────────────────────────────────────────────────────────────────────────┘

INVENTORY MAINTENANCE:
• Full inventory review: [YOUR INPUT - Annual]
• New vendor registration: [YOUR INPUT - Before contract signing]
• Status updates: [YOUR INPUT - After each assessment or change]
```

---

# SECTION B: VENDOR RISK TIERING

## B.1 Risk Tiering Methodology

```
[YOUR INPUT - Define risk tiering criteria]

VENDOR RISK TIERING
===================

PURPOSE:
Risk tiering determines the level of due diligence, assessment 
depth, and ongoing monitoring required for each third party.

TIERING FACTORS:

┌─────────────────────────────────────────────────────────────────────────┐
│  FACTOR 1: DATA SENSITIVITY                                             │
│  ─────────────────────────────────────────────────────────────────────  │
│  Score 4: Restricted data (health records, financial data, credentials)│
│  Score 3: Confidential data (PII, business sensitive)                  │
│  Score 2: Internal data only                                            │
│  Score 1: Public data only / No data access                            │
├─────────────────────────────────────────────────────────────────────────┤
│  FACTOR 2: SYSTEM ACCESS                                                │
│  ─────────────────────────────────────────────────────────────────────  │
│  Score 4: Privileged access to production systems                       │
│  Score 3: Non-privileged access to production / Privileged to non-prod │
│  Score 2: Read-only access / Development access only                   │
│  Score 1: No system access                                              │
├─────────────────────────────────────────────────────────────────────────┤
│  FACTOR 3: BUSINESS CRITICALITY                                         │
│  ─────────────────────────────────────────────────────────────────────  │
│  Score 4: Critical - Service disruption = major business impact        │
│  Score 3: High - Service disruption = significant impact               │
│  Score 2: Medium - Service disruption = moderate impact                │
│  Score 1: Low - Service disruption = minimal impact                    │
├─────────────────────────────────────────────────────────────────────────┤
│  FACTOR 4: FOURTH-PARTY RISK                                            │
│  ─────────────────────────────────────────────────────────────────────  │
│  Score 4: Extensive subcontractor use with data access                 │
│  Score 3: Some subcontractor use with data access                      │
│  Score 2: Limited subcontractor use                                     │
│  Score 1: No subcontractor use / Direct service only                   │
├─────────────────────────────────────────────────────────────────────────┤
│  FACTOR 5: GEOGRAPHIC RISK                                              │
│  ─────────────────────────────────────────────────────────────────────  │
│  Score 4: Data processed in high-risk jurisdiction                     │
│  Score 3: Data processed outside EU/EEA                                │
│  Score 2: Data processed in EU/EEA (non-Finland)                       │
│  Score 1: Data processed in Finland only                               │
└─────────────────────────────────────────────────────────────────────────┘

CALCULATION:
Total Score = Sum of all factors (5-20 points)

TIER MAPPING:
┌──────────────────────────────────────────────────────────────────────────┐
│  SCORE    │  TIER     │  ASSESSMENT              │  MONITORING          │
├───────────┼───────────┼──────────────────────────┼──────────────────────┤
│  16-20    │  CRITICAL │  Full assessment         │  Continuous + Annual │
│           │           │  On-site review option   │  review              │
├───────────┼───────────┼──────────────────────────┼──────────────────────┤
│  11-15    │  HIGH     │  Comprehensive           │  Annual assessment   │
│           │           │  questionnaire + evidence│  + quarterly check   │
├───────────┼───────────┼──────────────────────────┼──────────────────────┤
│  6-10     │  MEDIUM   │  Standard questionnaire  │  Annual assessment   │
├───────────┼───────────┼──────────────────────────┼──────────────────────┤
│  5        │  LOW      │  Self-certification or   │  Biennial assessment │
│           │           │  minimal review          │                      │
└───────────┴───────────┴──────────────────────────┴──────────────────────┘
```

## B.2 Tier-Based Requirements

| Requirement | Critical Tier | High Tier | Medium Tier | Low Tier |
|------------|---------------|-----------|-------------|----------|
| Security Questionnaire | [YOUR INPUT - Extended (200+ questions)] | [YOUR INPUT - Comprehensive (100+ questions)] | [YOUR INPUT - Standard (50 questions)] | [YOUR INPUT - Brief (15 questions) or self-cert] |
| Evidence Review | [YOUR INPUT - All domains] | [YOUR INPUT - Key domains] | [YOUR INPUT - Sampling] | [YOUR INPUT - Certification only] |
| SOC 2/ISO 27001 Required | [YOUR INPUT - Required] | [YOUR INPUT - Required or gap assessment] | [YOUR INPUT - Preferred] | [YOUR INPUT - Not required] |
| On-Site Assessment | [YOUR INPUT - Yes, if no SOC 2] | [YOUR INPUT - Risk-based] | [YOUR INPUT - No] | [YOUR INPUT - No] |
| Penetration Test (theirs) | [YOUR INPUT - Annual required] | [YOUR INPUT - Annual required] | [YOUR INPUT - Preferred] | [YOUR INPUT - Not required] |
| Data Processing Agreement | [YOUR INPUT - Required] | [YOUR INPUT - Required] | [YOUR INPUT - If applicable] | [YOUR INPUT - If applicable] |
| Security Contact | [YOUR INPUT - Required] | [YOUR INPUT - Required] | [YOUR INPUT - Required] | [YOUR INPUT - Optional] |
| Incident Notification SLA | [YOUR INPUT - 4 hours] | [YOUR INPUT - 24 hours] | [YOUR INPUT - 48 hours] | [YOUR INPUT - 72 hours] |
| Assessment Frequency | [YOUR INPUT - Annual + continuous monitoring] | [YOUR INPUT - Annual] | [YOUR INPUT - Annual] | [YOUR INPUT - Biennial] |
| CISO/SSC Approval | [YOUR INPUT - Required] | [YOUR INPUT - GRC approval] | [YOUR INPUT - Business owner] | [YOUR INPUT - Business owner] |

---

# SECTION C: VENDOR ASSESSMENT

## C.1 Assessment Process

```
[YOUR INPUT - Define assessment workflow]

VENDOR SECURITY ASSESSMENT PROCESS
==================================

┌─────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│  PHASE 1: INITIATION                                                    │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Trigger:                                                          │   │
│  │ • New vendor engagement                                           │   │
│  │ • Contract renewal                                                │   │
│  │ • Change in scope/access                                          │   │
│  │ • Scheduled periodic assessment                                   │   │
│  │                                                                   │   │
│  │ Activities:                                                       │   │
│  │ • Business owner submits request                                  │   │
│  │ • GRC performs inherent risk tiering                              │   │
│  │ • Determine assessment scope based on tier                        │   │
│  │ • Notify vendor of assessment requirements                        │   │
│  └───────────────────────────────┬──────────────────────────────────┘   │
│                                  │                                       │
│                                  ▼                                       │
│  PHASE 2: INFORMATION GATHERING                                         │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Activities:                                                       │   │
│  │ • Send security questionnaire to vendor                          │   │
│  │ • Request supporting documentation:                               │   │
│  │   - SOC 2 Type II report                                         │   │
│  │   - ISO 27001 certificate                                        │   │
│  │   - Penetration test executive summary                           │   │
│  │   - Security policies                                            │   │
│  │   - Insurance certificates                                       │   │
│  │   - Business continuity plan summary                             │   │
│  │ • Conduct follow-up calls as needed                              │   │
│  │                                                                   │   │
│  │ Timeline: [YOUR INPUT - 2-4 weeks]                               │   │
│  └───────────────────────────────┬──────────────────────────────────┘   │
│                                  │                                       │
│                                  ▼                                       │
│  PHASE 3: ASSESSMENT & ANALYSIS                                         │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Activities:                                                       │   │
│  │ • Review questionnaire responses                                  │   │
│  │ • Analyze SOC 2 report (if applicable):                          │   │
│  │   - Auditor opinion                                              │   │
│  │   - Control exceptions                                           │   │
│  │   - Complementary user entity controls (CUECs)                   │   │
│  │ • Review penetration test findings                               │   │
│  │ • Identify control gaps                                          │   │
│  │ • Calculate residual risk rating                                 │   │
│  │                                                                   │   │
│  │ Timeline: [YOUR INPUT - 1-2 weeks]                               │   │
│  └───────────────────────────────┬──────────────────────────────────┘   │
│                                  │                                       │
│                                  ▼                                       │
│  PHASE 4: RISK REMEDIATION (if gaps identified)                         │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Activities:                                                       │   │
│  │ • Document findings and recommendations                          │   │
│  │ • Request vendor remediation plan                                │   │
│  │ • Determine acceptable compensating controls                     │   │
│  │ • Negotiate contractual requirements if needed                   │   │
│  │ • Track remediation to completion                                │   │
│  │                                                                   │   │
│  │ Timeline: [YOUR INPUT - Based on finding severity]               │   │
│  └───────────────────────────────┬──────────────────────────────────┘   │
│                                  │                                       │
│                                  ▼                                       │
│  PHASE 5: DECISION & DOCUMENTATION                                      │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Outcomes:                                                         │   │
│  │ • APPROVED: Vendor meets requirements                            │   │
│  │ • CONDITIONAL: Approved with remediation plan                    │   │
│  │ • REJECTED: Unacceptable risk, cannot proceed                    │   │
│  │                                                                   │   │
│  │ Documentation:                                                    │   │
│  │ • Assessment report                                               │   │
│  │ • Risk rating                                                     │   │
│  │ • Findings and remediation tracker                               │   │
│  │ • Approval record with appropriate sign-off                      │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

## C.2 Security Questionnaire Domains

| Domain | Topics Covered | Weight |
|--------|---------------|--------|
| Information Security Governance | [YOUR INPUT - Policies, roles, management commitment, certifications] | [YOUR INPUT - 10%] |
| Access Management | [YOUR INPUT - IAM, authentication, privileged access, account lifecycle] | [YOUR INPUT - 15%] |
| Network Security | [YOUR INPUT - Segmentation, firewalls, IDS/IPS, DDoS protection] | [YOUR INPUT - 10%] |
| Data Protection | [YOUR INPUT - Encryption, data handling, DLP, backup] | [YOUR INPUT - 15%] |
| Endpoint Security | [YOUR INPUT - AV/EDR, patching, hardening] | [YOUR INPUT - 10%] |
| Application Security | [YOUR INPUT - SDLC, code review, SAST/DAST, vulnerabilities] | [YOUR INPUT - 10%] |
| Incident Response | [YOUR INPUT - IR plan, notification procedures, forensics] | [YOUR INPUT - 10%] |
| Business Continuity | [YOUR INPUT - BC/DR plans, testing, recovery objectives] | [YOUR INPUT - 5%] |
| Vendor Management | [YOUR INPUT - Fourth-party risk, subcontractor controls] | [YOUR INPUT - 5%] |
| HR Security | [YOUR INPUT - Background checks, training, termination] | [YOUR INPUT - 5%] |
| Physical Security | [YOUR INPUT - Facility access, environmental controls] | [YOUR INPUT - 5%] |

## C.3 SOC 2 Report Review Guide

```
[YOUR INPUT - Guide for reviewing SOC 2 reports]

SOC 2 REPORT REVIEW CHECKLIST
=============================

REPORT BASICS:
┌─────────────────────────────────────────────────────────────────────────┐
│ □ Report is Type II (not Type I)                                        │
│ □ Report period covers last 12 months                                   │
│ □ Report is not expired (issued within last 12 months)                 │
│ □ Auditor is reputable CPA firm                                        │
│ □ Trust Services Criteria are relevant:                                │
│   □ Security (required)                                                 │
│   □ Availability (if service is critical)                              │
│   □ Confidentiality (if handling confidential data)                    │
│   □ Processing Integrity (if data processing is core service)          │
│   □ Privacy (if vendor is a data processor)                            │
└─────────────────────────────────────────────────────────────────────────┘

SECTION I: AUDITOR'S OPINION
┌─────────────────────────────────────────────────────────────────────────┐
│ □ Opinion is "Unqualified" (clean)                                     │
│ □ If "Qualified" - review nature of qualification                      │
│ □ If "Adverse" - DO NOT proceed without escalation                     │
│                                                                         │
│ [YOUR INPUT - Document opinion type and any qualifications]            │
└─────────────────────────────────────────────────────────────────────────┘

SECTION II: MANAGEMENT ASSERTION
┌─────────────────────────────────────────────────────────────────────────┐
│ □ Scope covers services NordicShield uses                              │
│ □ No significant carve-outs affecting our service                      │
│                                                                         │
│ [YOUR INPUT - Document scope and any exclusions]                       │
└─────────────────────────────────────────────────────────────────────────┘

SECTION III: SYSTEM DESCRIPTION
┌─────────────────────────────────────────────────────────────────────────┐
│ □ System description matches vendor's service to us                    │
│ □ Data centers/locations are acceptable                                │
│ □ Subservice organizations are identified                              │
│                                                                         │
│ [YOUR INPUT - Note any concerns about system description]              │
└─────────────────────────────────────────────────────────────────────────┘

SECTION IV: CONTROL TESTS (Most Critical)
┌─────────────────────────────────────────────────────────────────────────┐
│ □ Review ALL exceptions/deviations                                     │
│ □ For each exception, assess:                                          │
│   - Severity (critical, high, medium, low)                             │
│   - Relevance to our use case                                          │
│   - Management response and remediation                                │
│   - Current status                                                      │
│ □ Controls with exceptions are documented                              │
│                                                                         │
│ [YOUR INPUT - List all exceptions and your assessment]                 │
│                                                                         │
│ EXCEPTION LOG:                                                         │
│ | Control | Exception | Severity | Impact to NS | Remediated? |        │
│ |---------|-----------|----------|--------------|-------------|        │
│ | [CTRL]  | [DESC]    | [H/M/L]  | [IMPACT]     | [Y/N]       |        │
└─────────────────────────────────────────────────────────────────────────┘

SECTION V: COMPLEMENTARY USER ENTITY CONTROLS (CUECs)
┌─────────────────────────────────────────────────────────────────────────┐
│ CUECs are controls that NordicShield must implement for the vendor's   │
│ controls to be effective.                                               │
│                                                                         │
│ □ Review all CUECs                                                      │
│ □ Document which are applicable                                        │
│ □ Verify NordicShield implements these controls                        │
│                                                                         │
│ [YOUR INPUT - List applicable CUECs and NordicShield status]          │
│                                                                         │
│ | CUEC Description | NS Status | Gap? | Owner |                        │
│ |------------------|-----------|------|-------|                        │
│ | [CUEC]           | [STATUS]  | [Y/N]| [OWNER]|                       │
└─────────────────────────────────────────────────────────────────────────┘

FINAL ASSESSMENT:
[YOUR INPUT - Overall conclusion on SOC 2 review]
```

---

# SECTION D: CONTRACT REQUIREMENTS

## D.1 Security Contract Clauses

```
[YOUR INPUT - Define required contract terms]

STANDARD SECURITY CONTRACT REQUIREMENTS
=======================================

The following security requirements must be included in 
contracts with third parties based on their risk tier.

REQUIRED FOR ALL TIERS:
┌─────────────────────────────────────────────────────────────────────────┐
│  1. COMPLIANCE WITH LAWS                                                │
│     Vendor shall comply with all applicable data protection and        │
│     security laws, including GDPR.                                     │
│                                                                         │
│  2. CONFIDENTIALITY                                                     │
│     Vendor shall maintain confidentiality of all NordicShield         │
│     information and not disclose without authorization.                │
│                                                                         │
│  3. DATA USE RESTRICTIONS                                               │
│     Vendor shall only use NordicShield data for the purposes          │
│     specified in the agreement.                                         │
│                                                                         │
│  4. DATA RETURN/DELETION                                                │
│     Upon termination, vendor shall return or securely destroy          │
│     all NordicShield data within [X] days.                            │
│                                                                         │
│  5. INCIDENT NOTIFICATION                                               │
│     Vendor shall notify NordicShield of security incidents            │
│     affecting NordicShield data within [24-72] hours per tier.        │
│                                                                         │
│  6. INSURANCE                                                           │
│     Vendor shall maintain cybersecurity liability insurance            │
│     of at least [€X million].                                          │
└─────────────────────────────────────────────────────────────────────────┘

ADDITIONAL FOR HIGH/CRITICAL TIERS:
┌─────────────────────────────────────────────────────────────────────────┐
│  7. AUDIT RIGHTS                                                        │
│     NordicShield has the right to audit vendor's security             │
│     practices, including on-site inspections with [X] days notice.     │
│                                                                         │
│  8. SECURITY ASSESSMENTS                                                │
│     Vendor shall complete NordicShield security questionnaire         │
│     annually and provide updated certifications.                       │
│                                                                         │
│  9. PENETRATION TESTING                                                 │
│     Vendor shall conduct annual penetration tests and provide         │
│     executive summary to NordicShield upon request.                   │
│                                                                         │
│  10. SUBCONTRACTOR CONTROLS                                             │
│      Vendor shall impose equivalent security requirements on           │
│      subcontractors and notify NordicShield of subcontractor use.     │
│                                                                         │
│  11. BUSINESS CONTINUITY                                                │
│      Vendor shall maintain business continuity and disaster           │
│      recovery plans and provide recovery time objectives.              │
│                                                                         │
│  12. SECURITY CERTIFICATIONS                                            │
│      Vendor shall maintain [ISO 27001/SOC 2] certification            │
│      and notify NordicShield of any certification changes.            │
│                                                                         │
│  13. TERMINATION ASSISTANCE                                             │
│      Vendor shall provide reasonable transition assistance             │
│      upon termination, including data migration support.               │
└─────────────────────────────────────────────────────────────────────────┘
```

## D.2 Data Processing Agreement (GDPR)

```
[YOUR INPUT - Key DPA elements]

DATA PROCESSING AGREEMENT REQUIREMENTS
======================================

Under GDPR Article 28, a Data Processing Agreement (DPA) is 
required when a third party processes personal data on behalf 
of NordicShield.

REQUIRED DPA ELEMENTS:

1. SUBJECT MATTER AND DURATION
   [YOUR INPUT - What data is processed, for how long]

2. NATURE AND PURPOSE OF PROCESSING
   [YOUR INPUT - What processing activities are performed]

3. TYPE OF PERSONAL DATA
   [YOUR INPUT - Categories of data processed]

4. CATEGORIES OF DATA SUBJECTS
   [YOUR INPUT - Whose data is processed (employees, customers, etc.)]

5. CONTROLLER OBLIGATIONS & RIGHTS
   [YOUR INPUT - NordicShield's rights and responsibilities]

6. PROCESSOR OBLIGATIONS (Article 28(3)):

   ┌─────────────────────────────────────────────────────────────────────┐
   │  (a) Process only on documented instructions from controller        │
   │  (b) Ensure persons processing have committed to confidentiality   │
   │  (c) Take appropriate security measures (Article 32)               │
   │  (d) Respect conditions for engaging sub-processors                │
   │  (e) Assist controller with data subject rights requests           │
   │  (f) Assist controller with security, breach notification, DPIA    │
   │  (g) Delete or return data at end of processing                    │
   │  (h) Make available all information to demonstrate compliance      │
   │      and allow for audits                                          │
   └─────────────────────────────────────────────────────────────────────┘

7. SUB-PROCESSOR REQUIREMENTS
   [YOUR INPUT - Prior authorization, list of sub-processors, 
   obligations flow-down]

8. INTERNATIONAL TRANSFERS
   [YOUR INPUT - SCCs if data transfers outside EU/EEA]

TEMPLATE LOCATION:
[YOUR INPUT - Link to approved DPA template]
```

---

# SECTION E: ONGOING MONITORING

## E.1 Continuous Monitoring Program

```
[YOUR INPUT - Design ongoing monitoring]

VENDOR CONTINUOUS MONITORING
============================

PURPOSE:
Monitor third parties for security changes, threats, and 
compliance drift between formal assessments.

MONITORING ACTIVITIES:

┌─────────────────────────────────────────────────────────────────────────┐
│  AUTOMATED MONITORING (Continuous)                                      │
│  ─────────────────────────────────────────────────────────────────────  │
│  Tool: [YOUR INPUT - BitSight, SecurityScorecard, etc.]                │
│                                                                          │
│  Metrics Monitored:                                                      │
│  • Security rating changes                                               │
│  • Compromised credentials (darkweb)                                    │
│  • Botnet infections                                                     │
│  • Open ports/vulnerabilities                                           │
│  • SSL/TLS certificate issues                                           │
│  • DNS security                                                          │
│  • IP reputation                                                         │
│                                                                          │
│  Alert Thresholds:                                                       │
│  • Rating drops below [YOUR INPUT - threshold]                          │
│  • New critical vulnerabilities                                          │
│  • Credential exposures                                                  │
├─────────────────────────────────────────────────────────────────────────┤
│  NEWS & THREAT MONITORING (Daily/Weekly)                                │
│  ─────────────────────────────────────────────────────────────────────  │
│  • Industry breach notifications                                        │
│  • Vendor-specific security news                                        │
│  • Regulatory actions against vendors                                   │
│  • Financial stability indicators                                       │
├─────────────────────────────────────────────────────────────────────────┤
│  PERIODIC REVIEWS                                                        │
│  ─────────────────────────────────────────────────────────────────────  │
│  Quarterly:                                                              │
│  • Review security rating trends                                        │
│  • Check certification status                                           │
│  • Review open remediation items                                        │
│                                                                          │
│  Annually:                                                               │
│  • Full reassessment (based on tier)                                    │
│  • Contract review                                                       │
│  • Inventory validation                                                  │
├─────────────────────────────────────────────────────────────────────────┤
│  TRIGGERED REVIEWS                                                       │
│  ─────────────────────────────────────────────────────────────────────  │
│  Triggers:                                                               │
│  • Vendor security incident                                              │
│  • Significant rating drop                                              │
│  • Acquisition/merger of vendor                                         │
│  • Change in service scope                                              │
│  • Subcontractor change                                                 │
│  • Certification lapse                                                   │
└─────────────────────────────────────────────────────────────────────────┘
```

## E.2 Vendor Incident Response

```
[YOUR INPUT - Define vendor incident handling]

THIRD-PARTY INCIDENT RESPONSE PROCEDURE
=======================================

When a vendor experiences a security incident that may affect 
NordicShield, the following process applies:

NOTIFICATION REQUIREMENTS (by tier):
┌─────────────────────────────────────────────────────────────────────────┐
│  Critical Tier: 4 hours                                                 │
│  High Tier: 24 hours                                                    │
│  Medium Tier: 48 hours                                                  │
│  Low Tier: 72 hours                                                     │
└─────────────────────────────────────────────────────────────────────────┘

RESPONSE PROCESS:

1. INITIAL NOTIFICATION RECEIVED
   [YOUR INPUT - GRC/SOC receives notification from vendor]
   • Log incident in tracking system
   • Initial triage: Is NordicShield data/systems affected?
   • Notify SOC, CISO, business owner

2. INFORMATION GATHERING
   [YOUR INPUT - Work with vendor to understand impact]
   • What data was potentially affected?
   • What systems were involved?
   • Timeline of incident
   • Vendor's containment actions
   • Ongoing risks

3. IMPACT ASSESSMENT
   [YOUR INPUT - Determine impact to NordicShield]
   • Data types and volumes affected
   • Customers/employees potentially impacted
   • Regulatory notification requirements (GDPR, etc.)
   • Business continuity impact

4. INTERNAL ESCALATION
   [YOUR INPUT - Escalate based on impact]
   • Activate NordicShield IR plan if needed
   • Executive notification
   • Legal/Privacy notification
   • Communications preparation

5. ONGOING COORDINATION
   [YOUR INPUT - Continue working with vendor]
   • Regular status updates
   • Forensics information
   • Remediation progress
   • Root cause analysis (when available)

6. POST-INCIDENT REVIEW
   [YOUR INPUT - Review vendor's handling and controls]
   • Review vendor's post-mortem
   • Assess need for additional controls
   • Update vendor risk rating
   • Consider contract implications
   • Document lessons learned

VENDOR INCIDENT TRACKING TEMPLATE:
| Field | Information |
|-------|-------------|
| Incident ID | [YOUR INPUT] |
| Vendor Name | [YOUR INPUT] |
| Notification Date/Time | [YOUR INPUT] |
| Incident Date | [YOUR INPUT] |
| Incident Type | [YOUR INPUT] |
| NS Data Affected? | [YOUR INPUT - Y/N, details] |
| Impact Assessment | [YOUR INPUT] |
| Vendor Status | [YOUR INPUT] |
| NS Actions Taken | [YOUR INPUT] |
| Closure Date | [YOUR INPUT] |
```

---

# SECTION F: SCENARIOS

## F.1 Scenario: New Vendor Assessment

```
[YOUR INPUT - Complete vendor assessment scenario]

SCENARIO: NEW CLOUD SERVICE PROVIDER
====================================

SITUATION:
The Product team wants to onboard "CloudMetrics Pro," a SaaS 
analytics platform. The service will:
- Process customer usage data (including some PII)
- Integrate with NordicShield's production database via API
- Store data in AWS EU (Frankfurt)
- Have 3 employees with admin access to dashboard
- Annual contract value: €75,000

TASKS:

1. RISK TIERING:
   [YOUR INPUT - Calculate the risk tier]
   
   Factor Scores:
   • Data Sensitivity: [YOUR INPUT - Score 1-4, justification]
   • System Access: [YOUR INPUT - Score 1-4, justification]
   • Business Criticality: [YOUR INPUT - Score 1-4, justification]
   • Fourth-Party Risk: [YOUR INPUT - Score 1-4, justification]
   • Geographic Risk: [YOUR INPUT - Score 1-4, justification]
   
   Total Score: [YOUR INPUT]
   Risk Tier: [YOUR INPUT]

2. ASSESSMENT REQUIREMENTS:
   Based on tier, what is required?
   [YOUR INPUT - Questionnaire type, evidence, approvals]

3. INFORMATION REQUESTED:
   What documentation do you request from the vendor?
   [YOUR INPUT - List specific items]

4. KEY CONTROL AREAS:
   What are the critical control areas to assess?
   [YOUR INPUT - List key areas and why]

5. CONTRACT REQUIREMENTS:
   What security terms are essential?
   [YOUR INPUT - List required clauses]

6. DECISION:
   After assessment, CloudMetrics Pro has SOC 2 Type II but with 
   3 exceptions. How do you proceed?
   [YOUR INPUT - Approval process, conditions]
```

## F.2 Scenario: Vendor Breach Notification

```
[YOUR INPUT - Handle vendor incident]

SCENARIO: CRITICAL VENDOR BREACH
================================

SITUATION:
At 9 PM on Friday, you receive notification from "PaymentGateway Inc" 
(Critical tier vendor) that they experienced a ransomware attack. 
Initial information:
- Attack discovered 6 hours ago
- Systems being restored from backup
- Unknown if data exfiltrated
- They process NordicShield customer payment transactions

RESPONSE:

1. IMMEDIATE ACTIONS (First 2 hours):
   [YOUR INPUT - What do you do immediately?]
   - Notifications: [YOUR INPUT]
   - Documentation: [YOUR INPUT]
   - Initial assessment: [YOUR INPUT]

2. INFORMATION GATHERING:
   [YOUR INPUT - What questions do you ask the vendor?]

3. INTERNAL ESCALATION:
   [YOUR INPUT - Who needs to be notified at NordicShield?]

4. RISK MITIGATION:
   [YOUR INPUT - What protective measures can NordicShield take?]

5. CUSTOMER/REGULATORY NOTIFICATION:
   If customer payment data was compromised:
   [YOUR INPUT - What are NordicShield's obligations?]

6. POST-INCIDENT:
   Once resolved, what actions do you take regarding the vendor?
   [YOUR INPUT - Assessment, contract review, etc.]
```

## F.3 Scenario: Vendor Non-Compliance

```
[YOUR INPUT - Address vendor security gap]

SCENARIO: SOC 2 REPORT SHOWS PROBLEMS
=====================================

SITUATION:
During annual review of "DataProcessor Ltd" (High tier), their 
new SOC 2 Type II report shows:
- 5 exceptions, including:
  - No MFA for privileged access (Critical)
  - Incomplete logging (High)
  - No annual penetration testing (Medium)
  - Background checks not completed for 2 employees (Medium)
  - Incident response plan not tested (Medium)
- Previous year's report had 0 exceptions

CONTRACT STATUS: Renews in 3 months

RESPONSE:

1. ASSESSMENT:
   [YOUR INPUT - How serious is this?]
   - Rating impact: [YOUR INPUT]
   - Risk to NordicShield: [YOUR INPUT]

2. VENDOR COMMUNICATION:
   [YOUR INPUT - What do you communicate to the vendor?]

3. REMEDIATION REQUIREMENTS:
   [YOUR INPUT - What remediation do you require?]
   - Timelines: [YOUR INPUT]
   - Evidence needed: [YOUR INPUT]

4. CONTRACT RENEWAL CONSIDERATIONS:
   [YOUR INPUT - How does this affect renewal decision?]
   - Continue as-is: [YOUR INPUT - Y/N, conditions]
   - Additional terms: [YOUR INPUT]
   - Terminate: [YOUR INPUT - Criteria]

5. ESCALATION:
   [YOUR INPUT - What internal escalation is needed?]
```

---

# SECTION G: METRICS & REPORTING

## G.1 TPRM KPIs

| Metric | Definition | Target | Current |
|--------|------------|--------|---------|
| Inventory Completeness | [YOUR INPUT - % of third parties in inventory] | [YOUR INPUT - 100%] | [YOUR INPUT] |
| Assessment Coverage | [YOUR INPUT - % of vendors assessed on schedule] | [YOUR INPUT - 100%] | [YOUR INPUT] |
| Assessment Cycle Time | [YOUR INPUT - Average days to complete assessment] | [YOUR INPUT - <30 days] | [YOUR INPUT] |
| Critical/High Vendor Coverage | [YOUR INPUT - % with current assessment] | [YOUR INPUT - 100%] | [YOUR INPUT] |
| Open Findings | [YOUR INPUT - Number of open vendor findings] | [YOUR INPUT - Decreasing] | [YOUR INPUT] |
| Overdue Findings | [YOUR INPUT - Vendor findings past remediation date] | [YOUR INPUT - 0 critical/high] | [YOUR INPUT] |
| Contract Compliance | [YOUR INPUT - % with required security clauses] | [YOUR INPUT - 100%] | [YOUR INPUT] |
| DPA Coverage | [YOUR INPUT - % of processors with DPAs] | [YOUR INPUT - 100%] | [YOUR INPUT] |
| Vendor Incident Response | [YOUR INPUT - Incidents reported within SLA] | [YOUR INPUT - 100%] | [YOUR INPUT] |
| Security Rating Average | [YOUR INPUT - Average external security rating] | [YOUR INPUT - >700/1000] | [YOUR INPUT] |

## G.2 Executive Dashboard

```
[YOUR INPUT - Design executive summary]

THIRD-PARTY RISK EXECUTIVE DASHBOARD
====================================

VENDOR POPULATION:
┌─────────────────────────────────────────────────────────────────────────┐
│  Total Vendors in Inventory: [YOUR INPUT - XXX]                        │
│                                                                          │
│  By Risk Tier:                                                          │
│  Critical: [XX] ███████████                                             │
│  High:     [XX] █████████████████                                       │
│  Medium:   [XX] ████████████████████████████                           │
│  Low:      [XX] ████████████████████████████████████████               │
├─────────────────────────────────────────────────────────────────────────┤
│  ASSESSMENT STATUS                                                       │
│                                                                          │
│  Current (assessed in last 12 months): [XX%]                           │
│  Due for Assessment: [XX]                                               │
│  Overdue: [XX]                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│  OPEN FINDINGS                                                           │
│                                                                          │
│  Critical: [X] 🔴                                                        │
│  High: [X] 🟠                                                           │
│  Medium: [X] 🟡                                                         │
│  Low: [X] 🟢                                                            │
│                                                                          │
│  Overdue Remediation: [X]                                               │
├─────────────────────────────────────────────────────────────────────────┤
│  VENDOR INCIDENTS (YTD)                                                  │
│                                                                          │
│  Total Reported: [X]                                                    │
│  Affecting NordicShield Data: [X]                                      │
├─────────────────────────────────────────────────────────────────────────┤
│  KEY RISKS / HIGHLIGHTS                                                  │
│                                                                          │
│  • [YOUR INPUT - Top 3-5 vendor risk concerns]                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 5.5 - Third-Party Risk Management Program |
| **Phase** | 5 - Security Program Management |
| **Exam Objectives** | 5.3 - Third-party risk assessment and management |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
