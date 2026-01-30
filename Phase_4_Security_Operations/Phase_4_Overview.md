# Phase 4: Security Operations
## NordicShield Technologies Oy - Capstone Project

---

```
╔══════════════════════════════════════════════════════════════════╗
║                    PHASE 4: SECURITY OPERATIONS                   ║
║                                                                    ║
║  CompTIA Security+ SY0-701 Domain 4                              ║
║  Weight: 28% of Exam (LARGEST DOMAIN)                            ║
║  Estimated Completion: 18-22 hours                                ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Phase Overview

Phase 4 focuses on **Security Operations** - the day-to-day activities that keep organizations secure. You will build NordicShield's operational security capabilities including their Security Operations Center (SOC), vulnerability management program, identity management, incident response procedures, and automation frameworks.

---

## 🚨 OPERATIONAL SCENARIO: SOC ESTABLISHMENT

### The Situation: Building Security Operations from the Ground Up

```
┌─────────────────────────────────────────────────────────────────┐
│                 SECURITY OPERATIONS INITIATIVE                   │
│                                                                   │
│  Following the security architecture design (Phase 3), the       │
│  Board has approved funding to establish NordicShield's first   │
│  Security Operations Center (SOC).                               │
│                                                                   │
│  CISO DIRECTIVE:                                                 │
│  "We're no longer a startup. With 10,000+ IoT devices, four     │
│   global offices, and nation-state threats like Arctic Fox,     │
│   we need 24/7 security operations. Build it right."            │
│                                                                   │
│  Budget: €1.2M (Year 1)                                         │
│  Timeline: 6 months to Initial Operating Capability (IOC)       │
│  Target: 24/7 coverage by end of year                           │
│                                                                   │
│                          - Sari Korhonen, CISO                   │
└─────────────────────────────────────────────────────────────────┘
```

### Operational Challenges

| Challenge | Current State | Target State |
|-----------|---------------|--------------|
| **Monitoring** | Limited visibility, reactive | 24/7 proactive monitoring |
| **Asset Management** | Spreadsheet-based, 40% coverage | Automated discovery, 100% coverage |
| **Vulnerability Management** | Ad-hoc scanning, no SLAs | Risk-based, continuous scanning |
| **Identity Management** | Manual provisioning, no PAM | Automated lifecycle, zero standing privilege |
| **Incident Response** | Informal process, no playbooks | Mature IR with automation |
| **Automation** | None | SOAR platform with automated response |

### SOC Operating Model

```
                         ┌─────────────────────────────────┐
                         │       SOC LEADERSHIP            │
                         │   SOC Manager (1 FTE)           │
                         └───────────────┬─────────────────┘
                                         │
         ┌───────────────────────────────┼───────────────────────────────┐
         │                               │                               │
    ┌────▼────┐                    ┌────▼────┐                    ┌────▼────┐
    │  TIER 1 │                    │  TIER 2 │                    │  TIER 3 │
    │ ANALYSTS│                    │ ANALYSTS│                    │ ENGINEERS│
    │ (4 FTE) │                    │ (2 FTE) │                    │ (2 FTE) │
    │         │                    │         │                    │         │
    │• Monitor│                    │• Triage │                    │• Hunt   │
    │• Alert  │─────Escalate──────►│• Invest │─────Escalate──────►│• IR Lead│
    │• Triage │                    │• Report │                    │• Forensic│
    └─────────┘                    └─────────┘                    └─────────┘
         │                               │                               │
         └───────────────────────────────┼───────────────────────────────┘
                                         │
                         ┌───────────────▼───────────────┐
                         │      TECHNOLOGY STACK         │
                         │                               │
                         │  SIEM: [To Be Implemented]   │
                         │  EDR:  [To Be Implemented]   │
                         │  SOAR: [To Be Implemented]   │
                         │  TIP:  [To Be Implemented]   │
                         └───────────────────────────────┘
```

---

## Exam Objectives Covered

### Domain 4.1: Security Techniques for Computing Resources (15%)
Given a scenario, apply common security techniques to computing resources

| Topic | Coverage |
|-------|----------|
| Secure baselines and hardening | Deliverable 4.1 |
| Wireless security settings | Deliverable 4.1 |
| Mobile device security | Deliverable 4.1 |
| Application security | Deliverable 4.1 |
| Sandboxing and isolation | Deliverable 4.1 |
| System monitoring | Deliverable 4.1/4.4 |

### Domain 4.2: Asset Management (10%)
Explain the security implications of proper hardware, software, and data asset management

| Topic | Coverage |
|-------|----------|
| Acquisition and procurement | Deliverable 4.2 |
| Assignment and accounting | Deliverable 4.2 |
| Monitoring and tracking | Deliverable 4.2 |
| Disposal and decommissioning | Deliverable 4.2 |
| Data sanitization | Deliverable 4.2 |

### Domain 4.3: Vulnerability Management (15%)
Explain various activities associated with vulnerability management

| Topic | Coverage |
|-------|----------|
| Identification methods | Deliverable 4.3 |
| Analysis (CVSS, prioritization) | Deliverable 4.3 |
| Vulnerability response and remediation | Deliverable 4.3 |
| Validation of remediation | Deliverable 4.3 |
| Reporting | Deliverable 4.3 |

### Domain 4.4: Security Monitoring (15%)
Explain security alerting and monitoring concepts and tools

| Topic | Coverage |
|-------|----------|
| Monitoring computing resources | Deliverable 4.4 |
| Activities (log aggregation, alerting, SCAP) | Deliverable 4.4 |
| Tools (SIEM, UEBA, antivirus, DLP) | Deliverable 4.4 |

### Domain 4.5: Enterprise Capabilities Enhancement (10%)
Given a scenario, modify enterprise capabilities to enhance security

| Topic | Coverage |
|-------|----------|
| Firewall rules and ACLs | Deliverable 4.1/4.4 |
| DLP and network monitoring | Deliverable 4.4 |
| Endpoint protection | Deliverable 4.1 |
| Content filtering | Deliverable 4.1 |

### Domain 4.6: Identity and Access Management (15%)
Given a scenario, implement and maintain identity and access management

| Topic | Coverage |
|-------|----------|
| Provisioning and deprovisioning | Deliverable 4.5 |
| Identity proofing | Deliverable 4.5 |
| SSO, MFA, and federation | Deliverable 4.5 |
| Privileged access management | Deliverable 4.5 |
| Access control models | Deliverable 4.5 |

### Domain 4.7: Automation and Orchestration (10%)
Explain the importance of automation and orchestration related to secure operations

| Topic | Coverage |
|-------|----------|
| Use cases (user provisioning, guardrails, escalation) | Deliverable 4.6 |
| Benefits (efficiency, consistency, reaction time) | Deliverable 4.6 |
| SOAR capabilities | Deliverable 4.6 |

### Domain 4.8: Incident Response (10%)
Explain appropriate incident response activities

| Topic | Coverage |
|-------|----------|
| Process (preparation, detection, containment, eradication, recovery, lessons learned) | Deliverable 4.7 |
| Training and testing | Deliverable 4.7 |
| Digital forensics | Deliverable 4.7 |

### Domain 4.9: Investigation Data Sources
Given a scenario, use data sources to support an investigation

| Topic | Coverage |
|-------|----------|
| Log data (firewall, application, IDS/IPS, OS, etc.) | Deliverable 4.4/4.7 |
| Data sources (vulnerability scans, dashboards, packet captures) | Deliverable 4.3/4.4 |

---

## Phase Deliverables

### Deliverable 4.1: Secure Computing & Hardening Guide
**File:** `Deliverable_4.1_Secure_Computing_Guide.md`

Create comprehensive hardening standards including:
- Secure baseline configurations
- Mobile and wireless security
- Application security controls
- Endpoint protection standards
- System isolation techniques

**Key Outputs:**
- Server hardening checklists (Windows/Linux)
- Endpoint security standards
- Mobile device policy
- Application whitelisting rules

---

### Deliverable 4.2: Asset Management Program
**File:** `Deliverable_4.2_Asset_Management_Program.md`

Build end-to-end asset lifecycle management:
- Hardware asset management
- Software asset management
- Data asset classification (ties to Phase 3)
- Disposal and sanitization procedures

**Key Outputs:**
- Asset inventory procedures
- Procurement security checklist
- Disposal/sanitization standards
- CMDB design

---

### Deliverable 4.3: Vulnerability Management Program
**File:** `Deliverable_4.3_Vulnerability_Management_Program.md`

Establish continuous vulnerability management:
- Scanning strategy
- Risk-based prioritization
- Remediation SLAs
- Exception management
- Metrics and reporting

**Key Outputs:**
- Vulnerability management policy
- Scan schedules
- Remediation workflows
- Exception request forms

---

### Deliverable 4.4: Security Monitoring & SIEM Operations
**File:** `Deliverable_4.4_Security_Monitoring_SIEM.md`

Design comprehensive monitoring program:
- SIEM architecture
- Log management strategy
- Alert rules and use cases
- Dashboards and reporting
- Investigation procedures

**Key Outputs:**
- SIEM use case library
- Log source matrix
- Alert escalation procedures
- SOC runbooks

---

### Deliverable 4.5: Identity & Access Management Program
**File:** `Deliverable_4.5_Identity_Access_Management.md`

Implement enterprise IAM:
- Identity lifecycle management
- Authentication standards (MFA, passwordless)
- Authorization models (RBAC, ABAC)
- Privileged Access Management (PAM)
- Access reviews and certification

**Key Outputs:**
- IAM policy document
- Role definitions
- PAM procedures
- Access review templates

---

### Deliverable 4.6: Security Automation & Orchestration
**File:** `Deliverable_4.6_Security_Automation_SOAR.md`

Build automation capabilities:
- SOAR platform design
- Automated playbooks
- Integration architecture
- Metrics and optimization

**Key Outputs:**
- Automation use cases
- SOAR playbook designs
- Integration specifications
- Automation ROI metrics

---

### Deliverable 4.7: Incident Response Plan & Playbooks
**File:** `Deliverable_4.7_Incident_Response_Plan.md`

Create comprehensive IR program:
- IR policy and procedures
- Role definitions and responsibilities
- Incident classification
- Response playbooks for common scenarios
- Forensics procedures
- Post-incident activities

**Key Outputs:**
- IR policy document
- Incident classification matrix
- Detailed response playbooks
- Forensics toolkit guide

---

## Operational Context & Scenarios

Throughout Phase 4, you'll work with these realistic scenarios:

### Scenario 1: Alert Triage Marathon
```
Monday 08:00: You arrive to find 847 alerts generated over the weekend.
The SOC needs procedures to efficiently triage, prioritize, and 
investigate alerts. Design the processes and automation to handle
alert volume without missing critical threats.
```

### Scenario 2: The Unpatched Server
```
A vulnerability scan reveals CVE-2025-XXXX (CVSS 9.8) on a production 
database server. The DBA says they can't patch until the next quarterly
maintenance window (in 6 weeks). The security team says it must be 
patched immediately. Design the vulnerability management program that 
handles this conflict.
```

### Scenario 3: New Employee Onboarding
```
NordicShield is hiring 50 new employees across 4 offices in 3 months.
Each needs accounts in 12 systems, appropriate group memberships, 
and role-specific access. Design the identity management and 
automation to handle this scale efficiently and securely.
```

### Scenario 4: Ransomware Response
```
At 14:32, Tier 1 analyst notices unusual network traffic from an 
engineering workstation. By 14:45, three more machines show similar
patterns. The IR team has never handled a live ransomware incident.
Create the playbooks and procedures they need.
```

### Scenario 5: The Insider Threat Investigation
```
HR reports concerns about an employee who gave two weeks notice and
has been accessing files they don't normally need. Legal requires
proper evidence collection. Design the investigation procedures using
available data sources.
```

---

## Technology Stack Reference

### Recommended Tools (Reference Only)

| Category | Options | Considerations |
|----------|---------|----------------|
| **SIEM** | Splunk, Microsoft Sentinel, Elastic SIEM, IBM QRadar | Cost, scale, cloud-native |
| **EDR/XDR** | CrowdStrike, Microsoft Defender, SentinelOne, Carbon Black | Coverage, integration |
| **SOAR** | Splunk SOAR, Palo Alto XSOAR, Swimlane, Tines | Playbook complexity |
| **Vulnerability Scanner** | Tenable Nessus, Qualys, Rapid7 InsightVM | Asset discovery, accuracy |
| **IAM** | Microsoft Entra ID, Okta, Ping Identity | Federation, lifecycle |
| **PAM** | CyberArk, BeyondTrust, Delinea | Session recording, JIT |
| **Asset Management** | ServiceNow, Snipe-IT, Lansweeper | CMDB, integration |

---

## Success Criteria

### Phase 4 Completion Requirements

| Deliverable | Criteria | Weight |
|-------------|----------|--------|
| 4.1 Secure Computing | Comprehensive hardening standards with checklists | 15% |
| 4.2 Asset Management | Complete lifecycle procedures | 10% |
| 4.3 Vulnerability Management | Risk-based program with SLAs | 15% |
| 4.4 Security Monitoring | SIEM design with use cases | 15% |
| 4.5 Identity Management | Full IAM/PAM program | 15% |
| 4.6 Automation | SOAR playbooks designed | 15% |
| 4.7 Incident Response | IR plan with tested playbooks | 15% |

### Operational Readiness Metrics

- [ ] 100% critical assets inventoried
- [ ] Vulnerability SLAs defined and achievable
- [ ] 24 core SIEM use cases documented
- [ ] Identity lifecycle < 24 hours for provisioning
- [ ] 10+ automated playbooks designed
- [ ] IR response time targets defined
- [ ] SOC operating procedures documented

---

## Getting Started

### Recommended Approach

1. **Read** the Phase 4 Overview thoroughly (this document)
2. **Review** Phase 2 (threats) and Phase 3 (architecture) for context
3. **Start with** Deliverable 4.2 (Asset Management) - foundational
4. **Build** vulnerability management (4.3) on asset foundation
5. **Design** monitoring (4.4) for visibility
6. **Implement** IAM (4.5) for access control
7. **Automate** with SOAR (4.6) for efficiency
8. **Complete** with IR (4.7) for response readiness

### Research Resources

- NIST SP 800-137 (Continuous Monitoring)
- NIST SP 800-61 (Incident Response)
- NIST SP 800-53 (Security Controls)
- CIS Controls v8
- MITRE ATT&CK Framework
- FIRST CSIRT Services Framework

---

## Document Control

| Field | Value |
|-------|-------|
| **Phase** | 4 - Security Operations |
| **Domain** | CompTIA Security+ SY0-701 Domain 4 |
| **Weight** | 28% of exam (LARGEST) |
| **Deliverables** | 7 |
| **Estimated Time** | 18-22 hours |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
