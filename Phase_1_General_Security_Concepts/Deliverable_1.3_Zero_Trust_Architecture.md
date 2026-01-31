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
| **Never Trust, Always Verify** | No implicit trust based on network location | All users (Turku HQ, Amsterdam, Austin, Kigali, remote) must authenticate regardless of location. VPN access ≠ automatic trust. IoT devices on customer networks treated same as external devices. |
| **Assume Breach** | Design as if attackers are already inside | With 827+ IoT devices on customer networks and expanding to 4 global offices, assume at least one endpoint is compromised. Design controls to prevent lateral movement even if perimeter is breached. |
| **Verify Explicitly** | Authenticate and authorize every request | Users: Azure AD + MFA for every session. IoT devices: X.509 certificate validation on every message. Services: OAuth 2.0 tokens with short expiry (15 min). No persistent trust tokens. |
| **Least Privilege Access** | Grant minimum necessary permissions | Contractors = access only to specific projects, revoked after contract. Kigali support staff = only customer tickets assigned to them. Temps = read-only by default. Time-boxed elevated permissions. |
| **Microsegmentation** | Isolate resources into secure zones | IoT/OT VLAN cannot reach corporate VLAN. R&D air-gapped network physically isolated. Critical systems (DC, DB) in separate segments with firewall rules. Customer data isolated per region (GDPR). |

## A.2 Zero Trust Maturity Assessment

Assess NordicShield's current state against Zero Trust maturity:

| Domain | Traditional (Current?) | Advanced | Optimal | Current State | Target State |
|--------|---------------------|----------|---------|---------------|--------------|
| **Identity** | Static passwords | MFA, SSO | Continuous auth | Traditional - Only M365 has MFA; VPN/AWS use passwords | Advanced - Universal MFA + conditional access (12-18 months) |
| **Devices** | Domain-joined only | MDM enrolled | Real-time posture | Traditional - AD-joined only; no BYOD policy; no IoT device management | Advanced - Intune MDM + compliance checks (12 months) |
| **Networks** | Perimeter-based | Segmented | Microsegmented | Traditional+ - VLANs exist but not enforced; VPN = full access | Advanced - Micro-segmentation + ZTNA (18-24 months) |
| **Applications** | Internal/External | ZTNA/SDP | Full SASE | Traditional - VPN for internal apps; cloud apps use internet | Advanced - ZTNA + Cloud App Security (18 months) |
| **Data** | Location-based | DLP | Data-centric | Traditional - No DLP; data classification not enforced | Advanced - DLP + data labels (12 months) |

---

# SECTION B: CURRENT ARCHITECTURE ANALYSIS

## B.1 Current Trust Relationships

Identify implicit trust in the current environment:

| Trust Relationship | Current State | Risk | Zero Trust Approach |
|--------------------|---------------|------|---------------------|
| On-premises network = trusted | Yes - Being on Turku LAN VLAN-10 (10.20.10.0/24) grants access to file servers, internal apps | High - Compromised laptop = lateral movement | Require re-authentication for each application; implement microsegmentation |
| VPN = full network access | Yes - FortiClient VPN grants full access to internal network (10.20.0.0/16) | High - Stolen VPN credentials = full breach | Replace VPN with ZTNA; grant access only to specific apps, not  entire network |
| IoT VLAN = isolated | Partial - VLAN-30 (10.20.30.0/24) exists but ACLs not strictly enforced | Critical - IoT breach could reach corporate systems | Enforce strict firewall rules; IoT devices can only reach AWS IoT Core endpoints |
| Cloud services = external | AWS/Azure accessed via public internet with IAM/Azure AD auth | Medium - Proper identity controls but no network-level enforcement | Implement private endpoints (AWS PrivateLink, Azure Private Link); enforce conditional access |
| Partner connections | No formal partner access currently; ad-hoc SSH keys for consultants | High - Unmanaged access creates audit gap | Implement partner ZTNA with JIT (Just-In-Time) access; revoke after project |

## B.2 Current Identity Architecture

| Component | Current Implementation | Limitations |
|-----------|----------------------|-------------|
| Directory Service | Azure AD (hybrid with on-prem AD) | On-prem AD still required for legacy apps; password hash sync creates risk |
| Authentication | Azure AD MFA (M365 only); passwords elsewhere | VPN, AWS Console, GitHub, internal apps lack MFA - credential stuffing risk |
| SSO | Azure AD SSO for M365, Salesforce, Workday, NetSuite | 15+ other apps require separate credentials; no central visibility |
| Service Accounts | Local service accounts in AD; AWS IAM users for services | Service accounts use static passwords; no rotation policy; overprivileged |
| IoT Identity | X.509 certificates (AWS IoT Core) | Manual certificate enrollment; no automated renewal; 827 devices difficult to manage |
| Privileged Access | Local admin accounts; AWS root account shared | No PAM solution; privileged passwords stored in Excel file; no session recording |

## B.3 Current Network Architecture

```
## Current Network Architecture (Turku HQ-centric)

Turku HQ:
- Corporate VLAN (VLAN-10: 10.20.10.0/24): User workstations, printers, conference room systems
- IoT/OT VLAN (VLAN-30: 10.20.30.0/24): IoT gateways, test sensors, OT controllers
- Guest VLAN (VLAN-40: 10.20.40.0/24): Visitor WiFi, BYOD (isolated, internet only)
- Server VLAN (VLAN-20: 10.20.20.0/24): Domain Controllers, file server, database
- Management VLAN (VLAN-99: 10.20.99.0/24): Network equipment, IPMI/iLO
- DMZ (10.20.100.0/24): External-facing web server (rarely used)

Cloud (AWS eu-north-1 Stockholm):
- VPC structure: Production VPC (10.50.0.0/16), DR VPC in eu-west-1 (10.60.0.0/16)
- Connectivity to on-prem: Site-to-site VPN (FortiGate to AWS VGW)
- IoT devices connect directly to AWS IoT Core endpoints via internet (TLS 1.3)

New Offices (Planned 2026):
- Amsterdam: Will use local internet + ZTNA (no site-to-site VPN planned)
- Austin: Will use local internet + ZTNA (no site-to-site VPN planned)  
- Kigali: Small office, internet-only access, concerns about reliability

Remote Workers:
- FortiClient VPN to Turku FortiGate firewall
- Once connected, full access to internal 10.20.0.0/16 network
```

---

# SECTION C: ZERO TRUST PILLARS FOR NORDICSHIELD

## C.1 Identity Pillar

### C.1.1 User Identity

| Requirement | Current State | Target State | Implementation |
|-------------|---------------|--------------|----------------|
| Strong MFA for all users | M365 only (Duo MFA) | All systems require MFA | Deploy Duo Universal Prompt to VPN, AWS, GitHub, internal apps - Priority 1 (Q2 2026) |
| Conditional Access policies | None configured | Device trust + location + risk-based | Azure AD Conditional Access: Block unmanaged devices, non-compliant devices, risky sign-ins |
| Risk-based authentication | None | Adaptive MFA based on risk score | Azure AD Identity Protection: Require MFA for medium+ risk; block high-risk sign-ins |
| Privileged Identity Management | Permanent admin rights | JIT elevation with approval | Azure AD PIM: Time-boxed (4-hour) admin access with manager approval; eliminate standing privileges |
| Identity governance | Annual access reviews only | Quarterly reviews + lifecycle automation | Implement access packages; auto-revoke access on termination; quarterly certification campaigns |

### C.1.2 Device Identity

| Device Type | Current Auth Method | Target Auth Method | Justification |
|-------------|--------------------|--------------------|---------------|
| Corporate laptops | Domain join (Kerberos) | Azure AD join + device certificate | Passwordless auth; certificate issued by internal CA during Intune enrollment; device identity independent of user |
| BYOD devices | Not allowed | MAM-enrolled with app-based cert | Microsoft Intune MAM; app-level certificate for M365/Salesforce access only; device not fully managed |
| IoT sensors | X.509 certs (AWS IoT Core) | X.509 certificates (automated renewal) | Continue current approach but automate cert issuance via AWS IoT Device Management; 1-year cert validity with 90-day renewal |
| IoT gateways | Static credentials (some) | Mutual TLS + TPM-backed keys | NS-GW-1000 devices get TPM-stored certificates; mutual TLS to AWS IoT Core; gateway identity validated before sensor data accepted |
| Mobile devices | Username/password | Intune MDM + device compliance | Corporate-owned mobiles must be MDM-enrolled; compliance policy checks OS version, encryption, jailbreak status |

### C.1.3 Service/Application Identity

| Service Type | Current Auth | Target Auth | Notes |
|--------------|--------------|-------------|-------|
| On-prem services | Service accounts (AD) | Managed identities (Azure Arc-enabled | Eliminate service account passwords; Azure Arc extends managed identity to on-prem VMs; rotate credentials automatically |
| AWS services | IAM users (static keys) | IAM roles (AssumeRole) | EC2 instances use instance profiles; Lambda uses execution roles; eliminate long-term access keys; keys auto-rotated by AWS |
| SaaS applications | Mix of passwords + SAML | SAML/OIDC federation via Azure AD | Centralize all SaaS auth through Azure AD; single IDP = single audit trail; conditional access policies apply uniformly |
| Internal APIs | Basic auth (username/password) | OAuth 2.0 + mTLS | Backend APIs require OAuth 2.0 bearer token (15-min expiry) + client certificate; API gateway validates both; prevents replay attacks |

## C.2 Device Pillar

### C.2.1 Device Trust Requirements

| Device Category | Compliance Requirements | Verification Method |
|-----------------|------------------------|---------------------|
| Corporate Windows | Patch level: Win 10/11 with updates <30 days old; EDR: CrowdStrike agent running; Encryption: BitLocker enabled; Firewall: Windows Firewall on | Microsoft Intune compliance policy checks + CrowdStrike device compliance; non-compliant devices blocked by Conditional Access |
| Corporate Mac | Patch level: macOS <3 versions behind current; EDR: CrowdStrike agent running; Encryption: FileVault enabled; Firewall: macOS firewall enabled | Intune for macOS compliance policy; CrowdStrike integration reports agent health |
| Corporate Linux | Patch level: Ubuntu LTS with unattended-upgrades enabled; EDR: CrowdStrike or Wazuh agent; Encryption: LUKS full-disk encryption | Custom compliance script reports to Intune; Wazuh SCA (Security Configuration Assessment) validates hardening |
| BYOD | Minimum: OS up to date (Android 12+, iOS 15+); App-level encryption; Passcode required (6+ digits); No jailbreak/root | Microsoft Intune MAM; compliance check before granting app access; device itself not managed but app container is |
| IoT Sensors | Firmware version tracked; Device certificate valid; Heartbeat within 5 minutes; No physical tampering detected | AWS IoT Device Defender detects anomalies; fleet monitoring dashboard tracks compliance; alerts on cert expiry <30 days |
| IoT Controllers | Same as sensors + FIM (File Integrity Monitoring) validation; Configuration matches baseline | Wazuh FIM agent on NS-GW-1000 gateway devices; CIS benchmark compliance checked daily; deviations trigger alert |

### C.2.2 Device Posture Assessment

```
## Device Posture Check Workflow (Pre-Access Validation)

Before access is granted, verify:
1. Device identity: Certificate present and valid (not expired, not revoked)
2. Device compliance: Intune compliance policy passes (encryption, EDR, patches, firewall)
3. Device health: CrowdStrike threat score acceptable (<50); no active malware detections
4. Device location: Geolocation reasonable (not from sanctioned country; alert if location jumps >1000km in <1 hour)
5. Device risk: Azure AD device risk level = Low (no suspicious activity reported by UEBA)

If device fails posture check:
- Action 1: Block access to corporate resources (Azure AD Conditional Access deny)
- Action 2: Notify user via email/SMS with remediation steps (e.g., "Update Windows" or "Enable BitLocker")
- Action 3: Create ticket for IT helpdesk if device cannot self-remediate (e.g., hardware TPM failure)
- Action 4: Log event to SIEM for compliance audit trail
- Action 5: Allow limited access to remediation resources (Intune Company Portal, patch server) but nothing else
```

## C.3 Network Pillar

### C.3.1 Microsegmentation Design

| Segment | Purpose | Allowed Inbound | Allowed Outbound | Isolation Level |
|---------|---------|-----------------|------------------|-----------------|
| Corporate Users | General business | From: Nothing (users initiate all connections) | To: Internet (443/80), SaaS apps, Server VLAN (SMB, RDP with auth) | Medium |
| R&D Systems | Development | From: R&D users only (cert-based auth) | To: GitHub, Package repos (npm, PyPI), NO production access | High - Sensitive IP |
| IoT Sensors | Data collection | From: AWS IoT Core only (MQTT port 8883) | To: AWS IoT Core only (TLS 1.3), NO internet, NO corporate VLAN | High - Safety critical |
| IoT Controllers | Operational control | From: Authorized admins (JIT access), IoT Sensors (data flow) | To: IoT Sensors (control commands), AWS (telemetry), NO corporate VLAN | Maximum - Safety + OT risk |
| Server VLAN | Core services | From: Corporate Users (auth required), Cloud (backups) | To: Internet (patches), Azure AD (auth), Corporate Users (responses) | High |
| Guest Network | Visitors | From: Nothing | To: Internet only (DNS, HTTP/HTTPS), NO internal networks | Isolated |

### C.3.2 Zero Trust Network Access (ZTNA) Design

Replace VPN with ZTNA for:

| Use Case | Current Solution | ZTNA Solution | Benefits |
|----------|-----------------|---------------|----------|
| Remote worker access | FortiClient VPN (full network access) | Cloudflare Access or Azure AD App Proxy | Access specific apps (email, Jira, GitHub), not entire network; per-app MFA; no client software potentially; better logging |
| Contractor access | VPN with AD account (expires manually) | ZTNA with time-boxed access | Automatic revocation after project end date; no network-level access; contractor can't browse internal network; audit trail per-app |
| New office connectivity | Site-to-site VPN planned | ZTNA from day 1 (no VPN) | Amsterdam/Austin/Kigali users access apps directly over internet; no single point of failure; scales better; lower latency; easier firewall management |
| Partner access | SSH keys, ad-hoc | ZTNA with JIT access request | Partner submits access request via portal; manager approves; access granted for 4 hours; session recorded; key auto-revoked; compliance-friendly |

### C.3.3 East-West Traffic Control

```
## East-West Traffic Control (Internal Lateral Movement Prevention)

Current state: 
- VLAN segmentation exists (Corporate, Server, IoT, Guest) but ACLs are permissive
- Once on Corporate VLAN, users can reach most Server VLAN resources
- No host-based firewall policies enforced (Windows Firewall often disabled by users)
- Lateral movement from one compromised workstation to another is trivial

Target state:
- Microsegmentation enforced at multiple layers (network, host, identity)
- Default deny posture: All east-west traffic blocked unless explicitly allowed
- Application-level segmentation: Access granted to specific apps/ports, not entire servers

Technologies to implement:
1. FortiGate internal segmentation firewall (ISFW) policies: Enforce strict ACLs between VLANs
2. Host-based firewall (Windows Firewall) via Group Policy: Enforce on all endpoints; block workstation-to-workstation traffic
3. Azure AD Conditional Access + App Proxy: Even internal apps require re-authentication
4. AWS Security Groups + NACLs: Microsegmentation in cloud; web tier cannot reach database directly
5. **NetBird mesh VPN**: Replace hub-and-spoke FortiGate VPN with peer-to-peer mesh network (100.64.0.0/16 overlay); automatic NAT traversal; WireGuard-based encryption; integrated with Azure AD or ZITADEL for identity-first access (see Section D.3 for reference implementation)
6. Service mesh (future): Istio/Linkerd for cloud workloads - mTLS between all services
```

## C.4 Application Pillar

### C.4.1 Application-Level Controls

| Application | Access Method | Authentication | Authorization | Data Protection |
|-------------|--------------|----------------|---------------|-----------------|
| NordicSense Platform | HTTPS (public internet) | Azure AD SAML + MFA | RBAC (Customer Admin, Viewer, Support) | TLS 1.3 in transit; data encrypted at rest in AWS S3 (KMS); API rate limiting |
| GitHub Enterprise | HTTPS | GitHub SSO (Azure AD) + MFA | Repo-level permissions, branch protection | Code scanning enabled; secrets detection; TLS 1.3; signed commits enforced |
| Salesforce | HTTPS | Salesforce SSO (Azure AD) + MFA | Profiles & Permission Sets | Shield Platform Encryption; IP allow listing; session timeout 2 hours |
| Internal ERP (NetSuite) | HTTPS | NetSuite SSO (Azure AD) + MFA | Role-based (Finance, Manager, Employee) | TLS 1.2; 2FA for privileged roles; audit trail enabled; data residency=EU |
| AWS Console | HTTPS | IAM + MFA (hardware token) | IAM policies (least privilege) | CloudTrail logging; GuardDuty threat detection; SCPs at org level; session timeout 1 hour |

### C.4.2 API Security

| API Type | Current Security | Zero Trust Controls |
|----------|-----------------|---------------------|
| Customer-facing APIs | TLS 1.3; API key auth; no rate limiting | AWS API Gateway with rate limiting (1000 req/min per customer); OAuth 2.0 bearer tokens (15-min expiry); WAF rules (SQL injection, XSS); DDoS protection (Shield) |
| Internal APIs | Basic auth (username/password) | Service-to-service mTLS; OAuth 2.0 client credentials flow; JWT tokens with short expiry; API gateway enforces auth + logging |
| IoT device APIs | X.509 certs (AWS IoT Core); MQTT TLS 1.3 | Continue current approach; add device attestation (TPM-based); implement message signing (verify integrity); anomaly detection (Device Defender) |
| Partner APIs | No formal partner API currently | When implemented: OAuth 2.0 with client credentials; partner-specific rate limits; dedicated VPC endpoint (PrivateLink); SLA tracking per partner; separate WAF rules |

## C.5 Data Pillar

### C.5.1 Data-Centric Security

| Data Type | Access Control | Encryption | DLP Policy | Monitoring |
|-----------|----------------|------------|------------|------------|
| PII (Employee/Customer) | RBAC: HR/Support only; MFA required | AES-256 at rest; TLS 1.3 in transit; field-level encryption (SSN, credit card) | Block external email with >10 PII records; alert on USB copy; block upload to personal cloud | SIEM alerts on bulk PII access; quarterly access reviews; UEBA detects anomalous access |
| Intellectual Property (Cooling Algorithm) | Physical: Air-gapped system; badge+PIN; Logical: Named users only (5 engineers) | AES-256 on encrypted drive; backups on tape in safe |禁止 (Prohibited) any network transfer; USB disabled; screen recording blocked | Manual audit log; video surveillance of R&D area; code review required for any changes |
| IoT Telemetry | RBAC: Customer sees own data only; multi-tenancy enforced | AES-256 in S3 (SSE-KMS); TLS 1.3 in transit | Alert on bulk download (>1GB in 1 hour); block non-EU data export (GDPR) | CloudWatch logs all data plane API calls; anomaly detection on access patterns; customer audit logs |
| Financial Data | RBAC: Finance team + auditors; dual approval for changes | TLS 1.2 in NetSuite; AES-256 at rest; audit trail immutable | Block screenshots of financial reports; alert on download of GL (General Ledger) data | NetSuite native audit trail; SIEM correlation with user behavior; quarterly SOC 2 audit review |

### C.5.2 Data Flow Controls

```
## Data Flow Controls (Ingress/Egress Validation)

Data entering the environment:
- IoT sensors → Gateway → AWS: Sensor sends MQTT message over TLS 1.3 to NS-GW-1000 gateway → Gateway validates device cert + message signature → Gateway forwards to AWS IoT Core → Data lands in Timestream (encrypted) → Lambda validates schema before processing
- Customer portal submissions: User submits ticket via web portal → WAF inspects for attacks → Azure AD authenticates user → Data validated (sanitized for XSS/SQL injection) → Stored in Jira → Email notification sent to support team
- Partner data exchanges: Partner uploads file to SFTP → Partner cert validated → File scanned for malware (ClamAV) → Data imported to NetSuite after manual review → Audit log created

Data leaving the environment:
- Customer reports: Customer requests report via API → Verify customer identity (OAuth token) → Check entitlement (only their data) → Generate PDF report → Watermark with customer ID + timestamp → Upload to S3 pre-signed URL (expires in 24 hours) → Email link to customer
- Partner integrations: Scheduled batch export → Data filtered to partner's scope → PGP encryption with partner's public key → SFTP upload to partner server → Confirmation receipt logged → Data deleted after 7 days
- Employee exports: Employee exports data from internal app → DLP checks data classification → If CONFIDENTIAL+, require manager approval → Log export event → Watermark file with employee name → Email alert to security team if >1000 records exported
```

---

# SECTION D: GLOBAL EXPANSION ZERO TRUST

## D.1 New Office Zero Trust Requirements

Each new office should be "born Zero Trust":

| Office | Network Approach | Identity Integration | Local Services | WAN Connectivity |
|--------|-----------------|---------------------|----------------|------------------|
| Amsterdam | Born Zero Trust - No VPN; internet-only with ZTNA | Azure AD (cloud-only); no local AD | No local servers; all services in cloud or Turku | SD-WAN (CloudFlare) or direct internet; users access apps via ZTNA; no site-to-site VPN |
| Austin | Born Zero Trust - Cloud-first architecture | Azure AD (cloud-only); federated with Workday for HR | No local servers; everything in AWS us-east-1 or SaaS | Direct internet; resilient ISP; ZTNA for all app access; no traditional WAN |
| Kigali | Hybrid - Internet primary with satellite backup | Azure AD (cloud-only); limited on-prem due to connectivity | Local NAS for ticket attachments (large files); everything else cloud | Primary: local ISP (fiber if available); Backup: Starlink for redundancy; ZTNA; expect higher latency |

## D.2 Cross-Office Access

| Access Need | Traditional Approach | Zero Trust Approach |
|-------------|---------------------|---------------------|
| Amsterdam accessing Turku apps | Site-to-site VPN with full network access | ZTNA (Cloudflare Access): Amsterdam users authenticate to specific apps (file server, internal wiki); no network-level access; per-app MFA; conditional access based on device compliance |
| Austin accessing AWS resources | VPN to Turku, then hairpin to AWS | Direct access from Austin to AWS via IAM roles; no VPN needed; users authenticate with Azure AD (federated to AWS IAM Identity Center); session limited to assigned AWS accounts only |
| Kigali accessing support systems | VPN (high latency, unreliable) | ZTNA to Jira/Salesforce directly over internet; application-level security; works even if VPN is down; lower latency by avoiding VPN hairpin through Turku |
| Any office accessing SaaS | Direct internet access (M365, Salesforce, etc.) | Continue current approach (correct one); SaaS accessed directly with Conditional Access enforcing device compliance + MFA; no need to backhaul through Turku |

## D.3 Reference Implementation: NetBird VPN + Kasm Workspaces Zero Trust Lab

### D.3.1 Implementation Overview

To validate Zero Trust Network Access (ZTNA) concepts before full NordicShield deployment, a production-ready Zero Trust architecture was prototyped using **NetBird VPN**, **Kasm Workspaces**, and **ZITADEL** Identity & Access Management. This implementation demonstrates the "Born Zero Trust" approach recommended for Amsterdam, Austin, and Kigali offices.

**Architecture Components:**

![Zero Trust Architecture - NetBird VPN + Kasm Workspaces + ZITADEL](images/netbird-kasm-zitadel-architecture.png)

*Figure D.3.1: Zero Trust Access Architecture using identity-based authentication, private VPN overlay (100.64.0.0/16), and containerized workspace delivery*

**Key Security Principles Implemented:**

| Zero Trust Principle | Implementation |
|---------------------|----------------|
| **Never Trust, Always Verify** | All users authenticate via ZITADEL SSO before accessing NetBird VPN; no implicit trust based on network location |
| **Identity-First Authentication** | ZITADEL provides SSO + MFA; role-based access control (RBAC) determines which workspaces users can access |
| **Microsegmentation** | NetBird creates private overlay network (100.64.0.0/16); Kasm server has no public SSH or web exposure; only VPN-authenticated users can reach Kasm web interface |
| **Least Privilege** | Users granted access only to specific containerized desktops/applications; principle of least privilege enforced via ZITADEL policies |
| **Assume Breach** | Even if user device is compromised, attacker cannot access Kasm server without valid ZITADEL SSO authentication + NetBird VPN enrollment |
| **Continuous Authorization** | NetBird VPN can revoke network access in real-time; ZITADEL can revoke SSO session; Kasm enforces session timeouts |

### D.3.2 Technical Architecture

```
Access Flow:

1. User navigates to ZITADEL authentication portal
2. ZITADEL authenticates user (SSO + optional MFA)
3. Upon successful authentication, user gains access to NetBird network enrollment
4. User installs NetBird client and joins private mesh network (100.64.0.0/16)
5. User can now reach Kasm Workspaces server at private IP (100.64.x.x)
6. Kasm enforces ZITADEL SSO for workspace access (second authentication layer)
7. User accesses containerized desktop/application via browser-based streaming
8. Session isolated in ephemeral Docker container (destroyed after logout)

Security Boundaries:
- No public SSH access to Kasm server (SSH disabled on public interface)
- No direct internet access to Kasm web interface (firewall rules block public 443)
- VPN-only access enforced via NetBird overlay network
- All connections encrypted (TLS 1.3 for web, WireGuard for VPN)
- Audit logging at every layer (ZITADEL auth logs, NetBird connection logs, Kasm session logs)
```

### D.3.3 Technology Stack

| Component | Technology | Purpose | NordicShield Applicability |
|-----------|-----------|---------|---------------------------|
| **Identity Provider** | ZITADEL (open-source IAM) | SSO, MFA, RBAC, user lifecycle management | Alternative to Azure AD for specific use cases; demonstrates OIDC/SAML integration; consider for partner/contractor access where Azure AD licensing prohibitive |
| **VPN Overlay** | NetBird (WireGuard-based mesh VPN) | Private network overlay (100.64.0.0/16); client-to-site and site-to-site connectivity; automatic NAT traversal | **Recommended for NordicShield new offices**: Replace traditional site-to-site VPN with mesh VPN; lower latency than hub-and-spoke VPN; automatic failover; scales to thousands of endpoints |
| **Secure Workspaces** | Kasm Workspaces (containerized VDI) | Browser-based access to containerized desktops and applications; ephemeral sessions; no data persists on user device | **Use case for NordicShield**: Secure contractor access (contractors work in isolated containers, cannot exfiltrate data), secure access to legacy apps (wrap legacy apps in Kasm container), BYOD support (users access corporate apps via browser without installing software) |
| **SIEM Integration** | NetBird → Wazuh/Splunk | VPN connection logs, authentication events, anomaly detection | **Already implemented**: [NetBird-SIEM Integration](https://github.com/robertpreshyl/allyship-securitylab-VpNSIEM) - ingest NetBird logs into Wazuh for correlation with other security events |

### D.3.4 Demonstration & Documentation

**Video Demonstration:**
📺 [Zero Trust Remote Workspace Architecture with Kasm, NetBird & ZITADEL (Secure Browser-Based Access)](https://youtu.be/1rHPworhH1k?si=D53YsjCsHPILWMOl)

**Key Highlights from Demo:**
- User onboarding workflow (ZITADEL SSO → NetBird VPN enrollment → Kasm workspace access)
- Automated provisioning (new NetBird users auto-approved via ZITADEL policies)
- Containerized isolation (user sessions run in ephemeral Docker containers)
- Audit logging across all layers (authentication, VPN connections, workspace sessions)
- Access revocation (demonstrate real-time user lockout at identity, network, and application layers)

**Source Code & Integration:**
🔗 [NetBird-SIEM Integration GitHub Repository](https://github.com/robertpreshyl/allyship-securitylab-VpNSIEM)
- NetBird VPN logs ingested into Wazuh SIEM
- Custom Wazuh rules for NetBird authentication failures, unusual connection patterns
- Dashboard showing VPN connections by user, time, geo-location
- Alert workflows for anomalous VPN usage (connection from unexpected country, multiple simultaneous connections)

### D.3.5 Lessons Learned & NordicShield Recommendations

| Lesson Learned | NordicShield Application |
|----------------|-------------------------|
| **NetBird over traditional VPN**: NetBird's mesh architecture eliminates VPN hairpinning (Amsterdam → Turku → AWS becomes Amsterdam → AWS direct). Latency reduced 60% in testing. | **Recommendation**: Deploy NetBird for new offices (Amsterdam, Austin, Kigali) instead of extending FortiGate VPN. Pilot with 10 remote workers by Month 3, cutover fully by Month 9. |
| **Identity-first access**: ZITADEL SSO worked seamlessly with NetBird and Kasm. Users authenticate once, access multiple resources. | **Recommendation**: Continue with Azure AD as primary IDP (existing investment), but consider ZITADEL or similar for partner/contractor access where Azure AD B2B licensing cost-prohibitive. |
| **Container isolation**: Kasm's ephemeral containers prevented data persistence on user endpoints. Contractors worked on sensitive projects without data exfiltration risk. | **Recommendation**: Use Kasm for high-risk contractor scenarios (firmware development, customer-facing support accessing customer data). Contractor session ends → container destroyed → no data remnants. |
| **SIEM integration critical**: NetBird logs integrated into Wazuh provided visibility into VPN access patterns. Detected test attack (brute force VPN enrollment attempts). | **Recommendation**: Extend Wazuh deployment to ingest NetBird logs (reference implementation already exists). Correlate VPN activity with endpoint alerts (CrowdStrike) and AWS activity (CloudTrail). |
| **No public attack surface**: Disabling SSH and public web access eliminated 90% of attack surface. Only VPN-authenticated users could reach Kasm server. | **Recommendation**: Apply same principle to new offices—no public RDP/SSH to any server. All access via NetBird VPN + Azure AD authentication. Amsterdam/Austin/Kigali offices have zero public inbound firewall rules. |
| **Automatic NAT traversal**: NetBird worked seamlessly behind NAT/firewalls without firewall rule changes. | **Recommendation**: Critical for Kigali office (limited control over local ISP firewall). NetBird will work even if Kigali ISP blocks VPN protocols (uses HTTPS/WebSockets as fallback). |

### D.3.6 Cost-Benefit Analysis vs Traditional VPN

| Factor | Traditional VPN (FortiGate) | NetBird Mesh VPN | Winner |
|--------|----------------------------|------------------|--------|
| **Licensing cost** | €15K initial + €3K/year (50-user FortiClient EMS license) | Open-source self-hosted: €0; Managed cloud: €8/user/month (€480/month for 60 users = €5,760/year) | NetBird (€9K savings in Year 1) |
| **Latency** | Hub-and-spoke forces hairpinning (Amsterdam → Turku → AWS = 40ms + 25ms = 65ms) | Mesh allows direct paths (Amsterdam → AWS = 25ms) | NetBird (40ms faster = 60% reduction) |
| **Reliability** | Single point of failure (Turku FortiGate); if Turku internet down, all remote workers disconnected | Mesh network self-heals; if one node down, traffic re-routes automatically | NetBird (no SPOF) |
| **Scalability** | FortiGate 200F supports 500 VPN tunnels (will need upgrade by 2027 for global expansion) | NetBird scales to 10,000+ nodes (no hardware bottleneck) | NetBird (future-proof) |
| **NAT traversal** | Requires UDP 500/4500 open; often blocked by hotel/airport WiFi | Built-in NAT traversal via STUN/TURN; works on any network | NetBird (better remote worker experience) |
| **Operational complexity** | Centralized config (all VPN rules in FortiGate); change requires CAB approval + maintenance window | Distributed config (users auto-enroll, policies enforced at client); no scheduled downtime | NetBird (faster changes, less downtime) |

**Net Benefit**: Replace FortiGate VPN with NetBird for new offices → Save €9K in Year 1, reduce latency 60%, eliminate single point of failure, improve remote worker experience, scale to 500+ users without hardware upgrade.

---

# SECTION E: IOT ZERO TRUST ARCHITECTURE

## E.1 IoT-Specific Challenges

| Challenge | Description | Zero Trust Solution |
|-----------|-------------|---------------------|
| Limited compute on devices | Sensors (NS-TEMP-200) have 256KB RAM, cannot run complex auth protocols or crypto | Gateway-based auth: Sensors auth to gateway using lightweight cert validation; gateway does heavy lifting (mTLS to AWS, logging, anomaly detection) |
| Long device lifecycles | Devices deployed 5-10+ years; cannot easily replace; firmware updates risky | Certificate rotation automated via AWS IoT Device Management; 1-year cert validity with 90-day auto-renewal; cert revocation handled by gateway; firmware signing enforced |
| Difficult patching | Customer sites require downtime for patching; SLA penalties if cooling disrupted | Implement blue/green deployment for gateways; sensors updated in rolling fashion (10% per day); automated rollback if anomalies detected; phased rollouts |
| Physical access risks | Deployed in customer data centers; physical tampering possible | Tamper detection: Sensors have tamper switch; gateway detects when sensor case opened; TPM (Trusted Platform Module) in gateways stores private keys (hardware-backed); device attestation validates integrity |
| Scale (827+ devices) | Manual device onboarding doesn't scale | Automated onboarding: Zero-touch provisioning via AWS IoT Device Management; bulk cert generation; factory pre-provisioning; automated fleet indexing and tagging |

## E.2 IoT Zero Trust Design

```
## IoT Zero Trust Architecture (Defense-in-Depth)

Device Layer (NS-TEMP-200 sensors, NS-HUMI-150 humidity sensors):
- Device identity: X.509 certificate uniquely identifies each sensor; certificate DN includes device serial number, customer ID, deployment site
- Device attestation: Sensor sends boot attestation message (TPM-signed) proving firmware integrity; gateway validates before accepting data
- Firmware integrity: Firmware signed with NordicShield private key; sensor validates signature before installing update; rollback to last-known-good if boot fails

Gateway Layer (NS-GW-1000 IoT gateways @ customer sites):
- Authentication: Gateway uses mutual TLS to AWS IoT Core; validates sensor certificates before accepting data; revoked certs checked against CRL
- Traffic inspection: Gateway inspects MQTT messages for schema compliance; validates sensor data ranges (temp: -40°C to +85°C); anomaly detection for unusual patterns
- Protocol translation: Sensors use lightweight proprietary protocol locally; gateway translates to MQTT/TLS for cloud; local buffer if WAN down (24 hours capacity)
- File Integrity Monitoring: Wazuh FIM agent on gateway detects unauthorized config/file changes; alerts to SIEM; auto-quarantine if tampering detected

Cloud Layer (AWS IoT Core, Timestream, S3):
- Ingestion authentication: AWS IoT Core validates device certificate against IoT policy; enforces per-device topic policies (device can only publish to its own topic)
- Data validation: IoT Rules Engine validates message schema; Lambda function checks business logic (e.g., temperature delta <10°C per minute); rejects anomalous data
- Access control: Customer can only query their own data (IAM policy + Cognito identity pool); RLS (Row-Level Security) in Timestream enforces multi-tenancy; API Gateway validates OAuth token
- Audit logging: All data plane operations logged to CloudTrail; S3 access logs enabled; Timestream query logs retained 1 year; anomaly detection via GuardDuty
```

## E.3 Client Site Security

For IoT deployments at customer facilities:

| Concern | Control | Implementation |
|---------|---------|----------------|
| Sensors on customer networks | Network isolation | Sensors connect ONLY to NS-GW-1000 gateway (local); customer VLAN isolates IoT devices from their corporate network; gateway firewalled to allow ONLY outbound MQTT to AWS IoT Core |
| Data transmission to NordicShield | Encrypted tunnels | TLS 1.3 with Perfect Forward Secrecy (PFS); mutual TLS (gateway cert + AWS cert); no data sent in clear; customer can inspect/monitor encrypted traffic for their compliance |
| Remote management access | Zero Standing Privileges (ZSP) | No persistent SSH access to gateways; NordicShield engineer requests access via portal → customer approves → 4-hour JIT access granted → session recorded → auto-logout; MFA required |
| Physical security | Tamper-evident hardware | Gateway chassis has tamper-evident seals; customer notified if seal broken; TPM detects firmware tampering; gateway in locked rack at customer site (customer controls physical access) |

---

# SECTION F: IMPLEMENTATION ROADMAP

## F.1 Phase 1: Foundation (Months 1-3)

| Activity | Priority | Owner | Dependencies |
|----------|----------|-------|--------------|
| Deploy universal MFA (Duo) to VPN, AWS, GitHub, internal apps | P1 | IT Director | Duo procurement; user training |
| Implement Azure AD Conditional Access policies (block non-compliant devices) | P1 | Cloud Architect | Intune MDM rollout; device compliance policies defined |
| Complete asset inventory (all devices, users, apps) | P1 | Security Analyst | Discovery tool (Lansweeper); CMDB update |
| Define data classification policy and labels | P1 | CISO + Legal | Review GDPR/NIS2 requirements; train staff |
| Deploy Intune MDM to all corporate endpoints (Windows, Mac, mobile) | P1 | IT Operations | Intune licenses; pilot with 20% of users first |
| Establish identity governance (Azure AD entitlements) | P2 | Identity Admin | Define role-based access packages; HR system integration |

## F.2 Phase 2: Core Capabilities (Months 4-6)

| Activity | Priority | Owner | Dependencies |
|----------|----------|-------|--------------|
| Implement risk-based Conditional Access (Azure AD Identity Protection) | P1 | Cloud Architect | Phase 1 Conditional Access baseline; risk score tuning |
| Deploy microsegmentation (enforce VLAN ACLs on FortiGate) | P1 | Network Engineer | Document traffic flows; plan maintenance window; pilot on Server VLAN first |
| Deploy DLP solution (endpoint, email, cloud) | P1 | Security Engineer | Data classification complete; DLP policies defined; Trellix or Purview procurement |
| Implement PAM (Privileged Access Management) | P2 | Security Admin | Azure AD PIM for cloud; CyberArk for on-prem considered; define privileged roles |
| Deploy SIEM (complete Wazuh rollout to all servers) | P2 | SOC Lead | Phase 1 asset inventory complete; define log sources and retention |
| Establish SOC processes (24/7 monitoring, runbooks) | P2 | CISO | SIEM operational; hire or outsource SOC analysts |

## F.3 Phase 3: Advanced (Months 7-12)

| Activity | Priority | Owner | Dependencies |
|----------|----------|-------|--------------|
| Deploy ZTNA solution (replace VPN) | P1 | Network Architect | **Proof-of-concept complete**: NetBird VPN + ZITADEL pilot validated (see Section D.3); production deployment: 10 remote workers pilot Month 3, full cutover Month 9; evaluate Cloudflare Access vs NetBird vs Azure AD App Proxy |
| Implement IoT device attestation (TPM-backed keys) | P1 | IoT Platform Lead | TPM integration in NS-GW-1000 gateways; firmware update rollout; test at 5 customer sites first |
| Deploy east-west traffic controls (host-based firewalls via GPO) | P2 | Systems Admin | Windows Firewall policies defined; test on 10% of endpoints; monitor for breakage |
| Implement Zero Trust for new offices (Amsterdam, Austin, Kigali) | P2 | COO + IT Director | ZTNA operational; SD-WAN or direct internet procurement; local ISP contracts |
| Deploy service mesh in AWS (Istio for microservices mTLS) | P3 | DevOps Lead | Migrate apps to containers; Kubernetes training; gradual rollout to prod services |
| Implement continuous authentication (behavior-based) | P3 | Cloud Architect | Azure AD Conditional Access advanced features; UEBA tuning; false positive management |

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
| Identity governance | 4.6, 5.1 | Administrative |
| Data loss prevention | 1.2, 4.3 | Technical |
| Zero Trust Network Access (ZTNA) | 3.3, 4.4 | Technical |
| Privileged Access Management (PAM) | 4.6 | Technical/Administrative |
| Certificate-based authentication | 1.4, 4.6 | Technical |
| API security (OAuth 2.0, mTLS) | 3.1, 4.4 | Technical |

---

# SECTION H: EXECUTIVE SUMMARY

# SECTION H: EXECUTIVE SUMMARY

NordicShield Technologies' global expansion from one office to four geographically distributed locations, combined with a hybrid cloud architecture and 827+ IoT devices deployed at customer sites, creates a complex threat landscape incompatible with traditional perimeter-based security. The current architecture implicitly trusts users on the corporate network, grants VPN users full network access, and lacks granular control over east-west traffic—creating significant lateral movement risk if any endpoint is compromised.

**Why Zero Trust is Essential:**
With remote workers, partner contractors, and global offices, the traditional "inside = trusted" model fails. IoT devices on customer networks extend the attack surface beyond NordicShield's control. The planned Kigali office introduces infrastructure reliability concerns, while Amsterdam and Austin require cloud-first architectures. Zero Trust's "never trust, always verify" model addresses these challenges by authenticating every request, enforcing least privilege, and assuming breach.

**Current Architecture Gaps:**
- Identity: MFA only on M365; VPN, AWS, and GitHub use passwords
- Devices: No device compliance checks; BYOD not supported; 90% of endpoints unmanaged
- Network: VLAN segmentation exists but ACLs not enforced; VPN = full network access
- Applications: No risk-based authentication; no PAM for privileged accounts
- Data: No DLP; data classification not enforced; exfiltration undetected

**Proposed Zero Trust Pillars (Prioritization):**
1. **Identity** (Months 1-3): Universal MFA, Conditional Access, device compliance—foundation for all other controls
2. **Network** (Months 4-6): Microsegmentation, ZTNA to replace VPN, enforce strict ACLs
3. **Data** (Months 4-6): DLP deployment, enforce data classification, monitor exfiltration
4. **Applications** (Months 7-12): ZTNA for new offices, PAM for privileged access, API security
5. **IoT** (Months 7-12): Device attestation, automated cert rotation, anomaly detection

**Expected Benefits:**
- Security: Reduce lateral movement risk; detect compromised devices; prevent data exfiltration
- Compliance: Align with ISO 27001, GDPR, NIS2; audit-ready access logs; demonstrate due diligence
- Operational: Eliminate VPN complexity for new offices; scale security with business growth; improve user experience with SSO

**Timeline & Resources:**
- 12-month phased implementation (Months 1-3: Foundation, 4-6: Core, 7-12: Advanced)
- Estimated budget: €250K-€350K (licenses: €150K, consulting: €100K, internal labor: €100K)
- Key hires: Security engineer (full-time), SOC analysts (2 FTE or outsource)

**Success Metrics:**
- 100% MFA coverage by Month 3; 100% device compliance by Month 6
- Reduce VPN usage 80% by Month 9 (replaced with ZTNA)
- Zero lateral movement detections in SOC by Month 12
- ISO 27001 certification achieved by Month 18

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 1.3 - Zero Trust Architecture Plan |
| **Phase** | 1 - General Security Concepts |
| **Exam Objective** | 1.2 - Summarize fundamental security concepts |
| **Status** | ✅ Complete |
| **Completed By** | Robert Preshyl |
| **Completion Date** | January 31, 2026 |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
