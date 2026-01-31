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
## Policy Statement

NordicShield Technologies Oy recognizes that uncontrolled changes to IT systems 
and infrastructure pose significant risks to business operations, customer service 
delivery, and regulatory compliance. This policy establishes a structured process 
to ensure all changes are evaluated, authorized, implemented, and reviewed in a 
controlled manner that balances business agility with operational stability.

Purpose: 
- Minimize disruption to business operations and customer-facing services
- Reduce security and operational risks associated with system changes
- Ensure changes are properly documented, tested, and approved
- Support compliance with ISO 27001, SOC 2, GDPR, and NIS2
- Establish accountability for change implementation and outcomes

Scope:
This policy applies to all changes affecting IT infrastructure, applications, cloud 
resources, IoT/OT systems, security configurations, and data structures across all 
NordicShield locations and customer deployments.

Objectives:
- Achieve 95%+ change success rate with minimal rollbacks
- Maintain comprehensive audit trail for compliance requirements
- Protect customer-facing IoT platform availability (99.9% SLA)
- Enable rapid response to security vulnerabilities while maintaining control
- Scale change management processes as company expands to 4 global offices
```

## A.2 Scope

This policy applies to:

| Category | In Scope | Examples |
|----------|----------|----------|
| IT Infrastructure | ☑ Yes | Physical/virtual servers, domain controllers, database servers, storage systems, network devices (FortiGate, switches, routers) |
| Cloud Resources | ☑ Yes | AWS VPCs, security groups, EC2 instances, RDS databases, S3 buckets, IAM policies, Azure AD configurations, M365 settings |
| Applications | ☑ Yes | NordicSense IoT platform, internal web apps, ERP (NetSuite), CRM (Salesforce), GitHub repositories, custom APIs |
| IoT/OT Systems | ☑ Yes | NS-TEMP-200 sensors, NS-GW-1000 gateways, cooling controllers, firmware updates, device configurations, certificate updates |
| Security Configurations | ☑ Yes | Firewall rules, VPN settings, MFA policies, Azure AD Conditional Access, CrowdStrike policies, vulnerability scan configs |
| Database Changes | ☑ Yes | Schema modifications, stored procedures, index changes, data migrations, permission changes, query optimization |

**Out of Scope:**
- Personal device changes (employee home computers, personal phones)
- Changes to development/test environments (must still follow version control)
- Document/content updates (marketing materials, help articles)
- Day-to-day SaaS application usage within existing configurations

## A.3 Roles and Responsibilities

| Role | Responsibilities |
|------|------------------|
| **Change Manager** | IT Director serves as Change Manager; coordinates CAB meetings (weekly); maintains change calendar; tracks metrics; escalates high-risk changes; ensures policy compliance |
| **Change Advisory Board (CAB)** | Members: IT Director, Cloud Architect, Network Engineer, Application Owner, Security Analyst, Customer Success Manager; meets every Wednesday 14:00 UTC; quorum = 4/6 members; reviews and approves normal changes |
| **Emergency CAB (ECAB)** | Members: IT Director + CTO (both required); available 24/7; approves emergency changes via phone/Slack within 1 hour; documents decision within 4 hours; reviews at next CAB meeting |
| **Change Implementer** | Engineer/developer assigned to change; executes implementation plan; monitors during implementation; performs rollback if needed; completes PIR (Post-Implementation Review) within 48 hours |
| **Change Requester** | Any employee submitting change; responsible for business justification, risk assessment, testing plan, rollback plan; must attend CAB if requested; signs off on successful implementation |
| **Security Team** | Security Analyst reviews all security-relevant changes; assesses security impact; can veto changes on security grounds; mandatory approval for firewall, authentication, IoT device changes |
| **Business Owners** | Application/system owner; provides business justification; defines success criteria; approves implementation timing; signs off on PIR; accountable for business impact |

---

# SECTION B: CHANGE TYPES AND CLASSIFICATION

## B.1 Change Categories

### Standard Changes (Pre-Approved)

Pre-approved changes that are low risk, well-documented, and frequently performed.

| Standard Change | Conditions | Auto-Approval |
|-----------------|------------|---------------|
| Password resets | User-initiated via self-service portal; must complete MFA challenge | ☑ Yes |
| New user provisioning | Follows standard template; manager approval in HR system (Workday); role-based access packages | ☑ Yes |
| Scheduled security patches | Pre-approved patch list (Microsoft, Linux, CrowdStrike definitions); tested in staging; scheduled in maintenance window | ☑ Yes |
| SSL certificate renewals | Automated via Let's Encrypt or same CA; no config changes; alert if manual intervention needed | ☑ Yes |
| IoT sensor replacement | Like-for-like hardware swap; same firmware version; customer notified 48 hours prior | ☑ Yes with customer notification |

### Normal Changes

Require CAB review and approval before implementation.

| Impact Level | Description | Approval Required | Example |
|--------------|-------------|-------------------|---------|
| **Minor** | Single system/app; <50 users; rollback <1 hour; dev/test environment | Change Manager approval (no CAB) | Update internal wiki software, add field to non-prod database, firewall rule for dev environment |
| **Moderate** | Multiple systems; 50-500 users; rollback <4 hours; internal business systems | CAB approval (4/6 quorum) | Upgrade Jira to new version, modify internal app API, change AD group policies, firmware update to 10% of IoT sensors |
| **Major** | Customer-facing systems; >500 users; rollback complex; revenue/SLA impact | CAB + CTO approval (unanimous CAB vote required) | NordicSense platform upgrade, AWS multi-region deployment, migrate email to new server, IoT gateway firmware update (all sites) |

Changes required to resolve critical incidents or vulnerabilities.

```
Emergency Change Criteria (must meet at least one):
1. Active security breach in progress (confirmed intrusion, ransomware, data exfiltration)
2. Production system down affecting >100 customers or preventing SLA compliance (>1 hour outage)
3. Critical vulnerability (CVSS 9.0+) being actively exploited in the wild with public exploit available
4. Data integrity issue affecting customer invoicing, IoT sensor data, or financial reporting
5. Regulatory compliance violation requiring immediate remediation (e.g., GDPR breach notification deadline)

Emergency Change Process:
- Authorization: ECAB (IT Director + CTO) must both approve verbally/Slack within 1 hour of request
- Documentation: Full change record created within 4 hours of implementation; photos/screenshots of before/after state
- Post-Implementation Review: Mandatory PIR within 24 hours; presented at next CAB meeting; root cause analysis required; process improvement identified
- Communication: Incident Commander notifies affected stakeholders within 30 minutes; status updates every hour; post-mortem shared within 72 hours
```

## B.2 Change Risk Assessment

### Risk Scoring Matrix

| Risk Factor | Low (1) | Medium (2) | High (3) |
|-------------|---------|------------|----------|
| **System Criticality** | Dev/test/staging environments | Internal business systems (Jira, file server, HR) | Customer-facing (IoT platform, website) or safety-critical (OT controllers) |\n| **Change Complexity** | Single-step procedure; well-documented; done before | Multi-step with dependencies; some documentation | Complex, first-time, requires multiple teams, custom scripts |\n| **Rollback Complexity** | Instant rollback (<15 min); automated | Manual rollback (15min-1hr); tested procedure | Complex rollback (>1 hour), data loss possible, customer coordination needed |\n| **User Impact** | <50 users; minimal disruption; optional feature | 50-500 users; noticeable disruption; scheduled downtime acceptable | >500 users or all customers; unplanned downtime; SLA breach risk |\n| **Security Impact** | No security change | Changes access controls, authentication, or monitoring | Changes perimeter security, encryption, or introduces new attack surface |\n\n**Risk Score Calculation:**\n```\nTotal Score = Sum of all 5 factors (range: 5-15)\n\nScore 5-8: Minor Change →  Change Manager approval (no CAB required; 1-day lead time)\nScore 9-12: Moderate Change → CAB approval (5-day lead time; documented at weekly CAB meeting)\nScore 13+: Major Change → CAB + CTO approval + comprehensive testing (10-day lead time; pilot/staging required)\n```

---

# SECTION C: CHANGE MANAGEMENT PROCESS

## C.1 Process Overview

```
## Change Management Process Flow

1. Request Initiation - Requester submits change via Jira Service Management (change request form)
   ↓
2. Risk Assessment - Change Manager scores risk (1-15 scale) and assigns impact level (Minor/Moderate/Major)
   ↓
3. Security Review - If security-relevant, Security Team reviews and approves/rejects (2-day SLA)
   ↓
4. CAB Review & Approval - Standard changes auto-approved; Minor = Change Manager approval; Moderate/Major = CAB approval
   ↓
5. Scheduling - Change scheduled in maintenance window; stakeholders notified; added to change calendar
   ↓
6. Implementation - Change Implementer executes per plan; monitors for issues; documents results; rollback if needed
   ↓
7. Post-Implementation Review - Verify success criteria; update documentation; close change ticket; capture lessons learned
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
| Frequency | Weekly (every Wednesday 14:00 UTC) | As needed (on-demand 24/7) |
| Attendees | IT Director, Cloud Architect, Network Engineer, Application Owner, Security Analyst, Customer Success Manager (6 total) | IT Director + CTO (both required) |
| Quorum Required | 4 out of 6 members | Both members (2/2) |
| Lead Time Required | 5 business days before meeting (changes submitted by Friday prior) | None (emergency = immediate) |
| Meeting Duration | 60 minutes (10 min per change avg) | 15-30 minutes (phone/Slack) |

### Security Review Criteria

The Security Team must review and approve changes that:

| Criteria | Review Required |
|----------|-----------------|
| Firewall/network changes (rules, VLANs, routing) | ☑ Yes |
| Authentication changes (MFA, SSO, passwords, certs) | ☑ Yes |
| Encryption changes (algorithms, key rotation, TLS versions) | ☑ Yes |
| Access control changes (permissions, roles, conditional access) | ☑ Yes |
| IoT device changes (firmware, certificates, config) | ☑ Yes |
| Third-party integration (new vendor, API access) | ☑ Yes |
| Public-facing services (new ports, DMZ changes) | ☑ Yes |

## C.4 Implementation Phase

### Implementation Requirements

| Requirement | Standard Changes | Normal Changes | Emergency Changes |
|-------------|-----------------|----------------|-------------------|
| Implementation during maintenance window | Not required (low-risk) | Required for production (Tue/Thu 22:00-02:00 UTC or Sunday 06:00-10:00 UTC) | Not required (emergency overrides window) |
| Change freeze blackout respect | Must respect | Must respect (no changes during freeze) | Only for P1 emergencies (CEO approval) |
| Communication to stakeholders | Automated email 24hr prior | Email 5 days prior + 24hr reminder; Slack notification | Immediate Slack notification + incident bridge call |
| Monitoring during implementation | Automated (synthetic checks) | Manual monitoring required (implementer + on-call engineer) | War room established; SOC + on-call + Change Manager monitor |
| Security team notification | None (pre-approved) | Email notification when change starts/completes | Immediate Slack notification to #security channel |

### Change Freeze Periods

| Period | Dates | Applies To | Exceptions |
|--------|-------|------------|------------|
| End of Quarter Financial Close | Last week of Q1/Q2/Q3/Q4 (March 25-31, June 25-30, Sept 25-30, Dec 20-31) | All changes to financial systems (NetSuite, invoicing, payroll) | P1 emergencies with CFO approval |
| Holiday Periods | December 20-January 2; Midsummer (June 20-25 in Finland) | All non-emergency changes (reduced staff coverage) | Security patches, P1/P2 emergencies |
| Audit Periods | SOC 2 audit (typically Feb-March); ISO 27001 surveillance audit (dates TBD) | All changes to in-scope systems; auditor may observe CAB | Critical security patches, emergencies |
| Major Company Events | New office openings (Amsterdam Apr 2026, Austin July 2026, Kigali Oct 2026) | Week before/after office opening - no infrastructure changes | Local IT changes only |

## C.5 Post-Implementation Review

### PIR Requirements

| Review Item | Standard | Normal | Emergency |
|-------------|----------|--------|-----------|
| Verification testing | Automated smoke tests | Requester validates success criteria; sign-off required | Full regression testing; customer validation if customer-impacting |
| Documentation update | Auto-update CMDB | Update runbooks, diagrams, asset inventory, knowledge base | Full incident report + PIR document; RCA within 72 hours |
| Stakeholder sign-off | Not required (automated) | Business owner sign-off in Jira within 48 hours | CTO + affected business unit sign-off; customer notification if applicable |
| Lessons learned | Not required | Document if issues encountered | ☑ Mandatory - presented at next CAB; process improvements identified |
| Metrics capture | Automated (success/fail) | Duration, issues, rollback (if any) | Full timeline, root cause, preventive measures, cost impact |

```
If a change fails or causes unexpected issues:

Immediate Actions (within 15 minutes):
1. Initiate rollback immediately per documented rollback plan; do not troubleshoot if SLA at risk
2. Create P1 incident ticket in Jira; link to change request; notify Change Manager + on-call engineer
3. Communicate status to affected stakeholders via Slack + email; establish incident bridge if customer-impacting

Within 24 Hours:
1. Complete rollback and verify system stability; document final state
2. Conduct hot wash meeting with implementer, Change Manager, and system owner
3. Update change ticket with failure details; mark change as "Failed - Rolled Back"
4. Notify customers if SLA was breached; calculate any penalties owed

Root Cause Analysis:
Required for: All emergency changes (even if successful), all failed normal/major changes, any customer-impacting incident
Timeline: RCA document due within 72 hours of incident closure
Process: 5 Whys methodology; identify root cause, contributing factors, preventive measures
Presentation: RCA presented at next CAB meeting; action items tracked in backlog
```

---

# SECTION D: SPECIAL CHANGE SCENARIOS

## D.1 IoT/OT Changes

Given NordicShield's 827+ IoT devices, special considerations apply:

| Consideration | Policy | Justification |
|---------------|--------|---------------|
| Firmware updates | Phased rollout: Pilot with 5% of devices (5 customer sites) → Monitor 48 hours → Rollout to 25% → Monitor 72 hours → Rollout to remaining 70% over 7 days | Safety critical systems; cannot update all 827 sensors at once; need time to detect anomalies; customer SLAs require staggered updates |
| Configuration changes | Require customer notification 48 hours prior; implement during customer-approved maintenance windows only | Customer owns the facility; changes affect their operations; contractual requirement for notification |
| Certificate rotation | Automated renewal 30 days before expiry; manual exception process if device unreachable; monitor cert expiry daily | 827 devices = cannot manage manually; automated renewal prevents outages; some customer firewalls may block auto-renewal |
| Remote vs on-site | Remote changes = default for config/firmware; On-site required for: hardware replacement, physical tampering investigation, customer network issues | Travel to 47 customer sites not scalable; remote access reduces cost/time; on-site only when absolutely necessary |
| Customer site changes | Customer approval required (email confirmation); customer representatives can request to observe; rollback plan must not require NordicShield on-site presence (<4 hour rollback) | Customer owns physical access; courtesy and contractual obligation; rollback must be remote to meet SLA |

### IoT Change Windows

| IoT System Type | Allowed Change Window | Justification |
|-----------------|----------------------|---------------|
| Temperature sensors (NS-TEMP-200) | Anytime (24/7) with 48hr notice; recommended: customer off-peak hours | Sensors are monitoring-only; no direct control of physical systems; brief outage acceptable (data buffered in gateway for 24 hours) |
| Cooling controllers (NS-CTRL-500) | Customer-approved maintenance window ONLY; typically: 02:00-05:00 local time on Sunday; max 2-hour window | Safety critical - controls physical HVAC equipment; failure could cause data center overheating; must coordinate with customer facility team |
| Gateway devices (NS-GW-1000) | Anytime with 48hr notice; redundant gateways = rolling updates; single gateway sites = customer maintenance window only | Gateways aggregate sensor data; loss of gateway = loss of monitoring; redundant sites can tolerate one gateway down; single gateway sites are high-risk |

## D.2 Cloud Infrastructure Changes

| Cloud Change Type | Approval Level | Additional Requirements |
|-------------------|----------------|------------------------|
| AWS security group changes | CAB + Security Team approval | Must document: source IP/port, destination IP/port, business justification, expiry date (if temporary); quarterly review of all rules |
| IAM policy changes | CAB + Security Team approval + peer review | Principle of least privilege enforced; MFA required for humans; service roles for automation; no wildcard (*) permissions without CISO approval |
| New resource provisioning | Change Manager approval (if within budget); CAB approval (if new service) | Must use Infrastructure as Code (Terraform); tag with: owner, cost-center, environment, expiry-date; encryption at rest required |
| Production deployments | Moderate change (CAB approval) for minor releases; Major change for breaking changes | Blue/green deployment required; automated rollback capability; canary testing (10% traffic) for 1 hour before full rollout |
| Infrastructure as Code changes | Peer review (2 engineers) + automated tests pass; CAB approval for production | GitHub pull request required; Terraform plan reviewed; automated security scanning (Checkov); state file backed up before apply |

## D.3 Multi-Region Changes

Changes affecting multiple offices:

| Scenario | Coordination Required | Rollout Strategy |
|----------|---------------------|------------------|
| Global security policy (firewall rules, MFA settings, Conditional Access) | All office IT leads must acknowledge (Turku, Amsterdam, Austin, Kigali); CAB must include at least one rep from each region | Staged: Pilot in Turku (HQ) → Monitor 1 week → Amsterdam → Austin → Kigali (stagger by 3-5 days to allow for issues) |
| Time zone considerations for maintenance windows | Schedule change at time acceptable for all offices; may require weekend implementation; calculate: Turku (UTC+2), Amsterdam (UTC+1), Austin (UTC-6), Kigali (UTC+2) | Use UTC for all scheduling; aim for: Sunday 04:00-08:00 UTC (acceptable for all regions) or stagger per-region outside business hours |
| Language/locale changes (M365, Salesforce, UI translations) | Coordinate with local office managers; provide translated documentation; schedule training in local language | Per-region rollout: Each office opts in when ready; Finnish/Dutch/English/French translations required; 2-week notice minimum |

## D.4 Third-Party/Vendor Changes

| Change Type | NordicShield Responsibility | Vendor Responsibility | Notification |
|-------------|---------------------------|----------------------|--------------|
| SaaS updates (M365, Salesforce, AWS services) | Review release notes; test in non-prod; assess impact; communicate to users | Provide 30-day advance notice (or per SLA); maintain backward compatibility; provide rollback window | Vendor must notify via: email to IT Director + update Change Calendar; emergency changes require 24-hour notice minimum |
| Managed service changes (CrowdStrike policies, FortiGate firmware) | Approve change; schedule window; monitor during implementation; validate post-change | Implement change per schedule; provide implementation plan + rollback plan; 24/7 support during change window | 2-week notice for standard changes; 48-hour notice for critical security patches; must attend CAB if requested |
| API changes (breaking changes, deprecations) | Update application code; test integration; plan cutover; monitor error rates | Provide 90-day deprecation notice for breaking changes; maintain backward compatibility during transition; version all APIs | Vendor must notify via: email + API changelog + developer portal announcement; breaking changes require CAB review |

---

# SECTION E: DOCUMENTATION AND RECORDS

## E.1 Required Documentation

| Document | Retention Period | Storage Location |
|----------|-----------------|------------------|
| Change requests (all types) | 7 years (regulatory requirement - SOC 2, ISO 27001) | Jira Service Management (primary); exported to SharePoint annually for long-term retention |
| CAB meeting minutes | 7 years | SharePoint (ISO 27001 A.16.1.7 records) |
| Implementation logs (scripts output, before/after screenshots) | 3 years | Jira attachments + S3 bucket (change-logs-bucket) with versioning enabled |
| Rollback documentation | 3 years or until system decommissioned (whichever longer) | Confluence wiki (linked from change ticket) + Git repository for scripts |
| PIR reports (including RCAs for failed changes) | 5 years | SharePoint (lessons learned repository); searchable by system/change type |

## E.2 Audit Trail Requirements

For compliance (ISO 27001, SOC 2, NIS2):

| Requirement | How Addressed |
|-------------|---------------|
| All changes logged | Every change tracked in Jira with workflow: Draft → Submitted → Under Review → Approved → Scheduled → Implementing → Complete/Failed; state transitions logged with timestamp + user |
| Approvals documented | Approval captured in Jira with approver name, timestamp, comments; CAB approvals documented in meeting minutes with vote tally; email confirmations archived |
| Implementation tracked | Start time, end time, implementer name logged; session recordings for critical changes; Git commits linked to change ticket; CloudTrail/Azure Activity Logs for cloud changes |
| Unauthorized changes detected | File Integrity Monitoring (Wazuh) on servers; AWS Config detects drift; Azure Policy compliance; CrowdStrike detects unauthorized software; SIEM correlates changes with change tickets; alerts on changes without approved ticket |

---

# SECTION F: METRICS AND REPORTING

## F.1 Change Management KPIs

| Metric | Target | Current | Measurement Method |
|--------|--------|---------|-------------------|
| Change success rate | ≥95% (successful without rollback) | Baseline TBD | (Successful changes / Total changes) * 100; measured monthly |
| Emergency change percentage | <10% (most changes should be planned) | Baseline TBD | (Emergency changes / Total changes) * 100; investigate if exceeds 10% |
| Average change lead time | Minor: 2 days; Moderate: 7 days; Major: 14 days | Baseline TBD | Time from submission to approval; tracked in Jira; reported weekly |
| Change-related incidents | <5% of changes cause incidents | Baseline TBD | Count of P1/P2 incidents with root cause = recent change; investigate each instance |
| Unauthorized changes detected | 0 (all changes must be authorized) | Baseline TBD | FIM/AWS Config/Azure Policy alerts; SIEM correlation; investigated as security incidents |
| CAB meeting attendance | ≥67% (4/6 members minimum) | Baseline TBD | Attendance logged in meeting minutes; notify absent members; escalate if quorum not met |

## F.2 Reporting Cadence

| Report | Audience | Frequency |
|--------|----------|-----------|
| Change calendar (upcoming changes) | All IT staff + business stakeholders | Weekly (every Monday); shows next 2 weeks of scheduled changes |
| Change success summary (KPIs dashboard) | IT management + CAB members | Monthly (first Wednesday of month); includes success rate, lead time, incident correlation |
| Failed changes analysis (deep-dive) | CAB + affected system owners | After each failed change (within 5 days); includes RCA, lessons learned, preventive measures |
| Emergency changes review | ECAB + CTO + CISO | Monthly (second Wednesday); reviews all emergency changes for patterns; identifies process improvements |
| Quarterly metrics report (executive summary) | Board of Directors + Executive team | Quarterly (within 2 weeks of quarter end); trends, compliance status, major changes summary, risks |

# SECTION G: COMPLIANCE MAPPING

## G.1 Regulatory Requirements

| Framework | Requirement | How This Policy Addresses |
|-----------|-------------|--------------------------|
| ISO 27001 (A.12.1.2) | Change management process | Formal CAB process; documented change types; approval workflows; testing requirements; rollback procedures - fully addresses control |
| SOC 2 (CC6.1) | Logical access controls monitored for changes | Security Team reviews all access control changes; unauthorized changes detected via SIEM/FIM; audit trail maintained with 7-year retention |
| SOC 2 (CC8.1) | Change management procedures implemented | Documented procedures for requesting, approving, testing, implementing changes; segregation of duties (requester ≠ implementer ≠ approver); change tickets retained for auditor review |
| NIS2 (Article 21.2) | Security measures for network/information systems | All infrastructure changes require security review; IoT OT systems have specific change controls; cyber incident response linked to failed changes |
| GDPR (Article 25) | Data protection by design and by default | Security & privacy impact assessment required for changes affecting personal data processing; DPO consulted for GDPR-relevant changes; data minimization considered in new system provisioning |

## G.2 Security+ Concepts Applied

| Security+ Concept | Application in This Policy |
|-------------------|---------------------------|
| Change management (1.3) | Core policy focus: documented process, approval workflows, CAB structure, impact assessment, rollback procedures, PIR - directly addresses exam objective |
| Technical controls (1.1) | FIM for unauthorized change detection; automated compliance checks (AWS Config, Azure Policy); SIEM correlation of changes with incidents; infrastructure  as code (Terraform) |
| Administrative controls (1.1) | Change Management Policy itself; CAB governance; approval authorities; change freeze periods; KPI tracking; quarterly reporting to executives |
| Documentation (5.4) | 7-year retention of change records; CAB meeting minutes; implementation logs; audit trail for compliance; PIR reports with lessons learned |
| Risk assessment (5.2) | Risk scoring matrix (1-15 scale) for every change; factors: criticality, complexity, rollback difficulty, user impact, security impact; score determines approval level |

---

# SECTION H: POLICY MAINTENANCE

## H.1 Policy Review

| Review Activity | Frequency | Responsible Party |
|-----------------|-----------|-------------------|
| Annual policy review (comprehensive update) | Annually (every January); version number incremented; staff notified of changes | Change Manager (IT Director) leads review; CAB approves updates; CISO signs off; published to policy portal |
| Post-incident review (if change-related) | Within 1 week of any P1/P2 incident caused by change | Change Manager + affected teams; assess if policy would have prevented incident; recommend policy updates |
| Regulatory update review (compliance-driven) | As needed when ISO 27001, SOC 2, NIS2, GDPR requirements change | Compliance Manager notifies Change Manager; policy updated within 30 days; legal review if needed; staff training on changes |

## H.2 Policy Exceptions

```
## Policy Exception Process

Rarely, circumstances may require an exception to this policy (e.g., vendor-mandated urgent change outside maintenance window, merger/acquisition activity, regulatory emergency).

Exception requests must include:
1. Business justification (why exception is required; what happens if not granted)
2. Risk assessment (what risks are introduced by bypassing normal process; mitigation measures)
3. Compensating controls (additional monitoring, additional approvals, accelerated PIR)
4. Duration (is this one-time or temporary ongoing; if ongoing, when will standard process resume)

Approval authority:
- Minor policy exceptions: Change Manager approval
- Moderate exceptions: CAB approval
- Major exceptions (e.g., skipping testing, bypassing CAB): CTO approval + CISO review

Duration: Exceptions are valid for single change only (default); if ongoing exception needed, must specify end date (maximum 90 days)

Documentation: Exception logged in Jira; rationale documented; reviewed at next CAB meeting; reported in quarterly metrics; auditor notified if compliance-relevant
```

---

# SECTION I: EXECUTIVE SUMMARY

# SECTION I: EXECUTIVE SUMMARY

NordicShield Technologies' rapid global expansion from one office to four, combined with 827+ IoT devices deployed at customer sites and hybrid cloud infrastructure, has dramatically increased the complexity and risk of IT changes. Uncontrolled changes to production systems, IoT firmware, or security configurations could result in customer SLA breaches (€5K-€50K per hour), safety incidents at customer facilities, data breaches, or regulatory non-compliance. This Change Management Policy establishes formal governance to balance business agility with operational stability.

**Why Change Management is Critical:**
- IoT Safety Risk: Firmware bugs in cooling controllers could cause data center equipment failure at 47 customer sites
- Compliance Obligation: ISO 27001 (A.12.1.2), SOC 2 (CC8.1), and NIS2 mandate documented change management
- Scale Challenge: Managing changes across 4 time zones, 4 languages, and 120 employees requires formal process
- Customer Trust: SLA commitments (99.9% availability) depend on controlled, tested changes

**Key Policy Elements:**
- Three change types: Standard (pre-approved, low-risk), Normal (CAB-reviewed), Emergency (ECAB-approved)
- Risk Scoring: 1-15 scale assessing criticality, complexity, rollback difficulty, user impact, security impact
- Change Advisory Board: 6 members meet weekly; 4/6 quorum; reviews all moderate/major changes
- Special Scenarios: IoT changes use phased rollout (5% → 25% → 70% over 7 days); cloud changes require Infrastructure as Code; multi-region changes stagger by time zone

**Special Considerations:**
- IoT/OT: 48-hour customer notification for sensor changes; cooling controller changes require customer maintenance window approval (safety critical)
- Global Offices: Sunday 04:00-08:00 UTC maintenance window acceptable for all 4 offices; change freeze during new office openings
- Compliance: 7-year retention of change records; unauthorized change detection via FIM/SIEM; quarterly metrics to Board

**Expected Benefits:**
- Reduce change-related incidents from current baseline to <5% (target: 95%+ success rate)
- Demonstrate compliance for ISO 27001 certification (addresses A.12.1.2 control)
- Enable auditable process for SOC 2 Type II attestation
- Prevent customer SLA breaches caused by failed changes (estimated savings: €100K+ annually)
- Scale change management as company grows to 200+ employees by end of 2027

**Implementation:** Policy effective immediately (February 1, 2026); CAB inaugural meeting February 5; Jira workflows configured February 1; staff training February 3-7; first monthly metrics report due March 12.

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 1.4 - Change Management Policy |
| **Phase** | 1 - General Security Concepts |
| **Exam Objective** | 1.3 - Explain the importance of change management processes |
| **Status** | ✅ Complete |
| **Completed By** | Robert Preshyl |
| **Completion Date** | January 31, 2026 |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
