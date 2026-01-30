# Deliverable 5.3: Compliance & Audit Program
## NordicShield Technologies Oy

---

```
╔══════════════════════════════════════════════════════════════════╗
║              COMPLIANCE & AUDIT PROGRAM                           ║
║                                                                    ║
║  Document ID: COMP-NS-2026-001                                    ║
║  Version: 1.0                                                     ║
║  Author: [YOUR NAME]                                              ║
║  Classification: Internal                                         ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Document Purpose

This document establishes NordicShield's Compliance and Audit Program, defining how the organization maintains compliance with regulations, standards, and contractual requirements, and how effectiveness is verified through internal and external audits.

---

## Instructions

1. Map applicable compliance requirements
2. Design the audit program structure
3. Establish evidence management processes
4. Create remediation tracking mechanisms
5. Complete all `[YOUR INPUT]` sections

---

# SECTION A: COMPLIANCE FRAMEWORK

## A.1 Regulatory & Standards Landscape

```
[YOUR INPUT - Map compliance requirements]

NORDICSHIELD COMPLIANCE REQUIREMENTS
====================================

┌─────────────────────────────────────────────────────────────────────────┐
│                    REGULATORY REQUIREMENTS                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  GDPR (General Data Protection Regulation)                              │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Scope: [YOUR INPUT - EU personal data processing]                │   │
│  │ Status: [YOUR INPUT - Active, must comply]                       │   │
│  │ Key Requirements:                                                 │   │
│  │ • [YOUR INPUT - Lawful basis for processing]                     │   │
│  │ • [YOUR INPUT - Data subject rights]                             │   │
│  │ • [YOUR INPUT - Data protection by design]                       │   │
│  │ • [YOUR INPUT - Breach notification (72 hours)]                  │   │
│  │ • [YOUR INPUT - DPO requirement]                                 │   │
│  │ Penalties: [YOUR INPUT - Up to €20M or 4% global revenue]        │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  NIS2 DIRECTIVE (Network and Information Security)                      │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Scope: [YOUR INPUT - Essential/important entities in EU]         │   │
│  │ Status: [YOUR INPUT - Applicable October 2024]                   │   │
│  │ Key Requirements:                                                 │   │
│  │ • [YOUR INPUT - Risk management measures]                        │   │
│  │ • [YOUR INPUT - Incident reporting (24h/72h)]                    │   │
│  │ • [YOUR INPUT - Supply chain security]                           │   │
│  │ • [YOUR INPUT - Business continuity]                             │   │
│  │ Penalties: [YOUR INPUT - Up to €10M or 2% global revenue]        │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  INDUSTRY-SPECIFIC (if applicable)                                      │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ PCI-DSS: [YOUR INPUT - If processing payment cards]              │   │
│  │ HIPAA: [YOUR INPUT - If handling US health data]                 │   │
│  │ Financial: [YOUR INPUT - MiFID II, DORA if fintech]             │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│                    STANDARDS & CERTIFICATIONS                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ISO 27001 (Information Security Management System)                     │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Scope: [YOUR INPUT - Entire organization / specific services]    │   │
│  │ Status: [YOUR INPUT - In progress, target Q4 2026]               │   │
│  │ Current Phase: [YOUR INPUT - Gap assessment complete]            │   │
│  │ Certification Body: [YOUR INPUT - To be selected]                │   │
│  │ Annex A Controls: [YOUR INPUT - 93 controls applicable]          │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  SOC 2 (Service Organization Control)                                   │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Trust Services Criteria:                                          │   │
│  │ • [YOUR INPUT - Security (Common Criteria)]                      │   │
│  │ • [YOUR INPUT - Availability]                                    │   │
│  │ • [YOUR INPUT - Confidentiality]                                 │   │
│  │ • [YOUR INPUT - Processing Integrity - if applicable]            │   │
│  │ • [YOUR INPUT - Privacy - if applicable]                         │   │
│  │ Type: [YOUR INPUT - Type I then Type II]                         │   │
│  │ Status: [YOUR INPUT - Planned Q2 2027]                           │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  ISO 27701 (Privacy Information Management)                             │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Scope: [YOUR INPUT - Extension to ISO 27001 for privacy]         │   │
│  │ Status: [YOUR INPUT - Planned after 27001 certification]         │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

## A.2 Compliance Requirements Matrix

| Requirement Source | Requirement ID | Control Domain | NordicShield Control | Status | Evidence |
|-------------------|----------------|----------------|---------------------|--------|----------|
| GDPR Art. 32 | GDPR-32 | Security of Processing | [YOUR INPUT - Encryption, access control, monitoring] | [YOUR INPUT - Compliant] | [YOUR INPUT - Encryption policy, access reports] |
| GDPR Art. 33 | GDPR-33 | Breach Notification | [YOUR INPUT - IR plan, 72h notification procedure] | [YOUR INPUT - Compliant] | [YOUR INPUT - IR plan, notification template] |
| ISO 27001 A.5.1 | ISO-A.5.1 | Information Security Policies | [YOUR INPUT - Security policy framework] | [YOUR INPUT - In progress] | [YOUR INPUT - Approved policies] |
| ISO 27001 A.8.2 | ISO-A.8.2 | Privileged Access Rights | [YOUR INPUT - PAM program] | [YOUR INPUT - Gap] | [YOUR INPUT - Planned PAM deployment] |
| SOC 2 CC6.1 | SOC-CC6.1 | Logical Access Controls | [YOUR INPUT - IAM, RBAC, MFA] | [YOUR INPUT - Partial] | [YOUR INPUT - IAM policy, access reports] |
| NIS2 Art. 21 | NIS2-21 | Cybersecurity Risk Measures | [YOUR INPUT - Risk management program] | [YOUR INPUT - In progress] | [YOUR INPUT - Risk register, assessments] |

## A.3 Compliance Calendar

| Month | Compliance Activity | Owner | Deliverable |
|-------|-------------------|-------|-------------|
| January | [YOUR INPUT - Annual policy review kickoff] | [YOUR INPUT - GRC] | [YOUR INPUT - Review schedule] |
| February | [YOUR INPUT - GDPR DPIA reviews] | [YOUR INPUT - DPO] | [YOUR INPUT - DPIA register update] |
| March | [YOUR INPUT - Q1 internal audit] | [YOUR INPUT - Internal Audit] | [YOUR INPUT - Audit report] |
| April | [YOUR INPUT - Risk assessment refresh] | [YOUR INPUT - GRC] | [YOUR INPUT - Updated risk register] |
| May | [YOUR INPUT - Third-party security reviews] | [YOUR INPUT - GRC] | [YOUR INPUT - Vendor assessments] |
| June | [YOUR INPUT - Q2 internal audit] | [YOUR INPUT - Internal Audit] | [YOUR INPUT - Audit report] |
| July | [YOUR INPUT - Security awareness review] | [YOUR INPUT - GRC] | [YOUR INPUT - Training metrics] |
| August | [YOUR INPUT - Business continuity test] | [YOUR INPUT - IT/Security] | [YOUR INPUT - BC test results] |
| September | [YOUR INPUT - Q3 internal audit] | [YOUR INPUT - Internal Audit] | [YOUR INPUT - Audit report] |
| October | [YOUR INPUT - External audit (ISO 27001)] | [YOUR INPUT - Certification body] | [YOUR INPUT - Audit results] |
| November | [YOUR INPUT - Management review] | [YOUR INPUT - CISO] | [YOUR INPUT - Management review minutes] |
| December | [YOUR INPUT - Q4 internal audit, year-end reporting] | [YOUR INPUT - Internal Audit/GRC] | [YOUR INPUT - Annual compliance report] |

---

# SECTION B: AUDIT PROGRAM

## B.1 Audit Types

| Audit Type | Purpose | Frequency | Conducted By | Scope |
|------------|---------|-----------|--------------|-------|
| Internal Audit | [YOUR INPUT - Verify control effectiveness, identify gaps] | [YOUR INPUT - Quarterly] | [YOUR INPUT - Internal audit team or co-sourced] | [YOUR INPUT - All security domains on rotation] |
| External Audit (Certification) | [YOUR INPUT - ISO 27001 certification/surveillance] | [YOUR INPUT - Annual] | [YOUR INPUT - Accredited certification body] | [YOUR INPUT - ISMS scope] |
| External Audit (Attestation) | [YOUR INPUT - SOC 2 attestation] | [YOUR INPUT - Annual] | [YOUR INPUT - CPA firm] | [YOUR INPUT - Trust Services Criteria] |
| Regulatory Examination | [YOUR INPUT - Regulatory compliance verification] | [YOUR INPUT - As scheduled by regulator] | [YOUR INPUT - Regulatory authority] | [YOUR INPUT - Regulatory requirements] |
| Customer Audit | [YOUR INPUT - Customer security due diligence] | [YOUR INPUT - As requested] | [YOUR INPUT - Customer audit team] | [YOUR INPUT - Per contract/scope agreed] |
| Penetration Test | [YOUR INPUT - Technical security validation] | [YOUR INPUT - Annual + after major changes] | [YOUR INPUT - Third-party pen test firm] | [YOUR INPUT - External/internal/app] |
| Vulnerability Assessment | [YOUR INPUT - Identify technical vulnerabilities] | [YOUR INPUT - Continuous/Monthly] | [YOUR INPUT - Internal security team] | [YOUR INPUT - All systems in scope] |

## B.2 Internal Audit Program

```
[YOUR INPUT - Design internal audit program]

INTERNAL SECURITY AUDIT PROGRAM
===============================

PURPOSE:
[YOUR INPUT - Provide independent assurance that security controls 
are designed effectively and operating consistently]

AUDIT UNIVERSE - DOMAINS:
[YOUR INPUT - List all auditable areas]

┌─────────────────────────────────────────────────────────────────────────┐
│  SECURITY DOMAIN                    │ RISK RATING │ AUDIT FREQUENCY    │
├─────────────────────────────────────┼─────────────┼────────────────────┤
│  1. Access Management (IAM)         │ [HIGH]      │ [Annual]           │
│  2. Network Security                │ [HIGH]      │ [Annual]           │
│  3. Endpoint Security               │ [MEDIUM]    │ [18 months]        │
│  4. Data Protection                 │ [HIGH]      │ [Annual]           │
│  5. Security Operations (SOC)       │ [HIGH]      │ [Annual]           │
│  6. Incident Response               │ [HIGH]      │ [Annual]           │
│  7. Vulnerability Management        │ [HIGH]      │ [Annual]           │
│  8. Change Management               │ [MEDIUM]    │ [18 months]        │
│  9. Third-Party Security            │ [HIGH]      │ [Annual]           │
│  10. Physical Security              │ [MEDIUM]    │ [Biennial]         │
│  11. Business Continuity            │ [HIGH]      │ [Annual]           │
│  12. Security Awareness             │ [MEDIUM]    │ [Annual]           │
│  13. Cloud Security                 │ [HIGH]      │ [Annual]           │
│  14. Application Security           │ [HIGH]      │ [Annual]           │
│  15. Privacy/Data Protection        │ [HIGH]      │ [Annual]           │
└─────────────────────────────────────┴─────────────┴────────────────────┘

3-YEAR AUDIT PLAN:

Year 1 (2026):
Q1: [YOUR INPUT - IAM, Network Security]
Q2: [YOUR INPUT - SOC, Incident Response]
Q3: [YOUR INPUT - Third-Party, Cloud Security]
Q4: [YOUR INPUT - Data Protection, Vulnerability Mgmt]

Year 2 (2027):
[YOUR INPUT - Remaining domains + high-risk follow-up]

Year 3 (2028):
[YOUR INPUT - Full cycle repeat + focused reviews]

AUDIT APPROACH:
1. Risk-based planning
2. Control design assessment
3. Operating effectiveness testing
4. Evidence-based conclusions
5. Actionable recommendations
```

## B.3 Audit Process

```
[YOUR INPUT - Define audit workflow]

INTERNAL AUDIT PROCESS
======================

┌─────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│  PHASE 1: PLANNING (2-3 weeks)                                          │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Activities:                                                       │   │
│  │ • [YOUR INPUT - Define audit objectives and scope]               │   │
│  │ • [YOUR INPUT - Review prior audit results]                      │   │
│  │ • [YOUR INPUT - Identify key controls to test]                   │   │
│  │ • [YOUR INPUT - Develop audit program/test procedures]           │   │
│  │ • [YOUR INPUT - Schedule interviews and walkthroughs]            │   │
│  │ • [YOUR INPUT - Send engagement letter to auditees]              │   │
│  │                                                                   │   │
│  │ Deliverable: Audit Plan                                          │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                 │                                        │
│                                 ▼                                        │
│  PHASE 2: FIELDWORK (3-6 weeks)                                         │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Activities:                                                       │   │
│  │ • [YOUR INPUT - Control walkthroughs with process owners]        │   │
│  │ • [YOUR INPUT - Document control design]                         │   │
│  │ • [YOUR INPUT - Test operating effectiveness (sample-based)]     │   │
│  │ • [YOUR INPUT - Collect and review evidence]                     │   │
│  │ • [YOUR INPUT - Document findings as identified]                 │   │
│  │ • [YOUR INPUT - Discuss preliminary findings with auditees]      │   │
│  │                                                                   │   │
│  │ Deliverable: Working papers, evidence files                      │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                 │                                        │
│                                 ▼                                        │
│  PHASE 3: REPORTING (1-2 weeks)                                         │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Activities:                                                       │   │
│  │ • [YOUR INPUT - Draft audit report]                              │   │
│  │ • [YOUR INPUT - Review findings with management]                 │   │
│  │ • [YOUR INPUT - Obtain management responses]                     │   │
│  │ • [YOUR INPUT - Finalize and issue report]                       │   │
│  │ • [YOUR INPUT - Present to audit committee]                      │   │
│  │                                                                   │   │
│  │ Deliverable: Audit Report                                        │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                 │                                        │
│                                 ▼                                        │
│  PHASE 4: FOLLOW-UP (Ongoing)                                           │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ Activities:                                                       │   │
│  │ • [YOUR INPUT - Track remediation progress]                      │   │
│  │ • [YOUR INPUT - Validate remediation effectiveness]              │   │
│  │ • [YOUR INPUT - Escalate overdue items]                          │   │
│  │ • [YOUR INPUT - Report status to audit committee]                │   │
│  │                                                                   │   │
│  │ Deliverable: Remediation Tracker                                 │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

## B.4 Audit Finding Classification

| Rating | Definition | Remediation Timeline | Escalation |
|--------|------------|---------------------|------------|
| Critical | [YOUR INPUT - Immediate risk to organization, fundamental control failure, regulatory non-compliance] | [YOUR INPUT - 30 days] | [YOUR INPUT - Board/Audit Committee immediately] |
| High | [YOUR INPUT - Significant control weakness, material risk] | [YOUR INPUT - 60 days] | [YOUR INPUT - Executive leadership, Audit Committee] |
| Medium | [YOUR INPUT - Control improvement needed, moderate risk] | [YOUR INPUT - 90 days] | [YOUR INPUT - CISO, department head] |
| Low | [YOUR INPUT - Minor improvement opportunity, best practice gap] | [YOUR INPUT - 180 days] | [YOUR INPUT - Control owner] |
| Observation | [YOUR INPUT - Advisory, no formal finding] | [YOUR INPUT - No formal tracking] | [YOUR INPUT - Process owner] |

---

# SECTION C: EVIDENCE MANAGEMENT

## C.1 Evidence Requirements

```
[YOUR INPUT - Define evidence standards]

AUDIT EVIDENCE REQUIREMENTS
===========================

EVIDENCE CHARACTERISTICS:

1. RELEVANT
   [YOUR INPUT - Directly supports the audit objective]

2. RELIABLE
   [YOUR INPUT - From trustworthy source, verifiable]

3. SUFFICIENT
   [YOUR INPUT - Enough to support conclusions]

4. TIMELY
   [YOUR INPUT - From the audit period being tested]

EVIDENCE TYPES:

┌─────────────────────────────────────────────────────────────────────────┐
│  TYPE              │ EXAMPLES                    │ STRENGTH           │
├────────────────────┼─────────────────────────────┼────────────────────┤
│  Documentary       │ Policies, logs, reports,    │ Strong if          │
│                    │ configurations, screenshots │ system-generated   │
├────────────────────┼─────────────────────────────┼────────────────────┤
│  Testimonial       │ Interviews, inquiries,      │ Moderate - needs   │
│                    │ explanations               │ corroboration      │
├────────────────────┼─────────────────────────────┼────────────────────┤
│  Observational     │ Walkthroughs, demos,        │ Strong for point   │
│                    │ facility tours             │ in time            │
├────────────────────┼─────────────────────────────┼────────────────────┤
│  Analytical        │ Comparisons, trend          │ Supportive         │
│                    │ analysis, benchmarking     │                    │
├────────────────────┼─────────────────────────────┼────────────────────┤
│  Re-performance    │ Auditor tests control       │ Strongest          │
│                    │ directly                   │                    │
└─────────────────────────────────────────────────────────────────────────┘
```

## C.2 Evidence Collection Matrix

| Control Area | Required Evidence | Source | Frequency | Owner |
|--------------|------------------|--------|-----------|-------|
| Access Control | [YOUR INPUT - User access reports, entitlement reviews, provisioning logs] | [YOUR INPUT - IAM system, AD] | [YOUR INPUT - Quarterly] | [YOUR INPUT - IAM Team] |
| Change Management | [YOUR INPUT - Change tickets, CAB minutes, approval records] | [YOUR INPUT - ITSM tool] | [YOUR INPUT - Per change] | [YOUR INPUT - IT Ops] |
| Incident Response | [YOUR INPUT - Incident tickets, post-mortems, IR plans] | [YOUR INPUT - SIEM, ticketing] | [YOUR INPUT - Per incident] | [YOUR INPUT - SOC] |
| Vulnerability Management | [YOUR INPUT - Scan reports, remediation tickets, exception approvals] | [YOUR INPUT - Vuln scanner] | [YOUR INPUT - Monthly] | [YOUR INPUT - Security] |
| Security Awareness | [YOUR INPUT - Training completion, phishing results, attestations] | [YOUR INPUT - LMS, phishing tool] | [YOUR INPUT - Monthly] | [YOUR INPUT - GRC] |
| Backup & Recovery | [YOUR INPUT - Backup logs, restore tests, DR test results] | [YOUR INPUT - Backup system] | [YOUR INPUT - Daily/Quarterly] | [YOUR INPUT - IT Ops] |
| Physical Security | [YOUR INPUT - Access logs, visitor logs, inspection reports] | [YOUR INPUT - Physical access system] | [YOUR INPUT - Monthly] | [YOUR INPUT - Facilities] |
| Third-Party Security | [YOUR INPUT - Vendor assessments, SOC reports, contract reviews] | [YOUR INPUT - GRC tool] | [YOUR INPUT - Annual] | [YOUR INPUT - GRC] |

## C.3 Evidence Repository

```
[YOUR INPUT - Design evidence management system]

EVIDENCE REPOSITORY STRUCTURE
=============================

LOCATION: [YOUR INPUT - SharePoint / GRC Tool / Dedicated system]

FOLDER STRUCTURE:
├── Compliance_Evidence/
│   ├── ISO_27001/
│   │   ├── A.5_Organizational_Controls/
│   │   ├── A.6_People_Controls/
│   │   ├── A.7_Physical_Controls/
│   │   └── A.8_Technological_Controls/
│   ├── SOC_2/
│   │   ├── CC1_Control_Environment/
│   │   ├── CC2_Communication_Information/
│   │   ├── CC3_Risk_Assessment/
│   │   └── [...]
│   ├── GDPR/
│   │   ├── Article_5_Principles/
│   │   ├── Article_32_Security/
│   │   └── [...]
│   └── Internal_Audits/
│       ├── 2026_Q1_IAM_Audit/
│       ├── 2026_Q2_SOC_Audit/
│       └── [...]

NAMING CONVENTION:
[YOUR INPUT - {Year}_{Control_ID}_{Evidence_Type}_{Date}.{ext}]
Example: 2026_ISO-A.9.2.1_AccessReport_20260115.pdf

RETENTION:
[YOUR INPUT - Minimum 3 years, 7 years for financial/regulatory]

ACCESS CONTROL:
[YOUR INPUT - GRC team full access, control owners read for their areas]
```

---

# SECTION D: ISO 27001 CERTIFICATION

## D.1 ISO 27001 Certification Roadmap

```
[YOUR INPUT - Plan certification journey]

ISO 27001 CERTIFICATION ROADMAP
===============================

TIMELINE: 18 months to certification

PHASE 1: GAP ASSESSMENT (Months 1-2)
┌──────────────────────────────────────────────────────────────────────────┐
│ Activities:                                                               │
│ • [YOUR INPUT - Document current state of ISMS]                          │
│ • [YOUR INPUT - Assess against ISO 27001 requirements]                   │
│ • [YOUR INPUT - Identify gaps in all 93 Annex A controls]               │
│ • [YOUR INPUT - Prioritize remediation]                                  │
│                                                                           │
│ Deliverables:                                                             │
│ • Gap assessment report                                                   │
│ • Remediation roadmap                                                     │
│ • Budget estimate                                                         │
└──────────────────────────────────────────────────────────────────────────┘

PHASE 2: ISMS DEVELOPMENT (Months 3-8)
┌──────────────────────────────────────────────────────────────────────────┐
│ Activities:                                                               │
│ • [YOUR INPUT - Define ISMS scope and boundaries]                        │
│ • [YOUR INPUT - Develop/update policies and procedures]                  │
│ • [YOUR INPUT - Conduct risk assessment]                                 │
│ • [YOUR INPUT - Create Statement of Applicability (SoA)]                │
│ • [YOUR INPUT - Implement missing controls]                              │
│ • [YOUR INPUT - Establish metrics and monitoring]                        │
│                                                                           │
│ Deliverables:                                                             │
│ • ISMS documentation                                                      │
│ • Risk assessment and treatment plan                                      │
│ • Statement of Applicability                                              │
│ • Implemented controls                                                    │
└──────────────────────────────────────────────────────────────────────────┘

PHASE 3: IMPLEMENTATION & OPERATION (Months 9-12)
┌──────────────────────────────────────────────────────────────────────────┐
│ Activities:                                                               │
│ • [YOUR INPUT - Roll out ISMS to organization]                          │
│ • [YOUR INPUT - Train staff on new processes]                           │
│ • [YOUR INPUT - Collect evidence of control operation]                  │
│ • [YOUR INPUT - Conduct internal audits]                                │
│ • [YOUR INPUT - Hold management review]                                 │
│                                                                           │
│ Deliverables:                                                             │
│ • Training records                                                        │
│ • Internal audit reports                                                  │
│ • Management review minutes                                               │
│ • 3+ months of operating evidence                                         │
└──────────────────────────────────────────────────────────────────────────┘

PHASE 4: CERTIFICATION AUDIT (Months 13-18)
┌──────────────────────────────────────────────────────────────────────────┐
│ Stage 1 Audit (Documentation Review):                                     │
│ • [YOUR INPUT - Auditor reviews ISMS documentation]                      │
│ • [YOUR INPUT - Confirms readiness for Stage 2]                         │
│ • [YOUR INPUT - Identifies any major gaps]                              │
│                                                                           │
│ Remediation Period (if needed): 1-2 months                               │
│                                                                           │
│ Stage 2 Audit (Certification Audit):                                      │
│ • [YOUR INPUT - On-site audit of ISMS implementation]                   │
│ • [YOUR INPUT - Interview staff, review evidence]                       │
│ • [YOUR INPUT - Verify controls operating effectively]                  │
│                                                                           │
│ Deliverables:                                                             │
│ • Stage 1 report                                                          │
│ • Stage 2 report                                                          │
│ • Certificate (if successful)                                             │
└──────────────────────────────────────────────────────────────────────────┘

POST-CERTIFICATION: MAINTAIN
• Annual surveillance audits
• Continuous improvement
• Re-certification every 3 years
```

## D.2 Statement of Applicability (SoA) Template

```
[YOUR INPUT - Complete SoA excerpt]

STATEMENT OF APPLICABILITY (SoA)
================================

Organization: NordicShield Technologies Oy
ISMS Scope: [YOUR INPUT - Define scope]
Version: 1.0
Date: [DATE]

┌──────────────────────────────────────────────────────────────────────────┐
│ ISO 27001:2022 Annex A Controls - Statement of Applicability             │
├──────────────────────────────────────────────────────────────────────────┤

A.5 ORGANIZATIONAL CONTROLS

| Control | Title | Applicable? | Justification | Implementation Status |
|---------|-------|-------------|---------------|----------------------|
| A.5.1 | Policies for information security | [YOUR INPUT - Yes] | [YOUR INPUT - Required for ISMS] | [YOUR INPUT - Implemented] |
| A.5.2 | Information security roles and responsibilities | [YOUR INPUT - Yes] | [YOUR INPUT - Required for ISMS] | [YOUR INPUT - Implemented] |
| A.5.3 | Segregation of duties | [YOUR INPUT - Yes] | [YOUR INPUT - Risk of fraud] | [YOUR INPUT - Partial] |
| A.5.4 | Management responsibilities | [YOUR INPUT - Yes] | [YOUR INPUT - Required] | [YOUR INPUT - Implemented] |
| A.5.5 | Contact with authorities | [YOUR INPUT - Yes] | [YOUR INPUT - Incident reporting] | [YOUR INPUT - Implemented] |
| A.5.6 | Contact with special interest groups | [YOUR INPUT - Yes] | [YOUR INPUT - Threat intel] | [YOUR INPUT - Implemented] |
| A.5.7 | Threat intelligence | [YOUR INPUT - Yes] | [YOUR INPUT - Risk management] | [YOUR INPUT - Partial] |
| A.5.8 | Information security in project management | [YOUR INPUT - Yes] | [YOUR INPUT - Secure SDLC] | [YOUR INPUT - In progress] |
| [...] | [...] | [...] | [...] | [...] |

A.6 PEOPLE CONTROLS
[YOUR INPUT - Continue for all controls]

A.7 PHYSICAL CONTROLS
[YOUR INPUT - Continue for all controls]

A.8 TECHNOLOGICAL CONTROLS
[YOUR INPUT - Continue for all controls]

EXCLUSIONS (with justification):
| Control | Title | Exclusion Justification |
|---------|-------|------------------------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - Must be valid business reason] |

└──────────────────────────────────────────────────────────────────────────┘
```

---

# SECTION E: REMEDIATION MANAGEMENT

## E.1 Finding Remediation Process

```
[YOUR INPUT - Define remediation workflow]

FINDING REMEDIATION PROCESS
===========================

┌─────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│  1. FINDING ISSUED                                                       │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ • Audit report issued with findings                              │   │
│  │ • Rating assigned (Critical/High/Medium/Low)                     │   │
│  │ • Finding owner identified                                       │   │
│  │ • Due date set per rating                                        │   │
│  └───────────────────────────────┬──────────────────────────────────┘   │
│                                  │                                       │
│                                  ▼                                       │
│  2. MANAGEMENT RESPONSE (Within 2 weeks)                                │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ • Finding owner reviews and accepts or disputes                  │   │
│  │ • Remediation plan developed                                     │   │
│  │ • Resources allocated                                            │   │
│  │ • Milestone dates set                                            │   │
│  └───────────────────────────────┬──────────────────────────────────┘   │
│                                  │                                       │
│                                  ▼                                       │
│  3. REMEDIATION EXECUTION                                               │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ • Implement corrective actions                                   │   │
│  │ • Update processes/controls                                      │   │
│  │ • Document changes                                               │   │
│  │ • Report progress monthly                                        │   │
│  └───────────────────────────────┬──────────────────────────────────┘   │
│                                  │                                       │
│                                  ▼                                       │
│  4. VALIDATION                                                          │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ • Owner submits evidence of remediation                          │   │
│  │ • GRC/Audit validates effectiveness                              │   │
│  │ • If inadequate, return to Step 3                               │   │
│  │ • If adequate, close finding                                     │   │
│  └───────────────────────────────┬──────────────────────────────────┘   │
│                                  │                                       │
│                                  ▼                                       │
│  5. CLOSURE                                                             │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │ • Finding marked closed                                          │   │
│  │ • Evidence archived                                              │   │
│  │ • Lessons learned documented                                     │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  ESCALATION FOR OVERDUE FINDINGS:                                       │
│  • 30 days overdue: [YOUR INPUT - Escalate to department head]         │
│  • 60 days overdue: [YOUR INPUT - Escalate to CISO]                    │
│  • 90 days overdue: [YOUR INPUT - Escalate to executive leadership]    │
│  • 120+ days overdue: [YOUR INPUT - Report to Audit Committee]         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

## E.2 Remediation Tracker Template

```
[YOUR INPUT - Design remediation tracker]

AUDIT FINDING REMEDIATION TRACKER
=================================

| Finding ID | Source | Title | Rating | Owner | Due Date | Status | % Complete | Evidence | Notes |
|------------|--------|-------|--------|-------|----------|--------|------------|----------|-------|
| AUD-2026-001 | [YOUR INPUT - IA Q1] | [YOUR INPUT - Excessive admin access] | [YOUR INPUT - High] | [YOUR INPUT - IAM Lead] | [YOUR INPUT - 2026-04-15] | [YOUR INPUT - In Progress] | [YOUR INPUT - 60%] | [YOUR INPUT - Access review report] | [YOUR INPUT - PAM phase 1 complete] |
| AUD-2026-002 | [YOUR INPUT - IA Q1] | [YOUR INPUT - Incomplete logging] | [YOUR INPUT - Medium] | [YOUR INPUT - SOC Manager] | [YOUR INPUT - 2026-05-30] | [YOUR INPUT - Open] | [YOUR INPUT - 20%] | [YOUR INPUT] | [YOUR INPUT - Pending SIEM upgrade] |
| AUD-2026-003 | [YOUR INPUT - ISO Gap] | [YOUR INPUT - No formal risk assessment] | [YOUR INPUT - High] | [YOUR INPUT - GRC Manager] | [YOUR INPUT - 2026-03-31] | [YOUR INPUT - Closed] | [YOUR INPUT - 100%] | [YOUR INPUT - Risk register, methodology] | [YOUR INPUT - Validated Q2] |

SUMMARY DASHBOARD:

Total Open Findings: [YOUR INPUT - XX]
├── Critical: [YOUR INPUT - X]
├── High: [YOUR INPUT - X]
├── Medium: [YOUR INPUT - X]
└── Low: [YOUR INPUT - X]

Overdue Findings: [YOUR INPUT - X]
Average Days to Closure: [YOUR INPUT - XX days]
Closure Rate (This Quarter): [YOUR INPUT - XX%]
```

---

# SECTION F: COMPLIANCE SCENARIOS

## F.1 Scenario: External Audit Preparation

```
[YOUR INPUT - Complete audit preparation scenario]

SCENARIO: ISO 27001 STAGE 2 AUDIT IN 6 WEEKS
============================================

SITUATION:
The ISO 27001 Stage 1 audit completed successfully with only 
minor observations. Stage 2 (certification audit) is scheduled 
in 6 weeks. You need to ensure NordicShield is ready.

The auditor will be on-site for 5 days and will interview 
staff from IT, Security, HR, Development, and Operations.

PREPARATION TASKS:

1. EVIDENCE REVIEW:
   [YOUR INPUT - What evidence needs to be updated/ready?]
   - Risk assessment: [YOUR INPUT - Current and complete?]
   - Policies: [YOUR INPUT - All approved and communicated?]
   - Training records: [YOUR INPUT - All staff trained?]
   - Internal audit: [YOUR INPUT - Results available?]
   - Management review: [YOUR INPUT - Meeting held?]

2. STAFF PREPARATION:
   [YOUR INPUT - How do you prepare staff for interviews?]
   - Identify interviewees: [YOUR INPUT]
   - Briefing sessions: [YOUR INPUT]
   - Practice questions: [YOUR INPUT]
   - Key messages: [YOUR INPUT]

3. LOGISTICS:
   [YOUR INPUT - Audit logistics planning]
   - Audit room: [YOUR INPUT]
   - System access: [YOUR INPUT]
   - Schedule: [YOUR INPUT]
   - Escorts: [YOUR INPUT]

4. GAP CLOSURE:
   [YOUR INPUT - Any remaining gaps to address?]
   - Stage 1 observations: [YOUR INPUT]
   - Known weaknesses: [YOUR INPUT]
   - Priority fixes: [YOUR INPUT]

5. AUDIT WEEK MANAGEMENT:
   [YOUR INPUT - During the audit]
   - Daily debriefs: [YOUR INPUT]
   - Issue escalation: [YOUR INPUT]
   - Evidence requests: [YOUR INPUT]
```

## F.2 Scenario: Regulatory Inquiry

```
[YOUR INPUT - Complete regulatory scenario]

SCENARIO: DATA PROTECTION AUTHORITY INQUIRY
===========================================

SITUATION:
NordicShield receives a letter from the Finnish Data Protection 
Authority (Tietosuojavaltuutetun toimisto) requesting information 
about data processing practices following a complaint from a 
former employee about their personal data.

The DPA has requested:
- List of personal data processed about employees
- Lawful basis for processing
- Retention periods
- Access controls
- Data subject access request procedures

Response deadline: 30 days

RESPONSE TASKS:

1. INITIAL ASSESSMENT:
   [YOUR INPUT - What do you do immediately?]
   - Notify who: [YOUR INPUT - Legal, DPO, CISO, HR]
   - Understand the complaint: [YOUR INPUT]
   - Assess validity: [YOUR INPUT]

2. INFORMATION GATHERING:
   [YOUR INPUT - What information needs to be compiled?]
   - HR data inventory: [YOUR INPUT]
   - Processing activities record: [YOUR INPUT]
   - Privacy notices: [YOUR INPUT]
   - DSAR procedures: [YOUR INPUT]

3. RESPONSE PREPARATION:
   [YOUR INPUT - How do you structure the response?]
   - Legal review: [YOUR INPUT]
   - Evidence compilation: [YOUR INPUT]
   - Response drafting: [YOUR INPUT]

4. REMEDIATION (if gaps found):
   [YOUR INPUT - What if you find compliance gaps?]
   - Document gaps: [YOUR INPUT]
   - Remediation plan: [YOUR INPUT]
   - Voluntary disclosure?: [YOUR INPUT]

5. DOCUMENTATION:
   [YOUR INPUT - What records do you keep?]
```

## F.3 Scenario: Failed Audit Finding

```
[YOUR INPUT - Complete finding remediation scenario]

SCENARIO: CRITICAL AUDIT FINDING
================================

SITUATION:
An internal audit of access management found:
- 47 generic/shared accounts in production systems
- No password rotation for service accounts in 2+ years
- 23 employees with access to systems they no longer need
- No documented privileged access review process

The finding is rated CRITICAL with 30-day remediation deadline.
The CISO is asking for your remediation plan.

REMEDIATION PLANNING:

1. ROOT CAUSE ANALYSIS:
   [YOUR INPUT - Why did this happen?]
   - Process gaps: [YOUR INPUT]
   - Tool limitations: [YOUR INPUT]
   - Resource constraints: [YOUR INPUT]

2. IMMEDIATE ACTIONS (Week 1):
   [YOUR INPUT - What can be done immediately?]
   - Generic accounts: [YOUR INPUT]
   - Orphaned access: [YOUR INPUT]
   - Emergency mitigations: [YOUR INPUT]

3. SHORT-TERM ACTIONS (Weeks 2-4):
   [YOUR INPUT - Complete the core remediation]
   - Service account rotation: [YOUR INPUT]
   - Access review completion: [YOUR INPUT]
   - Process documentation: [YOUR INPUT]

4. LONG-TERM ACTIONS (Post-deadline):
   [YOUR INPUT - Prevent recurrence]
   - PAM implementation: [YOUR INPUT]
   - Automated access reviews: [YOUR INPUT]
   - Policy updates: [YOUR INPUT]

5. EVIDENCE FOR CLOSURE:
   [YOUR INPUT - What evidence proves remediation?]
```

---

# SECTION G: METRICS & REPORTING

## G.1 Compliance KPIs

| Metric | Definition | Target | Current | Trend |
|--------|------------|--------|---------|-------|
| Control Effectiveness | [YOUR INPUT - % of controls operating effectively] | [YOUR INPUT - >95%] | [YOUR INPUT] | [YOUR INPUT] |
| Open Audit Findings | [YOUR INPUT - Number of unresolved findings] | [YOUR INPUT - 0 critical, <5 high] | [YOUR INPUT] | [YOUR INPUT] |
| Finding Closure Rate | [YOUR INPUT - % closed within SLA] | [YOUR INPUT - >90%] | [YOUR INPUT] | [YOUR INPUT] |
| Overdue Findings | [YOUR INPUT - Findings past due date] | [YOUR INPUT - 0] | [YOUR INPUT] | [YOUR INPUT] |
| Policy Compliance | [YOUR INPUT - % of policies reviewed on schedule] | [YOUR INPUT - 100%] | [YOUR INPUT] | [YOUR INPUT] |
| Training Compliance | [YOUR INPUT - % of staff with current training] | [YOUR INPUT - 100%] | [YOUR INPUT] | [YOUR INPUT] |
| Third-Party Assessments | [YOUR INPUT - % of vendors assessed] | [YOUR INPUT - 100% critical] | [YOUR INPUT] | [YOUR INPUT] |
| Certification Status | [YOUR INPUT - Certifications current] | [YOUR INPUT - All current] | [YOUR INPUT] | [YOUR INPUT] |

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 5.3 - Compliance & Audit Program |
| **Phase** | 5 - Security Program Management |
| **Exam Objectives** | 5.4 - Security compliance, 5.5 - Audits and assessments |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
