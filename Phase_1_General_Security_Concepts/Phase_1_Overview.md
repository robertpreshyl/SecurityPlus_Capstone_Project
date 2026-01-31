# Phase 1: General Security Concepts
## NordicShield Technologies Oy - Security Assessment

---

## Phase Overview

| Attribute | Details |
|-----------|---------|
| **Security+ Domain** | 1.0 - General Security Concepts |
| **Exam Weight** | 12% (~11 questions) |
| **Project Duration** | Estimated 4-6 hours |
| **Difficulty** | Foundation Level |

---

## Objectives

In this phase, you will establish the foundational security framework for NordicShield Technologies as they prepare for global expansion. This includes:

1. **Security Controls Assessment** - Categorize and evaluate existing controls
2. **CIA Triad Analysis** - Map business processes to security requirements
3. **Zero Trust Architecture** - Design a modern security model
4. **Change Management Framework** - Establish governance for technical changes
5. **Cryptographic Solutions Review** - Assess and recommend encryption standards

---

## Relevant Exam Objectives (SY0-701)

| Objective | Description |
|-----------|-------------|
| **1.1** | Compare and contrast various types of security controls |
| **1.2** | Summarize fundamental security concepts |
| **1.3** | Explain the importance of change management processes |
| **1.4** | Explain the importance of using appropriate cryptographic solutions |

---

## NordicShield Context

### Current State (From Company Profile)

**What Exists:**
- Perimeter firewall (FortiGate HA) - Maturity 4/5
- Endpoint protection (CrowdStrike) - Maturity 4/5
- Email security (Proofpoint) - Maturity 3/5
- Backup & recovery (Veeam) - Maturity 4/5

**Critical Gaps:**
- No formal security policies documented
- No Zero Trust architecture
- Inconsistent MFA implementation
- Ad-hoc change management
- PKI exists but undocumented

### Business Drivers

1. **Global Expansion** - 4 offices across 3 continents by end of 2026
2. **Compliance Requirements** - GDPR, NIS2, SOC 2, ISO 27001
3. **Board Mandate** - ISO 27001 certification within 18 months
4. **Customer Demands** - Enterprise clients requesting security documentation

---

## Deliverables Checklist

| # | Deliverable | Template | Status |
|---|-------------|----------|--------|
| 1.1 | Security Controls Matrix | `Deliverable_1.1_Security_Controls_Matrix.md` | ✅ Complete |
| 1.2 | CIA Requirements Document | `Deliverable_1.2_CIA_Requirements.md` | ✅ Complete |
| 1.3 | Zero Trust Architecture Plan | `Deliverable_1.3_Zero_Trust_Architecture.md` | ✅ Complete |
| 1.4 | Change Management Policy | `Deliverable_1.4_Change_Management_Policy.md` | ✅ Complete |
| 1.5 | Cryptographic Standards | `Deliverable_1.5_Cryptographic_Standards.md` | ⬜ Not Started |

---

## Instructions

### How to Complete This Phase

1. **Read** each deliverable template carefully
2. **Reference** the Company Profile for context (assets, current state)
3. **Fill in** all sections marked with `[YOUR INPUT]`
4. **Think** like a real security analyst - justify your decisions
5. **Mark** deliverable as complete when finished

### Tips for Success

- **Don't just copy/paste** - Demonstrate your understanding
- **Use specific examples** from NordicShield's environment
- **Reference actual assets** by their Asset IDs (SRV-001, NET-007, etc.)
- **Consider the global expansion** in all recommendations
- **Think compliance** - How does this support ISO 27001/GDPR?

---

## Security Controls Reference (Exam Objective 1.1)

### Control Categories

| Category | Definition | NordicShield Examples |
|----------|------------|----------------------|
| **Technical** | Hardware/software mechanisms | Firewalls, encryption, MFA |
| **Managerial** | Administrative policies | Risk assessments, security policies |
| **Operational** | Day-to-day procedures | Patch management, backup procedures |
| **Physical** | Tangible barriers | Badge access, CCTV, locks |

### Control Types

| Type | Purpose | Examples |
|------|---------|----------|
| **Preventive** | Stop incidents before they occur | Firewalls, training, access controls |
| **Detective** | Identify incidents in progress | SIEM, IDS, log monitoring |
| **Corrective** | Fix issues after detection | Patch deployment, incident response |
| **Deterrent** | Discourage threat actors | Warning banners, cameras, policies |
| **Compensating** | Alternative when primary fails | Manual review when automated fails |
| **Directive** | Guide behavior through policy | AUP, security policies |

---

## Fundamental Concepts Reference (Exam Objective 1.2)

### CIA Triad

| Principle | Definition | Business Impact |
|-----------|------------|-----------------|
| **Confidentiality** | Data accessible only to authorized parties | Trade secrets, customer data protection |
| **Integrity** | Data accurate and unaltered | Financial records, IoT sensor data |
| **Availability** | Systems accessible when needed | 24/7 monitoring platform, customer access |

### AAA Framework

| Component | Function | NordicShield Implementation |
|-----------|----------|----------------------------|
| **Authentication** | Verify identity | Azure AD, MFA |
| **Authorization** | Grant permissions | RBAC, security groups |
| **Accounting** | Track activity | Logs, SIEM |

### Zero Trust Principles

1. **Never trust, always verify**
2. **Assume breach**
3. **Verify explicitly**
4. **Least privilege access**
5. **Micro-segmentation**

---

## Getting Started

**Begin with:** `Deliverable_1.1_Security_Controls_Matrix.md`

This deliverable establishes the baseline understanding of all existing security controls and identifies gaps - essential before designing new solutions.

---

## Document Information

| Field | Value |
|-------|-------|
| **Phase** | 1 of 5 |
| **Domain** | General Security Concepts |
| **Version** | 1.0 |
| **Last Updated** | January 2026 |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
