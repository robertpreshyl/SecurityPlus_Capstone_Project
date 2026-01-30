# Deliverable 3.3: Enterprise Data Protection Strategy
## NordicShield Technologies Oy

---

```
╔══════════════════════════════════════════════════════════════════╗
║          ENTERPRISE DATA PROTECTION STRATEGY                     ║
║                                                                    ║
║  Document ID: DATA-NS-2026-001                                    ║
║  Version: 1.0                                                     ║
║  Author: [YOUR NAME]                                              ║
║  Classification: Confidential                                     ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Document Purpose

This document defines NordicShield's comprehensive data protection strategy, covering data classification, encryption standards, data loss prevention, data sovereignty compliance, and key management across all data states.

---

## Instructions

1. Design each data protection control with business context
2. Ensure GDPR and multi-jurisdictional compliance
3. Complete all `[YOUR INPUT]` sections
4. Create data flow diagrams as specified
5. Reference NordicShield's IoT and global expansion context

---

# SECTION A: DATA CLASSIFICATION FRAMEWORK

## A.1 Classification Levels

Define NordicShield's data classification scheme:

| Level | Name | Description | Examples | Handling Requirements |
|-------|------|-------------|----------|----------------------|
| **Level 4** | [YOUR INPUT - e.g., Top Secret/Critical] | [YOUR INPUT] | [YOUR INPUT - R&D algorithms, source code] | [YOUR INPUT - Encryption, access logging, etc.] |
| **Level 3** | [YOUR INPUT - e.g., Confidential] | [YOUR INPUT] | [YOUR INPUT - PII, financial] | [YOUR INPUT] |
| **Level 2** | [YOUR INPUT - e.g., Internal] | [YOUR INPUT] | [YOUR INPUT - Policies, org charts] | [YOUR INPUT] |
| **Level 1** | [YOUR INPUT - e.g., Public] | [YOUR INPUT] | [YOUR INPUT - Marketing, website] | [YOUR INPUT] |

## A.2 Data Types Inventory

### Structured Data

| Data Type | Classification | Location | Owner | Sensitivity | Retention |
|-----------|---------------|----------|-------|-------------|-----------|
| Customer PII | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Employee HR Data | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Financial Records | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Telemetry | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Proprietary Algorithms | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Sales/CRM Data | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Unstructured Data

| Data Type | Classification | Location | Owner | Discovery Method |
|-----------|---------------|----------|-------|------------------|
| Engineering Documents | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Email Communications | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Chat/Collaboration | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Source Code | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Research Notes | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## A.3 Classification Process

```
[YOUR INPUT - Design the data classification workflow]

┌─────────────────────────────────────────────────────────────────────────┐
│                    DATA CLASSIFICATION WORKFLOW                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. DATA CREATION/ACQUISITION                                            │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  [YOUR INPUT - Who creates? What triggers classification?]      │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                              │                                           │
│                              ▼                                           │
│  2. CLASSIFICATION DECISION                                              │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  [YOUR INPUT - Manual? Automated? What criteria?]               │    │
│  │                                                                  │    │
│  │  Decision Factors:                                               │    │
│  │  - [YOUR INPUT]                                                  │    │
│  │  - [YOUR INPUT]                                                  │    │
│  │  - [YOUR INPUT]                                                  │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                              │                                           │
│                              ▼                                           │
│  3. LABELING                                                             │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  [YOUR INPUT - How is data labeled? Tools? Markings?]           │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                              │                                           │
│                              ▼                                           │
│  4. HANDLING & PROTECTION                                                │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  [YOUR INPUT - Controls applied based on classification]        │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                              │                                           │
│                              ▼                                           │
│  5. REVIEW & RECLASSIFICATION                                            │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  [YOUR INPUT - When is data reclassified? Downgraded?]          │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

## A.4 Classification Policy

```
[YOUR INPUT - Write summary of classification policy]

DATA CLASSIFICATION POLICY - NORDICSHIELD TECHNOLOGIES

1. PURPOSE
   [YOUR INPUT]

2. SCOPE
   [YOUR INPUT]

3. ROLES AND RESPONSIBILITIES
   Data Owner: [YOUR INPUT]
   Data Custodian: [YOUR INPUT]
   Data User: [YOUR INPUT]

4. CLASSIFICATION REQUIREMENTS
   - [YOUR INPUT]
   - [YOUR INPUT]
   - [YOUR INPUT]

5. EXCEPTIONS
   [YOUR INPUT]
```

---

# SECTION B: DATA STATES & PROTECTION

## B.1 Data at Rest Protection

### Encryption Requirements by Classification

| Classification | Encryption Required | Algorithm | Key Length | Key Management |
|---------------|---------------------|-----------|------------|----------------|
| Level 4 (Critical) | [YOUR INPUT - Yes] | [YOUR INPUT - AES-256] | [YOUR INPUT] | [YOUR INPUT - HSM] |
| Level 3 (Confidential) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Level 2 (Internal) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Level 1 (Public) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Storage Encryption by Platform

| Platform | Encryption Method | Key Storage | Notes |
|----------|------------------|-------------|-------|
| AWS S3 | [YOUR INPUT - SSE-KMS, SSE-S3, client-side] | [YOUR INPUT] | [YOUR INPUT] |
| AWS EBS | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| AWS RDS | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| On-Prem Storage | [YOUR INPUT - NetApp, LUKS, etc.] | [YOUR INPUT] | [YOUR INPUT] |
| Endpoint Drives | [YOUR INPUT - BitLocker, FileVault] | [YOUR INPUT] | [YOUR INPUT] |
| Backup Storage | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Mobile Devices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Database Encryption

| Database | Encryption Type | Column-Level | Notes |
|----------|----------------|--------------|-------|
| PostgreSQL (Production) | [YOUR INPUT - TDE?] | [YOUR INPUT - For PII?] | [YOUR INPUT] |
| MySQL (Legacy) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| MongoDB (IoT) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Redis (Cache) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## B.2 Data in Transit Protection

### Encryption Standards

| Connection Type | Minimum Protocol | Cipher Suite | Certificate |
|-----------------|------------------|--------------|-------------|
| External Web | [YOUR INPUT - TLS 1.3] | [YOUR INPUT] | [YOUR INPUT - EV? DV?] |
| Internal Web | [YOUR INPUT - TLS 1.2+] | [YOUR INPUT] | [YOUR INPUT - Internal CA] |
| API Communications | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Database Connections | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Service-to-Service | [YOUR INPUT - mTLS] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Communications | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Email | [YOUR INPUT - TLS/SMTP] | [YOUR INPUT] | [YOUR INPUT] |
| File Transfer | [YOUR INPUT - SFTP] | [YOUR INPUT] | [YOUR INPUT] |
| VPN | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Certificate Management

| Certificate Type | CA | Validity | Renewal Process |
|-----------------|-----|----------|-----------------|
| Public Website | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - Auto-renew?] |
| Internal Services | [YOUR INPUT - Private CA] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Devices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Code Signing | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Email (S/MIME) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## B.3 Data in Use Protection

| Technology | Use Case | Implementation | Limitations |
|------------|----------|----------------|-------------|
| Memory Encryption | [YOUR INPUT] | [YOUR INPUT - AMD SME, Intel TME] | [YOUR INPUT] |
| Secure Enclaves | [YOUR INPUT] | [YOUR INPUT - Intel SGX, AWS Nitro] | [YOUR INPUT] |
| Confidential Computing | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Tokenization | [YOUR INPUT - Card data, PII] | [YOUR INPUT] | [YOUR INPUT] |
| Data Masking | [YOUR INPUT - Dev/test environments] | [YOUR INPUT] | [YOUR INPUT] |
| Homomorphic Encryption | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - Performance] |

---

# SECTION C: DATA LOSS PREVENTION (DLP)

## C.1 DLP Architecture

```
[YOUR INPUT - Design DLP architecture]

┌─────────────────────────────────────────────────────────────────────────┐
│                    DLP ARCHITECTURE                                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ENDPOINT DLP                   NETWORK DLP                              │
│  ┌─────────────────┐           ┌─────────────────┐                      │
│  │ [YOUR INPUT -   │           │ [YOUR INPUT -   │                      │
│  │  Agent-based    │           │  Inline/Proxy   │                      │
│  │  monitoring]    │           │  inspection]    │                      │
│  │                 │           │                 │                      │
│  │ Monitors:       │           │ Monitors:       │                      │
│  │ - USB/Removable │           │ - Email         │                      │
│  │ - Print         │           │ - Web uploads   │                      │
│  │ - Clipboard     │           │ - FTP           │                      │
│  │ - Screen capture│           │ - Cloud sync    │                      │
│  └─────────────────┘           └─────────────────┘                      │
│                                                                          │
│  CLOUD DLP                     DISCOVERY                                 │
│  ┌─────────────────┐           ┌─────────────────┐                      │
│  │ [YOUR INPUT -   │           │ [YOUR INPUT -   │                      │
│  │  CASB, SaaS    │           │  Scan repos,    │                      │
│  │  integration]   │           │  shares, DBs]   │                      │
│  │                 │           │                 │                      │
│  │ Monitors:       │           │ Discovers:      │                      │
│  │ - M365          │           │ - PII           │                      │
│  │ - Google        │           │ - PHI           │                      │
│  │ - Salesforce    │           │ - IP            │                      │
│  │ - Box/Dropbox   │           │ - Secrets       │                      │
│  └─────────────────┘           └─────────────────┘                      │
│                                                                          │
│                    CENTRAL MANAGEMENT                                    │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  [YOUR INPUT - Unified policy management, incident handling]    │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

## C.2 DLP Detection Methods

| Method | Description | Use Case | Accuracy |
|--------|-------------|----------|----------|
| **Regular Expressions** | [YOUR INPUT] | [YOUR INPUT - SSN, credit cards] | [YOUR INPUT] |
| **Keywords/Dictionaries** | [YOUR INPUT] | [YOUR INPUT - Project names] | [YOUR INPUT] |
| **File Fingerprinting** | [YOUR INPUT] | [YOUR INPUT - Source code] | [YOUR INPUT] |
| **Machine Learning** | [YOUR INPUT] | [YOUR INPUT - Context detection] | [YOUR INPUT] |
| **Exact Data Match** | [YOUR INPUT] | [YOUR INPUT - Customer database] | [YOUR INPUT] |
| **Optical Character Recognition** | [YOUR INPUT] | [YOUR INPUT - Scanned docs] | [YOUR INPUT] |

## C.3 DLP Policy Rules

### High-Risk Data Rules

| Rule Name | Data Pattern | Channels | Action | Notification |
|-----------|-------------|----------|--------|--------------|
| PII Detection (EU) | [YOUR INPUT - Personal ID, name+address] | [YOUR INPUT] | [YOUR INPUT - Block, alert] | [YOUR INPUT] |
| Financial Data | [YOUR INPUT - Bank accounts, card numbers] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Source Code | [YOUR INPUT - Code patterns, extensions] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| R&D Algorithms | [YOUR INPUT - Specific file names, content] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| API Keys/Secrets | [YOUR INPUT - Regex for keys] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Channel-Specific Policies

| Channel | Monitoring Scope | Actions Available | Considerations |
|---------|-----------------|-------------------|----------------|
| Email (Exchange/Gmail) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - Encryption options] |
| Cloud Storage | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - Sync blocking] |
| USB/Removable Media | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - Encryption requirement] |
| Web Upload | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - Category blocking] |
| Printing | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - Watermarking] |
| Instant Messaging | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## C.4 DLP Response Actions

| Violation Severity | Action | Escalation | User Notification |
|-------------------|--------|------------|-------------------|
| Critical | [YOUR INPUT - Block, SOC alert, manager notify] | [YOUR INPUT] | [YOUR INPUT] |
| High | [YOUR INPUT - Block, log, user educate] | [YOUR INPUT] | [YOUR INPUT] |
| Medium | [YOUR INPUT - Warn, log] | [YOUR INPUT] | [YOUR INPUT] |
| Low | [YOUR INPUT - Log only] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION D: DATA SOVEREIGNTY & GEOLOCATION

## D.1 Data Residency Requirements

### Jurisdictional Analysis

| Jurisdiction | Regulation | Data Types Affected | Residency Requirement | Transfer Rules |
|--------------|------------|--------------------|-----------------------|----------------|
| **EU/Finland** | [YOUR INPUT - GDPR] | [YOUR INPUT - EU citizen PII] | [YOUR INPUT] | [YOUR INPUT - SCCs, adequacy] |
| **Netherlands** | [YOUR INPUT - GDPR + local] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **United States** | [YOUR INPUT - CCPA, state laws] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Rwanda** | [YOUR INPUT - Data Protection Law 2021] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Cross-Border Data Transfer

| Transfer Type | From | To | Legal Basis | Controls |
|---------------|------|-----|-------------|----------|
| Employee Data | EU | US | [YOUR INPUT - SCCs? Binding Corporate Rules?] | [YOUR INPUT] |
| Customer Data | US | EU | [YOUR INPUT] | [YOUR INPUT] |
| IoT Telemetry | Global | EU (AWS) | [YOUR INPUT] | [YOUR INPUT] |
| Backup Data | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## D.2 Data Location Architecture

```
[YOUR INPUT - Design data residency architecture]

┌─────────────────────────────────────────────────────────────────────────┐
│                    DATA RESIDENCY ARCHITECTURE                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  EU DATA REGION (AWS eu-north-1 / eu-west-1)                            │
│  ┌────────────────────────────────────────────────────────────────┐     │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │     │
│  │  │ EU Employee  │  │ EU Customer  │  │ GDPR         │         │     │
│  │  │ PII          │  │ Data         │  │ Sensitive    │         │     │
│  │  │ [Controls]   │  │ [Controls]   │  │ [Controls]   │         │     │
│  │  └──────────────┘  └──────────────┘  └──────────────┘         │     │
│  │                                                                │     │
│  │  Processing: [YOUR INPUT]                                      │     │
│  │  Backup: [YOUR INPUT - Within EU]                             │     │
│  └────────────────────────────────────────────────────────────────┘     │
│                                                                          │
│  US DATA REGION (AWS us-west-2)                                         │
│  ┌────────────────────────────────────────────────────────────────┐     │
│  │  ┌──────────────┐  ┌──────────────┐                           │     │
│  │  │ US Employee  │  │ US Customer  │                           │     │
│  │  │ Data         │  │ Data         │                           │     │
│  │  │ [Controls]   │  │ [Controls]   │                           │     │
│  │  └──────────────┘  └──────────────┘                           │     │
│  │                                                                │     │
│  │  Processing: [YOUR INPUT]                                      │     │
│  │  Backup: [YOUR INPUT]                                         │     │
│  └────────────────────────────────────────────────────────────────┘     │
│                                                                          │
│  GLOBAL DATA (Non-Regulated)                                            │
│  ┌────────────────────────────────────────────────────────────────┐     │
│  │  [YOUR INPUT - IoT telemetry, anonymized analytics, etc.]     │     │
│  └────────────────────────────────────────────────────────────────┘     │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

## D.3 Data Sovereignty Controls

| Control | Implementation | Verification |
|---------|----------------|--------------|
| Geographic restrictions | [YOUR INPUT - AWS Regions, Resource policies] | [YOUR INPUT] |
| Data processing location | [YOUR INPUT] | [YOUR INPUT] |
| Backup location control | [YOUR INPUT] | [YOUR INPUT] |
| Transfer logging | [YOUR INPUT] | [YOUR INPUT] |
| Sub-processor management | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION E: RIGHTS MANAGEMENT & ACCESS CONTROL

## E.1 Information Rights Management (IRM)

### Rights Management Features

| Feature | Implementation | Use Case |
|---------|----------------|----------|
| View-Only Access | [YOUR INPUT - Microsoft Purview, Adobe DRM] | [YOUR INPUT] |
| Print Restriction | [YOUR INPUT] | [YOUR INPUT] |
| Copy Protection | [YOUR INPUT] | [YOUR INPUT] |
| Expiration | [YOUR INPUT] | [YOUR INPUT] |
| Revocation | [YOUR INPUT] | [YOUR INPUT] |
| Watermarking | [YOUR INPUT] | [YOUR INPUT] |
| Offline Access | [YOUR INPUT] | [YOUR INPUT] |

### Rights Templates

| Template | Permissions | Use Case | Applied To |
|----------|-------------|----------|------------|
| Executive Only | [YOUR INPUT - View, no forward, no print] | [YOUR INPUT] | [YOUR INPUT] |
| Internal Share | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Partner NDA | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Public Read | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## E.2 Data Access Control

### Role-Based Data Access

| Data Category | Roles with Access | Access Level | Approval |
|---------------|------------------|--------------|----------|
| R&D Algorithms | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Customer PII | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Financial Data | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| HR Records | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Telemetry | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Just-In-Time Access

| Data Type | JIT Method | Duration | Approval Chain |
|-----------|------------|----------|----------------|
| Production Database | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Customer Records | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Encryption Keys | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION F: KEY MANAGEMENT

## F.1 Key Management Architecture

```
[YOUR INPUT - Design key management architecture]

┌─────────────────────────────────────────────────────────────────────────┐
│                    KEY MANAGEMENT ARCHITECTURE                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  KEY HIERARCHY                                                           │
│                                                                          │
│                    ┌─────────────────────┐                              │
│                    │   ROOT KEY          │                              │
│                    │   [YOUR INPUT -     │                              │
│                    │    HSM protected]   │                              │
│                    └──────────┬──────────┘                              │
│                               │                                         │
│         ┌─────────────────────┼─────────────────────┐                  │
│         │                     │                     │                  │
│  ┌──────▼──────┐      ┌───────▼───────┐     ┌──────▼──────┐           │
│  │ MASTER KEY  │      │  MASTER KEY   │     │ MASTER KEY  │           │
│  │ (Region EU) │      │  (Region US)  │     │ (On-Prem)   │           │
│  │ [Controls]  │      │  [Controls]   │     │ [Controls]  │           │
│  └──────┬──────┘      └───────┬───────┘     └──────┬──────┘           │
│         │                     │                     │                  │
│    ┌────┴────┐           ┌────┴────┐          ┌────┴────┐             │
│    │         │           │         │          │         │             │
│ ┌──▼──┐  ┌──▼──┐     ┌──▼──┐  ┌──▼──┐    ┌──▼──┐  ┌──▼──┐           │
│ │ DEK │  │ DEK │     │ DEK │  │ DEK │    │ DEK │  │ DEK │           │
│ │(DB) │  │(S3) │     │(RDS)│  │(EBS)│    │(SAN)│  │(BKP)│           │
│ └─────┘  └─────┘     └─────┘  └─────┘    └─────┘  └─────┘           │
│                                                                        │
│  DEK = Data Encryption Key                                             │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

## F.2 Key Management Platform

| Component | Implementation | Location | Access Control |
|-----------|----------------|----------|----------------|
| Hardware Security Module | [YOUR INPUT - AWS CloudHSM, Thales Luna] | [YOUR INPUT] | [YOUR INPUT] |
| Key Management Service | [YOUR INPUT - AWS KMS, Azure Key Vault] | [YOUR INPUT] | [YOUR INPUT] |
| Secret Manager | [YOUR INPUT - HashiCorp Vault, AWS Secrets Manager] | [YOUR INPUT] | [YOUR INPUT] |
| Certificate Authority | [YOUR INPUT - AWS ACM, EJBCA] | [YOUR INPUT] | [YOUR INPUT] |

## F.3 Key Lifecycle Management

| Phase | Policy | Procedure | Responsible |
|-------|--------|-----------|-------------|
| Generation | [YOUR INPUT - Algorithm, length, entropy source] | [YOUR INPUT] | [YOUR INPUT] |
| Distribution | [YOUR INPUT - Secure channel, key wrapping] | [YOUR INPUT] | [YOUR INPUT] |
| Storage | [YOUR INPUT - HSM, encrypted, access logged] | [YOUR INPUT] | [YOUR INPUT] |
| Usage | [YOUR INPUT - Authorized apps, audit logging] | [YOUR INPUT] | [YOUR INPUT] |
| Rotation | [YOUR INPUT - Frequency, automation] | [YOUR INPUT] | [YOUR INPUT] |
| Backup | [YOUR INPUT - Secure backup, key escrow] | [YOUR INPUT] | [YOUR INPUT] |
| Revocation | [YOUR INPUT - Process, CRL distribution] | [YOUR INPUT] | [YOUR INPUT] |
| Destruction | [YOUR INPUT - Cryptographic erasure, audit] | [YOUR INPUT] | [YOUR INPUT] |

## F.4 Key Rotation Schedule

| Key Type | Rotation Frequency | Automated | Grace Period |
|----------|-------------------|-----------|--------------|
| Master/Root Keys | [YOUR INPUT - Annual?] | [YOUR INPUT] | [YOUR INPUT] |
| Data Encryption Keys | [YOUR INPUT - Monthly?] | [YOUR INPUT] | [YOUR INPUT] |
| TLS Certificates | [YOUR INPUT - 90 days?] | [YOUR INPUT] | [YOUR INPUT] |
| API Keys | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Service Account Passwords | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| User Passwords | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION G: DATA PROTECTION METHODS

## G.1 Encryption Standards

### Symmetric Encryption

| Algorithm | Key Size | Use Case | Performance |
|-----------|----------|----------|-------------|
| AES-256-GCM | 256-bit | [YOUR INPUT - Storage, database] | [YOUR INPUT] |
| AES-128-GCM | 128-bit | [YOUR INPUT] | [YOUR INPUT] |
| ChaCha20-Poly1305 | 256-bit | [YOUR INPUT - Mobile, IoT] | [YOUR INPUT] |

### Asymmetric Encryption

| Algorithm | Key Size | Use Case | Notes |
|-----------|----------|----------|-------|
| RSA | [YOUR INPUT - 2048/4096] | [YOUR INPUT] | [YOUR INPUT] |
| ECDSA | [YOUR INPUT - P-256/P-384] | [YOUR INPUT] | [YOUR INPUT] |
| Ed25519 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## G.2 Hashing Standards

| Algorithm | Use Case | Deprecated |
|-----------|----------|------------|
| SHA-256 | [YOUR INPUT - Integrity, fingerprints] | No |
| SHA-384/512 | [YOUR INPUT] | No |
| Argon2 | [YOUR INPUT - Password hashing] | No |
| bcrypt | [YOUR INPUT - Password hashing] | No |
| MD5 | [YOUR INPUT - NEVER for security] | Yes |
| SHA-1 | [YOUR INPUT - Legacy only] | Yes |

## G.3 Tokenization

| Data Type | Tokenization Method | Token Format | De-tokenization |
|-----------|--------------------| -------------|-----------------|
| Credit Cards | [YOUR INPUT - Format-preserving] | [YOUR INPUT] | [YOUR INPUT] |
| SSN/Personal IDs | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Customer IDs | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## G.4 Data Masking

| Environment | Masking Type | Data Affected | Consistency |
|-------------|-------------|---------------|-------------|
| Development | [YOUR INPUT - Dynamic/Static] | [YOUR INPUT] | [YOUR INPUT - Referential integrity?] |
| Testing | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Analytics | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Customer Support | [YOUR INPUT - Dynamic masking] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION H: DATA FLOW DIAGRAMS

## H.1 Customer Data Flow

```
[YOUR INPUT - Map how customer data flows through systems]

Customer → [YOUR INPUT] → [YOUR INPUT] → [YOUR INPUT] → Storage

Entry Points:
1. Web Portal: [YOUR INPUT]
2. Mobile App: [YOUR INPUT]
3. IoT Devices: [YOUR INPUT]
4. Sales/CRM: [YOUR INPUT]

Processing:
[YOUR INPUT]

Storage:
[YOUR INPUT]

Outbound:
[YOUR INPUT - Where does data go? Partners, analytics, etc.]
```

## H.2 IoT Data Flow

```
[YOUR INPUT - Map IoT telemetry data flow]

IoT Device → Edge Gateway → Cloud → Analytics

┌──────────────────────────────────────────────────────────────────────┐
│                      IOT DATA FLOW                                    │
├──────────────────────────────────────────────────────────────────────┤
│                                                                       │
│  DEVICE                   EDGE                    CLOUD               │
│  ┌─────────┐             ┌─────────┐             ┌─────────────┐     │
│  │   IoT   │──[TLS]─────►│ Gateway │──[VPN]─────►│  IoT Core   │     │
│  │ Sensor  │             │         │             │             │     │
│  │         │◄────────────│         │◄────────────│  [Auth]     │     │
│  │[Encrypt]│  Commands   │[Process]│   Config    │             │     │
│  └─────────┘             └─────────┘             └──────┬──────┘     │
│                                                         │            │
│                                                         ▼            │
│                                                  ┌──────────────┐    │
│                                                  │ Data Lake    │    │
│                                                  │ [Encrypted]  │    │
│                                                  └──────┬───────┘    │
│                                                         │            │
│                              ┌───────────────┬──────────┴────────┐   │
│                              │               │                   │   │
│                              ▼               ▼                   ▼   │
│                         ┌─────────┐    ┌─────────┐         ┌────────┐│
│                         │Analytics│    │ Alerts  │         │Customer││
│                         │[Masked] │    │ [Auth]  │         │Portal  ││
│                         └─────────┘    └─────────┘         └────────┘│
│                                                                       │
│  Security Controls Applied:                                          │
│  1. [YOUR INPUT]                                                     │
│  2. [YOUR INPUT]                                                     │
│  3. [YOUR INPUT]                                                     │
│                                                                       │
└──────────────────────────────────────────────────────────────────────┘
```

## H.3 R&D Data Flow

```
[YOUR INPUT - Map sensitive R&D data flow with isolation controls]

R&D Network (Air-Gapped/Isolated)
[YOUR INPUT - Design secure R&D data handling]

Security Controls:
- Network Isolation: [YOUR INPUT]
- Data Exfiltration Prevention: [YOUR INPUT]
- Access Control: [YOUR INPUT]
- Monitoring: [YOUR INPUT]
```

---

# SECTION I: DATA RETENTION & DISPOSAL

## I.1 Retention Schedule

| Data Category | Retention Period | Legal Basis | Storage Location | Disposal Method |
|---------------|------------------|-------------|------------------|-----------------|
| Customer PII (EU) | [YOUR INPUT - GDPR minimization] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Financial Records | [YOUR INPUT - 7 years?] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Employee Records | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Telemetry | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Security Logs | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Backups | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Email | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## I.2 Data Disposal Methods

| Media Type | Disposal Method | Standard | Verification |
|------------|-----------------|----------|--------------|
| HDD | [YOUR INPUT - DoD 5220.22-M, NIST 800-88] | [YOUR INPUT] | [YOUR INPUT] |
| SSD | [YOUR INPUT - Crypto-erase, destroy] | [YOUR INPUT] | [YOUR INPUT] |
| Cloud Storage | [YOUR INPUT - Crypto-erase, key destroy] | [YOUR INPUT] | [YOUR INPUT] |
| Paper | [YOUR INPUT - Cross-cut shred] | [YOUR INPUT] | [YOUR INPUT] |
| Backup Tapes | [YOUR INPUT - Degauss, destroy] | [YOUR INPUT] | [YOUR INPUT] |
| Mobile Devices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION J: DATA PROTECTION MONITORING

## J.1 Monitoring & Detection

| Monitoring Type | What to Monitor | Tools | Alert Threshold |
|-----------------|-----------------|-------|-----------------|
| Access Monitoring | [YOUR INPUT - Who accesses what data] | [YOUR INPUT] | [YOUR INPUT] |
| Anomaly Detection | [YOUR INPUT - Unusual access patterns] | [YOUR INPUT] | [YOUR INPUT] |
| DLP Alerts | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Encryption Status | [YOUR INPUT - Unencrypted data discovery] | [YOUR INPUT] | [YOUR INPUT] |
| Key Usage | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Transfer Monitoring | [YOUR INPUT - Cross-border flows] | [YOUR INPUT] | [YOUR INPUT] |

## J.2 Data Protection Metrics

| Metric | Current | Target | Measurement |
|--------|---------|--------|-------------|
| Data Classification Coverage | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Encryption at Rest % | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| DLP False Positive Rate | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| GDPR Request Response Time | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Key Rotation Compliance | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Data Breach Incidents | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 3.3 - Enterprise Data Protection Strategy |
| **Phase** | 3 - Security Architecture |
| **Exam Objective** | 3.3 - Compare and contrast concepts and strategies to protect data |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
