# Deliverable 1.3: Zero Trust Architecture Plan
## NordicShield Technologies Oy

---

## Document Purpose

This document develops a Zero Trust architecture strategy for NordicShield Technologies during its global expansion. It covers the core principles of Zero Trust, how they apply to NordicShield's hybrid environment, and provides an implementation roadmap.

---

## Instructions

1. Review Zero Trust principles and NordicShield's current architecture
2. Identify trust boundaries and authentication requirements
3. Fill in all `[YOUR INPUT]` sections
4. Design Zero Trust controls appropriate for each environment segment

---

# SECTION A: ZERO TRUST FUNDAMENTALS

## A.1 Core Zero Trust Principles

For each principle, explain how it applies to NordicShield:

| Principle | Definition | NordicShield Application |
|-----------|------------|-------------------------|
| **Never Trust, Always Verify** | No implicit trust based on network location | [YOUR INPUT - How does this apply to NordicShield's 4 offices and remote workers?] |
| **Assume Breach** | Design as if attackers are already inside | [YOUR INPUT - Given the IoT attack surface, what assumptions should be made?] |
| **Verify Explicitly** | Authenticate and authorize every request | [YOUR INPUT - How should this apply to IoT devices, users, and services?] |
| **Least Privilege Access** | Grant minimum necessary permissions | [YOUR INPUT - Consider contractors, temps, new expansion offices] |
| **Microsegmentation** | Isolate resources into secure zones | [YOUR INPUT - How should NordicShield segment OT vs IT?] |

## A.2 Zero Trust Maturity Assessment

Assess NordicShield's current state against Zero Trust maturity:

| Domain | Traditional (Current?) | Advanced | Optimal | Current State | Target State |
|--------|---------------------|----------|---------|---------------|--------------|
| **Identity** | Static passwords | MFA, SSO | Continuous auth | [YOUR INPUT] | [YOUR INPUT] |
| **Devices** | Domain-joined only | MDM enrolled | Real-time posture | [YOUR INPUT] | [YOUR INPUT] |
| **Networks** | Perimeter-based | Segmented | Microsegmented | [YOUR INPUT] | [YOUR INPUT] |
| **Applications** | Internal/External | ZTNA/SDP | Full SASE | [YOUR INPUT] | [YOUR INPUT] |
| **Data** | Location-based | DLP | Data-centric | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION B: CURRENT ARCHITECTURE ANALYSIS

## B.1 Current Trust Relationships

Identify implicit trust in the current environment:

| Trust Relationship | Current State | Risk | Zero Trust Approach |
|--------------------|---------------|------|---------------------|
| On-premises network = trusted | [YOUR INPUT - Does being on the Turku LAN grant automatic access?] | [YOUR INPUT] | [YOUR INPUT] |
| VPN = full network access | [YOUR INPUT - What access does VPN grant?] | [YOUR INPUT] | [YOUR INPUT] |
| IoT VLAN = isolated | [YOUR INPUT - Is the IoT VLAN truly isolated?] | [YOUR INPUT] | [YOUR INPUT] |
| Cloud services = external | [YOUR INPUT - How is cloud access controlled?] | [YOUR INPUT] | [YOUR INPUT] |
| Partner connections | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## B.2 Current Identity Architecture

| Component | Current Implementation | Limitations |
|-----------|----------------------|-------------|
| Directory Service | Azure AD | [YOUR INPUT - What's not covered?] |
| Authentication | [YOUR INPUT - MFA status?] | [YOUR INPUT] |
| SSO | [YOUR INPUT] | [YOUR INPUT] |
| Service Accounts | [YOUR INPUT - How managed?] | [YOUR INPUT] |
| IoT Identity | [YOUR INPUT - How do IoT devices authenticate?] | [YOUR INPUT] |
| Privileged Access | [YOUR INPUT - PAM in place?] | [YOUR INPUT] |

## B.3 Current Network Architecture

```
[YOUR INPUT - Describe or diagram the current network architecture]

Turku HQ:
- Corporate VLAN: 
- IoT/OT VLAN:
- Guest VLAN:
- Server VLAN:

Cloud (AWS):
- VPC structure:
- Connectivity to on-prem:

New Offices (Planned):
- Amsterdam:
- Austin:
- Kigali:
```

---

# SECTION C: ZERO TRUST PILLARS FOR NORDICSHIELD

## C.1 Identity Pillar

### C.1.1 User Identity

| Requirement | Current State | Target State | Implementation |
|-------------|---------------|--------------|----------------|
| Strong MFA for all users | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - What MFA method?] |
| Conditional Access policies | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Risk-based authentication | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Privileged Identity Management | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Identity governance | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### C.1.2 Device Identity

| Device Type | Current Auth Method | Target Auth Method | Justification |
|-------------|--------------------|--------------------|---------------|
| Corporate laptops | [YOUR INPUT] | Certificate-based auth | [YOUR INPUT] |
| BYOD devices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT sensors | [YOUR INPUT] | X.509 certificates | [YOUR INPUT] |
| IoT gateways | [YOUR INPUT] | Mutual TLS | [YOUR INPUT] |
| Mobile devices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### C.1.3 Service/Application Identity

| Service Type | Current Auth | Target Auth | Notes |
|--------------|--------------|-------------|-------|
| On-prem services | [YOUR INPUT] | Managed identities | [YOUR INPUT] |
| AWS services | [YOUR INPUT] | IAM roles | [YOUR INPUT] |
| SaaS applications | [YOUR INPUT] | SAML/OIDC federation | [YOUR INPUT] |
| Internal APIs | [YOUR INPUT] | OAuth 2.0 + mTLS | [YOUR INPUT] |

## C.2 Device Pillar

### C.2.1 Device Trust Requirements

| Device Category | Compliance Requirements | Verification Method |
|-----------------|------------------------|---------------------|
| Corporate Windows | [YOUR INPUT - List requirements: patch level, EDR, encryption, etc.] | [YOUR INPUT - Intune? SCCM?] |
| Corporate Mac | [YOUR INPUT] | [YOUR INPUT] |
| Corporate Linux | [YOUR INPUT] | [YOUR INPUT] |
| BYOD | [YOUR INPUT] | [YOUR INPUT - MAM? Conditional access?] |
| IoT Sensors | [YOUR INPUT] | [YOUR INPUT - Device attestation?] |
| IoT Controllers | [YOUR INPUT] | [YOUR INPUT] |

### C.2.2 Device Posture Assessment

```
[YOUR INPUT - Design a device posture check workflow]

Before access is granted, verify:
1. 
2. 
3. 
4. 
5. 

If device fails posture check:
- Action 1:
- Action 2:
```

## C.3 Network Pillar

### C.3.1 Microsegmentation Design

| Segment | Purpose | Allowed Inbound | Allowed Outbound | Isolation Level |
|---------|---------|-----------------|------------------|-----------------|
| Corporate Users | General business | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| R&D Systems | Development | [YOUR INPUT] | [YOUR INPUT] | High - Sensitive IP |
| IoT Sensors | Data collection | [YOUR INPUT] | [YOUR INPUT] | High - Safety critical |
| IoT Controllers | Operational control | [YOUR INPUT] | [YOUR INPUT] | Maximum |
| Server VLAN | Core services | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Guest Network | Visitors | [YOUR INPUT] | [YOUR INPUT] | Isolated |

### C.3.2 Zero Trust Network Access (ZTNA) Design

Replace VPN with ZTNA for:

| Use Case | Current Solution | ZTNA Solution | Benefits |
|----------|-----------------|---------------|----------|
| Remote worker access | [YOUR INPUT] | [YOUR INPUT - ZTNA product?] | [YOUR INPUT] |
| Contractor access | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| New office connectivity | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Partner access | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### C.3.3 East-West Traffic Control

```
[YOUR INPUT - How will internal traffic be controlled?]

Current state: 
Target state:
Technologies to implement:
```

## C.4 Application Pillar

### C.4.1 Application-Level Controls

| Application | Access Method | Authentication | Authorization | Data Protection |
|-------------|--------------|----------------|---------------|-----------------|
| NordicSense Platform | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| GitHub Enterprise | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Salesforce | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Internal ERP | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| AWS Console | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### C.4.2 API Security

| API Type | Current Security | Zero Trust Controls |
|----------|-----------------|---------------------|
| Customer-facing APIs | [YOUR INPUT] | [YOUR INPUT - API gateway, rate limiting, auth?] |
| Internal APIs | [YOUR INPUT] | [YOUR INPUT] |
| IoT device APIs | [YOUR INPUT] | [YOUR INPUT] |
| Partner APIs | [YOUR INPUT] | [YOUR INPUT] |

## C.5 Data Pillar

### C.5.1 Data-Centric Security

| Data Type | Access Control | Encryption | DLP Policy | Monitoring |
|-----------|----------------|------------|------------|------------|
| PII (Employee/Customer) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Intellectual Property | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Telemetry | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Financial Data | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### C.5.2 Data Flow Controls

```
[YOUR INPUT - Design data flow controls]

Data entering the environment:
- IoT sensors → Gateway → AWS:
- Customer portal submissions:
- Partner data exchanges:

Data leaving the environment:
- Customer reports:
- Partner integrations:
- Employee exports:
```

---

# SECTION D: GLOBAL EXPANSION ZERO TRUST

## D.1 New Office Zero Trust Requirements

Each new office should be "born Zero Trust":

| Office | Network Approach | Identity Integration | Local Services | WAN Connectivity |
|--------|-----------------|---------------------|----------------|------------------|
| Amsterdam | [YOUR INPUT - Full ZT or traditional?] | [YOUR INPUT - Azure AD federated?] | [YOUR INPUT - Local server?] | [YOUR INPUT - SDWAN? ZTNA?] |
| Austin | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Kigali | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - Consider local internet?] | [YOUR INPUT] |

## D.2 Cross-Office Access

| Access Need | Traditional Approach | Zero Trust Approach |
|-------------|---------------------|---------------------|
| Amsterdam accessing Turku apps | Site-to-site VPN | [YOUR INPUT] |
| Austin accessing AWS resources | [YOUR INPUT] | [YOUR INPUT] |
| Kigali accessing support systems | [YOUR INPUT] | [YOUR INPUT] |
| Any office accessing SaaS | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION E: IOT ZERO TRUST ARCHITECTURE

## E.1 IoT-Specific Challenges

| Challenge | Description | Zero Trust Solution |
|-----------|-------------|---------------------|
| Limited compute on devices | Sensors can't run complex auth | [YOUR INPUT - Gateway-based auth?] |
| Long device lifecycles | Devices deployed 5-10+ years | [YOUR INPUT - Certificate rotation?] |
| Difficult patching | Downtime impacts operations | [YOUR INPUT] |
| Physical access risks | Deployed in client facilities | [YOUR INPUT - Tamper detection?] |
| Scale | 827+ devices | [YOUR INPUT - Automated onboarding?] |

## E.2 IoT Zero Trust Design

```
[YOUR INPUT - Design the IoT Zero Trust architecture]

Device Layer:
- Device identity:
- Device attestation:
- Firmware integrity:

Gateway Layer:
- Authentication:
- Traffic inspection:
- Protocol translation:

Cloud Layer:
- Ingestion authentication:
- Data validation:
- Access control:
```

## E.3 Client Site Security

For IoT deployments at customer facilities:

| Concern | Control | Implementation |
|---------|---------|----------------|
| Sensors on customer networks | [YOUR INPUT] | [YOUR INPUT] |
| Data transmission to NordicShield | [YOUR INPUT] | [YOUR INPUT] |
| Remote management access | [YOUR INPUT] | [YOUR INPUT] |
| Physical security | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION F: IMPLEMENTATION ROADMAP

## F.1 Phase 1: Foundation (Months 1-3)

| Activity | Priority | Owner | Dependencies |
|----------|----------|-------|--------------|
| [YOUR INPUT - Identity foundation] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT - MFA enforcement] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT - Asset inventory] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## F.2 Phase 2: Core Capabilities (Months 4-6)

| Activity | Priority | Owner | Dependencies |
|----------|----------|-------|--------------|
| [YOUR INPUT - Conditional access] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT - Network segmentation] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## F.3 Phase 3: Advanced (Months 7-12)

| Activity | Priority | Owner | Dependencies |
|----------|----------|-------|--------------|
| [YOUR INPUT - ZTNA deployment] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT - IoT Zero Trust] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION G: ZERO TRUST CONTROL MAPPING

## G.1 Controls to Security+ Objectives

| Zero Trust Control | Security+ Objective | Control Type |
|-------------------|--------------------|--------------| 
| Multi-factor authentication | 1.2, 4.6 | Technical |
| Conditional access | 1.2, 4.6 | Technical |
| Microsegmentation | 4.1, 4.4 | Technical |
| Continuous monitoring | 4.4, 4.9 | Technical |
| Least privilege | 1.2, 4.6 | Technical |
| Device compliance | 1.1, 4.2 | Technical/Administrative |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION H: EXECUTIVE SUMMARY

```
[YOUR INPUT - Write a 200-300 word executive summary]

Include:
- Why Zero Trust is essential for NordicShield (global expansion, IoT, remote work)
- Current architecture gaps and risks
- Proposed Zero Trust pillars prioritization
- Expected benefits (security, compliance, operational)
- High-level timeline and resource requirements
- Key success metrics
```

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 1.3 - Zero Trust Architecture Plan |
| **Phase** | 1 - General Security Concepts |
| **Exam Objective** | 1.2 - Summarize fundamental security concepts |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
