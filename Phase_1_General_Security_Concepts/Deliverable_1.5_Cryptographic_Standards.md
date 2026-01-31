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
NordicShield requires comprehensive cryptographic standards to protect customer data, ensure regulatory
compliance, and maintain trust across our global IoT monitoring infrastructure.

This document establishes:
- Approved cryptographic algorithms and key sizes for all use cases
- Data encryption requirements for data at rest and in transit
- Digital signature standards for firmware, code, and documents
- Key management lifecycle procedures (generation, storage, rotation, revocation)
- PKI architecture and certificate management practices
- IoT-specific cryptographic guidance for resource-constrained devices

Scope includes:
- All NordicShield IT systems (databases, file servers, endpoints, cloud infrastructure)
- All IoT devices (sensors, controllers, gateways) - 827 deployed devices across 47 customer sites
- Cloud infrastructure (AWS primary: eu-north-1, us-east-1; Azure DR: West Europe)
- SaaS application configurations (Salesforce, Jira, Confluence, Microsoft 365)
- Data in transit and at rest across all data classifications (RESTRICTED, REGULATED, CONFIDENTIAL)
- Global operations across all regions (Finland, Netherlands, USA, Rwanda)
```

## A.2 Cryptographic Goals

| Goal | Definition | NordicShield Priority |
|------|------------|----------------------|
| **Confidentiality** | Protecting data from unauthorized access | CRITICAL for: Customer temperature/humidity data (GDPR personal data when linked to identifiable locations), cooling system configurations, AWS/Azure credentials, API keys, TLS private keys, customer contracts, employee PII, financial records |
| **Integrity** | Ensuring data hasn't been tampered with | CRITICAL for: IoT firmware updates (prevent malicious code injection), sensor readings (detect tampering), system logs (immutable audit trails), backups (verify uncorrupted recovery), API requests/responses |
| **Authentication** | Verifying identity of users/systems | CRITICAL for: All 827 IoT device certificates (X.509), user MFA (TOTP), microservice mTLS, API HMAC signatures, code/firmware signing |
| **Non-repudiation** | Preventing denial of actions | REQUIRED for: Firmware deployments (prove engineer identity), configuration changes (signed audit logs), customer reports (digitally signed PDFs), SLA breach notifications (signed emails), financial transactions |
| **Key Management** | Secure generation, storage, rotation of keys | CRITICAL for: Centralized key storage (AWS KMS, Azure Key Vault, HashiCorp Vault), automated key rotation (annual for TLS/IoT certs), secure distribution via AWS IoT Device Management, key lifecycle management |

---

# SECTION B: ENCRYPTION STANDARDS

## B.1 Symmetric Encryption

### Approved Algorithms

| Algorithm | Key Size | Use Case | Status |
|-----------|----------|----------|--------|
| AES-256-GCM | 256-bit | ☑ Data at rest ☑ Data in transit | ☑ Approved |
| AES-128-GCM | 128-bit | IoT temperature sensors with limited CPU (<100 MHz ARM Cortex-M), gateway devices where full AES-256 impacts performance | ☑ Approved |
| ChaCha20-Poly1305 | 256-bit | IoT devices without AES-NI hardware acceleration, mobile applications, high-performance web servers (alternative to AES-GCM) | ☑ Approved |
| 3DES | 168-bit | ONLY for legacy customer integrations requiring 3DES - must migrate to AES-256-GCM by Q4 2026 (insufficient key strength for modern threats) | ☑ Deprecated |
| DES | 56-bit | N/A | ☒ Prohibited |

### NordicShield Symmetric Encryption Decisions

| Use Case | Algorithm | Justification |
|----------|-----------|---------------|
| Database encryption at rest | AES-256-GCM | RDS PostgreSQL TDE (Transparent Data Encryption) with AWS KMS keys for eu-north-1 and us-east-1 regions. GCM mode provides authenticated encryption preventing tampering. FIPS 140-2 certified for SOC 2 compliance. |
| File/disk encryption | AES-256-GCM (BitLocker/FileVault) | BitLocker for Windows endpoints (85 laptops), FileVault for macOS (35 laptops). AWS S3 server-side encryption with KMS for cloud file storage. Azure Blob Storage encryption for DR region. |
| IoT sensor data encryption | AES-128-GCM | Temperature/humidity sensors use AES-128 due to ARM Cortex-M4 CPU constraints (80 MHz, 256 KB RAM). Acceptable security tradeoff per NIST SP 800-175B (128-bit adequate through 2030). Testing shows AES-256 adds 40ms latency per reading (unacceptable for 60-second polling). |
| Backup encryption | AES-256-GCM | Veeam Backup & Replication with hardware-accelerated AES-256 for nightly backups. 7-year retention for GDPR compliance. Backup encryption keys stored in HashiCorp Vault separate from AWS KMS (separate key custody). |
| Cloud storage encryption | AES-256-GCM | AWS S3 SSE-KMS for all buckets (firmware repository, customer reports, system logs). Azure Blob Storage with customer-managed keys (CMK) in Azure Key Vault for DR region. Encryption mandatory via SCPs (AWS) and Azure Policy. |

## B.2 Asymmetric Encryption

### Approved Algorithms

| Algorithm | Key Size | Use Case | Status |
|-----------|----------|----------|--------|
| RSA | 4096-bit | Digital signatures, key exchange | ☑ Approved |
| RSA | 2048-bit | Legacy systems | ☐ Allowed until December 31, 2029 |
| RSA | <2048-bit | N/A | ☒ Prohibited |
| ECDSA | P-256+ | Digital signatures | ☑ Approved |
| ECDH | P-256+ | Key exchange | ☑ Approved |
| Ed25519 | 256-bit | Digital signatures | ☑ Approved |
| X25519 | 256-bit | Key exchange | ☑ Approved |

### NordicShield Asymmetric Encryption Decisions

| Use Case | Algorithm | Key Size | Justification |
|----------|-----------|----------|---------------|
| TLS certificates | RSA | 4096-bit (public), 2048-bit (internal) | Public-facing API endpoints (*.nordicsense.fi) use RSA 4096 for maximum security (5-year future-proofing). Internal microservices use RSA 2048 for mTLS (acceptable performance tradeoff - avg 12ms auth time vs 8ms for 2048). Let's Encrypt for public certs (90-day auto-renewal), internal CA for private certs. |
| Code signing | RSA | 4096-bit | Firmware releases and internal applications signed with RSA 4096. Extended Validation code signing certificate from DigiCert stored on hardware security module (HSM - YubiKey 5 FIPS). NIST 800-218 SSDF compliance (secure software development). |
| Document signing | RSA | 2048-bit | Customer reports and SLA breach notifications signed with RSA 2048 via Adobe Sign API integration. S/MIME email certificates for executive communications (CEO, CTO, CISO). |
| SSH keys | Ed25519 | 256-bit | All engineers use Ed25519 keys for server access (45 cloud servers, 120 employee laptops). Superior security to RSA 2048 with 10x faster key generation. Enforced via /etc/ssh/sshd_config (PubkeyAcceptedAlgorithms ssh-ed25519). |
| IoT device certificates | ECDSA | P-256 (secp256r1) | All 827 IoT devices use ECDSA P-256 certificates issued by AWS IoT Device Management internal CA. Testing shows 60ms authentication time vs 340ms for RSA 2048 on ARM Cortex-M4 (80 MHz). Certificate stored in device secure element (ATECC608A crypto chip). 1-year validity with 90-day automated renewal. |
| VPN | X25519 (ECDH) + Ed25519 (auth) | 256-bit | WireGuard VPN for site-to-site connections (Turku ↔ Amsterdam ↔ Austin ↔ Kigali). X25519 for key exchange, Ed25519 for peer authentication. CloudFlare WARP for  client VPN (employee laptops). |

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
| Argon2id | Memory: 64 MiB, Iterations: 3, Parallelism: 4 | Passwords | ☑ Preferred |
| bcrypt | Cost factor ≥12 | Passwords | ☑ Approved |
| scrypt | N=32768, r=8, p=1 (min) | Passwords | ☑ Approved |
| PBKDF2 | ≥310,000 iterations | Legacy | ☐ Allowed |
| MD5/SHA1 unsalted | N/A | N/A | ☒ Prohibited |

### NordicShield Password Hashing Decisions

| System | Algorithm | Parameters | Implementation |
|--------|-----------|------------|----------------|
| Azure AD | Microsoft-managed (PBKDF2) | Not configurable - Microsoft default (600,000+ iterations estimated per MS Security documentation) | Cloud-managed, supports passwordless (Windows Hello, FIDO2), enforces MFA for all privileged accounts |
| NordicSense application | Argon2id | Memory: 64 MiB, Time: 3 iterations, Parallelism: 4 threads, Salt: 128-bit random per password | Python passlib library in Django backend, passwords hashed at registration/password change, rehash on login if parameters below minimum |
| Local admin accounts | bcrypt | Cost factor:  12 (4,096 rounds, ~250ms on 2024 hardware) | Linux: PAM module libpam-yescrypt, Windows: LAPS with stored hashes in Active Directory using bcrypt, Emergency break-glass admin passwords rotated quarterly |

## C.3 HMAC Standards

| Use Case | Algorithm | Key Size | Implementation |
|----------|-----------|----------|----------------|
| API authentication | HMAC-SHA256 | 256-bit | REST API requests signed with HMAC-SHA256(secret_key, request_method + request_path + request_body + timestamp). Timestamp validates request freshness (±5 min tolerance). AWS Signature Version 4 for AWS API calls. Keys rotated every 90 days. |
| Session tokens | HMAC-SHA256 | 256-bit | JWT (JSON Web Token) session tokens signed with HMAC-SHA256 (HS256). Token payload includes user_id, roles, exp (expiration: 8 hours for standard users, 1 hour for privileged users). Token refresh requires re-authentication after 24 hours. |
| IoT message authentication | HMAC-SHA256 | 256-bit | IoT device messages signed with HMAC-SHA256 using device-specific symmetric key provisioned during device onboarding. Message format: timestamp + device_id + sensor_reading + HMAC. Gateway validates HMAC and timestamp (±2 min tolerance) before accepting reading. Prevents replay attacks and message tampering. |

---

# SECTION D: DATA ENCRYPTION REQUIREMENTS

## D.1 Data at Rest

### Classification-Based Requirements

| Data Classification | Encryption Required | Algorithm/Method | Key Management |
|--------------------|---------------------|------------------|----------------|
| RESTRICTED | ☑ Mandatory | AES-256-GCM + Field-level encryption for keys/credentials | AWS KMS with CloudHSM backing (FIPS 140-2 Level 3), keys never leave HSM, manual approval for key usage by CISO |
| REGULATED (PII) | ☑ Mandatory | AES-256-GCM (database TDE, file encryption) | AWS KMS (primary), Azure Key Vault (DR), automatic key rotation annually, access logged to CloudTrail/Azure Monitor |
| CONFIDENTIAL | ☑ Mandatory | AES-256-GCM | AWS KMS with role-based access, keys rotated annually, separate keys per environment (prod/staging/dev) |
| INTERNAL | ☑ Recommended (mandatory for laptops/cloud) | AES-256-GCM (BitLocker/FileVault, S3 SSE-S3) | TPM 2.0 for endpoints, AWS-managed keys (SSE-S3) for cloud storage |
| PUBLIC | ☐ Not required (but encrypt in transit) | N/A | N/A - public data (marketing materials, public documentation, press releases) |

### System-Specific Requirements

| System/Storage | Encryption Method | Key Storage | Rotation Period |
|----------------|-------------------|-------------|-----------------|
| Corporate laptops | BitLocker (Windows: AES-256-XTS), FileVault (macOS: AES-256-XTS) | TPM 2.0 (Windows), T2/Apple Silicon Secure Enclave (macOS), recovery keys escrowed in Azure AD | Keys regenerated annually via GPO/Intune, recovery key rotated on each OS major upgrade |
| Servers (Turku DC) | LUKS (Linux: AES-256-XTS), BitLocker (Windows Server: AES-256-XTS) | TPM 2.0 (physical servers), HashiCorp Vault (VM encryption keys) | Annual key rotation, emergency rotation within 24 hours if server decommissioned |
| AWS S3 buckets | SSE-KMS (AES-256-GCM with AWS KMS customer-managed keys) | AWS KMS in same region (eu-north-1, us-east-1), separate keys per bucket purpose (firmware repo, customer reports, system logs, backups) | Automatic annual rotation enabled via KMS, immediate rotation if IAM policy breach detected |
| AWS RDS databases | TDE with AWS KMS (AES-256), separate CMKs per database instance | AWS KMS customer-managed keys, cross-region key replication for DR | Automatic annual rotation, database snapshots re-encrypted with new key |
| Azure storage | Azure Storage Service Encryption with customer-managed keys (AES-256) | Azure Key Vault (West Europe region), RBAC limits access to KeyVault Crypto Officer role | Annual rotation via Azure Key Vault auto-rotation, manual rotation if key compromise suspected |
| Backup media | Veeam AES-256-GCM encryption, separate encryption keys from source data | HashiCorp Vault (primary Turku DC), offline encrypted USB key stored in fireproof safe (CTO custody) | 2-year rotation cycle, test key recovery quarterly during DR drills |
| Mobile devices | iOS: Data Protection API (AES-256), Android: File-based encryption (AES-256-XTS via dm-crypt) | iOS Secure Enclave, Android Keystore (hardware-backed on recent Samsung devices) | User passcode change triggers key derivation update, full wipe after 10 failed passcode attempts |

## D.2 Data in Transit

### Protocol Requirements

| Protocol | Minimum Version | Cipher Suites | Use Case |
|----------|-----------------|---------------|----------|
| TLS | TLS 1.3 (preferred), TLS 1.2 (minimum) | TLS 1.3: TLS_AES_256_GCM_SHA384, TLS_AES_128_GCM_SHA256, TLS_CHACHA20_POLY1305_SHA256 / TLS 1.2: TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384, TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 | Web traffic, APIs, cloud services |
| TLS | TLS 1.2 only | TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256, TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256 (optimized for ARM Cortex-M4) | IoT temperature sensors, gateway communication (TLS 1.3 not supported on constrained devices) |
| SSH | OpenSSH 8.0+ (protocol 2 only) | Kex: curve25519-sha256 / Ciphers: chacha20-poly1305@openssh.com, aes256-gcm@openssh.com / MACs: hmac-sha2-512-etm@openssh.com / HostKey: ssh-ed25519 | Administrative access to servers, Git operations, secure file transfers |
| IPsec | IKEv2 | ESP: AES-256-GCM / IKE: AES-256-GCM, DH Group 19 (256-bit ECP), PRF: HMAC-SHA-256 | VPN tunnels (site-to-site: Turku-Amsterdam-Austin-Kigali), AWS Site-to-Site VPN, client VPN (WireGuard alternative) |
| DTLS | DTLS 1.2 | DTLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256 (CoAP over UDP for constrained sensors) | IoT over UDP (sensors transmitting over cellular networks with high latency where TCP overhead unacceptable) |

### TLS Configuration Standards

```
TLS Configuration Standards for NordicShield

Minimum TLS Version: TLS 1.2 (for IoT device compatibility - deprecated December 31, 2026)
Preferred TLS Version: TLS 1.3 (mandatory for all new systems deployed after January 1, 2026)

Approved Cipher Suites (in priority order):

TLS 1.3 (preferred):
1. TLS_AES_256_GCM_SHA384 (maximum security for sensitive customer data)
2. TLS_AES_128_GCM_SHA256 (performance balance for high-traffic APIs - 10K+ req/min)
3. TLS_CHACHA20_POLY1305_SHA256 (mobile clients, IoT gateways without AES-NI)

TLS 1.2 (legacy support until Dec 2026):
1. TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 (perfect forward secrecy, RSA 4096 certs)
2. TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 (perfect forward secrecy, performance-optimized)
3. TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256 (IoT devices with ECDSA P-256 certificates)

Prohibited:
- SSL 2.0, SSL 3.0, TLS 1.0, TLS 1.1 (all vulnerable to POODLE, BEAST, CRIME attacks)
- RC4 (stream cipher with known biases - CVE-2013-2566)
- 3DES (meet-in-the-middle attack reduces effective key strength to 112 bits)
- NULL ciphers (no encryption)
- Export ciphers (intentionally weakened for 1990s export compliance - 40/56-bit keys)
- Anonymous ciphers (no authentication - vulnerable to MITM)
- CBC mode ciphers (vulnerable to padding oracle attacks like Lucky13)

Certificate Requirements:
- Minimum key size: RSA 2048-bit (internal), RSA 4096-bit (public-facing), ECDSA P-256 (IoT)
- Signature algorithm: SHA-256 (minimum), SHA-384 (preferred for RSA 4096)
- Validity period: 397 days maximum (per CA/Browser Forum Baseline Requirements), 90 days for Let's Encrypt,
  1 year for internal CA certificates (IoT devices), 5 years for root CA only
- Certificate Transparency: All public certificates logged to CT logs (automatic with Let's Encrypt)
- OCSP stapling: Required for all public-facing TLS servers (reduces client latency)
- HSTS: Enabled with max-age=31536000; includeSubDomains; preload for *.nordicsense.fi
```

### Network Communication Matrix

| Source | Destination | Protocol | Encryption Required | Standard |
|--------|-------------|----------|---------------------|----------|
| User browsers | Web applications (*.nordicsense.fi) | HTTPS | ☑ Yes | TLS 1.3 preferred, TLS 1.2 minimum, RSA 4096 or ECDSA P-256 cert, HSTS enabled |
| IoT sensors | IoT gateways (local Modbus network) | MQTT over TLS 1.2 | ☑ Yes | TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256, ECDSA P-256 device certs, mutual TLS (gateway validates sensor cert) |
| IoT gateways | AWS IoT Core (mqtt.iot.eu-north-1.amazonaws.com) | MQTT over TLS 1.2 (port 8883) | ☑ Yes | AWS IoT Core certificate-based auth, X.509 client certs, TLS 1.2 with AES-128-GCM, AWS root CA validation |
| Turku ↔ Amsterdam ↔ Austin ↔ Kigali | Site-to-site connectivity | WireGuard VPN (UDP 51820) | ☑ Yes | WireGuard (X25519 key exchange, ChaCha20-Poly1305 encryption, Ed25519 authentication), fallback to AWS Site-to-Site VPN (IPsec IKEv2) if WireGuard blocked |
| Internal APIs (microservices) | Service mesh (AWS EKS with Istio) | HTTP/2 over mTLS | ☑ Yes (mandatory mTLS) | Istio service mesh enforces mTLS for all pod-to-pod communication, automatic cert rotation every 24 hours, SPIFFE identities |
| Email (external) | Customer/vendor SMTP servers | SMTP with STARTTLS | ☑ Yes (opportunistic TLS) | STARTTLS with TLS 1.2+, S/MIME signing for executive emails, SPF/DKIM/DMARC for anti-spoofing, reject unencrypted for REGULATED data recipients |

---

# SECTION E: IOT CRYPTOGRAPHIC REQUIREMENTS

## E.1 IoT Device Constraints

| Constraint | Impact | Mitigation |
|------------|--------|------------|
| Limited CPU | ARM Cortex-M4 @ 80 MHz can't run RSA 4096 efficiently (340ms auth time vs 60ms target) | Use ECDSA P-256 for device certificates (60ms auth time - 5.6x faster). Use AES-128-GCM instead of AES-256 (acceptable 128-bit security through 2030 per NIST SP 800-175B). Consider ChaCha20 for devices without AES-NI hardware acceleration. |
| Limited memory | 256 KB RAM insufficient for TLS 1.3 with large certificate chains | Use TLS 1.2 with compact ECDSA P-256 certificates (256-byte cert vs 2048-byte RSA 4096 cert). Store root CA cert hash only (32 bytes) instead of full cert chain. Use  session resumption (TLS session tickets) to avoid full handshake on reconnection. |
| Limited power | Temperature sensor battery-powered (5-year CR2 lithium battery, 3V 800mAh) - crypto increases power draw by 15-20% | Minimize TLS handshakes: use MQTT persistent connections (connect once daily, not per reading). Use AES-128 (30% less power than AES-256 on Cortex-M4). Implement crypto acceleration in hardware (ATECC608A crypto chip uses 150 µA vs 8 mA for software crypto on main MCU). |
| Long lifecycle | Devices deployed for 10+ years - SHA-256 or ECDSA P-256 may be compromised by 2035 | Crypto agility: Design firmware to support algorithm upgrades via OTA updates. Store algorithm identifiers in device config (not hardcoded). Plan migration path from ECDSA P-256 to P-384 or post-quantum algorithms (CRYSTALS-Dilithium) by 2030. Test firmware upgrade process quarterly. |
| Remote deployment | 827 devices at 47 customer sites across 4 countries - can't manually rotate keys easily | Automated certificate renewal via AWS IoT Device Management (device requests renewal 90 days before expiry). MQTT-based OTA firmware updates for key rotation. Backup key rotation procedure: gateway-initiated key update pushed to sensors over local Modbus network if AWS unreachable. |
| Physical access | Customer facility employees can access sensors (mounted on walls/ceilings) - tamper risk | Hardware security: Use ATECC608A secure element to store private keys (keys never leave chip, physically unclonable). Implement tamper detection: if device cover opened, wipe keys and require reprovisioning. Use anti-tamper epoxy coating on PCB. Log unauthorized physical access attempts to SIEM. |

## E.2 IoT Cryptographic Standards

| Function | Constrained (Sensors) | Capable (Gateways) | Justification |
|----------|----------------------|-------------------|---------------|
| Symmetric encryption | AES-128-GCM (hardware-accelerated via ATECC608A), ChaCha20-Poly1305 (fallback for devices without AES-NI) | AES-256-GCM | Sensors: ARM Cortex-M4 @ 80 MHz with 256 KB RAM requires lighter AES-128 (NIST SP 800-175B: adequate through 2030). Testing shows 30% power savings vs AES-256. Gateways: More capable hardware (ARM Cortex-A53 @ 1.5 GHz, 4 GB RAM) supports full AES-256 with negligible performance impact. |
| Hashing | SHA-256 (integrity checks, firmware verification, certificate fingerprints) | SHA-256 primary, SHA-384 for long-term integrity (logs, audit trails) | Sensors: SHA-256 hardware-accelerated in ATECC608A (30 ms for 1 KB data). SHA-384/512 too slow (95 ms) for 60-second polling cycle. Gateways: Use SHA-384 for 10-year audit log integrity (collision resistance: 2^192 vs 2^128 for SHA-256). |
| Signatures | ECDSA P-256 (secp256r1) - device authentication, firmware verification | ECDSA P-256 (device auth), RSA 4096 (gateway-to-cloud) | Sensors: ECDSA P-256 signature verification takes 85 ms vs 420 ms for RSA 2048 on ARM Cortex-M4. Private key stored in ATECC608A secure element (non-extractable). Gateways: Use RSA 4096 for long-term TLS certs to AWS IoT Core (5-year validity requires stronger keys). |
| Key exchange | ECDH P-256 (ephemeral keys for TLS 1.2 handshakes - perfect forward secrecy) | ECDH P-256, X25519 | Sensors: ECDH P-256 supported natively by ATECC608A (180 ms key agreement time - acceptable for daily TLS handshake). X25519 not supported on constrained hardware. Gateways: Support both ECDH P-256 (for sensor compatibility) and X25519 (for WireGuard VPN to AWS - 3x faster than ECDH). |
| TLS version | TLS 1.2 with lightweight cipher suites (TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256, TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256) | TLS 1.3 (primary), TLS 1.2 (fallback for sensors) | Sensors: TLS 1.3 not supported on ARM Cortex-M4 with mbedTLS library (insufficient RAM for TLS 1.3 key schedule). TLS 1.2 session resumption reduces handshake overhead (reconnection: 85 ms vs 780 ms full handshake). Gateways: TLS 1.3 mandatory for gateway-to-AWS connections (lower latency: 1-RTT handshake vs 2-RTT for TLS 1.2). |

## E.3 IoT Certificate Strategy

```
NordicShield IoT PKI Strategy

Device Identity Certificates:
- Issuing CA: AWS IoT Device Management Internal CA (subordinate CA under NordicShield Root CA) - dedicated CA for IoT devices separate from user/server certificates to limit blast radius if CA compromised
- Key type: ECDSA P-256 (secp256r1) generated in device ATECC608A secure element during  initial provisioning (keys never leave hardware, physically unclonable function prevents cloning)
- Validity period: 1 year (365 days) with automated renewal 90 days before expiry. Device requests new cert via MQTT, AWS IoT CA issues renewed cert immediately (signed with same private key). Max 3 renewal failures before manual intervention required.
- Provisioning method: 
  * Factory provisioning: Devices provisioned at NordicShield Turku HQ before shipment to customers. CSR generated on-device, signed by ATECC608A, uploaded to AWS via USB during manufacturing QA.
  * Field provisioning: If device replaced at customer site, technician initiates Just-In-Time Provisioning (JITP) via mobile app. Device connects with temp cert, AWS IoT Core validates temp cert against allowlist, issues permanent cert.
- Rotation approach: Certificate rotates annually (new cert with same key). Private key rotates only if: (1) device firmware upgraded to new crypto algorithm, (2) tamper event detected, (3) customer requests device decommission. Key rotation involves 30-second device downtime (sensor readings queued locally during rotation).

Code Signing Certificates (Firmware):
- Issuing CA: NordicShield Root CA (offline root - HSM-backed in fireproof safe) → NordicShield Code Signing CA (online subordinate CA)
- Key type: RSA 4096 (long-term security for firmware deployed to devices with 10-year lifespan). Private key stored in YubiKey 5 FIPS hardware security key (FIPS 140-2 Level 2 certified) requiring physical presence + PIN for each signing operation.
- Signature algorithm: RSA 4096 with SHA-384 (firmware binary hashed with SHA-384, signature created with RSA private key). Device verifies signature using RSA 4096 public key embedded in bootloader (read-only firmware partition).
- Verification method: Multi-stage verification:
  1. Device bootloader verifies firmware signature using hardcoded RSA 4096 public key (prevents unauthorized firmware flashing)
  2. If signature valid, compute SHA-384 hash of firmware binary and compare to hash in signature (prevents tampering)
  3. Check firmware version >= current version (prevents downgrade attacks to vulnerable versions)
  4. Verify firmware signed <2 years ago (reject old firmware even if signature valid - prevents replay of known-vulnerable older versions)
  5. Log verification result to local flash + report to AWS IoT Core for centralized monitoring (SIEM alert if verification fails)
- Signing process: Engineer submits firmware build to CI/CD pipeline (GitLab) → automated security scan (Checkmarx SAST) → if pass, engineer physically taps YubiKey + enters PIN → GitLab Runner signs firmware → signed firmware uploaded to S3 firmware repository → devices poll S3 daily for new firmware
```

---

# SECTION F: DIGITAL SIGNATURES

## F.1 Signature Use Cases

| Use Case | Algorithm | Certificate Type | Verification Method |
|----------|-----------|------------------|---------------------|
| Code signing (applications) | RSA 4096 + SHA-384 | Extended Validation (EV) Code Signing Certificate from DigiCert | Windows: Authenticode signature verified by OS before execution. Signature includes timestamp (valid even after cert expiry). Certificate pinning in GPO (only trust NordicShield signing cert). macOS: Developer ID signature verified by Gatekeeper. |
| Firmware signing (IoT) | RSA 4096 + SHA-384 | NordicShield Code Signing CA (internal) | Device bootloader verifies signature using hardcoded RSA 4096 public key. Multi-stage verification: signature validity → hash integrity → version >= current → signed <2 years ago → log to AWS IoT Core. Reject unsigned firmware (prevents unauthorized flashing). |
| Document signing (contracts) | RSA 2048 + SHA-256 via Adobe Sign API | Document Signing Certificate from DigiCert | Adobe Sign API signs PDF with embedded certificate + trusted timestamp. Recipients verify signature via Adobe Reader (validates certificate chain to DigiCert root CA). Legal non-repudiation: timestamp proves signing date, certificate proves signer identity. 10-year retention. |
| Email signing (S/MIME) | RSA 2048 + SHA-256 (S/MIME v3.2) | S/MIME Certificate from Sectigo (for executives: CEO, CTO, CISO, CFO) | Email client verifies S/MIME signature against sender's public key. Certificate distributed via corporate LDAP directory. Outlook/Thunderbird display signed badge if signature valid. Prevents email spoofing for executive communications. |
| API request signing | HMAC-SHA256 (shared secret), RSA 2048 + SHA-256 (public key) | N/A for HMAC (symmetric), API Client Certificate for RSA | Server verifies HMAC signature: compute HMAC(secret, request_method + path + body + timestamp) and compare to signature header. Timestamp tolerance: ±5 minutes (prevents replay attacks). RSA variant: client signs request with private key, server verifies with public key from API Client Certificate. |
| Log file signing | RSA 4096 + SHA-384 or ECDSA P-384 + SHA-384 | Internal Log Signing Certificate (HSM-backed) | SIEM (Splunk) aggregates logs → compute SHA-384 hash of log batch (1-hour windows) → sign hash with RSA 4096 private key in AWS CloudHSM → store signature in audit log metadata. Forensics team verifies log integrity by recomputing hash and verifying signature (detects log tampering). 7-year retention for compliance. |

## F.2 Non-Repudiation Requirements

| Transaction Type | Signature Required | Timestamp Required | Retention |
|------------------|-------------------|-------------------|-----------|
| Financial transactions | ☑ Yes - RSA 2048 digital signature for invoices >€10K, approved by CFO via YubiKey-backed signing key | ☑ Yes - RFC 3161 trusted timestamp from DigiCert TSA (Timestamp Authority). Proves transaction approved at specific datetime. | 10 years (Finnish Accounting Act requirement: VAT records 6 years, extended to 10 years for audit trail) |
| Contract execution | ☑ Yes - Digital signatures via Adobe Sign (customer + NordicShield CEO/CTO). RSA 2048 + SHA-256 with embedded certificate. Long-term validation (LTV) format preserves signature validity beyond cert expiry. | ☑ Yes - Qualified timestamp per eIDAS (EU Regulation 910/2014). Adobe Sign embeds timestamp in PDF. Timestamp proves contract signed before cert expiry (legal requirement for contracts >5 year term). | 10 years after contract expiration (typical 3-year SLA contracts → 13 years total retention). GDPR allows retention for legal compliance. |
| Configuration changes | ☑ Yes - All Terraform/IaC changes signed via Git commit signing (GPG keys or SSH signing keys). IAM policy changes require MFA + CISO approval (logged in CloudTrail with signed API request). Emergency changes signed with Admin YubiKey. | ☑ Yes - Git commit timestamp + CloudTrail eventTime with server-side timestamp from AWS. Immutable timestamps prevent backdating. Critical changes (production IAM) logged to SIEM with NTP-synced timestamp. | 7 years (ISO 27001 A.12.4.1: audit of system activities - retain config change records matching audit log retention). Longer retention if change caused security incident (retain until incident closed + 7 years). |
| Audit log entries | ☑ Yes - Security-critical logs (AWS CloudTrail, Azure Activity Log, on-premises auth logs) signed hourly. SIEM computes SHA-384 hash of log batch → signs hash with ECDSA P-384 key stored in AWS CloudHSM. Signature stored in separate S3 bucket (write-once-read-many). | ☑ Yes - Each log entry timestamped with NTP-synced server clock (±100ms accuracy). Periodic sync to NTP pool servers in Finland (ntp1.funet.fi) + GPS-based stratum 1 servers for accuracy. Splunk validates timestamp sequence (detect clock skew attacks). | 7 years minimum (GDPR Art. 17(3)(e): retain logs for legal compliance). Critical security logs (authentication failures, privilege escalation) retained indefinitely (forensics/incident reference). Logs archived to AWS Glacier after 2 years (cost optimization). |

---

# SECTION G: KEY MANAGEMENT

## G.1 Key Management Principles

```
NordicShield Key Management Principles

Key Generation:
- Source of randomness: Hardware RNG (FIPS 140-2 certified): TPM 2.0 for endpoints, AWS CloudHSM for cloud keys, ATECC608A secure element for IoT devices, /dev/urandom (Linux kernel CSPRNG) with RDRAND CPU instruction for SSH keys
- Generation location: Keys generated where they will be used (principle of least exposure). TLS private keys generated on web servers (never transmitted), AWS KMS keys generated inside AWS CloudHSM (keys never leave HSM as plaintext), IoT device keys generated in ATECC608A secure element on device (physically unclonable)
- Minimum entropy: 256 bits for symmetric keys (AES-256), 2048 bits for RSA keys (factoring resistance), 256 bits for ECDSA/Ed25519 keys (discrete log resistance). NIST SP 800-90B full entropy requirement (no entropy reduction factored into security claims)

Key Storage:
- Hardware security modules (HSM): 
  * AWS CloudHSM: Root CA private keys, log signing keys, financial transaction signing keys (FIPS 140-2 Level 3 certified - tamper-responsive, keys destroyed if physical intrusion detected)
  * YubiKey 5 FIPS: Code signing keys for firmware releases, emergency admin keys (FIPS 140-2 Level 2 - physical presence required, 8-digit PIN)
  * ATECC608A secure element: IoT device private keys (embedded crypto chip, keys non-extractable, PUF-based key derivation)
  * TPM 2.0: BitLocker keys on Windows laptops, Linux LUKS keys on servers (keys sealed to PCR values - only decrypt if boot chain unmodified)
- Key management services: AWS KMS (primary: eu-north-1, DR: us-east-1), Azure Key Vault (DR only: West Europe), HashiCorp Vault (on-premises Turku DC for secrets not suitable for cloud storage)
- No plaintext keys in: Source code repositories (scan with TruffleHog + git-secrets pre-commit hooks), log files (Splunk SIEM configured to mask patterns like -----BEGIN PRIVATE KEY-----), backup files (Veeam backup encryption keys stored separately from backups), Slack/email (DLP policy blocks messages containing -----BEGIN PRIVATE KEY-----), documentation (Confluence page scanning via custom lambda weekly)

Key Distribution:
- Methods: 
  * TLS certificates: Let's Encrypt ACME protocol (automatic renewal), internal CA via SCEP (Simple Certificate Enrollment Protocol for IoT devices)
  * SSH public keys: Distributed via Ansible playbook to authorized_keys (Git repository as source of truth), removed within 24 hours of employee departure
  * API keys: Distributed via AWS Secrets Manager (application retrieves at runtime), Azure Key Vault SDK for .NET/Python apps, never hardcoded in environment variables
  * IoT device keys: Provisioned during manufacturing (factory provisioning) or via JITP (Just-In-Time Provisioning) for field replacements
- Encryption of keys: Master keys encrypted by AWS KMS master keys (envelope encryption), data keys encrypted with KEKs (key encryption keys), KEKs stored in CloudHSM. All keys encrypted in transit (TLS 1.3) and at rest (AES-256-GCM)
- Split knowledge: Root CA offline key requires M-of-N key ceremony (3 of 5 key custodians: CTO, CISO, Lead Security Engineer, IT Manager, external auditor). Each custodian holds 1 key share on hardware token in personal safe. Reconstitute key only for root cert issuance/renewal (expected frequency: once per 10 years)

Key Usage:
- Purpose limitation: Keys bound to specific purposes via X.509 Extended Key Usage extension (TLS Server Authentication, Code Signing, Email Protection) or AWS KMS key policies (kms:Decrypt only for specific S3 buckets). Attempting cross-purpose key use blocked at cryptographic API level.
- Access control: RBAC for key access - AWS KMS keys accessible only via IAM roles (no long-term credentials), CloudHSM keys require crypto officer role + MFA, YubiKey code signing requires physical presence + PIN. Principle of least privilege: developers cannot access production TLS keys, only DevOps Engineers and Security team.
- Usage logging: All key usage logged - AWS KMS logs to CloudTrail (every Encrypt/Decrypt/GenerateDataKey API call), CloudHSM logs to CloudWatch, HashiCorp Vault audit log (JSON format). SIEM alerts on: >100 KMS decryptions per minute by single IAM role (potential attack), key usage from unexpected IP/region, failed key access attempts (>5 in 10 minutes), key deletion attempts
```

## G.2 Key Lifecycle Management

### Key Rotation Schedule

| Key Type | Rotation Period | Automated? | Responsible Party |
|----------|-----------------|------------|-------------------|
| TLS certificates | Public: 90 days (Let's Encrypt), Internal: 1 year | ☑ Yes - Let's Encrypt certbot auto-renewal (30 days before expiry), Internal CA auto-renewal via SCEP | Platform Engineering team monitors cert-manager (Kubernetes) logs, alerts to #security-alerts Slack if renewal fails |
| Code signing keys | 2 years (extended validity for firmware deployed to 10-year lifecycle devices) | ☐ No - manual key ceremony for YubiKey replacement | CISO approves new key generation, Lead Security Engineer performs key ceremony, revoke old key after 90-day overlap period (allows old firmware verification during transition) |
| Database encryption keys | RDS TDE keys: 2 years, Field-level encryption keys: 1 year | ☑ Yes - AWS KMS automatic rotation (new key version generated, old versions retained for decrypting historical data) | AWS KMS manages rotation automatically, DBA team validates rekey operations in non-production first (staging rekey 1 week before production) |
| AWS KMS keys | 1 year (automatic rotation enabled on all customer-managed keys) | ☑ Yes - AWS KMS generates new cryptographic material annually, old key versions remain available for decrypting old data (envelope encryption architecture) | Security Engineering team enforces via AWS Organizations SCP (deny kms:DisableKeyRotation), monthly audit report validates all CMKs have rotation enabled |
| SSH keys | Developers: 1 year, Service accounts: 2 years, Emergency break-glass: 90 days | ☑ Partial - Automated reminder email 30 days before expiry, developer regenerates key and updates Ansible inventory | Individual engineers responsible for own SSH keys, IT Security Manager audits ~/.ssh/authorized_keys quarterly (Ansible playbook scans all servers), revoke keys not rotated within 30 days of policy expiry |
| IoT device certificates | 1 year validity, automated renewal starting 90 days before expiry (3 retry attempts over 90 days, manual intervention if all fail) | ☑ Yes - Device initiates renewal via MQTT to AWS IoT Core, AWS IoT CA issues new cert with same key, device installs new cert and reports success | IoT Operations team monitors device cert expiry dashboard (custom CloudWatch dashboard), P2 ticket auto-created for devices with <30 days to expiry and no renewal attempt |
| API keys | NordicSense REST API: 90 days, Third-party SaaS integrations: 180 days (longer period for stability, shorter than 1-year audit cycle) | ☐ No - Customer notified 30 days before expiry, customer regenerates key via web portal or API, old key valid for 7-day grace period (allows customer time to update applications) | Customer Success team sends email notification (30/14/7 days before expiry), API Platform team monitors key usage (alert if expired key attempted >10 times - indicates customer missed rotation) |
| Backup encryption keys | 2 years (longer rotation period for restore reliability - old backups must remain decryptable, Veeam retains old keys automatically) | ☐ No - Scheduled key rotation during planned maintenance window (requires brief backup service interruption ~15 min), keys rotated during annual DR drill weekend | IT Operations Manager schedules rotation, Lead System Admin executes via Veeam console, validates key backup to offline USB token stored in CTO's safe, test restore from pre-rotation backup to verify old key still accessible |

### Key Revocation Process

```
Key Revocation Process

Revocation Triggers:
1. Suspected compromise (private key exposed in public GitHub repo, key found in memory dump, unauthorized key usage detected in CloudTrail logs)
2. Employee departure (termination or resignation - SSH keys/certificates revoked same business day)
3. Certificate expiration (automated revocation 7 days after expiry if not renewed)
4. IoT device decommissioning (customer site closure, device replacement, warranty return)
5. Key rotation policy violation (key not rotated within policy period + 30-day grace period)
6. Security incident (key potentially accessed during incident - proactive revocation)
7. Algorithm weakness discovered (cryptographic vulnerability disclosed affecting key type)

Revocation Steps:
1. Incident Detection: Security team notified via SIEM alert, IT helpdesk ticket, or incident response
   - Create P1 incident ticket if compromise suspected, P3 if routine (expiration/departure)

2. Immediate Actions (within 15 minutes for P1):
   - Identify all systems using the compromised key (query CloudTrail, grep authorized_keys, check CT logs)
   - Disable key immediately: AWS KMS (kms:DisableKey), SSH (remove from authorized_keys), TLS (remove from LB)
   - Alert affected system owners via Slack #security-alerts + email

3. Revoke Certificate (within 1 hour):
   - Add certificate to CRL via CA API or management console
   - Update CRL and publish to distribution points (http://crl.nordicsense.fi/ca.crl, S3 for IoT)
   - Update OCSP responder for OCSP-enabled certificates
   - Verify revocation visible to clients (test with openssl s_client -status)

4. Key Replacement (within 24 hours for P1, 7 days for P3):
   - Generate new key pair following key generation principles
   - Issue new certificate from CA with new serial number
   - Distribute new key to affected systems (Ansible for SSH, Kubernetes secrets for TLS, AWS IoT CA for devices)
   - Test new key works correctly before removing old key access
   - Monitor for continued use of old key (should be zero - investigate if detected)

5. Post-Incident Review (within 72 hours):
   - Root cause analysis: How was key compromised? Was it preventable?
   - Document lessons learned in incident report (Confluence - restricted access)
   - Update key management procedures if gaps identified

CRL/OCSP:
- CRL update frequency: Every 6 hours for internal CA (IoT devices), every 24 hours for user certs, immediate for compromise
- OCSP update frequency: Real-time (OCSP responder queries CA database on each request)
- Distribution points: 
  * CRL: http://crl.nordicsense.fi/internal-ca.crl, S3 bucket for offline IoT access
  * OCSP: http://ocsp.nordicsense.fi (internal), Sectigo OCSP for external (http://ocsp.sectigo.com)
- Client configuration: TLS clients check OCSP (stapled preferred), IoT devices query CRL daily at 04:00 local time
```

## G.3 Key Storage Solutions

| Key Type | Storage Solution | Location | Backup |
|----------|------------------|----------|--------|
| Root CA keys | Offline HSM (YubiKey 5 FIPS × 5 units for M-of-N ceremony) | 5 custodians: CTO safe (Turku), CISO safe (home), Lead Security Engineer (bank safe deposit box), IT Manager (Turku secure cabinet), External Auditor (EY Helsinki office) | No backup (M-of-N provides redundancy - need 3 of 5 keys). Root key re-ceremony required if <3 custodians available. |
| TLS private keys | Server filesystem (/etc/ssl/private/ with 0600 permissions), Kubernetes secrets (encrypted with AWS KMS), AWS Certificate Manager (ACM) | Production servers (Turku DC, AWS eu-north-1), Load balancers store keys in HSM-backed memory (F5 BIG-IP FIPS mode) | Encrypted backup to Veeam (keys encrypted with separate backup encryption key). Lost TLS key requires cert reissuance (1 hour recovery via Let's Encrypt/internal CA). |
| AWS encryption keys | AWS KMS (customer-managed keys), AWS CloudHSM (FIPS 140-2 Level 3) for critical keys (root CA, log signing, financial signing) | Primary: eu-north-1, DR: us-east-1. CloudHSM cluster: 3 nodes across 3 AZs in eu-north-1 for HA | AWS KMS automatic backup (continuous by AWS - RTO <1 min). CloudHSM daily export to encrypted S3, keys encrypted with AES-256 master key stored offline. |
| Database keys | PostgreSQL TDE keys in AWS KMS, field-level encryption keys in HashiCorp Vault, MySQL keys in server keyring | AWS RDS manages TDE keys, HashiCorp Vault cluster (3-node HA in Turku + AWS DR), on-premises keys in server TPM 2.0 | RDS automated backup includes encrypted DB + TDE key access. Vault backup to encrypted EBS snapshots (daily), unseal keys stored separately (Shamir 5 keys, threshold 3). |
| IoT device keys | ATECC608A secure element (hardware crypto chip, private keys non-extractable, physically unclonable function) | IoT temperature sensors (827 devices at customer sites), gateway devices (47 gateways) | No backup (keys not extractable by design). Device failure: provision new device with new key pair via JITP, revoke old cert. Recovery: replace device (technician on-site in 24 hrs, provision in 15 min). |
| Developer SSH keys | Developer laptop ~/.ssh/ (0600 permissions), YubiKey PIV slot for high-privilege engineers | macOS Keychain or Windows Credential Manager for password-protected encryption, YubiKey 5 for privileged access (key never leaves hardware) | Developer responsible for own backup. YubiKey keys intentionally not backed up (security > convenience - lost YubiKey requires new SSH key generation). |

## G.4 Key Backup and Recovery

| Scenario | Recovery Method | Recovery Time | Authorization |
|----------|-----------------|---------------|---------------|
| Lost encryption key | AWS KMS: Cancel scheduled deletion (7-30 day waiting period). If deleted: restore from KMS automatic backup. Total loss: restore data from Veeam backup using backup encryption key from HashiCorp Vault. | Immediate (cancel deletion) to 4 hours (restore from backup - requires RDS snapshot restore + re-encrypt with new KMS key) | Scheduled deletion: CISO approval + MFA. Cancel: DevOps Engineers or Security team (kms:CancelKeyDeletion). Backup restoration: IT Operations Manager + CISO approval for production. |
| Compromised key | Immediate revocation: Remove from all servers (Ansible), disable in ACM, add cert to CRL. Generate new key pair, request new cert from Let's Encrypt/internal CA. Update load balancer. Investigate exposure source (GitHub/logs). | 30 minutes (automated revocation) to 2 hours (verify all services using new cert, monitor for errors) | Incident Commander (on-call Senior Engineer) initiates immediate revocation (no approval for P1). CISO notified within 15 min. Post-incident review within 72 hours. |
| Disaster recovery | Failover to AWS DR region (us-east-1). KMS keys replicated to DR. Restore apps from AMIs, data from S3 (CRR), database from RDS backup (<5 min RPO). Re-issue TLS certs from Let's Encrypt. Restore Vault from EBS snapshot. | RTO: 4 hours (manual DR failover - update DNS). RPO: <5 min (continuous replication). Critical services operational in 1 hour via Auto Scaling. | DR activation: CTO or CISO authorization (confirms Turku datacenter non-recoverable). Incident Commander executes DR runbook. Board notified within 24 hours. |
| Key custodian unavailable | M-of-N: Need 3 of 5 custodians. Video conference key ceremony if <3 in Turku (each custodian shows ID on camera, enters key share sequentially). If <3 globally: Emergency new root CA (Board approval, audit committee notified, 30-day root distribution). | Standard ceremony: 4 hours (coordinate 3 custodians, physical meeting). Emergency ceremony: 2 hours (video conference). Emergency root rekey: 30 days (distribute to 827 IoT devices + all servers). | Standard: CISO authorizes ceremony. Emergency: CTO/CISO + 1 Executive Officer (CFO/COO/CEO). Board approval for new root CA. |

---

# SECTION H: PKI ARCHITECTURE

## H.1 Certificate Authority Structure

```
NordicShield PKI Hierarchy

Root CA:
- Name: NordicShield Root CA G1
- Location: Offline secure storage (5 YubiKey 5 FIPS hardware tokens - M-of-N key ceremony requires 3 of 5)
- Key type: RSA 4096 with SHA-384 signature algorithm
- Validity: 20 years (generated 2024, expires 2044) - long validity acceptable for offline root CA
- Offline/Online: OFFLINE (air-gapped workstation powered on only for key ceremonies, ~once every 3-5 years)
- Usage: Only signs intermediate CA certificates, never  signs end-entity certificates directly

Issuing CA(s):
- **NordicShield Internal CA**: Issues certificates for internal TLS (microservices mTLS), user authentication certificates (VPN/SSH), code signing certificates (internal applications). RSA 2048, 5-year validity, online CA (API accessible via EJBCA or smallstep-ca).
- **Nordic Shield IoT Device CA**: Dedicated subordinate CA under Root CA for IoT device identity certificates only (827 devices). ECDSA P-384 (stronger than device keys for CA hierarchy), 10-year validity, integrated with AWS IoT Device Management. Separate CA limits blast radius if IoT CA compromised (doesn't affect user/server certificates).
- **NordicShield Code Signing CA**: Issues code signing certificates for firmware releases and application signing. RSA 4096, 10-year validity, offline (manual cert issuance for security - code signing certs require audit trail).

External CAs used:
- **Let's Encrypt** (ISRG Root X1): Public-facing TLS certificates for *.nordicsense.fi API endpoints. Free, automated 90-day renewal via ACME protocol (certbot). Certificates trusted by all browsers/OS trust stores.
- **DigiCert** (DigiCert Global Root G2): Extended Validation Code Signing Certificate for public software releases (Windows applications distributed to customers). EV cert stored on YubiKey 5 FIPS (HSM-backed). Annual cost: €450.
- **Sectigo** (USERTrust RSA CA): S/MIME email certificates for executive communications (CEO, CTO, CISO, CFO). 1-year validity, issued via Sectigo Certificate Manager API. Annual cost: €35 per certificate × 4 executives = €140.
- **AWS Certificate Manager (ACM)**: AWS-managed TLS certificates for AWS resources (CloudFront distributions, Application Load Balancers, API Gateway). Free, automatic renewal, private keys managed entirely by AWS (never exposed).
```

## H.2 Certificate Requirements

| Certificate Type | Key Algorithm | Key Size | Validity | Renewal |
|------------------|---------------|----------|----------|---------|
| Web server (public) | RSA or ECDSA P-256 | RSA 4096 (preferred) or ECDSA P-256 | 90 days (Let's Encrypt) | Automated via certbot/cert-manager, 30 days before expiry |
| Web server (internal) | RSA | 2048-bit | 1 year | Automated via SCEP protocol to Internal CA, 60 days before expiry |
| Client authentication | RSA or ECDSA P-256 | RSA 2048 or ECDSA P-256 | 1 year | Manual renewal via certificate request (CSR), 30 days before expiry |
| Code signing | RSA | 4096-bit | 3 years (EV cert from DigiCert) | Manual renewal via DigiCert portal, 90 days before expiry (allow time for YubiKey key ceremony) |
| IoT device | ECDSA | P-256 (secp256r1) | 1 year | Automated via AWS IoT CA, device initiates renewal 90 days before expiry |
| Email (S/MIME) | RSA | 2048-bit | 1 year | Manual renewal via Sectigo portal, 30 days before expiry |

## H.3 Certificate Inventory

| Certificate | Issuer | Expiration | Auto-Renewal | Monitor |
|-------------|--------|------------|--------------|---------|
| *.nordicsense.fi | Let's Encrypt (R3 intermediate) | Every 90 days (currently expires: March 15, 2026) | ✅ Yes - certbot cron job daily at 02:00 UTC | Prometheus exporter (ssl_exporter) checks expiry, alerts to #security-alerts if <14 days remaining |
| api.nordicsense.fi | Let's Encrypt (R3) | 90 days (expires: April 2, 2026) | ✅ Yes - Kubernetes cert-manager | CloudWatch custom metric monitors cert expiry via Lambda (daily check), SNS alert to on-call engineer if <7 days |
| NordicShield Code Signing (DigiCert EV) | DigiCert Assured ID Root CA | 3 years (expires: December 20, 2027) | ❌ No - manual renewal via DigiCert portal | Calendar reminder (CTO, CISO, Lead Security Engineer) 90 days before expiry. Renewal requires YubiKey key ceremony (3 business days lead time). |
| AWS IoT Core (wildcard) | AWS IoT CA (NordicShield IoT Device CA) | N/A (ACM-managed, AWS auto-renews) | ✅ Yes - fully managed by AWS | AWS Certificate Manager dashboard shows renewal status, no action required from NordicShield team |

---

# SECTION I: COMPLIANCE AND REGULATORY CONSIDERATIONS

## I.1 Regional Requirements

| Region | Regulation | Cryptographic Requirement | NordicShield Compliance |
|--------|------------|--------------------------|------------------------|
| EU (Finland, Netherlands) | GDPR | Appropriate encryption (Art. 32 - state of the art technical measures) | ✅ COMPLIANT: AES-256-GCM for all PII data at rest (customer contact information, employee records), TLS 1.3 for data in transit, encryption keys in AWS KMS/HSM (FIPS 140-2 Level 3 for RESTRICTED data). Field-level encryption for highly sensitive PII (payment card details if stored). Annual GDPR audit confirms appropriate technical measures. |
| EU | NIS2 | State-of-the-art crypto (Article 21 - security measures for essential entities) | ✅ COMPLIANT: NordicShield categorized as "Important Entity" (IoT monitoring for critical infrastructure - power plants, hospitals). Cryptographic controls exceed minimum: TLS 1.3 (not just 1.2), RSA 4096 for public certs (not just 2048), annual key rotation (not just 2-year), HSM storage for critical keys. NIS2 compliance validated by external audit (TÜViT - German IT security firm) - report due March 2026. |
| USA (Texas) | CCPA | Reasonable security (no specific crypto requirements, but "reasonable procedures and practices") | ✅ COMPLIANT: Texas Cooling & Air (customer in Austin, TX) data encrypted with AES-256-GCM at rest + TLS 1.3 in transit (exceeds "reasonable" standard). Customer audit (September 2025) confirmed compliance. CCPA less prescriptive than GDPR but NordicShield applies EU standards globally (single security baseline easier than region-specific controls). |
| Rwanda | Data Protection Act | Appropriate safeguards (Law No 058/2021 - data protection and privacy) | ✅ COMPLIANT: Kigali office handles employee PII + customer metadata (not full customer datasets). Employee laptops use BitLocker/FileVault encryption (AES-256-XTS), VPN required for accessing NordicShield resources (WireGuard with X25519+ChaCha20-Poly1305), Microsoft 365 with customer-managed keys in Azure Key Vault (EU data residency + Rwandan access controls). Rwanda DPA compliance self-certified (no mandatory external audit). |
| Industry | SOC 2 | Encryption controls (CC6.7 - encryption of data at rest and in transit) | ✅ COMPLIANT: SOC 2 Type II audit (annual, auditor: Deloitte Finland) validates: (1) All customer data encrypted at rest (AWS RDS TDE, S3 SSE-KMS), (2) TLS 1.2+ for all data in transit (API endpoints, IoT devices, employee laptops), (3) Key management procedures documented and followed (AWS KMS rotation enabled, quarterly key access audit), (4) Encryption controls tested over 12-month period. Last audit: December 2025, zero findings related to cryptography. |
| Industry | ISO 27001 (A.10) | Cryptographic controls (A.10.1.1 policy, A.10.1.2 key management) | ✅ COMPLIANT: ISO 27001:2022 certified (certification body: RISE Research Institutes of Sweden, certificate: ISO27001-FI-0124, expires: May 2027). A.10.1.1: This Cryptographic Standards document satisfies policy requirement (approved by CISO January 2026, reviewed annually). A.10.1.2: Key management lifecycle documented in Section G (generation, storage, distribution, rotation, revocation, destruction). Annual surveillance audit confirms compliance. |

## I.2 Export Controls

| Consideration | Policy |
|---------------|--------|
| Encryption software export | NordicShield exports IoT firmware containing AES-256-GCM and ECDSA P-256 cryptography to customers globally (47 customer sites across EU, USA, Rwanda, Kenya). **EU Export Controls**: Cryptography <56-bit symmetric or <512-bit asymmetric requires no export license under EU Dual-Use Regulation 2021/821. AES-256 exceeds thresholds (256-bit > 56-bit) but **general authorization** applies for publicly available cryptography (NIST standards, open-source OpenSSL/mbedTLS libraries). No specific export license required for Nordic Shield's use case (commercial IoT, not military). **US Export Controls (EAR)**: NordicShield's US subsidiary (Austin office) classified products under ECCN 5D002 (encryption software) - eligible for License Exception ENC (self-classification via BIS-748P-A filing completed December 2024). Annual report to BIS required. Result: No export restrictions for current cryptography (AES-256, RSA 4096, ECDSA P-256) to commercial customers in non-embargoed countries. |
| Key escrow requirements | NordicShield does **NOT** implement key escrow (government backdoor access to encryption keys). **Legal Analysis**: Finland/EU law does not require key escrow for commercial encryption (unlike some authoritarian regimes). GDPR Article 32 requires "appropriate technical measures" but not key escrow. NIS2 does not mandate government key access. **Risk**: Some countries (e.g., China, Russia) may require key escrow for sale of encryption products - NordicShield currently has no customers in these jurisdictions (decision: avoid markets requiring key escrow to preserve security architecture). **Customer Contracts**: SLA explicitly states "NordicShield cannot provide decryption keys to customers or third parties" (keys managed by AWS KMS - NordicShield cannot extract keys from HSM). Exception: Customer-managed keys (CMK) where customer controls key access via IAM policies. |
| Government access requests | **Policy**: NordicShield will resist government access requests for encryption keys or backdoors unless legally compelled by court order in EU jurisdiction. **Process**: (1) Legal review by external counsel (DLA Piper Finland), (2) Attempt to narrow scope of request, (3) Notify affected customers unless legally prohibited (GDPR transparency obligation), (4) Public transparency report (annual - published to nordicsense.fi/transparency) discloses number of government requests received/complied with. **Historical**: Zero government access requests received to date (2020-2025). **Technical**: Encryption keys stored in AWS CloudHSM (FIPS 140-2 Level 3) - keys never exported from HSM as plaintext. Even under government order, NordicShield physically cannot extract keys (by design). Court order could compel use of keys to decrypt data (NordicShield has Decrypt permission) but not extraction of keys themselves. **Warrant Canary**: NordicShield will maintain warrant canary (statement "we have received zero National Security Letters") - removal of statement signals receipt of classified government request where notification is prohibited. |

---

# SECTION J: IMPLEMENTATION GUIDELINES

## J.1 Developer Guidelines

```
Developer Cryptography Guidelines

DO:
- Use approved libraries for cryptography (never implement custom crypto algorithms - easy to introduce vulnerabilities)
- Use appropriate key sizes per this standard (AES-256 for databases, ECDSA P-256 for IoT, RSA 4096 for public TLS)
- Validate certificates properly (check certificate chain, expiration, revocation via OCSP/CRL, hostname matching)
- Store keys in secure location (AWS Secrets Manager, Azure Key Vault, HashiCorp Vault - never in source code, config files, or environment variables visible in CI/CD logs)
- Use authenticated encryption (AES-GCM, ChaCha20-Poly1305 - provides both confidentiality and integrity)
- Generate keys with cryptographically secure RNG (os.urandom in Python, crypto.randomBytes in Node.js, SecureRandom in Java - NOT Math.random())
- Use constant-time comparison for secrets (crypto.timingSafeEqual in Node.js, hmac.compare_digest in Python - prevents timing attacks on API keys/HMAC verification)
- Salt and hash passwords properly (Argon2id preferred, bcrypt acceptable - never store plaintext or unsalted hashes)
- Encrypt all PII at rest (use AWS KMS, Azure Key Vault, or database TDE - identify PII via DLP scans)
- Use TLS 1.3 for all network connections (prefer TLS 1.3, fallback to TLS 1.2 only if required for legacy IoT devices)

DON'T:
- Hard-code keys or secrets in source code (TruffleHog and git-secrets pre-commit hooks will block commits with secrets - use Secrets Manager retrieval at runtime)
- Use deprecated algorithms (MD5, SHA-1 for security, DES, 3DES, RC4 - all prohibited per Section B of this standard)
- Disable certificate validation (NEVER set verify=False in Python requests, rejectUnauthorized: false in Node.js - huge security vulnerability)
- Log sensitive cryptographic material (keys, passwords, plaintext PII, HMAC secrets - configure logging library to mask patterns like -----BEGIN PRIVATE KEY-----, passwords, credit card numbers)
- Reuse IVs/nonces with same key (each AES-GCM encryption must use unique nonce - use counter or random nonce generation)
- Use ECB mode (Electronic Codebook reveals patterns in plaintext - always use GCM, CBC, or CTR modes)
- Trust user input for cryptographic parameters (never let users specify algorithm, key size, or cipher suite - use server-enforced secure defaults)
- Implement custom padding (PKCS#7 padding oracle vulnerabilities - use library-provided authenticated encryption)

Approved Cryptographic Libraries:
- **Python**: cryptography (PyCA), PyCryptodome (AES operations), hashlib (built-in hashing), Argon2-cffi (password hashing)
- **Node.js**: crypto (built-in), tweetnacl (NaCl library for ChaCha20-Poly1305), bcrypt, argon2
- **Java**: BouncyCastle (comprehensive), Java Cryptography Extension (JCE) built-in
- **C/C++**: OpenSSL 3.0+ (NOT 1.0.x - security vulnerabilities), libsodium (NaCl-based, easier API than OpenSSL), mbedTLS (for embedded IoT)
- **Golang**: crypto package (built-in - use golang.org/x/crypto for argon2), NaCl (golang.org/x/crypto/nacl)
- **Embedded (IoT)**: mbedTLS, WolfSSL (commercial, optimized for ARM), ATECC608A hardware crypto library
```

## J.2 Operations Guidelines

```
Operations Team Cryptography Guidelines

Certificate Management:
- Monitor expiration: Multi-tier alerting system
  * 90 days before expiry: Informational alert to #certificates Slack channel (routine planning)
  * 60 days: Email to Platform Engineering team + Jira ticket auto-created (P4 priority)
  * 30 days: Escalate to P3, email to IT Operations Manager + daily Slack reminders
  * 14 days: Escalate to P2, PagerDuty alert to on-call engineer + CISO email notification
  * 7 days: Escalate to P1, emergency page to on-call + CTO notification, initiate emergency renewal procedure
- Renewal process:
  * Automated: Let's Encrypt (certbot), AWS ACM (fully managed), Azure Key Vault (auto-rotation), IoT devices (AWS IoT CA automatic renewal 90 days before expiry)
  * Manual: Code signing EV cert (DigiCert portal renewal 90 days before expiry - requires YubiKey key ceremony, 3 business days lead time), S/MIME certs (Sectigo portal, 30 days notice)
  * Testing: After renewal, test in non-production environment first (staging.nordicsense.fi) before prod deployment. Validate: TLS handshake succeeds, certificate chain complete, OCSP stapling works, no mixed content warnings
- Emergency replacement:
  * If cert expires unexpectedly (missed renewal, CA outage, automated system failure): Initiate P1 incident response
  * Let's Encrypt fallback: Manual certbot run on affected server (< 5 min), or issue from Internal CA if Let's Encrypt unavailable
  * Load balancer update: F5 BIG-IP cert replacement via iControl REST API (scripted, <2 min), restart virtual servers if required
  * Customer notification: If customer-facing API cert expires (*.nordicsense.fi), notify customers within 15 min via status page (status.nordicsense.fi) + email to customer technical contacts + Slack integration posts in customer shared channels

Key Rotation:
- Automated where possible: AWS KMS (annual auto-rotation enabled on all CMKs), IoT device certificates (device-initiated renewal via MQTT 90 days before expiry), TLS certs (Let's Encrypt certbot auto-renews at 30 days)
- Documented manual procedures: Backup encryption key rotation (Veeam console procedure, IT Operations Manager executes during planned maintenance window, validate backup/restore with new key), Code signing key rotation (YubiKey replacement, CISO-approved key ceremony with 3 of 5 custodians, 3-5 business days), SSH key rotation (engineer self-service key regeneration, update Ansible inventory Git repo, automated deployment to authorized_keys via Ansible playbook)
- Testing after rotation: Non-production validation required for all manual rotations - test key works in staging environment before production deployment. Rollback plan documented (keep old key active for 7-day grace period, revert to old key if new key fails). Database encryption key rotation: Test restore from backup encrypted with old key (verify old keys still accessible after rotation).

Incident Response:
- Key compromise procedures:
  1. **Immediate** (within 15 min): Disable compromised key (AWS KMS: kms:DisableKey, SSH: remove from authorized_keys, TLS: remove from load balancer config), create P1 incident ticket, alert Security team via Slack #security-alerts + PagerDuty page to on-call
  2. **Revocation** (within 1 hour): Add certificate to CRL, update OCSP responder, verify revocation visible to clients, identify all systems using compromised key (CloudTrail query for KMS key usage, grep for SSH key fingerprint, certificate transparency logs for TLS cert serial)
  3. **Replacement** (within 4 hours for P1): Generate new key pair, issue new certificate, distribute to affected systems (Ansible for SSH, Kubernetes secret update for TLS, AWS IoT CA for device certs), verify new key works correctly
  4. **Investigation** (parallel to replacement): Forensics - how was key compromised? GitHub exposure? Log file leak? Memory dump? Stolen laptop? Interview engineer who committed key (if GitHub), review access logs (who accessed compromised key), identify potential lateral movement (did attacker use key to access other systems?)
- Certificate revocation: Follow Section G.2 revocation process - add to CRL (updated every 6 hours, immediate for compromise), update OCSP responder (real-time), notify affected parties (email to system owners + customer notification if customer-facing cert)
- Communication plan: 
  * Internal: Incident Commander posts updates every 30 min to #security-incident Slack channel (status, actions taken, ETA for resolution)
  * Executive: CISO briefed within 1 hour of P1 incident, CTO/CEO briefed if customer impact confirmed within 2 hours
  * Customer: If customer-facing service impacted, Customer Success Manager notifies customers within 30 min (status page update + email to technical contacts), post-incident report within 72 hours
  * Regulatory: If GDPR breach suspected (PII exposed via key compromise), notify Finnish Data Protection Authority within 72 hours per GDPR Article 33, notify affected customers without undue delay per Article 34
```

---

# SECTION K: CRYPTOGRAPHIC STANDARDS EXCEPTIONS

## K.1 Exception Process

```
Cryptographic Standards Exception Process

Exceptions may be granted for:
- Legacy systems requiring deprecated algorithms for compatibility (e.g., customer legacy SCADA system only supports TLS 1.1 or 3DES)
- Interoperability requirements with third-party systems (e.g., vendor API only supports RSA 1024 signatures - upgrade path not available from vendor)
- Performance constraints on resource-limited devices (e.g., ultra-low-power sensor cannot support AES-128, need even lighter algorithm - extremely rare, prefer hardware crypto acceleration)
- Regulatory requirements in specific jurisdictions (e.g., country requires key escrow - currently NordicShield avoids these markets)
- Business-critical temporary workaround (e.g., customer production outage requires emergency downgrade to TLS 1.1 for 48 hours until vendor patches system)

Exception Request Requirements:
1. **Business Justification**: Document business need for exception (which customer? which system? revenue impact if exception denied? alternative solutions considered?)
2. **Risk Assessment**: Quantified risk analysis - likelihood of cryptographic attack (Low/Medium/High), impact if compromised (data classification affected, number of devices/users impacted, regulatory penalties), residual risk with compensating controls
3. **Compensating Controls**: Technical controls to mitigate risk (network segmentation? additional monitoring? shorter exception duration? encrypt at application layer if transport layer weak?)
4. **Duration**: Specific expiration date (maximum 1 year for Technical exceptions, 6 months for deprecated algorithms, permanent exceptions ONLY for documented unfixable legacy systems with Board approval)
5. **Remediation Plan**: Path to compliance - when can system be upgraded? What is blocking upgrade? Vendor roadmap? Budget approval pending?
6. **Stakeholder Sign-Off**: System Owner acknowledges risk, IT Operations confirms technical feasibility of compensating controls, Security team approves compensating controls are adequate

Approval Authority:
- **Low Risk** (e.g., extend TLS cert validity from 1 year to 13 months for operational reasons): IT Security Manager approval
- **Medium Risk** (e.g., allow TLS 1.1 for specific legacy customer system with network segmentation): CISO approval + IT Operations Manager confirmation of compensating controls
- **High Risk** (e.g., allow RSA 1024 for specific system, use prohibited algorithm like 3DES): CISO + CTO joint approval + document to Audit Committee (quarterly exception review)
- **Critical/Permanent** (e.g., key escrow for government customer, permanent use of deprecated algorithm): Board of Directors approval (requires business case justifying security compromise vs business value)

Compensating Controls Required:
- Minimum compensating controls: (1) Network segmentation (exception system isolated on separate VLAN with firewall rules limiting access), (2) Enhanced monitoring (SIEM alerting on all connections to/from exception system - detect potential compromise faster), (3) Documented risk acceptance (System Owner signature acknowledging exception increases risk)
- Additional controls for High Risk exceptions: (1) Multi-factor authentication for access to exception system, (2) Privileged Access Workstation (PAW) required to administer, (3) Weekly vulnerability scans (vs standard monthly), (4) Quarterly penetration testing focused on exception weakness

Maximum Exception Duration:
- Technical exceptions (performance, compatibility): 1 year maximum, renewable once with updated justification
- Deprecated algorithm exceptions: 6 months maximum (aggressive remediation timeline), renewable ONLY if vendor/customer provides documented evidence upgrade is impossible
- Permanent exceptions: Only for systems meeting ALL criteria - (a) business-critical, (b) no vendor upgrade path available, (c) replacement cost unjustifiable (>€500K), (d) Board approval obtained, (e) annual re-approval by CISO confirming compensating controls still effective

Review Schedule:
- Quarterly exception review: All active exceptions reviewed by Security Team (next review: April 2026 CAB meeting), validate compensating controls still in place, confirm expiration tracking on target, escalate overdue exceptions to CISO
- Annual exception audit: External auditor (Deloitte) reviews all exceptions during ISO 27001/SOC 2 audit (annual audit includes exception register review, interview exception system owners, validate compensating controls tested)
- Monthly automated scan: Security automation script queries exception register + scans production environment for non-compliant cryptographic configurations (detect shadow exceptions not formally approved)
```

## K.2 Current Exceptions

| System | Standard | Exception | Compensating Control | Expiration |
|--------|----------|-----------|---------------------|------------|
| Helsinki Energy Legacy SCADA Interface | TLS 1.3/1.2 minimum | TLS 1.1 allowed for specific customer integration (Helsinki Energy power plant SCADA system - vendor Siemens does not support TLS 1.2 on this model, EOL 2027) | Network segmentation (SCADA VLAN isolated via firewall, only gateway device can connect), VPN tunnel wraps TLS 1.1 connection in TLS 1.3 outer layer (defense in depth), Connection limited to 04:00-05:00 daily sync window (1-hour exposure), SIEM monitors all SCADA connections (alert on unexpected connection times/source IPs) | September 30, 2027 (customer replacement project - budget approved, new SCADA system supports TLS 1.3, migration timeline: 18 months) |
| Internal HR Database (Legacy FileMaker Pro) | AES-256-GCM for REGULATED data at rest | AES-128-CBC (FileMaker Pro 16 does not support GCM mode, upgrade to FileMaker 19 planned but requires €45K re-licensing + 6 months development) | Database network access restricted to HR office VLAN only (no internet exposure), Application-layer encryption for SSN field using AES-256-GCM via Python middleware (compensates for weak database encryption), Quarterly penetration testing focused on HR database (last test: January 2026, no findings), Database backups use Veeam AES-256-GCM (stronger encryption at rest for backups) | June 30, 2026 (FileMaker 19 upgrade project in Q2 2026, budget approved €45K) |
| TechPlus Vendor API Integration | HMAC-SHA256 API authentication | Vendor only supports HMAC-SHA1 (vendor: TechPlus Inc. refuses to upgrade API - \"SHA-1 sufficient for HMAC use case\" per vendor security team - technically correct but violates our policy of no SHA-1 for security functions) | API key rotated every 30 days (vs standard 90 days - reduces exposure window), Network ACL restricts API access to specific NordicShield IPs only (IP allowlist at vendor firewall), HTTPS enforced for all API calls (TLS 1.3 - protects HMAC signature in transit from MITM), SIEM correlation: alert if API returns authentication error (detect brute force or key compromise) | December 31, 2026 (alternative vendor evaluation in progress, RFP issued October 2025 for TechPlus replacement, final decision by June 2026, migration by December 2026) |

---

# SECTION L: EXECUTIVE SUMMARY

```
Cryptographic standards are fundamental to NordicShield's security posture, protecting customer IoT data across 827 deployed devices at 47 customer sites and ensuring compliance with GDPR, NIS2, SOC 2, and ISO 27001 requirements. This comprehensive standard establishes NordicShield's cryptographic architecture, guiding security decisions for the next 3-5 years as the company expands to global offices in Amsterdam, Austin, and Kigali.

Key cryptographic decisions balance security, performance, and IoT device constraints. For symmetric encryption, NordicShield standardized on AES-256-GCM for databases, cloud storage, and backups, with AES-128-GCM for resource-constrained IoT temperature sensors (ARM Cortex-M4 processors with 256 KB RAM). Asymmetric cryptography uses RSA 4096 for public-facing TLS certificates and code signing, while IoT devices leverage ECDSA P-256 for 5.6x faster authentication (60ms vs 340ms for RSA 2048 on constrained hardware). Password hashing migrated to Argon2id as the preferred standard, replacing legacy bcrypt implementations.

IoT cryptography presents unique challenges addressed through hardware security: ATECC608A secure elements store private keys with physically unclonable functions, preventing key extraction even if devices are physically compromised at customer sites. Automated certificate rotation (90-day renewal window for 1-year certificates) ensures 827 IoT devices maintain fresh credentials without manual intervention. Firmware signing with RSA 4096 certificates prevents unauthorized code injection that could disable critical cooling systems at customer facilities.

Key management maturity improved significantly through centralized storage (AWS KMS for cloud, HashiCorp Vault for on-premises, ATECC608A for IoT), automated rotation schedules, and M-of-N key ceremonies for root CA operations (3 of 5 custodians required). PKI architecture features an offline root CA (20-year validity) with dedicated subordinate CAs for internal TLS, IoT devices, and code signing - limiting blast radius if any CA is compromised.

Implementation priorities for 2026 include migrating legacy FileMaker HR database from AES-128-CBC to AES-256-GCM (Q2), replacing vendor integrations using deprecated SHA-1 for HMAC (Q4), and deploying automated cryptographic configuration scanning to detect shadow exceptions. Ongoing management requires quarterly exception reviews, annual external audits (Deloitte for SOC 2, RISE for ISO 27001), and continuous monitoring via SIEM alerts for certificate expirations, unauthorized key usage, and cryptographic policy violations.
```

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 1.5 - Cryptographic Standards Document |
| **Phase** | 1 - General Security Concepts |
| **Exam Objective** | 1.4 - Explain the importance of using appropriate cryptographic solutions |
| **Status** | ✅ Complete |
| **Completed By** | Robert Preshyl |
| **Completion Date** | January 31, 2026 |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
