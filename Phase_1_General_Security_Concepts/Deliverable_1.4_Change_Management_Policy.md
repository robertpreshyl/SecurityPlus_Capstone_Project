# Deliverable 1.4: Change Management Policy
## NordicShield Technologies Oy

---

## Document Purpose

This document establishes a comprehensive Change Management Policy for NordicShield Technologies, ensuring that all changes to IT systems, applications, and infrastructure are controlled, documented, and implemented with minimal risk to business operations.

---

## Instructions

1. Review the company profile for systems and infrastructure
2. Complete all `[YOUR INPUT]` sections with appropriate policies
3. Consider the unique challenges of IoT, global operations, and rapid expansion
4. Align with compliance requirements (ISO 27001, SOC 2, NIS2)

---

# SECTION A: POLICY OVERVIEW

## A.1 Policy Statement

```
[YOUR INPUT - Write a formal policy statement]

NordicShield Technologies Oy recognizes that uncontrolled changes to IT systems 
and infrastructure pose significant risks to...

Purpose: 
Scope:
Objectives:
```

## A.2 Scope

This policy applies to:

| Category | In Scope | Examples |
|----------|----------|----------|
| IT Infrastructure | ☐ Yes / ☐ No | [YOUR INPUT - servers, network devices, firewalls] |
| Cloud Resources | ☐ Yes / ☐ No | [YOUR INPUT - AWS, Azure, SaaS configurations] |
| Applications | ☐ Yes / ☐ No | [YOUR INPUT - NordicSense platform, internal apps] |
| IoT/OT Systems | ☐ Yes / ☐ No | [YOUR INPUT - sensors, controllers, gateways] |
| Security Configurations | ☐ Yes / ☐ No | [YOUR INPUT - firewall rules, access policies] |
| Database Changes | ☐ Yes / ☐ No | [YOUR INPUT - schema changes, stored procedures] |

**Out of Scope:**
- [YOUR INPUT - What is explicitly excluded?]

## A.3 Roles and Responsibilities

| Role | Responsibilities |
|------|------------------|
| **Change Manager** | [YOUR INPUT - Who is this? What do they do?] |
| **Change Advisory Board (CAB)** | [YOUR INPUT - Who is on the CAB? When do they meet?] |
| **Emergency CAB (ECAB)** | [YOUR INPUT - Who approves emergencies?] |
| **Change Implementer** | [YOUR INPUT] |
| **Change Requester** | [YOUR INPUT] |
| **Security Team** | [YOUR INPUT - Security review responsibilities] |
| **Business Owners** | [YOUR INPUT] |

---

# SECTION B: CHANGE TYPES AND CLASSIFICATION

## B.1 Change Categories

### Standard Changes (Pre-Approved)

Pre-approved changes that are low risk, well-documented, and frequently performed.

| Standard Change | Conditions | Auto-Approval |
|-----------------|------------|---------------|
| [YOUR INPUT - e.g., Password resets] | [YOUR INPUT] | ☐ Yes / ☐ No |
| [YOUR INPUT - e.g., New user provisioning] | [YOUR INPUT] | ☐ Yes / ☐ No |
| [YOUR INPUT - e.g., Scheduled patches] | [YOUR INPUT] | ☐ Yes / ☐ No |
| [YOUR INPUT] | [YOUR INPUT] | ☐ Yes / ☐ No |
| [YOUR INPUT] | [YOUR INPUT] | ☐ Yes / ☐ No |

### Normal Changes

Require CAB review and approval before implementation.

| Impact Level | Description | Approval Required | Example |
|--------------|-------------|-------------------|---------|
| **Minor** | [YOUR INPUT] | [YOUR INPUT - Single approver?] | [YOUR INPUT] |
| **Moderate** | [YOUR INPUT] | [YOUR INPUT - CAB approval?] | [YOUR INPUT] |
| **Major** | [YOUR INPUT] | [YOUR INPUT - CAB + Executive?] | [YOUR INPUT] |

### Emergency Changes

Changes required to resolve critical incidents or vulnerabilities.

```
Emergency Change Criteria (must meet at least one):
1. [YOUR INPUT - e.g., Active security breach in progress]
2. [YOUR INPUT - e.g., Production system down affecting customers]
3. [YOUR INPUT - e.g., Critical vulnerability being actively exploited]
4. [YOUR INPUT]

Emergency Change Process:
- Authorization: [YOUR INPUT]
- Documentation: [YOUR INPUT - When must it be documented?]
- Post-Implementation Review: [YOUR INPUT - Required within X hours?]
```

## B.2 Change Risk Assessment

### Risk Scoring Matrix

| Risk Factor | Low (1) | Medium (2) | High (3) |
|-------------|---------|------------|----------|
| **System Criticality** | [YOUR INPUT - Dev/test] | [YOUR INPUT - Internal business] | [YOUR INPUT - Customer-facing/IoT] |
| **Change Complexity** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Rollback Complexity** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **User Impact** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Security Impact** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

**Risk Score Calculation:**
```
Total Score = [YOUR INPUT - How are these factors combined?]

Score 5-8: Minor Change - [YOUR INPUT - Approval level]
Score 9-12: Moderate Change - [YOUR INPUT - Approval level]
Score 13+: Major Change - [YOUR INPUT - Approval level]
```

---

# SECTION C: CHANGE MANAGEMENT PROCESS

## C.1 Process Overview

```
[YOUR INPUT - Create a process flow description or diagram]

1. Request Initiation
   ↓
2. [YOUR INPUT]
   ↓
3. [YOUR INPUT]
   ↓
4. [YOUR INPUT]
   ↓
5. [YOUR INPUT]
   ↓
6. [YOUR INPUT]
   ↓
7. Post-Implementation Review
```

## C.2 Request Initiation

### Required Information

| Field | Required | Description |
|-------|----------|-------------|
| Change Title | ☑ Yes | [YOUR INPUT] |
| Requester | ☑ Yes | [YOUR INPUT] |
| Business Justification | ☑ Yes | [YOUR INPUT] |
| Systems Affected | ☑ Yes | [YOUR INPUT - Link to asset inventory] |
| Implementation Plan | ☑ Yes | [YOUR INPUT] |
| Rollback Plan | ☑ Yes | [YOUR INPUT] |
| Test Plan | ☑ Yes | [YOUR INPUT] |
| Scheduled Window | ☑ Yes | [YOUR INPUT] |
| Estimated Duration | ☑ Yes | [YOUR INPUT] |
| Security Impact Assessment | ☑ Yes | [YOUR INPUT] |
| Communication Plan | ☐ Depends | [YOUR INPUT - When required?] |

### Change Request Form Template

```
CHANGE REQUEST #: [Auto-generated]
DATE SUBMITTED: 
REQUESTER:
DEPARTMENT:

CHANGE DESCRIPTION:
[YOUR INPUT - What format?]

BUSINESS JUSTIFICATION:
[YOUR INPUT]

SYSTEMS/ASSETS AFFECTED:
[YOUR INPUT - Reference asset IDs from inventory]

RISK ASSESSMENT SCORE: [X/15]

IMPLEMENTATION PLAN:
1.
2.
3.

ROLLBACK PLAN:
1.
2.
3.

TEST VALIDATION:
☐ 
☐ 
☐ 

SCHEDULED IMPLEMENTATION WINDOW:
Date:
Time (UTC):
Duration:

APPROVALS REQUIRED:
☐ Change Manager
☐ System Owner
☐ Security Team
☐ CAB
☐ [OTHER]
```

## C.3 Review and Approval Process

### CAB Meeting Structure

| Element | Standard CAB | ECAB |
|---------|--------------|------|
| Frequency | [YOUR INPUT - Weekly?] | [YOUR INPUT - As needed?] |
| Attendees | [YOUR INPUT] | [YOUR INPUT] |
| Quorum Required | [YOUR INPUT] | [YOUR INPUT] |
| Lead Time Required | [YOUR INPUT - 5 days?] | [YOUR INPUT] |
| Meeting Duration | [YOUR INPUT] | [YOUR INPUT] |

### Security Review Criteria

The Security Team must review and approve changes that:

| Criteria | Review Required |
|----------|-----------------|
| [YOUR INPUT - Firewall/network changes] | ☐ Yes |
| [YOUR INPUT - Authentication changes] | ☐ Yes |
| [YOUR INPUT - Encryption changes] | ☐ Yes |
| [YOUR INPUT - Access control changes] | ☐ Yes |
| [YOUR INPUT - IoT device changes] | ☐ Yes |
| [YOUR INPUT - Third-party integration] | ☐ Yes |
| [YOUR INPUT] | ☐ Yes |

## C.4 Implementation Phase

### Implementation Requirements

| Requirement | Standard Changes | Normal Changes | Emergency Changes |
|-------------|-----------------|----------------|-------------------|
| Implementation during maintenance window | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Change freeze blackout respect | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Communication to stakeholders | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Monitoring during implementation | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Security team notification | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Change Freeze Periods

| Period | Dates | Applies To | Exceptions |
|--------|-------|------------|------------|
| [YOUR INPUT - End of quarter?] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT - Holiday periods?] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT - Audit periods?] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## C.5 Post-Implementation Review

### PIR Requirements

| Review Item | Standard | Normal | Emergency |
|-------------|----------|--------|-----------|
| Verification testing | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Documentation update | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Stakeholder sign-off | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Lessons learned | [YOUR INPUT] | [YOUR INPUT] | ☑ Required |
| Metrics capture | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Failed Change Process

```
If a change fails or causes unexpected issues:

Immediate Actions:
1. [YOUR INPUT - Initiate rollback?]
2. [YOUR INPUT - Incident ticket?]
3. [YOUR INPUT - Notify stakeholders?]

Within 24 Hours:
1. [YOUR INPUT]
2. [YOUR INPUT]

Root Cause Analysis:
[YOUR INPUT - When is RCA required?]
```

---

# SECTION D: SPECIAL CHANGE SCENARIOS

## D.1 IoT/OT Changes

Given NordicShield's 827+ IoT devices, special considerations apply:

| Consideration | Policy | Justification |
|---------------|--------|---------------|
| Firmware updates | [YOUR INPUT - Staged rollout?] | [YOUR INPUT - Safety critical, can't update all at once] |
| Configuration changes | [YOUR INPUT] | [YOUR INPUT] |
| Certificate rotation | [YOUR INPUT] | [YOUR INPUT] |
| Remote vs on-site | [YOUR INPUT] | [YOUR INPUT] |
| Customer site changes | [YOUR INPUT - Customer notification?] | [YOUR INPUT] |

### IoT Change Windows

| IoT System Type | Allowed Change Window | Justification |
|-----------------|----------------------|---------------|
| Temperature sensors | [YOUR INPUT] | [YOUR INPUT] |
| Cooling controllers | [YOUR INPUT - More restrictive?] | [YOUR INPUT - Safety critical] |
| Gateway devices | [YOUR INPUT] | [YOUR INPUT] |

## D.2 Cloud Infrastructure Changes

| Cloud Change Type | Approval Level | Additional Requirements |
|-------------------|----------------|------------------------|
| AWS security group changes | [YOUR INPUT] | [YOUR INPUT - Security review?] |
| IAM policy changes | [YOUR INPUT] | [YOUR INPUT] |
| New resource provisioning | [YOUR INPUT] | [YOUR INPUT] |
| Production deployments | [YOUR INPUT] | [YOUR INPUT] |
| Infrastructure as Code changes | [YOUR INPUT] | [YOUR INPUT - Peer review?] |

## D.3 Multi-Region Changes

Changes affecting multiple offices:

| Scenario | Coordination Required | Rollout Strategy |
|----------|---------------------|------------------|
| Global security policy | [YOUR INPUT - All regions must approve?] | [YOUR INPUT - Simultaneous or staged?] |
| Time zone considerations | [YOUR INPUT] | [YOUR INPUT] |
| Language/locale changes | [YOUR INPUT] | [YOUR INPUT] |

## D.4 Third-Party/Vendor Changes

| Change Type | NordicShield Responsibility | Vendor Responsibility | Notification |
|-------------|---------------------------|----------------------|--------------|
| SaaS updates | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - When must vendor notify?] |
| Managed service changes | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| API changes | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION E: DOCUMENTATION AND RECORDS

## E.1 Required Documentation

| Document | Retention Period | Storage Location |
|----------|-----------------|------------------|
| Change requests | [YOUR INPUT - 7 years?] | [YOUR INPUT - ITSM tool?] |
| CAB meeting minutes | [YOUR INPUT] | [YOUR INPUT] |
| Implementation logs | [YOUR INPUT] | [YOUR INPUT] |
| Rollback documentation | [YOUR INPUT] | [YOUR INPUT] |
| PIR reports | [YOUR INPUT] | [YOUR INPUT] |

## E.2 Audit Trail Requirements

For compliance (ISO 27001, SOC 2, NIS2):

| Requirement | How Addressed |
|-------------|---------------|
| All changes logged | [YOUR INPUT] |
| Approvals documented | [YOUR INPUT] |
| Implementation tracked | [YOUR INPUT] |
| Unauthorized changes detected | [YOUR INPUT - Integrity monitoring?] |

---

# SECTION F: METRICS AND REPORTING

## F.1 Change Management KPIs

| Metric | Target | Current | Measurement Method |
|--------|--------|---------|-------------------|
| Change success rate | [YOUR INPUT - 95%?] | [YOUR INPUT] | [YOUR INPUT] |
| Emergency change percentage | [YOUR INPUT - <10%?] | [YOUR INPUT] | [YOUR INPUT] |
| Average change lead time | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Change-related incidents | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Unauthorized changes detected | [YOUR INPUT - 0?] | [YOUR INPUT] | [YOUR INPUT] |
| CAB meeting attendance | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## F.2 Reporting Cadence

| Report | Audience | Frequency |
|--------|----------|-----------|
| Change calendar | [YOUR INPUT] | [YOUR INPUT] |
| Change success summary | [YOUR INPUT] | [YOUR INPUT] |
| Failed changes analysis | [YOUR INPUT] | [YOUR INPUT] |
| Emergency changes review | [YOUR INPUT] | [YOUR INPUT] |
| Quarterly metrics report | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION G: COMPLIANCE MAPPING

## G.1 Regulatory Requirements

| Framework | Requirement | How This Policy Addresses |
|-----------|-------------|--------------------------|
| ISO 27001 (A.12.1.2) | Change management | [YOUR INPUT] |
| SOC 2 (CC6.1) | Logical access controls | [YOUR INPUT] |
| SOC 2 (CC8.1) | Change management | [YOUR INPUT] |
| NIS2 | Security measures | [YOUR INPUT] |
| GDPR | Data protection by design | [YOUR INPUT] |

## G.2 Security+ Concepts Applied

| Security+ Concept | Application in This Policy |
|-------------------|---------------------------|
| Change management (1.3) | [YOUR INPUT] |
| Technical controls | [YOUR INPUT] |
| Administrative controls | [YOUR INPUT] |
| Documentation | [YOUR INPUT] |
| Risk assessment | [YOUR INPUT] |

---

# SECTION H: POLICY MAINTENANCE

## H.1 Policy Review

| Review Activity | Frequency | Responsible Party |
|-----------------|-----------|-------------------|
| Annual policy review | [YOUR INPUT] | [YOUR INPUT] |
| Post-incident review | [YOUR INPUT] | [YOUR INPUT] |
| Regulatory update review | [YOUR INPUT] | [YOUR INPUT] |

## H.2 Policy Exceptions

```
[YOUR INPUT - Define the exception process]

Exception requests must include:
1.
2.
3.

Approval authority:
Duration:
Documentation:
```

---

# SECTION I: EXECUTIVE SUMMARY

```
[YOUR INPUT - Write a 150-250 word executive summary]

Include:
- Why change management is critical for NordicShield
- Key policy elements
- Special considerations (IoT, global expansion, compliance)
- Expected benefits
- Implementation approach
```

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 1.4 - Change Management Policy |
| **Phase** | 1 - General Security Concepts |
| **Exam Objective** | 1.3 - Explain the importance of change management processes |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
