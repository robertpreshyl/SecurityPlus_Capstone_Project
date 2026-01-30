# Deliverable 4.5: Identity & Access Management Program
## NordicShield Technologies Oy

---

```
╔══════════════════════════════════════════════════════════════════╗
║          IDENTITY & ACCESS MANAGEMENT PROGRAM                     ║
║                                                                    ║
║  Document ID: IAM-NS-2026-001                                     ║
║  Version: 1.0                                                     ║
║  Author: [YOUR NAME]                                              ║
║  Classification: Confidential                                     ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Document Purpose

This document establishes NordicShield's Identity and Access Management (IAM) program, covering authentication, authorization, account lifecycle management, and privileged access controls. IAM is foundational to security - identity is the new perimeter.

---

## Instructions

1. Design the IAM architecture and governance model
2. Define authentication and authorization policies
3. Create account lifecycle procedures
4. Complete all `[YOUR INPUT]` sections
5. Consider Zero Trust principles throughout

---

# SECTION A: IAM GOVERNANCE

## A.1 IAM Strategy

```
[YOUR INPUT - Define IAM strategy vision]

NORDICSHIELD IAM STRATEGIC VISION
=================================

GUIDING PRINCIPLES:

1. ZERO TRUST: [YOUR INPUT - Never trust, always verify]
   - All access requires authentication
   - Continuous verification throughout session
   - Least privilege by default

2. IDENTITY-CENTRIC SECURITY: [YOUR INPUT - Identity is the new perimeter]
   - Strong authentication for all identities
   - Context-aware access decisions
   - Risk-based adaptive controls

3. SEAMLESS USER EXPERIENCE: [YOUR INPUT - Security without friction]
   - Single Sign-On where possible
   - Passwordless options
   - Self-service capabilities

4. AUTOMATION: [YOUR INPUT - Reduce manual processes]
   - Automated provisioning/deprovisioning
   - Policy-driven access
   - Integration with HR systems

5. AUDITABILITY: [YOUR INPUT - Complete visibility]
   - All access logged and monitored
   - Regular access reviews
   - Compliance reporting
```

## A.2 IAM Architecture

```
[YOUR INPUT - Design the IAM architecture]

┌─────────────────────────────────────────────────────────────────────────┐
│                    NORDICSHIELD IAM ARCHITECTURE                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│                         USERS & ENTITIES                                 │
│         ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐             │
│         │Employees│  │Partners │  │Customers│  │ Service │             │
│         │         │  │Vendors  │  │         │  │Accounts │             │
│         └────┬────┘  └────┬────┘  └────┬────┘  └────┬────┘             │
│              │            │            │            │                    │
│              └────────────┴────────────┴────────────┘                    │
│                                │                                         │
│                                ▼                                         │
│  ┌───────────────────────────────────────────────────────────────────┐  │
│  │                    IDENTITY PROVIDER (IdP)                         │  │
│  │                [YOUR INPUT - Azure AD / Okta]                      │  │
│  │  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐               │  │
│  │  │ Directory    │ │ MFA/Auth     │ │ SSO Services │               │  │
│  │  │ Services     │ │ Services     │ │ SAML/OIDC    │               │  │
│  │  └──────────────┘ └──────────────┘ └──────────────┘               │  │
│  │  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐               │  │
│  │  │ Conditional  │ │ Self-Service │ │ Identity     │               │  │
│  │  │ Access       │ │ Portal       │ │ Governance   │               │  │
│  │  └──────────────┘ └──────────────┘ └──────────────┘               │  │
│  └───────────────────────────────────────────────────────────────────┘  │
│                                │                                         │
│         ┌──────────────────────┼──────────────────────┐                 │
│         │                      │                      │                 │
│         ▼                      ▼                      ▼                 │
│  ┌─────────────┐       ┌─────────────┐       ┌─────────────┐           │
│  │ On-Premises │       │ Cloud Apps  │       │ PAM System  │           │
│  │ Resources   │       │ (SaaS)      │       │ [YOUR INPUT │           │
│  │             │       │             │       │  CyberArk]  │           │
│  │ • AD        │       │ • M365      │       │             │           │
│  │ • File Svrs │       │ • Salesforce│       │ • Vault     │           │
│  │ • Apps      │       │ • AWS/Azure │       │ • Session   │           │
│  │ • Network   │       │ • Custom    │       │ • Recording │           │
│  └─────────────┘       └─────────────┘       └─────────────┘           │
│                                                                          │
│  ┌───────────────────────────────────────────────────────────────────┐  │
│  │                    IDENTITY GOVERNANCE (IGA)                       │  │
│  │               [YOUR INPUT - SailPoint / Saviynt]                   │  │
│  │  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐               │  │
│  │  │ Lifecycle    │ │ Access       │ │ Certification│               │  │
│  │  │ Management   │ │ Requests     │ │ Reviews      │               │  │
│  │  └──────────────┘ └──────────────┘ └──────────────┘               │  │
│  └───────────────────────────────────────────────────────────────────┘  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

## A.3 IAM Roles & Responsibilities

| Role | Responsibilities | Examples |
|------|-----------------|----------|
| Identity Administrator | [YOUR INPUT - Day-to-day IAM operations, account provisioning] | [YOUR INPUT - IT Help Desk, IAM Team] |
| Access Manager | [YOUR INPUT - Access approvals, certification campaigns] | [YOUR INPUT - Application Owners, Managers] |
| PAM Administrator | [YOUR INPUT - Privileged account management, vault administration] | [YOUR INPUT - Security Team] |
| IAM Engineer | [YOUR INPUT - System configuration, integrations, automation] | [YOUR INPUT - IAM Team] |
| IAM Architect | [YOUR INPUT - Strategy, design, standards] | [YOUR INPUT - Security Architecture] |
| Compliance Officer | [YOUR INPUT - Access reviews, audit support, compliance validation] | [YOUR INPUT - GRC Team] |

---

# SECTION B: AUTHENTICATION

## B.1 Authentication Methods

### Primary Authentication Factors

| Factor Type | Methods | Use Case | Strength |
|-------------|---------|----------|----------|
| Knowledge (Something you know) | [YOUR INPUT - Password, PIN, security questions] | [YOUR INPUT - Primary factor, declining use] | [YOUR INPUT - Low-Medium (phishable)] |
| Possession (Something you have) | [YOUR INPUT - Hardware token, authenticator app, smart card, phone] | [YOUR INPUT - MFA factor, passwordless] | [YOUR INPUT - Medium-High] |
| Inherence (Something you are) | [YOUR INPUT - Fingerprint, facial recognition, voice, retina] | [YOUR INPUT - MFA factor, device unlock] | [YOUR INPUT - High] |
| Location (Somewhere you are) | [YOUR INPUT - GPS, network location, IP geolocation] | [YOUR INPUT - Contextual factor, risk signal] | [YOUR INPUT - Medium (supplemental)] |
| Behavior (Something you do) | [YOUR INPUT - Typing patterns, mouse movement, usage patterns] | [YOUR INPUT - Continuous auth, fraud detection] | [YOUR INPUT - Medium (supplemental)] |

### MFA Requirements Matrix

| User Type | Minimum Factors | Required Methods | Exceptions |
|-----------|-----------------|------------------|------------|
| Employees - Standard | [YOUR INPUT - 2FA] | [YOUR INPUT - Password + Authenticator app or FIDO2] | [YOUR INPUT - Device in trusted location may reduce] |
| Employees - Privileged | [YOUR INPUT - 2FA minimum, phishing-resistant preferred] | [YOUR INPUT - FIDO2 key or certificate] | [YOUR INPUT - None] |
| Administrators | [YOUR INPUT - Phishing-resistant MFA required] | [YOUR INPUT - Hardware security key (FIDO2)] | [YOUR INPUT - None] |
| External Partners | [YOUR INPUT - 2FA] | [YOUR INPUT - Authenticator app] | [YOUR INPUT - Based on data access level] |
| Service Accounts | [YOUR INPUT - Certificate or managed identity] | [YOUR INPUT - No interactive password auth] | [YOUR INPUT - Legacy systems (documented)] |
| Customers (B2B Portal) | [YOUR INPUT - Optional 2FA, strongly encouraged] | [YOUR INPUT - TOTP, SMS (fallback)] | [YOUR INPUT - Customer choice] |

## B.2 Passwordless Authentication Strategy

```
[YOUR INPUT - Define passwordless roadmap]

NORDICSHIELD PASSWORDLESS JOURNEY
=================================

CURRENT STATE:
- [YOUR INPUT - Password + MFA for most users]
- [YOUR INPUT - % using passwordless today]

TARGET STATE:
- [YOUR INPUT - Passwordless for all employees by YEAR]
- [YOUR INPUT - Passwords eliminated for privileged accounts]

PHASE 1: FOUNDATION (Months 1-6)
- [YOUR INPUT - Deploy Windows Hello for Business]
- [YOUR INPUT - Roll out FIDO2 security keys to admins]
- [YOUR INPUT - Enable passwordless in Azure AD]

PHASE 2: EXPANSION (Months 7-12)
- [YOUR INPUT - Passwordless option for all employees]
- [YOUR INPUT - Mobile authenticator passwordless]
- [YOUR INPUT - Application integration]

PHASE 3: OPTIMIZATION (Year 2)
- [YOUR INPUT - Password elimination for eligible accounts]
- [YOUR INPUT - Continuous auth exploration]
- [YOUR INPUT - Metrics and refinement]

SUPPORTED METHODS:
┌─────────────────────────────────────────────────────────┐
│  METHOD              │ USE CASE            │ PRIORITY  │
├──────────────────────┼─────────────────────┼───────────┤
│  FIDO2 Security Keys │ Privileged users    │ HIGH      │
│  Windows Hello       │ Windows devices     │ HIGH      │
│  Microsoft Auth App  │ Mobile, all users   │ HIGH      │
│  Certificate/PIV     │ Gov/high security   │ MEDIUM    │
│  [YOUR INPUT]        │ [YOUR INPUT]        │ [YOUR INPUT]│
└─────────────────────────────────────────────────────────┘
```

## B.3 Password Policy

| Policy Setting | Standard Users | Privileged Accounts | Service Accounts |
|---------------|----------------|--------------------:|------------------|
| Minimum Length | [YOUR INPUT - 12 characters] | [YOUR INPUT - 16 characters] | [YOUR INPUT - 24 characters or certificate] |
| Complexity | [YOUR INPUT - 3 of 4 character types] | [YOUR INPUT - 3 of 4] | [YOUR INPUT - 4 of 4 or random] |
| Expiration | [YOUR INPUT - No expiration (NIST 800-63B)] | [YOUR INPUT - 90 days or credential rotation] | [YOUR INPUT - 90 days automatic rotation] |
| History | [YOUR INPUT - 24 passwords remembered] | [YOUR INPUT - 24] | [YOUR INPUT - N/A] |
| Lockout Threshold | [YOUR INPUT - 10 attempts] | [YOUR INPUT - 5 attempts] | [YOUR INPUT - 3 attempts] |
| Lockout Duration | [YOUR INPUT - 30 minutes] | [YOUR INPUT - Until admin reset] | [YOUR INPUT - Until admin review] |
| Banned Password List | [YOUR INPUT - Yes, includes breached + company terms] | [YOUR INPUT - Yes] | [YOUR INPUT - N/A] |

## B.4 Conditional Access Policies

| Policy Name | Conditions | Access Grant/Block | Control |
|-------------|------------|-------------------|---------|
| Require MFA - All Users | [YOUR INPUT - All cloud apps, all users] | [YOUR INPUT - Grant with MFA] | [YOUR INPUT - Enforced] |
| Block Legacy Authentication | [YOUR INPUT - Legacy auth protocols] | [YOUR INPUT - Block] | [YOUR INPUT - Enforced] |
| Require Compliant Device | [YOUR INPUT - Corporate apps from untrusted devices] | [YOUR INPUT - Require device compliance] | [YOUR INPUT - Report > Enforce] |
| High Risk Sign-in | [YOUR INPUT - Sign-in risk = High] | [YOUR INPUT - Block or require password change + MFA] | [YOUR INPUT - Enforced] |
| Privileged Admin Access | [YOUR INPUT - Azure admin portals, admin roles] | [YOUR INPUT - Require phishing-resistant MFA + compliant device] | [YOUR INPUT - Enforced] |
| Impossible Travel | [YOUR INPUT - Impossible travel detected] | [YOUR INPUT - Block and alert] | [YOUR INPUT - Enforced] |
| Named Locations - Trusted | [YOUR INPUT - Office IPs, VPN egress] | [YOUR INPUT - Reduce MFA frequency] | [YOUR INPUT - Optional] |
| Country Block | [YOUR INPUT - Non-business countries] | [YOUR INPUT - Block unless VPN] | [YOUR INPUT - Enforce with exceptions] |

---

# SECTION C: AUTHORIZATION

## C.1 Access Control Models

| Model | Definition | Use Case at NordicShield | Example |
|-------|------------|-------------------------|---------|
| RBAC (Role-Based) | [YOUR INPUT - Access based on job role] | [YOUR INPUT - Primary model for applications] | [YOUR INPUT - Finance role = access finance systems] |
| ABAC (Attribute-Based) | [YOUR INPUT - Access based on user/resource attributes] | [YOUR INPUT - Fine-grained cloud access] | [YOUR INPUT - Access if department=Engineering AND clearance=Confidential] |
| MAC (Mandatory) | [YOUR INPUT - System-enforced based on labels] | [YOUR INPUT - Classified data handling] | [YOUR INPUT - Top Secret data only for cleared users] |
| DAC (Discretionary) | [YOUR INPUT - Owner controls access] | [YOUR INPUT - File sharing within teams] | [YOUR INPUT - SharePoint site owner grants access] |
| Rule-Based | [YOUR INPUT - Access based on rules/conditions] | [YOUR INPUT - Network access, time-based] | [YOUR INPUT - Access only during business hours] |

## C.2 Role-Based Access Control Framework

### Role Hierarchy

```
[YOUR INPUT - Design role hierarchy]

NORDICSHIELD RBAC HIERARCHY
===========================

ORGANIZATIONAL ROLES (Inherited)
├── NS-All-Employees
│   ├── [YOUR INPUT - Basic system access]
│   ├── [YOUR INPUT - Email, collaboration tools]
│   └── [YOUR INPUT - Self-service portal]
│
├── NS-Managers
│   ├── Inherits: NS-All-Employees
│   ├── [YOUR INPUT - Team management tools]
│   ├── [YOUR INPUT - Approval capabilities]
│   └── [YOUR INPUT - Reporting dashboards]
│
└── NS-Executives
    ├── Inherits: NS-Managers
    ├── [YOUR INPUT - Strategic dashboards]
    └── [YOUR INPUT - Board materials]

DEPARTMENTAL ROLES
├── NS-Finance
│   ├── Inherits: NS-All-Employees
│   ├── [YOUR INPUT - ERP Finance module]
│   ├── [YOUR INPUT - Banking systems]
│   └── [YOUR INPUT - Financial reporting]
│
├── NS-Engineering
│   ├── Inherits: NS-All-Employees
│   ├── [YOUR INPUT - Development tools]
│   ├── [YOUR INPUT - Code repositories]
│   └── [YOUR INPUT - CI/CD pipelines]
│
├── NS-HR
│   ├── [YOUR INPUT - HRIS system]
│   └── [YOUR INPUT - Personnel files]
│
└── NS-IT
    ├── [YOUR INPUT - IT service management]
    └── [YOUR INPUT - Infrastructure tools]

APPLICATION ROLES (Per-Application)
├── App-ERP
│   ├── ERP-User (Read-only)
│   ├── ERP-Editor (Read/Write)
│   ├── ERP-Approver (Workflow approval)
│   └── ERP-Admin (Configuration)
│
└── App-CRM
    ├── CRM-Sales (Sales data)
    ├── CRM-Support (Support data)
    └── CRM-Admin (All data + config)
```

## C.3 Access Request Process

```
[YOUR INPUT - Design access request workflow]

ACCESS REQUEST WORKFLOW
=======================

┌─────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│  USER INITIATES REQUEST                                                 │
│  ┌────────────────────────────────────────────────────────────────┐    │
│  │  Via: Self-service portal                                       │    │
│  │  Info required:                                                 │    │
│  │  - [YOUR INPUT - System/resource requested]                     │    │
│  │  - [YOUR INPUT - Access level/role needed]                      │    │
│  │  - [YOUR INPUT - Business justification]                        │    │
│  │  - [YOUR INPUT - Duration (permanent/temporary)]                │    │
│  └───────────────────────────┬────────────────────────────────────┘    │
│                              │                                          │
│                              ▼                                          │
│  MANAGER APPROVAL                                                       │
│  ┌────────────────────────────────────────────────────────────────┐    │
│  │  [YOUR INPUT - Direct manager reviews business need]            │    │
│  │  Approval SLA: [YOUR INPUT - 2 business days]                   │    │
│  │  Auto-escalation if not actioned: [YOUR INPUT - 3 days]        │    │
│  └───────────────────────────┬────────────────────────────────────┘    │
│                              │                                          │
│                    ┌─────────┴─────────┐                               │
│                    │                   │                               │
│              Standard Access      Sensitive Access                     │
│                    │                   │                               │
│                    ▼                   ▼                               │
│  ┌─────────────────────┐  ┌────────────────────────────────────┐      │
│  │  AUTO-PROVISIONING  │  │  ADDITIONAL APPROVAL               │      │
│  │  (If approved)      │  │  - [YOUR INPUT - Data owner]       │      │
│  │                     │  │  - [YOUR INPUT - Security (high)]  │      │
│  └──────────┬──────────┘  └─────────────────┬──────────────────┘      │
│             │                               │                          │
│             └───────────────┬───────────────┘                          │
│                             │                                          │
│                             ▼                                          │
│  PROVISIONING                                                          │
│  ┌────────────────────────────────────────────────────────────────┐   │
│  │  - [YOUR INPUT - Automated via IGA or manual ticket]           │   │
│  │  - SLA: [YOUR INPUT - Same day for automated, 2 days manual]   │   │
│  │  - Notification sent to user upon completion                   │   │
│  └───────────────────────────┬────────────────────────────────────┘   │
│                              │                                         │
│                              ▼                                         │
│  VERIFICATION & DOCUMENTATION                                         │
│  ┌────────────────────────────────────────────────────────────────┐   │
│  │  - [YOUR INPUT - Access verified functional]                   │   │
│  │  - [YOUR INPUT - Audit trail complete]                         │   │
│  │  - [YOUR INPUT - Certification scheduled if applicable]        │   │
│  └────────────────────────────────────────────────────────────────┘   │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

## C.4 Segregation of Duties (SoD)

### SoD Matrix

| Conflicting Functions | Function A | Function B | Risk | Control |
|----------------------|------------|------------|------|---------|
| Purchase & Payment | [YOUR INPUT - Create purchase orders] | [YOUR INPUT - Approve payments] | [YOUR INPUT - Fraud] | [YOUR INPUT - IGA SoD rule, requires exception approval] |
| User Creation & Approval | [YOUR INPUT - Create user accounts] | [YOUR INPUT - Approve account creation] | [YOUR INPUT - Unauthorized access] | [YOUR INPUT - Workflow separation] |
| Development & Production | [YOUR INPUT - Write code] | [YOUR INPUT - Deploy to production] | [YOUR INPUT - Unauthorized changes] | [YOUR INPUT - CI/CD controls, different roles] |
| Data Entry & Audit | [YOUR INPUT - Enter financial data] | [YOUR INPUT - Review/audit transactions] | [YOUR INPUT - Undetected fraud] | [YOUR INPUT - Role separation] |
| Security Admin & Audit | [YOUR INPUT - Manage security tools] | [YOUR INPUT - Review security logs] | [YOUR INPUT - Cover up incidents] | [YOUR INPUT - SIEM access separation] |

---

# SECTION D: ACCOUNT LIFECYCLE MANAGEMENT

## D.1 Lifecycle Stages

```
[YOUR INPUT - Define account lifecycle]

IDENTITY LIFECYCLE MANAGEMENT
=============================

┌─────────────┐
│  1. CREATE  │──► New employee, contractor, service account
│  (Joiner)   │    - [YOUR INPUT - HR triggers creation]
│             │    - [YOUR INPUT - Baseline access granted]
└──────┬──────┘    - [YOUR INPUT - Welcome communication sent]
       │
       ▼
┌─────────────┐
│ 2. MAINTAIN │──► Day-to-day access management
│  (Active)   │    - [YOUR INPUT - Access requests/changes]
│             │    - [YOUR INPUT - Role changes (mover)]
└──────┬──────┘    - [YOUR INPUT - Periodic certification]
       │
       ▼
┌─────────────┐
│ 3. MODIFY   │──► Job change, transfer, promotion
│  (Mover)    │    - [YOUR INPUT - Old access reviewed]
│             │    - [YOUR INPUT - New access provisioned]
└──────┬──────┘    - [YOUR INPUT - Inappropriate access removed]
       │
       ▼
┌─────────────┐
│ 4. SUSPEND  │──► Leave of absence, investigation
│ (Temporary) │    - [YOUR INPUT - Access suspended not deleted]
│             │    - [YOUR INPUT - Reactivation process defined]
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ 5. DISABLE  │──► Employment ends, contract expires
│  (Leaver)   │    - [YOUR INPUT - Same-day access termination]
│             │    - [YOUR INPUT - Data handling procedures]
└──────┬──────┘    - [YOUR INPUT - Knowledge transfer]
       │
       ▼
┌─────────────┐
│ 6. ARCHIVE  │──► Account removed from active systems
│  /DELETE    │    - [YOUR INPUT - Retain audit logs per policy]
│             │    - [YOUR INPUT - Delete PII per GDPR]
└─────────────┘    - [YOUR INPUT - Archive for legal hold if needed]
```

## D.2 Joiner Process (Onboarding)

| Step | Trigger | Action | Timeline | Owner |
|------|---------|--------|----------|-------|
| 1 | [YOUR INPUT - HR completes new hire in HRIS] | [YOUR INPUT - IGA receives feed] | [YOUR INPUT - Start date -5 days] | [YOUR INPUT - HR] |
| 2 | [YOUR INPUT - IGA creates identity] | [YOUR INPUT - AD account, mailbox, baseline groups] | [YOUR INPUT - Start date -3 days] | [YOUR INPUT - Automated] |
| 3 | [YOUR INPUT - Manager notified] | [YOUR INPUT - Request additional access if needed] | [YOUR INPUT - Start date -3 days] | [YOUR INPUT - Manager] |
| 4 | [YOUR INPUT - Additional access provisioned] | [YOUR INPUT - Application accounts created] | [YOUR INPUT - Start date -1 day] | [YOUR INPUT - Automated/IT] |
| 5 | [YOUR INPUT - Credentials delivered] | [YOUR INPUT - Secure delivery of initial credentials] | [YOUR INPUT - Start date] | [YOUR INPUT - IT/Self-service] |
| 6 | [YOUR INPUT - First login] | [YOUR INPUT - Force password change, MFA setup] | [YOUR INPUT - Day 1] | [YOUR INPUT - User] |
| 7 | [YOUR INPUT - Security training] | [YOUR INPUT - Complete security awareness] | [YOUR INPUT - Week 1] | [YOUR INPUT - User] |

## D.3 Leaver Process (Offboarding)

| Step | Trigger | Action | Timeline | Owner |
|------|---------|--------|----------|-------|
| 1 | [YOUR INPUT - HR records termination date] | [YOUR INPUT - IGA receives notification] | [YOUR INPUT - Immediately upon HR update] | [YOUR INPUT - HR] |
| 2 | [YOUR INPUT - Manager notification] | [YOUR INPUT - Knowledge transfer, data handling] | [YOUR INPUT - 2 weeks before (if planned)] | [YOUR INPUT - Manager] |
| 3 | [YOUR INPUT - Access review] | [YOUR INPUT - Identify shared passwords, data access] | [YOUR INPUT - Before last day] | [YOUR INPUT - IT/Security] |
| 4 | [YOUR INPUT - Account disable] | [YOUR INPUT - Disable AD, email, all apps] | [YOUR INPUT - Last day end of business (or immediate if involuntary)] | [YOUR INPUT - Automated/IT] |
| 5 | [YOUR INPUT - Remove from groups] | [YOUR INPUT - All security group memberships] | [YOUR INPUT - Same as disable] | [YOUR INPUT - Automated] |
| 6 | [YOUR INPUT - Shared password rotation] | [YOUR INPUT - Rotate any known shared credentials] | [YOUR INPUT - Within 24 hours] | [YOUR INPUT - IT/App owners] |
| 7 | [YOUR INPUT - Data handling] | [YOUR INPUT - Mailbox retention, file transfer, deletion] | [YOUR INPUT - Per retention policy] | [YOUR INPUT - IT/Manager] |
| 8 | [YOUR INPUT - Hardware return] | [YOUR INPUT - Collect devices, badges, keys] | [YOUR INPUT - Last day] | [YOUR INPUT - IT/HR] |
| 9 | [YOUR INPUT - Account deletion] | [YOUR INPUT - Remove identity from systems] | [YOUR INPUT - +30 days (after retention period)] | [YOUR INPUT - Automated] |

## D.4 Mover Process (Role Change)

| Type | Process | Key Consideration |
|------|---------|-------------------|
| Same Department | [YOUR INPUT - Review current access, add new role access] | [YOUR INPUT - Remove access no longer needed] |
| Different Department | [YOUR INPUT - Full access review, treat like partial leaver/joiner] | [YOUR INPUT - High risk of access accumulation] |
| Promotion to Management | [YOUR INPUT - Add management access, retain individual contributor if needed] | [YOUR INPUT - Review reports' access] |
| Demotion | [YOUR INPUT - Remove elevated access immediately] | [YOUR INPUT - Sensitive, handle with HR] |
| Contractor to Employee | [YOUR INPUT - Migrate identity, retain access history] | [YOUR INPUT - Update identity attributes] |

---

# SECTION E: PRIVILEGED ACCESS MANAGEMENT (PAM)

## E.1 Privileged Account Types

| Account Type | Definition | Examples | Risk Level |
|--------------|------------|----------|------------|
| Domain Admin | [YOUR INPUT - Full control of AD domain] | [YOUR INPUT - Domain Admins, Enterprise Admins] | [YOUR INPUT - Critical] |
| Local Admin | [YOUR INPUT - Admin rights on specific systems] | [YOUR INPUT - Local Administrators group] | [YOUR INPUT - High] |
| Cloud Admin | [YOUR INPUT - Admin roles in cloud platforms] | [YOUR INPUT - Global Admin, AWS root, Subscription Owner] | [YOUR INPUT - Critical] |
| Database Admin | [YOUR INPUT - Full database access] | [YOUR INPUT - sa, postgres superuser] | [YOUR INPUT - Critical] |
| Application Admin | [YOUR INPUT - Admin access to applications] | [YOUR INPUT - ERP admin, security tool admin] | [YOUR INPUT - High] |
| Network Admin | [YOUR INPUT - Network infrastructure access] | [YOUR INPUT - Enable 15, firewall admin] | [YOUR INPUT - Critical] |
| Security Admin | [YOUR INPUT - Security tool administration] | [YOUR INPUT - SIEM admin, EDR admin] | [YOUR INPUT - Critical] |
| Service Account (Privileged) | [YOUR INPUT - Automated processes with elevated rights] | [YOUR INPUT - Backup service, deployment pipeline] | [YOUR INPUT - High-Critical] |
| Emergency/Break-Glass | [YOUR INPUT - Last-resort access] | [YOUR INPUT - Emergency admin accounts] | [YOUR INPUT - Critical] |

## E.2 PAM Controls

### PAM Architecture

```
[YOUR INPUT - Design PAM architecture]

┌─────────────────────────────────────────────────────────────────────────┐
│                        PAM SOLUTION                                      │
│                   [YOUR INPUT - CyberArk / BeyondTrust]                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │                    PRIVILEGED VAULT                               │   │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐           │   │
│  │  │ Windows       │  │ Unix/Linux   │  │ Cloud        │           │   │
│  │  │ Credentials   │  │ Credentials  │  │ Credentials  │           │   │
│  │  └──────────────┘  └──────────────┘  └──────────────┘           │   │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐           │   │
│  │  │ Database      │  │ Network      │  │ Application  │           │   │
│  │  │ Credentials   │  │ Credentials  │  │ Credentials  │           │   │
│  │  └──────────────┘  └──────────────┘  └──────────────┘           │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                              │                                           │
│                              ▼                                           │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐              │
│  │ Just-in-Time │    │ Session      │    │ Privileged   │              │
│  │ Access       │    │ Management   │    │ Threat       │              │
│  │              │    │              │    │ Analytics    │              │
│  │ [YOUR INPUT -│    │ [YOUR INPUT -│    │ [YOUR INPUT -│              │
│  │ Request &    │    │ Recording,   │    │ Anomaly      │              │
│  │ approval]    │    │ monitoring]  │    │ detection]   │              │
│  └──────────────┘    └──────────────┘    └──────────────┘              │
│                              │                                           │
│         ┌────────────────────┼────────────────────┐                     │
│         │                    │                    │                     │
│         ▼                    ▼                    ▼                     │
│  ┌─────────────┐     ┌─────────────┐     ┌─────────────┐               │
│  │ Windows     │     │ Linux/Unix  │     │ Cloud       │               │
│  │ Servers     │     │ Servers     │     │ Resources   │               │
│  │ [RDP]       │     │ [SSH]       │     │ [API/Portal]│               │
│  └─────────────┘     └─────────────┘     └─────────────┘               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### PAM Policy Requirements

| Control | Requirement | Implementation |
|---------|-------------|----------------|
| Credential Vaulting | [YOUR INPUT - All privileged credentials stored in vault] | [YOUR INPUT - No direct credential knowledge] |
| Password Rotation | [YOUR INPUT - Automatic rotation after each use or max 24 hours] | [YOUR INPUT - Vault-managed rotation] |
| Just-in-Time Access | [YOUR INPUT - No standing privileges, request when needed] | [YOUR INPUT - Time-limited checkout] |
| Approval Workflow | [YOUR INPUT - Dual approval for highest-risk access] | [YOUR INPUT - Manager + Security] |
| Session Recording | [YOUR INPUT - All privileged sessions recorded] | [YOUR INPUT - Video + keystroke logging] |
| Session Monitoring | [YOUR INPUT - Real-time session viewing for critical systems] | [YOUR INPUT - SOC can observe live] |
| Command Filtering | [YOUR INPUT - Block dangerous commands] | [YOUR INPUT - Prevent rm -rf, shutdown, etc.] |
| MFA | [YOUR INPUT - Phishing-resistant MFA required] | [YOUR INPUT - FIDO2 security key] |

## E.3 Break-Glass Procedure

```
[YOUR INPUT - Create emergency access procedure]

EMERGENCY/BREAK-GLASS ACCESS PROCEDURE
======================================

PURPOSE:
Emergency access for critical situations when normal access 
methods are unavailable or too slow.

TRIGGER CONDITIONS:
1. [YOUR INPUT - Major outage affecting normal authentication]
2. [YOUR INPUT - Security incident requiring immediate response]
3. [YOUR INPUT - Business-critical situation with no available admin]

BREAK-GLASS ACCOUNTS:

| Account | Scope | Access Level | Physical Location |
|---------|-------|--------------|-------------------|
| BG-AD-Admin | [YOUR INPUT - AD Domain] | [YOUR INPUT - Domain Admin] | [YOUR INPUT - Safe + PAM] |
| BG-Azure-Admin | [YOUR INPUT - Azure Tenant] | [YOUR INPUT - Global Admin] | [YOUR INPUT - Safe + PAM] |
| BG-AWS-Root | [YOUR INPUT - AWS Organization] | [YOUR INPUT - Root access] | [YOUR INPUT - Physical safe] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

ACCESS PROCEDURE:

Step 1: AUTHORIZATION
- Verbal approval from: [YOUR INPUT - CISO or CTO]
- Document: [YOUR INPUT - Requester, reason, approver, time]
- If approvers unavailable: [YOUR INPUT - Escalation path]

Step 2: RETRIEVE CREDENTIALS
- Location 1 (Primary): [YOUR INPUT - PAM system emergency checkout]
- Location 2 (Backup): [YOUR INPUT - Physical safe, sealed envelope]
- Dual custody: [YOUR INPUT - Two people required for physical]

Step 3: EXECUTE
- Document all actions taken
- Use for minimum necessary scope
- Have witness if possible

Step 4: POST-USE (Within 1 hour)
- [YOUR INPUT - Immediately rotate credential]
- [YOUR INPUT - Document all activities in incident ticket]
- [YOUR INPUT - Review session recording]
- [YOUR INPUT - Replace physical envelope if used]

Step 5: REVIEW (Within 24 hours)
- [YOUR INPUT - Security review of all actions]
- [YOUR INPUT - Verify no unauthorized changes]
- [YOUR INPUT - Root cause analysis of why break-glass needed]
```

---

# SECTION F: ACCESS CERTIFICATION

## F.1 Certification Campaign Schedule

| Campaign | Scope | Frequency | Reviewers | Deadline |
|----------|-------|-----------|-----------|----------|
| All User Access | [YOUR INPUT - All active users, all access] | [YOUR INPUT - Annual] | [YOUR INPUT - Managers] | [YOUR INPUT - 30 days] |
| Privileged Access | [YOUR INPUT - All privileged accounts] | [YOUR INPUT - Quarterly] | [YOUR INPUT - Manager + Security] | [YOUR INPUT - 14 days] |
| Service Accounts | [YOUR INPUT - All service accounts] | [YOUR INPUT - Semi-annual] | [YOUR INPUT - Application owners] | [YOUR INPUT - 30 days] |
| Sensitive Applications | [YOUR INPUT - Financial, HR systems] | [YOUR INPUT - Quarterly] | [YOUR INPUT - Manager + App owner] | [YOUR INPUT - 21 days] |
| External/Partner Access | [YOUR INPUT - Non-employee access] | [YOUR INPUT - Quarterly] | [YOUR INPUT - Business sponsor] | [YOUR INPUT - 14 days] |

## F.2 Certification Decision Options

| Decision | Definition | Action |
|----------|------------|--------|
| Certify | [YOUR INPUT - Access is appropriate and needed] | [YOUR INPUT - No change, document approval] |
| Revoke | [YOUR INPUT - Access should be removed] | [YOUR INPUT - Remove immediately, notify user] |
| Modify | [YOUR INPUT - Access level should change] | [YOUR INPUT - Adjust to appropriate level] |
| Delegate | [YOUR INPUT - Reviewer cannot assess] | [YOUR INPUT - Reassign to appropriate reviewer] |
| Escalate | [YOUR INPUT - Unsure, needs investigation] | [YOUR INPUT - Security/IAM team review] |

## F.3 Certification Report Template

```
[YOUR INPUT - Design certification report]

ACCESS CERTIFICATION CAMPAIGN REPORT
====================================

Campaign Name: [YOUR INPUT]
Campaign Period: [START DATE] - [END DATE]
Report Generated: [DATE]

SUMMARY:
┌────────────────────────────────────────────────────────────┐
│  Users in Scope:         [XX]                              │
│  Entitlements Reviewed:  [XXXX]                            │
│  Certifications Made:    [XX]%                             │
│  Access Revoked:         [XX] ([XX]%)                      │
│  Access Modified:        [XX] ([XX]%)                      │
│  Not Completed:          [XX] ([XX]%) ⚠️                    │
└────────────────────────────────────────────────────────────┘

COMPLETION STATUS BY REVIEWER:
| Reviewer | Assigned | Completed | Pending | Status |
|----------|----------|-----------|---------|--------|
| [YOUR INPUT] | | | | |

HIGH-RISK FINDINGS:
1. [YOUR INPUT - Orphaned privileged accounts]
2. [YOUR INPUT - Excessive access accumulation]
3. [YOUR INPUT - SoD violations]

REMEDIATION ACTIONS:
| Finding | Action | Owner | Due Date | Status |
|---------|--------|-------|----------|--------|
| [YOUR INPUT] | | | | |

METRICS:
- Average review time per entitlement: [XX minutes]
- Revocation rate trend: [↑/↓ vs last campaign]
- Overdue certifications: [XX]

RECOMMENDATIONS:
1. [YOUR INPUT]
2. [YOUR INPUT]
```

---

# SECTION G: IAM SCENARIOS

## G.1 Scenario: Account Compromise

```
[YOUR INPUT - Complete this scenario]

SCENARIO: COMPROMISED USER ACCOUNT
==================================

SITUATION:
The SOC receives an alert at 3:15 PM: "Impossible travel detected" 
for user pekka.virtanen@nordicshield.fi. Pekka is a Senior 
Engineer based in Helsinki.

ALERT DETAILS:
- 2:30 PM: Successful login from Helsinki office (usual)
- 3:10 PM: Successful login from an IP in Russia
- 3:12 PM: Multiple failed MFA attempts from Russia
- 3:14 PM: Successful login bypassing MFA (legacy auth)
- 3:15 PM: Alert fires

ACCOUNT DETAILS:
- Role: Senior Engineer
- Access: Code repositories, CI/CD pipeline, AWS development
- MFA: Yes (Microsoft Authenticator)
- Recent activity: Normal until today

RESPONSE TASKS:

1. IMMEDIATE CONTAINMENT (0-15 minutes):
   [YOUR INPUT - What do you do immediately?]
   - Account: [YOUR INPUT - Disable? Force sign-out?]
   - Sessions: [YOUR INPUT - Revoke tokens?]
   - Communication: [YOUR INPUT - Contact user?]

2. INVESTIGATION:
   [YOUR INPUT - What do you need to determine?]
   - Was MFA actually bypassed? How?
   - What did the attacker access?
   - How were credentials compromised?

3. ACCESS REVIEW:
   [YOUR INPUT - What access needs to be reviewed?]
   - Code repositories: [YOUR INPUT]
   - AWS resources: [YOUR INPUT]
   - Email/files: [YOUR INPUT]

4. REMEDIATION:
   [YOUR INPUT - After containment, what's the recovery plan?]
   - Password: [YOUR INPUT]
   - MFA: [YOUR INPUT]
   - Access: [YOUR INPUT]
   - Legacy auth: [YOUR INPUT]

5. ROOT CAUSE:
   [YOUR INPUT - How do you determine how this happened?]
```

## G.2 Scenario: Privileged Escalation Request

```
[YOUR INPUT - Complete this scenario]

SCENARIO: URGENT PRIVILEGED ACCESS REQUEST
==========================================

SITUATION:
Friday 4:45 PM. You receive an urgent request:

"I need Domain Admin access immediately. One of our core database 
servers is down and I need to troubleshoot. My manager approved 
verbally. Please provision ASAP - we're losing €10,000 per hour."

- Requestor: mikko.lahtinen@nordicshield.fi
- Role: Database Administrator
- Current Access: Local admin on database servers, no domain admin

EVALUATION TASKS:

1. INITIAL ASSESSMENT:
   [YOUR INPUT - Is this request legitimate?]
   - Does DBA role require domain admin? [YOUR INPUT]
   - Is there an alternative approach? [YOUR INPUT]

2. VERIFICATION:
   [YOUR INPUT - How do you verify this is legitimate?]
   - Requestor identity: [YOUR INPUT]
   - Manager approval: [YOUR INPUT]
   - Incident existence: [YOUR INPUT]

3. RISK EVALUATION:
   [YOUR INPUT - What are the risks of granting vs. denying?]
   - Grant without process: [YOUR INPUT]
   - Deny/delay: [YOUR INPUT]

4. ALTERNATIVES:
   [YOUR INPUT - What alternatives could address the need?]
   - Alternative 1: [YOUR INPUT - Just-in-time specific access?]
   - Alternative 2: [YOUR INPUT - Have existing admin assist?]
   - Alternative 3: [YOUR INPUT - Supervised session?]

5. YOUR DECISION:
   [YOUR INPUT - What do you do and why?]

6. DOCUMENTATION:
   [YOUR INPUT - What must be documented regardless of decision?]
```

## G.3 Scenario: Orphaned Accounts

```
[YOUR INPUT - Complete this scenario]

SCENARIO: ORPHANED ACCOUNT DISCOVERY
====================================

SITUATION:
During quarterly access certification, you discover:
- 47 active accounts with no manager assigned in HR system
- 23 accounts have no login activity in 90+ days
- 12 accounts belong to people who left the company 6-18 months ago
- 5 service accounts have no documented owner

ANALYSIS TASKS:

1. RISK ASSESSMENT:
   [YOUR INPUT - What's the risk of each category?]
   - No manager accounts: [YOUR INPUT]
   - Inactive accounts: [YOUR INPUT]
   - Former employee accounts: [YOUR INPUT]
   - Ownerless service accounts: [YOUR INPUT]

2. PRIORITIZATION:
   [YOUR INPUT - Which do you address first?]
   Priority 1: [YOUR INPUT]
   Priority 2: [YOUR INPUT]
   Priority 3: [YOUR INPUT]

3. REMEDIATION PLAN:

   Category A - No Manager:
   [YOUR INPUT - How to find/assign owners?]

   Category B - Inactive:
   [YOUR INPUT - Disable? Investigate? Timeline?]

   Category C - Former Employees:
   [YOUR INPUT - Immediate disable? Check for usage?]

   Category D - Service Accounts:
   [YOUR INPUT - How to find owners? What if no owner found?]

4. PROCESS IMPROVEMENT:
   [YOUR INPUT - How did this happen? What controls failed?]
   - HR integration: [YOUR INPUT]
   - Offboarding process: [YOUR INPUT]
   - Service account governance: [YOUR INPUT]

5. METRICS TO TRACK:
   [YOUR INPUT - What KPIs would prevent recurrence?]
```

---

# SECTION H: METRICS & REPORTING

## H.1 IAM KPIs

| Metric | Definition | Target | Current | Status |
|--------|------------|--------|---------|--------|
| Provisioning Time | [YOUR INPUT - Time from request approval to access granted] | [YOUR INPUT - <4 hours automated, <24 hours manual] | [YOUR INPUT] | [YOUR INPUT] |
| Deprovisioning Time | [YOUR INPUT - Time from termination notification to access removed] | [YOUR INPUT - Same day (involuntary), <24 hours (voluntary)] | [YOUR INPUT] | [YOUR INPUT] |
| MFA Adoption | [YOUR INPUT - % of users with MFA enabled] | [YOUR INPUT - 100%] | [YOUR INPUT] | [YOUR INPUT] |
| Passwordless Adoption | [YOUR INPUT - % of users using passwordless] | [YOUR INPUT - 50% by EOY] | [YOUR INPUT] | [YOUR INPUT] |
| Access Review Completion | [YOUR INPUT - % of certifications completed on time] | [YOUR INPUT - 100%] | [YOUR INPUT] | [YOUR INPUT] |
| Orphaned Accounts | [YOUR INPUT - Active accounts without valid owner] | [YOUR INPUT - 0] | [YOUR INPUT] | [YOUR INPUT] |
| Privileged Account Ratio | [YOUR INPUT - Privileged accounts / total accounts] | [YOUR INPUT - <5%] | [YOUR INPUT] | [YOUR INPUT] |
| SoD Violations | [YOUR INPUT - Number of segregation of duties violations] | [YOUR INPUT - 0 critical, <5 high with mitigations] | [YOUR INPUT] | [YOUR INPUT] |
| Failed Auth Rate | [YOUR INPUT - Failed logins / total logins] | [YOUR INPUT - <5%] | [YOUR INPUT] | [YOUR INPUT] |

## H.2 IAM Dashboard

```
[YOUR INPUT - Design IAM executive dashboard]

┌─────────────────────────────────────────────────────────────────────────┐
│                    NORDICSHIELD IAM DASHBOARD                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  IDENTITY OVERVIEW                                                       │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐│
│  │ Total        │  │ Active       │  │ Privileged   │  │ External     ││
│  │ Identities   │  │ Users        │  │ Accounts     │  │ Partners     ││
│  │   [XXXX]     │  │   [XXXX]     │  │   [XXX]      │  │   [XXX]      ││
│  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘│
│                                                                          │
│  SECURITY POSTURE                                                        │
│  ┌─────────────────────────────────────────────────────────────────────┐│
│  │  MFA Coverage: [██████████░░] 95%     Target: 100%                  ││
│  │  Passwordless: [████░░░░░░░░] 32%     Target: 50%                   ││
│  │  Legacy Auth:  [██░░░░░░░░░░] 8%      Target: 0%                    ││
│  │  Compliant:    [█████████░░░] 89%     Target: 95%                   ││
│  └─────────────────────────────────────────────────────────────────────┘│
│                                                                          │
│  RISK INDICATORS                        RECENT ACTIVITY                  │
│  ┌───────────────────────────┐         ┌───────────────────────────┐   │
│  │ 🔴 High Risk Sign-ins: XX │         │ New Users (7d): XX        │   │
│  │ 🟠 Orphaned Accounts: XX  │         │ Terminated (7d): XX       │   │
│  │ 🟡 Expired Reviews: XX    │         │ Access Requests: XX       │   │
│  │ 🟢 SoD Exceptions: XX     │         │ Privileged Sessions: XX   │   │
│  └───────────────────────────┘         └───────────────────────────┘   │
│                                                                          │
│  ACCESS CERTIFICATION STATUS                                            │
│  ┌─────────────────────────────────────────────────────────────────────┐│
│  │  Campaign: Q1 Privileged Access Review                              ││
│  │  Progress: [████████████████░░░░] 80%     Due: [DATE]               ││
│  │  Certified: XXX   Revoked: XX   Pending: XX                         ││
│  └─────────────────────────────────────────────────────────────────────┘│
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 4.5 - Identity & Access Management Program |
| **Phase** | 4 - Security Operations |
| **Exam Objectives** | 4.6 - Identity and access management |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
