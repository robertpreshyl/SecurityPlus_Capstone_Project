# Deliverable 1.5: Cryptographic Standards Document
## NordicShield Technologies Oy

---

## Document Purpose

This document establishes cryptographic standards and guidelines for NordicShield Technologies, ensuring consistent and appropriate use of encryption, hashing, digital signatures, and key management across all systems, including IoT devices, cloud infrastructure, and global operations.

---

## Instructions

1. Review the company profile for systems requiring cryptographic protection
2. Complete all `[YOUR INPUT]` sections with NordicShield-specific decisions
3. Ensure alignment with industry standards and compliance requirements
4. Consider the constraints of IoT devices and global regulations

---

# SECTION A: CRYPTOGRAPHIC STANDARDS OVERVIEW

## A.1 Purpose and Scope

```
[YOUR INPUT - Write a purpose statement]

This document establishes:
- 
- 
- 

Scope includes:
- All NordicShield IT systems
- All IoT devices (sensors, controllers, gateways)
- Cloud infrastructure (AWS, Azure)
- SaaS application configurations
- Data in transit and at rest
- Global operations across all regions
```

## A.2 Cryptographic Goals

| Goal | Definition | NordicShield Priority |
|------|------------|----------------------|
| **Confidentiality** | Protecting data from unauthorized access | [YOUR INPUT - Critical for which data?] |
| **Integrity** | Ensuring data hasn't been tampered with | [YOUR INPUT - Critical for which systems?] |
| **Authentication** | Verifying identity of users/systems | [YOUR INPUT] |
| **Non-repudiation** | Preventing denial of actions | [YOUR INPUT] |
| **Key Management** | Secure generation, storage, rotation of keys | [YOUR INPUT] |

---

# SECTION B: ENCRYPTION STANDARDS

## B.1 Symmetric Encryption

### Approved Algorithms

| Algorithm | Key Size | Use Case | Status |
|-----------|----------|----------|--------|
| AES-256-GCM | 256-bit | ☐ Data at rest ☐ Data in transit | ☑ Approved |
| AES-128-GCM | 128-bit | [YOUR INPUT - When acceptable?] | ☑ Approved |
| ChaCha20-Poly1305 | 256-bit | [YOUR INPUT] | ☑ Approved |
| 3DES | 168-bit | [YOUR INPUT - Legacy only?] | ☐ Deprecated |
| DES | 56-bit | N/A | ☒ Prohibited |

### NordicShield Symmetric Encryption Decisions

| Use Case | Algorithm | Justification |
|----------|-----------|---------------|
| Database encryption at rest | [YOUR INPUT] | [YOUR INPUT] |
| File/disk encryption | [YOUR INPUT] | [YOUR INPUT] |
| IoT sensor data encryption | [YOUR INPUT - Consider device constraints] | [YOUR INPUT] |
| Backup encryption | [YOUR INPUT] | [YOUR INPUT] |
| Cloud storage encryption | [YOUR INPUT] | [YOUR INPUT] |

## B.2 Asymmetric Encryption

### Approved Algorithms

| Algorithm | Key Size | Use Case | Status |
|-----------|----------|----------|--------|
| RSA | 4096-bit | Digital signatures, key exchange | ☑ Approved |
| RSA | 2048-bit | Legacy systems | ☐ Allowed until [DATE] |
| RSA | <2048-bit | N/A | ☒ Prohibited |
| ECDSA | P-256+ | Digital signatures | ☑ Approved |
| ECDH | P-256+ | Key exchange | ☑ Approved |
| Ed25519 | 256-bit | Digital signatures | ☑ Approved |
| X25519 | 256-bit | Key exchange | ☑ Approved |

### NordicShield Asymmetric Encryption Decisions

| Use Case | Algorithm | Key Size | Justification |
|----------|-----------|----------|---------------|
| TLS certificates | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Code signing | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Document signing | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| SSH keys | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT device certificates | [YOUR INPUT - Consider constrained devices] | [YOUR INPUT] | [YOUR INPUT] |
| VPN | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION C: HASHING STANDARDS

## C.1 Approved Hash Functions

| Algorithm | Output Size | Use Case | Status |
|-----------|-------------|----------|--------|
| SHA-256 | 256-bit | General integrity, certificates | ☑ Approved |
| SHA-384 | 384-bit | Higher security requirements | ☑ Approved |
| SHA-512 | 512-bit | Maximum security | ☑ Approved |
| SHA-3-256 | 256-bit | Future-proofing | ☑ Approved |
| SHA-1 | 160-bit | Legacy only | ☐ Deprecated |
| MD5 | 128-bit | Non-security only | ☒ Prohibited for security |

## C.2 Password Hashing

| Algorithm | Parameters | Use Case | Status |
|-----------|------------|----------|--------|
| Argon2id | [YOUR INPUT - Memory, iterations] | Passwords | ☑ Preferred |
| bcrypt | Cost factor ≥12 | Passwords | ☑ Approved |
| scrypt | [YOUR INPUT] | Passwords | ☑ Approved |
| PBKDF2 | ≥310,000 iterations | Legacy | ☐ Allowed |
| MD5/SHA1 unsalted | N/A | N/A | ☒ Prohibited |

### NordicShield Password Hashing Decisions

| System | Algorithm | Parameters | Implementation |
|--------|-----------|------------|----------------|
| Azure AD | [YOUR INPUT - Managed by Microsoft] | [YOUR INPUT] | [YOUR INPUT] |
| NordicSense application | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Local admin accounts | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## C.3 HMAC Standards

| Use Case | Algorithm | Key Size | Implementation |
|----------|-----------|----------|----------------|
| API authentication | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Session tokens | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT message authentication | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION D: DATA ENCRYPTION REQUIREMENTS

## D.1 Data at Rest

### Classification-Based Requirements

| Data Classification | Encryption Required | Algorithm/Method | Key Management |
|--------------------|---------------------|------------------|----------------|
| RESTRICTED | ☑ Mandatory | [YOUR INPUT] | [YOUR INPUT - HSM required?] |
| REGULATED (PII) | ☑ Mandatory | [YOUR INPUT] | [YOUR INPUT] |
| CONFIDENTIAL | ☑ Mandatory | [YOUR INPUT] | [YOUR INPUT] |
| INTERNAL | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| PUBLIC | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### System-Specific Requirements

| System/Storage | Encryption Method | Key Storage | Rotation Period |
|----------------|-------------------|-------------|-----------------|
| Corporate laptops | [YOUR INPUT - BitLocker? FileVault?] | [YOUR INPUT - TPM?] | [YOUR INPUT] |
| Servers (Turku DC) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| AWS S3 buckets | [YOUR INPUT - SSE-S3? SSE-KMS? SSE-C?] | [YOUR INPUT] | [YOUR INPUT] |
| AWS RDS databases | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Azure storage | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Backup media | [YOUR INPUT] | [YOUR INPUT - Offline key storage?] | [YOUR INPUT] |
| Mobile devices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## D.2 Data in Transit

### Protocol Requirements

| Protocol | Minimum Version | Cipher Suites | Use Case |
|----------|-----------------|---------------|----------|
| TLS | [YOUR INPUT - 1.2 or 1.3?] | [YOUR INPUT] | Web traffic, APIs |
| TLS | [YOUR INPUT - IoT constraint?] | [YOUR INPUT] | IoT communications |
| SSH | [YOUR INPUT] | [YOUR INPUT] | Administrative access |
| IPsec | [YOUR INPUT] | [YOUR INPUT] | VPN tunnels |
| DTLS | [YOUR INPUT] | [YOUR INPUT] | IoT over UDP |

### TLS Configuration Standards

```
[YOUR INPUT - Define TLS configuration requirements]

Minimum TLS Version: 
Preferred TLS Version:

Approved Cipher Suites (in priority order):
1. 
2. 
3. 

Prohibited:
- SSL 2.0, SSL 3.0, TLS 1.0, TLS 1.1
- RC4
- 3DES
- NULL ciphers
- Export ciphers
- Anonymous ciphers

Certificate Requirements:
- Minimum key size:
- Signature algorithm:
- Validity period:
```

### Network Communication Matrix

| Source | Destination | Protocol | Encryption Required | Standard |
|--------|-------------|----------|---------------------|----------|
| User browsers | Web applications | HTTPS | ☑ Yes | [YOUR INPUT] |
| IoT sensors | IoT gateways | [YOUR INPUT] | ☑ Yes | [YOUR INPUT] |
| IoT gateways | AWS IoT Core | [YOUR INPUT] | ☑ Yes | [YOUR INPUT] |
| Turku ↔ Amsterdam | Site connectivity | [YOUR INPUT] | ☑ Yes | [YOUR INPUT] |
| Internal APIs | Service mesh | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Email (external) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION E: IOT CRYPTOGRAPHIC REQUIREMENTS

## E.1 IoT Device Constraints

| Constraint | Impact | Mitigation |
|------------|--------|------------|
| Limited CPU | Can't run heavy crypto | [YOUR INPUT - Lighter algorithms?] |
| Limited memory | Key storage challenges | [YOUR INPUT] |
| Limited power | Crypto increases consumption | [YOUR INPUT] |
| Long lifecycle | Algorithms may become weak | [YOUR INPUT - Crypto agility?] |
| Remote deployment | Hard to rotate keys | [YOUR INPUT] |
| Physical access | Attackers can extract keys | [YOUR INPUT - Hardware security?] |

## E.2 IoT Cryptographic Standards

| Function | Constrained (Sensors) | Capable (Gateways) | Justification |
|----------|----------------------|-------------------|---------------|
| Symmetric encryption | [YOUR INPUT - AES-128? ChaCha20?] | [YOUR INPUT] | [YOUR INPUT] |
| Hashing | [YOUR INPUT - SHA-256? SHA-3?] | [YOUR INPUT] | [YOUR INPUT] |
| Signatures | [YOUR INPUT - ECDSA P-256?] | [YOUR INPUT] | [YOUR INPUT] |
| Key exchange | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| TLS version | [YOUR INPUT - TLS 1.2 with specific suites?] | [YOUR INPUT] | [YOUR INPUT] |

## E.3 IoT Certificate Strategy

```
[YOUR INPUT - Define the IoT PKI strategy]

Device Identity Certificates:
- Issuing CA:
- Key type:
- Validity period:
- Provisioning method:
- Rotation approach:

Code Signing Certificates (Firmware):
- Issuing CA:
- Key type:
- Verification method:
```

---

# SECTION F: DIGITAL SIGNATURES

## F.1 Signature Use Cases

| Use Case | Algorithm | Certificate Type | Verification Method |
|----------|-----------|------------------|---------------------|
| Code signing (applications) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Firmware signing (IoT) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Document signing (contracts) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Email signing (S/MIME) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| API request signing | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Log file signing | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## F.2 Non-Repudiation Requirements

| Transaction Type | Signature Required | Timestamp Required | Retention |
|------------------|-------------------|-------------------|-----------|
| Financial transactions | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Contract execution | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Configuration changes | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Audit log entries | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION G: KEY MANAGEMENT

## G.1 Key Management Principles

```
[YOUR INPUT - Define key management principles]

Key Generation:
- Source of randomness:
- Generation location:
- Minimum entropy:

Key Storage:
- Hardware security modules (HSM):
- Key management services:
- No plaintext keys in:

Key Distribution:
- Methods:
- Encryption of keys:
- Split knowledge:

Key Usage:
- Purpose limitation:
- Access control:
- Usage logging:
```

## G.2 Key Lifecycle Management

### Key Rotation Schedule

| Key Type | Rotation Period | Automated? | Responsible Party |
|----------|-----------------|------------|-------------------|
| TLS certificates | [YOUR INPUT - 1 year?] | [YOUR INPUT] | [YOUR INPUT] |
| Code signing keys | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Database encryption keys | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| AWS KMS keys | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| SSH keys | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT device certificates | [YOUR INPUT - Consider lifecycle] | [YOUR INPUT] | [YOUR INPUT] |
| API keys | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Backup encryption keys | [YOUR INPUT - Longer for restore?] | [YOUR INPUT] | [YOUR INPUT] |

### Key Revocation Process

```
[YOUR INPUT - Define revocation procedures]

Revocation Triggers:
1. Suspected compromise
2. Employee departure
3. Certificate expiration
4. [YOUR INPUT]

Revocation Steps:
1.
2.
3.
4.

CRL/OCSP:
- Update frequency:
- Distribution points:
```

## G.3 Key Storage Solutions

| Key Type | Storage Solution | Location | Backup |
|----------|------------------|----------|--------|
| Root CA keys | [YOUR INPUT - Offline HSM?] | [YOUR INPUT] | [YOUR INPUT] |
| TLS private keys | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| AWS encryption keys | AWS KMS | AWS eu-north-1 | [YOUR INPUT] |
| Database keys | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT device keys | [YOUR INPUT - Secure element?] | [YOUR INPUT] | [YOUR INPUT] |
| Developer SSH keys | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## G.4 Key Backup and Recovery

| Scenario | Recovery Method | Recovery Time | Authorization |
|----------|-----------------|---------------|---------------|
| Lost encryption key | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Compromised key | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Disaster recovery | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Key custodian unavailable | [YOUR INPUT - M of N?] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION H: PKI ARCHITECTURE

## H.1 Certificate Authority Structure

```
[YOUR INPUT - Design the PKI hierarchy]

Root CA:
- Location:
- Key type:
- Validity:
- Offline/Online:

Issuing CA(s):
- [YOUR INPUT - Internal CA for...]
- [YOUR INPUT - IoT CA for...]

External CAs used:
- [YOUR INPUT - Which public CAs?]
```

## H.2 Certificate Requirements

| Certificate Type | Key Algorithm | Key Size | Validity | Renewal |
|------------------|---------------|----------|----------|---------|
| Web server (public) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Web server (internal) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Client authentication | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Code signing | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT device | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Email (S/MIME) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## H.3 Certificate Inventory

| Certificate | Issuer | Expiration | Auto-Renewal | Monitor |
|-------------|--------|------------|--------------|---------|
| *.nordicsense.fi | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION I: COMPLIANCE AND REGULATORY CONSIDERATIONS

## I.1 Regional Requirements

| Region | Regulation | Cryptographic Requirement | NordicShield Compliance |
|--------|------------|--------------------------|------------------------|
| EU (Finland, Netherlands) | GDPR | Appropriate encryption | [YOUR INPUT] |
| EU | NIS2 | State-of-the-art crypto | [YOUR INPUT] |
| USA (Texas) | CCPA | Reasonable security | [YOUR INPUT] |
| Rwanda | Data Protection Act | Appropriate safeguards | [YOUR INPUT] |
| Industry | SOC 2 | Encryption controls | [YOUR INPUT] |
| Industry | ISO 27001 (A.10) | Cryptographic controls | [YOUR INPUT] |

## I.2 Export Controls

| Consideration | Policy |
|---------------|--------|
| Encryption software export | [YOUR INPUT] |
| Key escrow requirements | [YOUR INPUT] |
| Government access requests | [YOUR INPUT] |

---

# SECTION J: IMPLEMENTATION GUIDELINES

## J.1 Developer Guidelines

```
[YOUR INPUT - Guidelines for developers]

DO:
- Use approved libraries for cryptography
- Never implement custom crypto
- Use appropriate key sizes
- Validate certificates properly
- [YOUR INPUT]

DON'T:
- Hard-code keys or secrets
- Use deprecated algorithms
- Disable certificate validation
- Log sensitive cryptographic material
- [YOUR INPUT]

Approved Cryptographic Libraries:
- [YOUR INPUT - e.g., OpenSSL, BouncyCastle, libsodium]
```

## J.2 Operations Guidelines

```
[YOUR INPUT - Guidelines for operations]

Certificate Management:
- Monitor expiration: [YOUR INPUT - 30, 60, 90 day alerts?]
- Renewal process:
- Emergency replacement:

Key Rotation:
- Automated where possible
- Documented manual procedures
- Testing after rotation

Incident Response:
- Key compromise procedures:
- Certificate revocation:
- Communication plan:
```

---

# SECTION K: CRYPTOGRAPHIC STANDARDS EXCEPTIONS

## K.1 Exception Process

```
[YOUR INPUT - Define exceptions process]

Exceptions may be granted for:
- Legacy systems requiring deprecated algorithms
- Interoperability requirements
- Performance constraints

Exception Request Requirements:
1.
2.
3.

Approval Authority:
Compensating Controls Required:
Maximum Exception Duration:
Review Schedule:
```

## K.2 Current Exceptions

| System | Standard | Exception | Compensating Control | Expiration |
|--------|----------|-----------|---------------------|------------|
| [YOUR INPUT - Legacy system?] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION L: EXECUTIVE SUMMARY

```
[YOUR INPUT - Write a 200-250 word executive summary]

Include:
- Importance of cryptographic standards for NordicShield
- Key decisions made (algorithm selections, key management approach)
- Special considerations for IoT devices
- Compliance alignment
- Implementation priorities
- Ongoing management requirements
```

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 1.5 - Cryptographic Standards Document |
| **Phase** | 1 - General Security Concepts |
| **Exam Objective** | 1.4 - Explain the importance of using appropriate cryptographic solutions |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
