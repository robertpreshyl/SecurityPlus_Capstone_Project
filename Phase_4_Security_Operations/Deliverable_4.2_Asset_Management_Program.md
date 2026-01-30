# Deliverable 4.2: Asset Management Program
## NordicShield Technologies Oy

---

```
╔══════════════════════════════════════════════════════════════════╗
║                 ASSET MANAGEMENT PROGRAM                          ║
║                                                                    ║
║  Document ID: ASSET-NS-2026-001                                   ║
║  Version: 1.0                                                     ║
║  Author: [YOUR NAME]                                              ║
║  Classification: Internal Use Only                                ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Document Purpose

This document establishes NordicShield's comprehensive asset management program, covering the complete lifecycle from acquisition through disposal. Effective asset management is fundamental to security - you cannot protect what you don't know exists.

---

## Instructions

1. Design asset classification and ownership framework
2. Create inventory management procedures
3. Define procurement and disposal processes
4. Complete all `[YOUR INPUT]` sections
5. Consider NordicShield's global operations and IoT assets

---

# SECTION A: ASSET MANAGEMENT FRAMEWORK

## A.1 Program Objectives

```
[YOUR INPUT - Define asset management objectives]

NORDICSHIELD ASSET MANAGEMENT OBJECTIVES
========================================

1. VISIBILITY: [YOUR INPUT - Complete inventory of all assets]

2. ACCOUNTABILITY: [YOUR INPUT - Clear ownership for every asset]

3. SECURITY: [YOUR INPUT - Appropriate protection based on classification]

4. COMPLIANCE: [YOUR INPUT - Meet regulatory requirements for asset tracking]

5. EFFICIENCY: [YOUR INPUT - Optimize asset utilization and costs]

6. LIFECYCLE: [YOUR INPUT - Manage assets from procurement to disposal]
```

## A.2 Asset Categories

| Category | Description | Examples | Criticality Range |
|----------|-------------|----------|-------------------|
| Hardware - Endpoint | [YOUR INPUT - User computing devices] | [YOUR INPUT - Laptops, desktops, tablets] | [YOUR INPUT - Medium-High] |
| Hardware - Server | [YOUR INPUT - Data center and cloud compute] | [YOUR INPUT - Physical servers, VMs] | [YOUR INPUT - High-Critical] |
| Hardware - Network | [YOUR INPUT - Network infrastructure] | [YOUR INPUT - Routers, switches, firewalls] | [YOUR INPUT - High-Critical] |
| Hardware - Mobile | [YOUR INPUT - Mobile devices] | [YOUR INPUT - Smartphones, field devices] | [YOUR INPUT - Medium-High] |
| Hardware - IoT | [YOUR INPUT - Smart devices, sensors] | [YOUR INPUT - Energy sensors, controllers] | [YOUR INPUT - Variable] |
| Hardware - OT | [YOUR INPUT - Operational technology] | [YOUR INPUT - PLCs, SCADA components] | [YOUR INPUT - Critical] |
| Software - OS | [YOUR INPUT - Operating systems] | [YOUR INPUT - Windows, Linux, macOS] | [YOUR INPUT - High] |
| Software - Application | [YOUR INPUT - Business applications] | [YOUR INPUT - ERP, CRM, custom apps] | [YOUR INPUT - Variable] |
| Software - Security | [YOUR INPUT - Security tools] | [YOUR INPUT - EDR, SIEM, firewalls] | [YOUR INPUT - Critical] |
| Data - Structured | [YOUR INPUT - Database records] | [YOUR INPUT - Customer DB, financial] | [YOUR INPUT - Variable] |
| Data - Unstructured | [YOUR INPUT - Files and documents] | [YOUR INPUT - Documents, emails] | [YOUR INPUT - Variable] |
| Cloud - IaaS | [YOUR INPUT - Infrastructure services] | [YOUR INPUT - EC2, Azure VMs] | [YOUR INPUT - High] |
| Cloud - SaaS | [YOUR INPUT - Software services] | [YOUR INPUT - M365, Salesforce] | [YOUR INPUT - Medium-High] |
| Virtual Assets | [YOUR INPUT - Virtual infrastructure] | [YOUR INPUT - VMs, containers] | [YOUR INPUT - High] |

## A.3 Asset Management Architecture

```
[YOUR INPUT - Design the asset management ecosystem]

┌─────────────────────────────────────────────────────────────────────────┐
│                    ASSET MANAGEMENT ECOSYSTEM                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  DISCOVERY TOOLS                    CMDB (SINGLE SOURCE OF TRUTH)       │
│  ┌──────────────────┐              ┌──────────────────┐                 │
│  │ Network Scanner  │──────────────▶│                  │                 │
│  │ [YOUR INPUT]     │              │  Configuration   │                 │
│  └──────────────────┘              │  Management      │                 │
│  ┌──────────────────┐              │  Database        │                 │
│  │ Agent-based      │──────────────▶│                  │                 │
│  │ [YOUR INPUT]     │              │  [YOUR INPUT -   │                 │
│  └──────────────────┘              │   ServiceNow/    │                 │
│  ┌──────────────────┐              │   Device42]      │                 │
│  │ Cloud API        │──────────────▶│                  │                 │
│  │ [YOUR INPUT]     │              └────────┬─────────┘                 │
│  └──────────────────┘                       │                            │
│  ┌──────────────────┐                       │                            │
│  │ IoT Platform     │──────────────────────►│                            │
│  │ [YOUR INPUT]     │                       │                            │
│  └──────────────────┘                       │                            │
│                                             │                            │
│  CONSUMING SYSTEMS                          │                            │
│  ┌──────────────────┐                       │                            │
│  │ Vulnerability    │◀──────────────────────┤                            │
│  │ Management       │                       │                            │
│  └──────────────────┘                       │                            │
│  ┌──────────────────┐                       │                            │
│  │ SIEM             │◀──────────────────────┤                            │
│  │                  │                       │                            │
│  └──────────────────┘                       │                            │
│  ┌──────────────────┐                       │                            │
│  │ Patch Management │◀──────────────────────┘                            │
│  │                  │                                                    │
│  └──────────────────┘                                                    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

# SECTION B: ASSET INVENTORY

## B.1 Asset Attribute Schema

### Hardware Asset Attributes

| Attribute | Required | Description | Example |
|-----------|----------|-------------|---------|
| Asset ID | Yes | [YOUR INPUT - Unique identifier] | [YOUR INPUT - NS-HW-2026-00001] |
| Asset Tag | Yes | [YOUR INPUT - Physical label number] | [YOUR INPUT - 00001234] |
| Hostname | Yes | [YOUR INPUT - Network name] | [YOUR INPUT - NS-HEL-WS-001] |
| Serial Number | Yes | [YOUR INPUT - Manufacturer serial] | [YOUR INPUT - ABC123XYZ] |
| MAC Address(es) | Yes | [YOUR INPUT - Network interface MACs] | [YOUR INPUT - AA:BB:CC:DD:EE:FF] |
| Asset Type | Yes | [YOUR INPUT - Category from A.2] | [YOUR INPUT - Hardware - Endpoint] |
| Make/Model | Yes | [YOUR INPUT - Manufacturer and model] | [YOUR INPUT - Dell Latitude 5540] |
| Owner | Yes | [YOUR INPUT - Accountable individual] | [YOUR INPUT - employee@nordicshield.fi] |
| Custodian | Yes | [YOUR INPUT - Person with physical possession] | [YOUR INPUT - employee@nordicshield.fi] |
| Business Unit | Yes | [YOUR INPUT - Organizational unit] | [YOUR INPUT - Engineering] |
| Location | Yes | [YOUR INPUT - Physical location] | [YOUR INPUT - Helsinki HQ, Floor 3] |
| Criticality | Yes | [YOUR INPUT - Business criticality] | [YOUR INPUT - High] |
| Data Classification | Yes | [YOUR INPUT - Highest data handled] | [YOUR INPUT - Confidential] |
| Purchase Date | Yes | [YOUR INPUT - Acquisition date] | [YOUR INPUT - 2026-01-15] |
| Warranty Expiry | Yes | [YOUR INPUT - Warranty end date] | [YOUR INPUT - 2029-01-15] |
| End of Life | Yes | [YOUR INPUT - Planned replacement date] | [YOUR INPUT - 2030-01-15] |
| IP Address(es) | No | [YOUR INPUT - Assigned IPs] | [YOUR INPUT - 10.1.1.50] |
| Operating System | No | [YOUR INPUT - Installed OS] | [YOUR INPUT - Windows 11 Enterprise] |
| Encryption Status | Yes | [YOUR INPUT - Disk encryption status] | [YOUR INPUT - BitLocker Enabled] |
| Compliance Status | Yes | [YOUR INPUT - Hardening compliance] | [YOUR INPUT - Compliant/95%] |
| Last Scanned | Yes | [YOUR INPUT - Last inventory scan] | [YOUR INPUT - 2026-01-28] |
| Notes | No | [YOUR INPUT - Additional information] | [YOUR INPUT - Executive device] |

### Software Asset Attributes

| Attribute | Required | Description | Example |
|-----------|----------|-------------|---------|
| Software ID | Yes | [YOUR INPUT - Unique identifier] | [YOUR INPUT - NS-SW-001] |
| Software Name | Yes | [YOUR INPUT - Application name] | [YOUR INPUT - Microsoft 365 E5] |
| Publisher | Yes | [YOUR INPUT - Vendor] | [YOUR INPUT - Microsoft] |
| Version | Yes | [YOUR INPUT - Installed version] | [YOUR INPUT - 16.0.18] |
| License Type | Yes | [YOUR INPUT - Licensing model] | [YOUR INPUT - Subscription/Per-user] |
| License Count | Yes | [YOUR INPUT - Purchased licenses] | [YOUR INPUT - 250] |
| Installed Count | Yes | [YOUR INPUT - Active installations] | [YOUR INPUT - 234] |
| License Expiry | Yes | [YOUR INPUT - Renewal date] | [YOUR INPUT - 2027-03-15] |
| Owner | Yes | [YOUR INPUT - Business owner] | [YOUR INPUT - IT Director] |
| Criticality | Yes | [YOUR INPUT - Business importance] | [YOUR INPUT - Critical] |
| Support Status | Yes | [YOUR INPUT - Vendor support] | [YOUR INPUT - Mainstream support] |

### Cloud Asset Attributes

| Attribute | Required | Description | Example |
|-----------|----------|-------------|---------|
| Resource ID | Yes | [YOUR INPUT - Cloud-assigned ID] | [YOUR INPUT - i-0abc123def456] |
| Resource Type | Yes | [YOUR INPUT - Service type] | [YOUR INPUT - EC2 Instance] |
| Cloud Provider | Yes | [YOUR INPUT - AWS/Azure/GCP] | [YOUR INPUT - AWS] |
| Account/Subscription | Yes | [YOUR INPUT - Cloud account] | [YOUR INPUT - prod-123456] |
| Region | Yes | [YOUR INPUT - Geographic region] | [YOUR INPUT - eu-north-1] |
| Owner | Yes | [YOUR INPUT - Accountable person] | [YOUR INPUT - CloudOps Team] |
| Cost Center | Yes | [YOUR INPUT - Billing allocation] | [YOUR INPUT - CC-5001] |
| Environment | Yes | [YOUR INPUT - Prod/Dev/Test] | [YOUR INPUT - Production] |
| Tags | Yes | [YOUR INPUT - Resource tags] | [YOUR INPUT - Env:Prod, App:ERP] |

## B.2 Asset Naming Convention

```
[YOUR INPUT - Design naming convention]

NORDICSHIELD ASSET NAMING CONVENTION
===================================

FORMAT: [ORG]-[LOCATION]-[TYPE]-[SEQUENCE]

ORGANIZATION PREFIX:
- NS = NordicShield

LOCATION CODES:
- HEL = Helsinki, Finland
- STO = Stockholm, Sweden
- OSL = Oslo, Norway
- CPH = Copenhagen, Denmark
- AMS = Amsterdam, Netherlands
- AWS = Amazon Web Services
- AZR = Azure
- GCP = Google Cloud

DEVICE TYPE CODES:
- SRV = Server
- WKS = Workstation
- LPT = Laptop
- FW  = Firewall
- RTR = Router
- SWT = Switch
- AP  = Access Point
- IOT = IoT Device
- MOB = Mobile Device
- VM  = Virtual Machine
- [YOUR INPUT - Add more]

EXAMPLES:
- NS-HEL-SRV-001 = [YOUR INPUT - Helsinki Server #1]
- NS-AWS-VM-042 = [YOUR INPUT - AWS VM #42]
- NS-STO-LPT-103 = [YOUR INPUT - Stockholm Laptop #103]
- NS-HEL-IOT-501 = [YOUR INPUT - Helsinki IoT Device #501]
```

## B.3 Asset Tagging

### Physical Asset Tags

| Tag Type | Use Case | Information Contained | Attachment Method |
|----------|----------|----------------------|-------------------|
| Barcode Label | [YOUR INPUT - Standard equipment] | [YOUR INPUT - Asset ID, barcode] | [YOUR INPUT - Adhesive] |
| QR Code Label | [YOUR INPUT - Quick scanning] | [YOUR INPUT - Asset ID, URL to CMDB entry] | [YOUR INPUT - Adhesive] |
| RFID Tag | [YOUR INPUT - High-value assets] | [YOUR INPUT - Asset ID, location tracking] | [YOUR INPUT - Embedded/Attached] |
| Tamper-Evident | [YOUR INPUT - Sensitive equipment] | [YOUR INPUT - Asset ID, security seal] | [YOUR INPUT - Destructible adhesive] |
| Engraved | [YOUR INPUT - Permanent marking] | [YOUR INPUT - Company name, Asset ID] | [YOUR INPUT - Laser engraving] |

### Cloud Resource Tagging

| Tag Key | Required | Values | Purpose |
|---------|----------|--------|---------|
| Owner | Yes | [YOUR INPUT - Email address] | [YOUR INPUT - Accountability] |
| Environment | Yes | [YOUR INPUT - prod/staging/dev/test] | [YOUR INPUT - Environment identification] |
| CostCenter | Yes | [YOUR INPUT - Cost center code] | [YOUR INPUT - Financial allocation] |
| Application | Yes | [YOUR INPUT - Application name] | [YOUR INPUT - App association] |
| DataClassification | Yes | [YOUR INPUT - Public/Internal/Confidential/Restricted] | [YOUR INPUT - Security controls] |
| Criticality | Yes | [YOUR INPUT - Low/Medium/High/Critical] | [YOUR INPUT - Priority handling] |
| Compliance | No | [YOUR INPUT - GDPR/PCI/HIPAA] | [YOUR INPUT - Compliance scope] |
| AutoShutdown | No | [YOUR INPUT - true/false with time] | [YOUR INPUT - Cost optimization] |
| BackupPolicy | Yes | [YOUR INPUT - Policy name] | [YOUR INPUT - Backup assignment] |

---

# SECTION C: ASSET OWNERSHIP & ACCOUNTABILITY

## C.1 Ownership Model

### Role Definitions

| Role | Definition | Responsibilities | Example |
|------|------------|------------------|---------|
| Asset Owner | [YOUR INPUT - Business accountable for asset] | [YOUR INPUT - Approve access, define requirements, fund maintenance] | [YOUR INPUT - IT Director for infrastructure] |
| System Administrator | [YOUR INPUT - Technical management] | [YOUR INPUT - Configure, patch, maintain, monitor] | [YOUR INPUT - Sysadmin for servers] |
| Custodian | [YOUR INPUT - Physical possession] | [YOUR INPUT - Safeguard, report issues, return on request] | [YOUR INPUT - Employee with assigned laptop] |
| Information Owner | [YOUR INPUT - Accountable for data on asset] | [YOUR INPUT - Classify data, approve access, define retention] | [YOUR INPUT - Finance Director for financial data] |
| Security Steward | [YOUR INPUT - Security oversight] | [YOUR INPUT - Verify compliance, review configurations, approve exceptions] | [YOUR INPUT - Security team member] |

## C.2 Ownership Assignment Matrix

| Asset Category | Default Owner | Owner Department | Assignment Trigger |
|----------------|--------------|------------------|-------------------|
| End User Devices | [YOUR INPUT - Assigned employee] | [YOUR INPUT - User's department] | [YOUR INPUT - Onboarding/request] |
| Servers - Infrastructure | [YOUR INPUT - IT Operations Manager] | [YOUR INPUT - IT] | [YOUR INPUT - Deployment] |
| Servers - Application | [YOUR INPUT - Application owner] | [YOUR INPUT - Business unit] | [YOUR INPUT - Application deployment] |
| Network Equipment | [YOUR INPUT - Network Manager] | [YOUR INPUT - IT] | [YOUR INPUT - Installation] |
| Cloud Resources | [YOUR INPUT - Requestor/workload owner] | [YOUR INPUT - Varies] | [YOUR INPUT - Provisioning] |
| IoT Devices | [YOUR INPUT - IoT Platform Owner] | [YOUR INPUT - Operations/IT] | [YOUR INPUT - Deployment] |
| Security Tools | [YOUR INPUT - CISO/Security Manager] | [YOUR INPUT - Security] | [YOUR INPUT - Implementation] |
| SaaS Applications | [YOUR INPUT - Business sponsor] | [YOUR INPUT - Business unit] | [YOUR INPUT - Contract signing] |

## C.3 Ownership Transfer Process

```
[YOUR INPUT - Design ownership transfer workflow]

ASSET OWNERSHIP TRANSFER PROCEDURE
==================================

TRIGGER EVENTS:
1. [YOUR INPUT - Employee departure/transfer]
2. [YOUR INPUT - Organizational restructure]
3. [YOUR INPUT - Asset reassignment]
4. [YOUR INPUT - Project completion]

TRANSFER WORKFLOW:

Step 1: INITIATION
- Current owner submits transfer request
- Include: [YOUR INPUT - Asset ID, new owner, justification]

Step 2: VALIDATION
- IT verifies: [YOUR INPUT - Asset exists, condition, data]
- Security verifies: [YOUR INPUT - Data handling requirements]

Step 3: DATA HANDLING
- IF contains confidential data:
  [YOUR INPUT - Backup, verify, sanitize, document]
- IF contains personal data:
  [YOUR INPUT - Evaluate GDPR requirements]

Step 4: PHYSICAL TRANSFER
- [YOUR INPUT - Collect from current custodian]
- [YOUR INPUT - Inspect condition]
- [YOUR INPUT - Update physical location]

Step 5: SYSTEM UPDATES
- [YOUR INPUT - Update CMDB ownership fields]
- [YOUR INPUT - Update access controls]
- [YOUR INPUT - Update cost allocation]

Step 6: ACKNOWLEDGMENT
- New owner signs acceptance: [YOUR INPUT - Form/System]
- Updated liability: [YOUR INPUT - Effective date]

Step 7: DOCUMENTATION
- [YOUR INPUT - Audit trail in CMDB]
- [YOUR INPUT - Transfer certificate]
```

---

# SECTION D: PROCUREMENT PROCESS

## D.1 Procurement Security Requirements

### Hardware Procurement Checklist

| Requirement | Description | Verification Method | Status |
|-------------|-------------|---------------------|--------|
| Vendor Assessment | [YOUR INPUT - Security questionnaire] | [YOUR INPUT - Complete vendor risk assessment] | ☐ |
| Supply Chain Security | [YOUR INPUT - Verify sourcing, no counterfeit] | [YOUR INPUT - Authorized reseller, chain of custody] | ☐ |
| Hardware Security Features | [YOUR INPUT - TPM, Secure Boot support] | [YOUR INPUT - Verify specifications] | ☐ |
| Compatibility | [YOUR INPUT - Compatible with security tools] | [YOUR INPUT - Verify EDR, encryption support] | ☐ |
| Support Lifecycle | [YOUR INPUT - Minimum support period] | [YOUR INPUT - Verify EOL date >5 years] | ☐ |
| Warranty | [YOUR INPUT - Minimum warranty period] | [YOUR INPUT - 3+ years next-business-day] | ☐ |
| Spare Parts | [YOUR INPUT - Availability of parts] | [YOUR INPUT - Verify parts support] | ☐ |
| Disposal Agreement | [YOUR INPUT - End of life handling] | [YOUR INPUT - Vendor take-back option] | ☐ |

### Software Procurement Checklist

| Requirement | Description | Verification Method | Status |
|-------------|-------------|---------------------|--------|
| Security Assessment | [YOUR INPUT - Vendor security posture] | [YOUR INPUT - SOC 2, ISO 27001, penetration test results] | ☐ |
| Data Handling | [YOUR INPUT - Where/how data processed] | [YOUR INPUT - GDPR compliance, DPA signed] | ☐ |
| Authentication | [YOUR INPUT - SSO, MFA support] | [YOUR INPUT - Verify SAML/OIDC, MFA] | ☐ |
| Encryption | [YOUR INPUT - Data encryption capabilities] | [YOUR INPUT - TLS 1.2+, encryption at rest] | ☐ |
| Audit Logging | [YOUR INPUT - Security event logging] | [YOUR INPUT - Log availability, SIEM integration] | ☐ |
| Vulnerability Management | [YOUR INPUT - Vendor patching process] | [YOUR INPUT - SLA for critical patches] | ☐ |
| Incident Response | [YOUR INPUT - Vendor breach notification] | [YOUR INPUT - <72 hours notification SLA] | ☐ |
| License Audit | [YOUR INPUT - Clear license terms] | [YOUR INPUT - Legal review of EULA] | ☐ |
| Exit Strategy | [YOUR INPUT - Data portability] | [YOUR INPUT - Data export capabilities, format] | ☐ |

## D.2 Procurement Workflow

```
[YOUR INPUT - Design secure procurement workflow]

SECURE PROCUREMENT WORKFLOW
===========================

┌──────────────────────────────────────────────────────────────────────┐
│                                                                       │
│  1. REQUEST                                                           │
│  ┌─────────────────────────────────────────────┐                     │
│  │ Requestor submits:                          │                     │
│  │ - Business justification                    │                     │
│  │ - Requirements specification                │                     │
│  │ - Budget allocation                         │                     │
│  │ - Data classification of data to be handled │                     │
│  └──────────────────────┬──────────────────────┘                     │
│                         │                                             │
│  2. SECURITY REVIEW     ▼                                             │
│  ┌─────────────────────────────────────────────┐                     │
│  │ Security team evaluates:                    │                     │
│  │ - [YOUR INPUT - Risk assessment]            │                     │
│  │ - [YOUR INPUT - Vendor security review]     │                     │
│  │ - [YOUR INPUT - Compliance requirements]    │                     │
│  │ - [YOUR INPUT - Architecture fit]           │                     │
│  └──────────────────────┬──────────────────────┘                     │
│                         │                                             │
│  3. APPROVAL            ▼                                             │
│  ┌─────────────────────────────────────────────┐                     │
│  │ Approval requirements:                      │                     │
│  │ - < €5,000: [YOUR INPUT - Manager]          │                     │
│  │ - €5,000-€25,000: [YOUR INPUT - Director]   │                     │
│  │ - > €25,000: [YOUR INPUT - VP/C-Level]      │                     │
│  │ - Cloud/SaaS: [YOUR INPUT - Always Security]│                     │
│  └──────────────────────┬──────────────────────┘                     │
│                         │                                             │
│  4. PURCHASE            ▼                                             │
│  ┌─────────────────────────────────────────────┐                     │
│  │ Procurement team:                           │                     │
│  │ - [YOUR INPUT - Approved vendor list check] │                     │
│  │ - [YOUR INPUT - Contract negotiation]       │                     │
│  │ - [YOUR INPUT - Security clauses]           │                     │
│  │ - [YOUR INPUT - Purchase order]             │                     │
│  └──────────────────────┬──────────────────────┘                     │
│                         │                                             │
│  5. RECEIPT             ▼                                             │
│  ┌─────────────────────────────────────────────┐                     │
│  │ IT/Security team:                           │                     │
│  │ - [YOUR INPUT - Verify delivery]            │                     │
│  │ - [YOUR INPUT - Tamper check]               │                     │
│  │ - [YOUR INPUT - Serial number verification] │                     │
│  │ - [YOUR INPUT - Register in CMDB]           │                     │
│  └──────────────────────┬──────────────────────┘                     │
│                         │                                             │
│  6. DEPLOYMENT          ▼                                             │
│  ┌─────────────────────────────────────────────┐                     │
│  │ - [YOUR INPUT - Apply secure baseline]      │                     │
│  │ - [YOUR INPUT - Install security agents]    │                     │
│  │ - [YOUR INPUT - Configure encryption]       │                     │
│  │ - [YOUR INPUT - Validate compliance]        │                     │
│  │ - [YOUR INPUT - Assign to owner/custodian]  │                     │
│  └─────────────────────────────────────────────┘                     │
│                                                                       │
└──────────────────────────────────────────────────────────────────────┘
```

## D.3 Approved Vendor List

| Category | Approved Vendors | Security Tier | Review Date |
|----------|-----------------|---------------|-------------|
| Workstations | [YOUR INPUT - Dell, Lenovo, HP] | [YOUR INPUT - Tier 1] | [YOUR INPUT] |
| Servers | [YOUR INPUT - Dell, HPE, Lenovo] | [YOUR INPUT - Tier 1] | [YOUR INPUT] |
| Network Equipment | [YOUR INPUT - Cisco, Palo Alto, Aruba] | [YOUR INPUT - Tier 1] | [YOUR INPUT] |
| Cloud IaaS | [YOUR INPUT - AWS, Azure, GCP] | [YOUR INPUT - Tier 1] | [YOUR INPUT] |
| Productivity Suite | [YOUR INPUT - Microsoft] | [YOUR INPUT - Tier 1] | [YOUR INPUT] |
| Security Tools | [YOUR INPUT - Vendor list] | [YOUR INPUT - Tier 1] | [YOUR INPUT] |

---

# SECTION E: ASSET LIFECYCLE MANAGEMENT

## E.1 Lifecycle Stages

```
[YOUR INPUT - Define complete asset lifecycle]

ASSET LIFECYCLE STAGES
======================

    ┌─────────────┐
    │   REQUEST   │ ──► Business need identified
    └──────┬──────┘
           │
    ┌──────▼──────┐
    │  PROCURE    │ ──► Secure procurement process
    └──────┬──────┘
           │
    ┌──────▼──────┐
    │   RECEIVE   │ ──► Verify, tag, register in CMDB
    └──────┬──────┘
           │
    ┌──────▼──────┐
    │   DEPLOY    │ ──► Secure baseline, install agents
    └──────┬──────┘
           │
    ┌──────▼──────┐
    │   OPERATE   │ ──► Monitor, maintain, patch, audit
    │             │     [YOUR INPUT - Longest phase]
    └──────┬──────┘
           │
    ┌──────▼──────┐
    │ MAINTENANCE │ ──► Repairs, upgrades, refresh
    └──────┬──────┘
           │
    ┌──────▼──────┐
    │   RETIRE    │ ──► End of useful life decision
    └──────┬──────┘
           │
    ┌──────▼──────┐
    │  DISPOSE    │ ──► Secure data destruction, disposal
    └─────────────┘
```

## E.2 Lifecycle Timing Standards

| Asset Type | Expected Lifespan | Warranty Period | Refresh Trigger | End of Life Handling |
|------------|-------------------|-----------------|-----------------|---------------------|
| Workstations | [YOUR INPUT - 4 years] | [YOUR INPUT - 3 years] | [YOUR INPUT - Performance, security, warranty] | [YOUR INPUT - Secure wipe, recycle] |
| Laptops | [YOUR INPUT - 4 years] | [YOUR INPUT - 3 years] | [YOUR INPUT - Performance, damage, security] | [YOUR INPUT] |
| Servers - Physical | [YOUR INPUT - 5-7 years] | [YOUR INPUT - 3-5 years] | [YOUR INPUT - Performance, support ending] | [YOUR INPUT - Destroy drives, recycle] |
| Network Equipment | [YOUR INPUT - 7-10 years] | [YOUR INPUT - 3-5 years] | [YOUR INPUT - Support ending, capacity] | [YOUR INPUT] |
| Mobile Devices | [YOUR INPUT - 2-3 years] | [YOUR INPUT - 1-2 years] | [YOUR INPUT - OS support ending, damage] | [YOUR INPUT] |
| IoT Devices | [YOUR INPUT - Varies] | [YOUR INPUT - 1-3 years] | [YOUR INPUT - Security vulnerability, EOL] | [YOUR INPUT] |
| Cloud Resources | [YOUR INPUT - Variable] | [YOUR INPUT - N/A] | [YOUR INPUT - Business need, cost] | [YOUR INPUT - Delete, verify] |

## E.3 Maintenance & Support Tracking

| Status | Definition | Action Required |
|--------|------------|-----------------|
| Current | [YOUR INPUT - In warranty, fully supported] | [YOUR INPUT - Normal operations] |
| Extended Support | [YOUR INPUT - Warranty expired, extended purchased] | [YOUR INPUT - Plan replacement] |
| End of Support | [YOUR INPUT - No vendor support available] | [YOUR INPUT - Urgent replacement, risk acceptance] |
| End of Life | [YOUR INPUT - No longer manufactured] | [YOUR INPUT - Replacement mandatory] |
| Retired | [YOUR INPUT - Removed from production] | [YOUR INPUT - Pending disposal] |
| Disposed | [YOUR INPUT - Securely destroyed/recycled] | [YOUR INPUT - Close CMDB record] |

---

# SECTION F: DECOMMISSIONING & DISPOSAL

## F.1 Decommissioning Process

### Pre-Decommissioning Checklist

| Step | Activity | Responsible | Verification | Status |
|------|----------|-------------|--------------|--------|
| 1 | [YOUR INPUT - Identify all data on asset] | [YOUR INPUT - Data owner] | [YOUR INPUT - Data inventory] | ☐ |
| 2 | [YOUR INPUT - Determine data retention needs] | [YOUR INPUT - Legal/Compliance] | [YOUR INPUT - Retention schedule] | ☐ |
| 3 | [YOUR INPUT - Backup required data] | [YOUR INPUT - IT] | [YOUR INPUT - Backup verification] | ☐ |
| 4 | [YOUR INPUT - Transfer data to new system] | [YOUR INPUT - IT] | [YOUR INPUT - Migration validation] | ☐ |
| 5 | [YOUR INPUT - Remove from production] | [YOUR INPUT - IT Operations] | [YOUR INPUT - Service validation] | ☐ |
| 6 | [YOUR INPUT - Revoke access/certificates] | [YOUR INPUT - Security] | [YOUR INPUT - Access audit] | ☐ |
| 7 | [YOUR INPUT - Remove from monitoring] | [YOUR INPUT - SOC] | [YOUR INPUT - CMDB update] | ☐ |
| 8 | [YOUR INPUT - Update DNS/documentation] | [YOUR INPUT - IT] | [YOUR INPUT - Documentation review] | ☐ |

### Decommissioning Authorization

```
[YOUR INPUT - Create authorization form]

ASSET DECOMMISSIONING AUTHORIZATION

Date: ___________________
Asset ID: ___________________
Asset Type: ___________________
Serial Number: ___________________
Current Owner: ___________________

DECOMMISSIONING REASON:
[ ] End of life / obsolete
[ ] Replaced by new asset (ID: _____________)
[ ] Organizational change
[ ] Security risk - cannot be remediated
[ ] Other: ___________________

DATA DISPOSITION:
[ ] No sensitive data present
[ ] Data backed up - Location: ___________________
[ ] Data migrated to: ___________________
[ ] Data retention requirement: ___________ years

APPROVALS:
Asset Owner: _________________ Date: _______
IT Manager: _________________ Date: _______
Security: _________________ Date: _______ (if sensitive data)

DISPOSAL METHOD:
[ ] Secure wipe and recycle
[ ] Physical destruction
[ ] Vendor return
[ ] Donation (after sanitization)
```

## F.2 Data Sanitization Methods

### Sanitization Decision Matrix

| Data Classification | Media Type | Minimum Sanitization Method | Verification Required |
|--------------------|------------|---------------------------|----------------------|
| Public | HDD | [YOUR INPUT - Clear (overwrite)] | [YOUR INPUT - No] |
| Public | SSD | [YOUR INPUT - Clear (crypto erase)] | [YOUR INPUT - No] |
| Internal | HDD | [YOUR INPUT - Purge (NIST 800-88)] | [YOUR INPUT - Spot check] |
| Internal | SSD | [YOUR INPUT - Crypto erase or destroy] | [YOUR INPUT - Spot check] |
| Confidential | HDD | [YOUR INPUT - Purge + verification] | [YOUR INPUT - Yes, certificate] |
| Confidential | SSD | [YOUR INPUT - Crypto erase + verification OR destroy] | [YOUR INPUT - Yes, certificate] |
| Restricted | Any | [YOUR INPUT - Physical destruction] | [YOUR INPUT - Yes, witnessed, certificate] |

### Sanitization Methods (NIST SP 800-88 Rev. 1)

| Method | Description | Use Case | Verification |
|--------|-------------|----------|--------------|
| Clear | [YOUR INPUT - Logical techniques to sanitize; data may be recoverable with forensics] | [YOUR INPUT - Low-risk, device reuse internal] | [YOUR INPUT - Software verification] |
| Purge | [YOUR INPUT - Physical or logical techniques to render data unrecoverable; media can be reused] | [YOUR INPUT - Medium-risk, device reuse/sale] | [YOUR INPUT - Laboratory verification possible] |
| Destroy | [YOUR INPUT - Physical destruction rendering recovery infeasible] | [YOUR INPUT - High-risk, no reuse] | [YOUR INPUT - Visual confirmation] |

### Sanitization Techniques by Media

| Media Type | Clear | Purge | Destroy |
|------------|-------|-------|---------|
| HDD | [YOUR INPUT - Overwrite all locations] | [YOUR INPUT - Secure erase (ATA), cryptographic erase, degaussing] | [YOUR INPUT - Shred, disintegrate, incinerate] |
| SSD/NVMe | [YOUR INPUT - Apply manufacturer sanitize command] | [YOUR INPUT - Cryptographic erase, manufacturer sanitize] | [YOUR INPUT - Shred, disintegrate] |
| USB/Flash | [YOUR INPUT - Overwrite] | [YOUR INPUT - Crypto erase] | [YOUR INPUT - Shred] |
| Tape | [YOUR INPUT - Overwrite] | [YOUR INPUT - Degauss] | [YOUR INPUT - Shred, incinerate] |
| Optical | [YOUR INPUT - N/A] | [YOUR INPUT - N/A] | [YOUR INPUT - Shred] |
| Mobile Device | [YOUR INPUT - Factory reset] | [YOUR INPUT - Crypto erase + factory reset] | [YOUR INPUT - Shred] |
| Paper | [YOUR INPUT - N/A] | [YOUR INPUT - N/A] | [YOUR INPUT - Cross-cut shred (DIN 66399 P-4+)] |

## F.3 Certificate of Destruction

```
[YOUR INPUT - Design certificate template]

╔══════════════════════════════════════════════════════════════════╗
║              CERTIFICATE OF DESTRUCTION                          ║
║                                                                    ║
║  Certificate Number: COD-[YEAR]-[SEQUENCE]                        ║
╚══════════════════════════════════════════════════════════════════╝

ORGANIZATION:
NordicShield Technologies Oy

ASSETS DESTROYED:

| Asset ID | Description | Serial Number | Media Type |
|----------|-------------|---------------|------------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

DESTRUCTION DETAILS:
Method Used: [YOUR INPUT - Physical destruction/Cryptographic erase/Purge]
Standard Applied: [YOUR INPUT - NIST SP 800-88 Rev. 1]
Machine/Software Used: [YOUR INPUT - e.g., Blancco Drive Eraser 6.x]
Date of Destruction: [YOUR INPUT]
Location: [YOUR INPUT]

VERIFICATION:
Verification Method: [YOUR INPUT - Software report/Visual inspection/Lab verification]
Verification Result: [YOUR INPUT - Pass/Fail]

PERFORMED BY:
Organization: [YOUR INPUT - Internal IT / Vendor Name]
Technician Name: _________________
Technician Signature: _________________

WITNESSED BY (if required):
Witness Name: _________________
Witness Signature: _________________

AUTHORIZED BY:
IT Manager: _________________ Date: _______

This certificate confirms that the above-listed assets have been 
sanitized/destroyed in accordance with NordicShield's data 
protection policies and NIST SP 800-88 Rev. 1 guidelines.

Retain this certificate for: [YOUR INPUT - 7 years]
```

## F.4 Disposal Methods

| Disposal Method | When to Use | Security Requirements | Documentation |
|-----------------|-------------|----------------------|---------------|
| Internal Redeployment | [YOUR INPUT - Asset suitable for different use] | [YOUR INPUT - Sanitize to Clear/Purge] | [YOUR INPUT - CMDB update, transfer form] |
| Resale/Auction | [YOUR INPUT - Asset has value, not sensitive] | [YOUR INPUT - Purge, CoD required] | [YOUR INPUT - Bill of sale, CoD] |
| Donation | [YOUR INPUT - Charitable giving] | [YOUR INPUT - Purge, CoD required] | [YOUR INPUT - Donation receipt, CoD] |
| Vendor Trade-In | [YOUR INPUT - Refresh with credit] | [YOUR INPUT - Purge or Destroy media] | [YOUR INPUT - Trade-in agreement, CoD] |
| Certified Recycling | [YOUR INPUT - No value, environmentally responsible] | [YOUR INPUT - Destroy, use R2/e-Stewards certified] | [YOUR INPUT - Recycling certificate, CoD] |
| Destruction Vendor | [YOUR INPUT - Sensitive assets requiring destruction] | [YOUR INPUT - Destroy, witnessed if restricted] | [YOUR INPUT - CoD with serial numbers] |

---

# SECTION G: ASSET DISCOVERY & INVENTORY ACCURACY

## G.1 Discovery Methods

| Method | Tool/Technology | Coverage | Frequency | Limitation |
|--------|-----------------|----------|-----------|------------|
| Network Scanning | [YOUR INPUT - Nmap, Qualys, Tenable] | [YOUR INPUT - All networked devices] | [YOUR INPUT - Continuous/Daily] | [YOUR INPUT - Offline devices missed] |
| Agent-Based | [YOUR INPUT - SCCM, Intune, CrowdStrike] | [YOUR INPUT - Managed devices] | [YOUR INPUT - Real-time] | [YOUR INPUT - Requires agent] |
| DHCP/DNS Mining | [YOUR INPUT - Core network services] | [YOUR INPUT - Dynamic IP devices] | [YOUR INPUT - Continuous] | [YOUR INPUT - Static IP missed] |
| Active Directory | [YOUR INPUT - AD query tools] | [YOUR INPUT - Domain-joined devices] | [YOUR INPUT - Daily] | [YOUR INPUT - Non-domain missed] |
| Cloud API | [YOUR INPUT - AWS/Azure/GCP APIs] | [YOUR INPUT - Cloud resources] | [YOUR INPUT - Continuous] | [YOUR INPUT - API permissions needed] |
| IoT Platform | [YOUR INPUT - IoT hub/platform] | [YOUR INPUT - IoT devices] | [YOUR INPUT - Real-time] | [YOUR INPUT - Onboarded devices only] |
| Physical Audit | [YOUR INPUT - Manual inspection] | [YOUR INPUT - All physical assets] | [YOUR INPUT - Annual] | [YOUR INPUT - Labor intensive] |
| NAC/802.1X | [YOUR INPUT - Network access control] | [YOUR INPUT - Network-connected] | [YOUR INPUT - Real-time] | [YOUR INPUT - NAC deployment needed] |

## G.2 Unknown Asset Handling

```
[YOUR INPUT - Create unknown asset process]

UNKNOWN ASSET DETECTION & HANDLING PROCEDURE
============================================

DEFINITION:
Unknown asset = Device detected on network not in CMDB

DETECTION METHODS:
1. [YOUR INPUT - NAC quarantine notification]
2. [YOUR INPUT - Vulnerability scanner unknown host]
3. [YOUR INPUT - SIEM correlation - new MAC/IP]
4. [YOUR INPUT - Network monitoring anomaly]

RESPONSE PROCEDURE:

STEP 1: INITIAL INVESTIGATION (SLA: [YOUR INPUT - 4 hours])
- Identify device type via: [YOUR INPUT - Fingerprinting, port scanning]
- Identify location via: [YOUR INPUT - Switch port, AP association]
- Check recent authorized changes: [YOUR INPUT - Change tickets]
- Attempt to identify owner: [YOUR INPUT - User queries, manager contact]

STEP 2: CLASSIFICATION ([YOUR INPUT - Within 24 hours])
- Category A: [YOUR INPUT - Known authorized, CMDB update needed]
  Action: [YOUR INPUT - Add to CMDB, close ticket]
  
- Category B: [YOUR INPUT - Unknown but appears legitimate]
  Action: [YOUR INPUT - Continue investigation, contact suspected owner]
  
- Category C: [YOUR INPUT - Suspicious/Unauthorized]
  Action: [YOUR INPUT - Trigger incident response, isolate]

STEP 3: RESOLUTION
- Document findings: [YOUR INPUT - Ticket/CMDB notes]
- Update inventory: [YOUR INPUT - Add or block device]
- Process improvement: [YOUR INPUT - How did it get on network?]
```

## G.3 Inventory Accuracy Metrics

| Metric | Definition | Target | Measurement |
|--------|------------|--------|-------------|
| Inventory Completeness | [YOUR INPUT - % of actual assets in CMDB] | [YOUR INPUT - >98%] | [YOUR INPUT - Discovery vs CMDB comparison] |
| Data Accuracy | [YOUR INPUT - % of CMDB records with correct data] | [YOUR INPUT - >95%] | [YOUR INPUT - Sample audit] |
| Orphaned Records | [YOUR INPUT - CMDB records for non-existent assets] | [YOUR INPUT - <2%] | [YOUR INPUT - Reconciliation] |
| Unknown Devices | [YOUR INPUT - Network devices not in CMDB] | [YOUR INPUT - <1%] | [YOUR INPUT - Discovery scan] |
| Owner Assignment | [YOUR INPUT - % assets with valid owner] | [YOUR INPUT - 100%] | [YOUR INPUT - CMDB query] |
| Scan Coverage | [YOUR INPUT - % network segments scanned] | [YOUR INPUT - 100%] | [YOUR INPUT - Scan reports] |

---

# SECTION H: ASSET SCENARIOS

## H.1 Scenario: Shadow IT Discovery

```
[YOUR INPUT - Complete this scenario]

SCENARIO: SHADOW IT APPLICATION DISCOVERY
=========================================

SITUATION:
The SOC analyst notices unusual outbound traffic to an unknown 
SaaS application. Investigation reveals that the Marketing 
department has been using an unauthorized file-sharing service 
(FileSharePlus) for the past 6 months to share campaign materials 
with external agencies.

DISCOVERY DETAILS:
- 47 employees have accounts
- Estimated 2TB of data stored
- Includes customer lists and unreleased product information
- Service is free tier with no security guarantees

TASKS:

1. IMMEDIATE RISK ASSESSMENT:
   [YOUR INPUT - Evaluate data exposure risk, compliance implications]

2. DATA CLASSIFICATION:
   [YOUR INPUT - What data classifications are involved?]

3. STAKEHOLDER COMMUNICATION:
   [YOUR INPUT - Who needs to be informed? What's the message?]

4. REMEDIATION PLAN:
   [YOUR INPUT - How to handle existing data, transition users]

5. ASSET MANAGEMENT UPDATES:
   [YOUR INPUT - Register as asset? Block? Provide alternative?]

6. POLICY IMPLICATIONS:
   [YOUR INPUT - What policies were violated? What changes needed?]

7. PREVENTIVE MEASURES:
   [YOUR INPUT - How to prevent similar future incidents]
```

## H.2 Scenario: Emergency Laptop Wiping

```
[YOUR INPUT - Complete this scenario]

SCENARIO: LOST EXECUTIVE LAPTOP
===============================

SITUATION:
The CFO reports their laptop was left in a taxi in Copenhagen 
during a business trip. The laptop contains quarterly financial 
results that haven't been publicly announced. It's 8:00 PM Friday.

LAPTOP DETAILS:
- Asset ID: NS-HEL-LPT-002
- Model: Dell Latitude 5550
- Owner: CFO
- Data Classification: Restricted
- BitLocker: Enabled (TPM+PIN)
- Intune Enrolled: Yes
- Last Check-in: 4 hours ago (device was online)

RESPONSE TASKS:

1. IMMEDIATE ACTIONS (0-15 minutes):
   [YOUR INPUT - What do you do first?]

2. REMOTE WIPE DECISION:
   [YOUR INPUT - Factors to consider, who authorizes?]

3. CONTAINMENT MEASURES:
   [YOUR INPUT - What access needs to be revoked?]

4. NOTIFICATION REQUIREMENTS:
   [YOUR INPUT - Internal notifications, potential external]

5. RECOVERY VS REPLACEMENT:
   [YOUR INPUT - Decision criteria, timeline]

6. DOCUMENTATION:
   [YOUR INPUT - What gets documented, where?]
```

## H.3 Scenario: IoT Firmware Vulnerability

```
[YOUR INPUT - Complete this scenario]

SCENARIO: VULNERABLE IOT DEVICES
================================

SITUATION:
A critical vulnerability (CVSS 9.8) is announced affecting the 
firmware in the energy monitoring sensors deployed across 
NordicShield's data center and manufacturing facilities. 
Approximately 200 sensors are affected.

ASSET DETAILS:
- Device Type: PowerSense Pro 3000 Energy Sensors
- Firmware Version: 2.3.1 (vulnerable: <2.4.0)
- Deployment: 150 in data center, 50 in manufacturing
- Network: IoT VLAN (segmented from corporate)
- Criticality: Medium (monitoring, not control)
- Patched Firmware: Available (2.4.0)

ASSESSMENT TASKS:

1. INVENTORY VERIFICATION:
   [YOUR INPUT - Confirm affected devices, their locations, firmware versions]

2. RISK ASSESSMENT:
   [YOUR INPUT - Exploitability, network position, potential impact]

3. PATCH STRATEGY:
   [YOUR INPUT - How to test and deploy firmware update]

4. COMPENSATING CONTROLS:
   [YOUR INPUT - While patching, what additional protections?]

5. COMMUNICATION:
   [YOUR INPUT - Who needs to know? Operations, management?]

6. ASSET MANAGEMENT UPDATES:
   [YOUR INPUT - How to track patching progress, update CMDB?]
```

---

# SECTION I: METRICS & REPORTING

## I.1 Asset Management Dashboard

| Metric | Current Value | Target | Status | Trend |
|--------|---------------|--------|--------|-------|
| Total Hardware Assets | [YOUR INPUT] | - | - | - |
| Total Software Licenses | [YOUR INPUT] | - | - | - |
| Total Cloud Resources | [YOUR INPUT] | - | - | - |
| Inventory Accuracy | [YOUR INPUT] | >95% | [YOUR INPUT] | [YOUR INPUT] |
| Assets with Owner | [YOUR INPUT] | 100% | [YOUR INPUT] | [YOUR INPUT] |
| Assets Past EOL | [YOUR INPUT] | <5% | [YOUR INPUT] | [YOUR INPUT] |
| Unknown Devices | [YOUR INPUT] | <1% | [YOUR INPUT] | [YOUR INPUT] |
| Software License Compliance | [YOUR INPUT] | 100% | [YOUR INPUT] | [YOUR INPUT] |
| Assets Pending Disposal | [YOUR INPUT] | - | [YOUR INPUT] | - |

## I.2 Reporting Schedule

| Report | Audience | Frequency | Content |
|--------|----------|-----------|---------|
| Asset Inventory Summary | [YOUR INPUT - IT Management] | [YOUR INPUT - Monthly] | [YOUR INPUT - Counts, changes, issues] |
| License Compliance | [YOUR INPUT - IT, Finance] | [YOUR INPUT - Quarterly] | [YOUR INPUT - Over/under licensing] |
| EOL/EOS Report | [YOUR INPUT - IT, Management] | [YOUR INPUT - Monthly] | [YOUR INPUT - Assets approaching/past EOL] |
| Security Posture | [YOUR INPUT - Security, IT] | [YOUR INPUT - Weekly] | [YOUR INPUT - Unmanaged, non-compliant assets] |
| Cloud Resource Utilization | [YOUR INPUT - IT, Finance] | [YOUR INPUT - Monthly] | [YOUR INPUT - Costs, orphaned resources] |

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 4.2 - Asset Management Program |
| **Phase** | 4 - Security Operations |
| **Exam Objectives** | 4.2 - Asset management |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
