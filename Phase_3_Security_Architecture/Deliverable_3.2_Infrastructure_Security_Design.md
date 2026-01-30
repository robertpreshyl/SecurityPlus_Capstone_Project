# Deliverable 3.2: Enterprise Infrastructure Security Design
## NordicShield Technologies Oy

---

```
╔══════════════════════════════════════════════════════════════════╗
║       ENTERPRISE INFRASTRUCTURE SECURITY DESIGN                  ║
║                                                                    ║
║  Document ID: INFRA-NS-2026-001                                   ║
║  Version: 1.0                                                     ║
║  Author: [YOUR NAME]                                              ║
║  Classification: Internal Use Only                                ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Document Purpose

This document defines the secure infrastructure design for NordicShield Technologies, covering network architecture, device hardening, secure protocols, and security appliance placement following Zero Trust principles.

---

## Instructions

1. Design each infrastructure component with security as a priority
2. Apply Zero Trust principles throughout
3. Complete all `[YOUR INPUT]` sections
4. Create network diagrams as specified
5. Reference Phase 2 threat analysis for context

---

# SECTION A: ZERO TRUST NETWORK ARCHITECTURE

## A.1 Zero Trust Principles Application

For each Zero Trust principle, describe how NordicShield will implement it:

| Principle | Implementation | Technologies |
|-----------|----------------|--------------|
| **Never Trust, Always Verify** | [YOUR INPUT - How will every access request be verified?] | [YOUR INPUT] |
| **Assume Breach** | [YOUR INPUT - How will you limit blast radius?] | [YOUR INPUT] |
| **Verify Explicitly** | [YOUR INPUT - What factors verify identity?] | [YOUR INPUT] |
| **Least Privilege Access** | [YOUR INPUT - How enforced?] | [YOUR INPUT] |
| **Inspect and Log Traffic** | [YOUR INPUT - What visibility mechanisms?] | [YOUR INPUT] |
| **Secure All Communications** | [YOUR INPUT - Encryption requirements] | [YOUR INPUT] |

## A.2 Zero Trust Architecture Components

### Identity Verification Layer

| Component | Function | Implementation |
|-----------|----------|----------------|
| Identity Provider | [YOUR INPUT] | [YOUR INPUT - Azure AD, Okta, etc.] |
| Multi-Factor Authentication | [YOUR INPUT] | [YOUR INPUT - FIDO2, TOTP, push] |
| Conditional Access | [YOUR INPUT] | [YOUR INPUT - Policies defined] |
| Device Trust | [YOUR INPUT] | [YOUR INPUT - Certificate, compliance check] |
| User Behavior Analytics | [YOUR INPUT] | [YOUR INPUT] |

### Network Verification Layer

| Component | Function | Implementation |
|-----------|----------|----------------|
| Software-Defined Perimeter | [YOUR INPUT] | [YOUR INPUT] |
| Zero Trust Network Access | [YOUR INPUT] | [YOUR INPUT - Zscaler, Palo Alto Prisma] |
| Microsegmentation | [YOUR INPUT] | [YOUR INPUT] |
| Encrypted DNS | [YOUR INPUT] | [YOUR INPUT - DoH, DoT] |
| Network Access Control | [YOUR INPUT] | [YOUR INPUT - 802.1X] |

### Application Verification Layer

| Component | Function | Implementation |
|-----------|----------|----------------|
| Application Proxy | [YOUR INPUT] | [YOUR INPUT] |
| API Gateway | [YOUR INPUT] | [YOUR INPUT] |
| Service Mesh | [YOUR INPUT] | [YOUR INPUT] |
| Web Application Firewall | [YOUR INPUT] | [YOUR INPUT] |

## A.3 Zero Trust Architecture Diagram

```
[YOUR INPUT - Design Zero Trust architecture for NordicShield]

┌─────────────────────────────────────────────────────────────────────────┐
│                    ZERO TRUST ARCHITECTURE                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  USERS/DEVICES                    POLICY ENGINE                          │
│  ┌─────────────────┐             ┌───────────────────┐                  │
│  │ Corporate Device│             │  Policy Decision  │                  │
│  │ BYOD            │             │  Point (PDP)      │                  │
│  │ IoT Device      │             │  [YOUR INPUT]     │                  │
│  │ Partner         │             └─────────┬─────────┘                  │
│  └────────┬────────┘                       │                            │
│           │                                │                            │
│           ▼                                ▼                            │
│  ┌────────────────────────────────────────────────────────────┐        │
│  │              POLICY ENFORCEMENT POINT (PEP)                 │        │
│  │  [YOUR INPUT - What enforces access decisions?]            │        │
│  │                                                            │        │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐   │        │
│  │  │ Identity │  │ Device   │  │ Network  │  │ App      │   │        │
│  │  │ Check    │  │ Check    │  │ Check    │  │ Check    │   │        │
│  │  │[INPUT]   │  │[INPUT]   │  │[INPUT]   │  │[INPUT]   │   │        │
│  │  └──────────┘  └──────────┘  └──────────┘  └──────────┘   │        │
│  └────────────────────────────────────────────────────────────┘        │
│                              │                                          │
│                              ▼                                          │
│  ┌─────────────────────────────────────────────────────────────┐       │
│  │                    PROTECTED RESOURCES                       │       │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐    │       │
│  │  │ Apps     │  │ Data     │  │ Services │  │ Systems  │    │       │
│  │  └──────────┘  └──────────┘  └──────────┘  └──────────┘    │       │
│  └─────────────────────────────────────────────────────────────┘       │
│                                                                          │
│  MONITORING & ANALYTICS                                                  │
│  ┌─────────────────────────────────────────────────────────────┐       │
│  │  [YOUR INPUT - SIEM, UEBA, threat analytics]               │       │
│  └─────────────────────────────────────────────────────────────┘       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

# SECTION B: NETWORK SEGMENTATION DESIGN

## B.1 Network Segmentation Strategy

### Segmentation Levels

| Level | Strategy | Implementation | Use Case |
|-------|----------|----------------|----------|
| **Macro-segmentation** | [YOUR INPUT - VLAN-based zones] | [YOUR INPUT] | [YOUR INPUT] |
| **Microsegmentation** | [YOUR INPUT - Workload isolation] | [YOUR INPUT] | [YOUR INPUT] |
| **Application Segmentation** | [YOUR INPUT - App-specific rules] | [YOUR INPUT] | [YOUR INPUT] |
| **User Segmentation** | [YOUR INPUT - Role-based network] | [YOUR INPUT] | [YOUR INPUT] |

### Network Zones

| Zone | Purpose | Security Level | Allowed Traffic |
|------|---------|----------------|-----------------|
| **DMZ** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - Inbound/Outbound rules] |
| **Corporate** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Server/Data Center** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **R&D** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **IoT/OT** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Guest** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Management** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## B.2 VLAN Design

| VLAN ID | Name | Purpose | Subnet | Security Controls |
|---------|------|---------|--------|-------------------|
| 10 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 20 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 30 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 40 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 50 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 100 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 200 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## B.3 Network Segmentation Diagram

```
[YOUR INPUT - Design network segmentation for Turku HQ]

                           ┌─────────────────┐
                           │    INTERNET     │
                           └────────┬────────┘
                                    │
                           ┌────────▼────────┐
                           │  EDGE FIREWALL  │
                           │  [YOUR INPUT]   │
                           └────────┬────────┘
                                    │
              ┌─────────────────────┼─────────────────────┐
              │                     │                     │
     ┌────────▼────────┐   ┌───────▼───────┐   ┌────────▼────────┐
     │      DMZ        │   │   CORPORATE   │   │   DATA CENTER   │
     │  VLAN: [INPUT]  │   │  VLAN: [INPUT]│   │   VLAN: [INPUT] │
     │                 │   │               │   │                 │
     │ ┌─────────────┐ │   │ ┌───────────┐ │   │ ┌─────────────┐ │
     │ │Web Servers  │ │   │ │Workstations│ │   │ │App Servers  │ │
     │ │[Controls]   │ │   │ │[Controls] │ │   │ │[Controls]   │ │
     │ └─────────────┘ │   │ └───────────┘ │   │ └─────────────┘ │
     │ ┌─────────────┐ │   │ ┌───────────┐ │   │ ┌─────────────┐ │
     │ │Email Gateway│ │   │ │VoIP       │ │   │ │Databases    │ │
     │ │[Controls]   │ │   │ │[Controls] │ │   │ │[Controls]   │ │
     │ └─────────────┘ │   │ └───────────┘ │   │ └─────────────┘ │
     └─────────────────┘   └───────────────┘   └─────────────────┘
              │                     │                     │
              └─────────────────────┼─────────────────────┘
                                    │
                           ┌────────▼────────┐
                           │INTERNAL FIREWALL│
                           │  [YOUR INPUT]   │
                           └────────┬────────┘
                                    │
              ┌─────────────────────┼─────────────────────┐
              │                     │                     │
     ┌────────▼────────┐   ┌───────▼───────┐   ┌────────▼────────┐
     │      R&D        │   │   IoT/OT      │   │   MANAGEMENT    │
     │  VLAN: [INPUT]  │   │  VLAN: [INPUT]│   │   VLAN: [INPUT] │
     │  [Controls]     │   │  [Controls]   │   │   [Controls]    │
     └─────────────────┘   └───────────────┘   └─────────────────┘

Inter-zone firewall rules:
1. [YOUR INPUT]
2. [YOUR INPUT]
3. [YOUR INPUT]
```

## B.4 Microsegmentation Policy Matrix

| Source | Destination | Protocol | Port | Action | Justification |
|--------|-------------|----------|------|--------|---------------|
| Corporate | DMZ Web | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| DMZ | Database | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT | IoT Gateway | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| R&D | Internet | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Any | Any | Any | Any | Deny | Default deny |

---

# SECTION C: FIREWALL ARCHITECTURE

## C.1 Firewall Types and Placement

| Firewall Type | Function | Placement | Product |
|---------------|----------|-----------|---------|
| **Next-Gen Firewall (NGFW)** | [YOUR INPUT - App awareness, IPS, TLS inspection] | [YOUR INPUT] | [YOUR INPUT] |
| **Web Application Firewall** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Database Firewall** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Host-Based Firewall** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Cloud Firewall** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## C.2 NGFW Configuration Standards

### Basic Configuration

| Setting | Configuration | Justification |
|---------|---------------|---------------|
| Default Policy | [YOUR INPUT - Deny all?] | [YOUR INPUT] |
| Logging Level | [YOUR INPUT] | [YOUR INPUT] |
| Time Synchronization | [YOUR INPUT] | [YOUR INPUT] |
| Management Access | [YOUR INPUT] | [YOUR INPUT] |
| Update Frequency | [YOUR INPUT] | [YOUR INPUT] |

### Advanced Features

| Feature | Configuration | Use Case |
|---------|---------------|----------|
| Application Control | [YOUR INPUT] | [YOUR INPUT] |
| User-ID Integration | [YOUR INPUT] | [YOUR INPUT] |
| TLS/SSL Inspection | [YOUR INPUT] | [YOUR INPUT] |
| Threat Prevention | [YOUR INPUT] | [YOUR INPUT] |
| URL Filtering | [YOUR INPUT] | [YOUR INPUT] |
| File Blocking | [YOUR INPUT] | [YOUR INPUT] |
| DNS Security | [YOUR INPUT] | [YOUR INPUT] |

## C.3 Firewall Ruleset Design

### Inbound Rules (Internet → DMZ)

| Rule # | Source | Destination | Service | Action | Logging | Notes |
|--------|--------|-------------|---------|--------|---------|-------|
| 1 | Any | Web Server | HTTPS/443 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 2 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 3 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 999 | Any | Any | Any | Deny | Yes | Default deny |

### Outbound Rules (Internal → Internet)

| Rule # | Source | Destination | Service | Action | Logging | Notes |
|--------|--------|-------------|---------|--------|---------|-------|
| 1 | Corporate | Any | HTTPS/443 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 2 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 3 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 999 | Any | Any | Any | Deny | Yes | Default deny |

### Inter-Zone Rules

| Rule # | Source Zone | Dest Zone | Service | Action | Justification |
|--------|-------------|-----------|---------|--------|---------------|
| 1 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 2 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 3 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## C.4 Firewall High Availability Design

```
[YOUR INPUT - Design HA firewall architecture]

                    ┌─────────────────┐
                    │    INTERNET     │
                    └────────┬────────┘
                             │
              ┌──────────────┴──────────────┐
              │                             │
     ┌────────▼────────┐          ┌────────▼────────┐
     │   FIREWALL A    │◄────────►│   FIREWALL B    │
     │   (Primary)     │ Heartbeat│   (Secondary)   │
     │   [YOUR INPUT]  │          │   [YOUR INPUT]  │
     └────────┬────────┘          └────────┬────────┘
              │                             │
              └──────────────┬──────────────┘
                             │
                    ┌────────▼────────┐
                    │  CORE SWITCH    │
                    └─────────────────┘

HA Configuration:
- Mode: [YOUR INPUT - Active/Passive, Active/Active]
- Failover Time: [YOUR INPUT]
- Session Sync: [YOUR INPUT]
- State Sharing: [YOUR INPUT]
```

---

# SECTION D: NETWORK APPLIANCES & SECURITY DEVICES

## D.1 Security Appliance Inventory

| Device Type | Function | Placement | Product | Quantity |
|-------------|----------|-----------|---------|----------|
| **IDS/IPS** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Network TAP** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Packet Broker** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **SSL/TLS Inspection** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **NAC Appliance** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Proxy Server** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Load Balancer** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **VPN Concentrator** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## D.2 Intrusion Detection/Prevention Configuration

### IDS/IPS Placement

```
[YOUR INPUT - Design IDS/IPS placement]

Position sensors at:
1. [YOUR INPUT - Network perimeter]
2. [YOUR INPUT - Key segments]
3. [YOUR INPUT - Critical assets]

Detection Mode vs Prevention Mode:
- [YOUR INPUT - Where inline, where passive]
```

### Signature and Rule Management

| Rule Category | Action | Sensitivity | Comments |
|---------------|--------|-------------|----------|
| Critical Exploits | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Web Application Attacks | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Malware Traffic | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Suspicious DNS | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Protocol Anomalies | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## D.3 Jump Server/Bastion Host Design

```
[YOUR INPUT - Design bastion host architecture]

┌─────────────────────────────────────────────────────────────────┐
│                    BASTION HOST ARCHITECTURE                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ADMINISTRATOR                ┌─────────────────┐               │
│  ┌──────────┐                │  BASTION HOST    │               │
│  │  Admin   │───MFA─────────►│                 │               │
│  │Workstation│               │  [YOUR INPUT -  │               │
│  └──────────┘                │   hardening,    │               │
│                              │   logging,      │               │
│                              │   controls]     │               │
│                              └────────┬────────┘               │
│                                       │                        │
│                      ┌────────────────┼────────────────┐       │
│                      │                │                │       │
│               ┌──────▼──────┐  ┌──────▼──────┐  ┌──────▼──────┐│
│               │ Servers     │  │ Network     │  │ Cloud       ││
│               │ (RDP/SSH)   │  │ Devices     │  │ Console     ││
│               └─────────────┘  └─────────────┘  └─────────────┘│
│                                                                  │
│  Controls:                                                       │
│  - [YOUR INPUT]                                                  │
│  - [YOUR INPUT]                                                  │
│  - [YOUR INPUT]                                                  │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

## D.4 Network Access Control (NAC)

| NAC Feature | Configuration | Purpose |
|-------------|---------------|---------|
| 802.1X Authentication | [YOUR INPUT] | [YOUR INPUT] |
| MAC Authentication Bypass | [YOUR INPUT] | [YOUR INPUT] |
| Guest Portal | [YOUR INPUT] | [YOUR INPUT] |
| Posture Assessment | [YOUR INPUT] | [YOUR INPUT] |
| Profiling | [YOUR INPUT] | [YOUR INPUT] |
| VLAN Assignment | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION E: SECURE PROTOCOLS

## E.1 Protocol Security Standards

### Approved Protocols

| Function | Approved Protocol | Deprecated Protocol | Notes |
|----------|------------------|--------------------|----|
| Web Traffic | [YOUR INPUT - TLS 1.3, TLS 1.2] | [YOUR INPUT - SSL, TLS 1.0/1.1] | [YOUR INPUT] |
| Email | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Remote Access | [YOUR INPUT - SSH, VPN] | [YOUR INPUT - Telnet] | [YOUR INPUT] |
| File Transfer | [YOUR INPUT - SFTP, SCP] | [YOUR INPUT - FTP] | [YOUR INPUT] |
| DNS | [YOUR INPUT - DoH, DoT, DNSSEC] | [YOUR INPUT] | [YOUR INPUT] |
| SNMP | [YOUR INPUT - SNMPv3] | [YOUR INPUT - v1, v2c] | [YOUR INPUT] |
| NTP | [YOUR INPUT - NTPsec] | [YOUR INPUT] | [YOUR INPUT] |
| Management | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### TLS/SSL Configuration

| Setting | Minimum Requirement | Justification |
|---------|---------------------|---------------|
| Minimum Version | [YOUR INPUT] | [YOUR INPUT] |
| Cipher Suites | [YOUR INPUT - AEAD ciphers] | [YOUR INPUT] |
| Key Exchange | [YOUR INPUT - ECDHE, DHE] | [YOUR INPUT] |
| Certificate Type | [YOUR INPUT] | [YOUR INPUT] |
| Certificate Validity | [YOUR INPUT] | [YOUR INPUT] |
| HSTS | [YOUR INPUT] | [YOUR INPUT] |
| OCSP Stapling | [YOUR INPUT] | [YOUR INPUT] |

## E.2 VPN Architecture

### Site-to-Site VPN

| Connection | Endpoints | Protocol | Encryption | Auth | Purpose |
|------------|-----------|----------|------------|------|---------|
| Turku ↔ Amsterdam | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Turku ↔ Austin | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Turku ↔ Kigali | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Turku ↔ AWS | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Remote Access VPN

| Type | Use Case | Protocol | MFA | Split Tunnel |
|------|----------|----------|-----|--------------|
| Always-On VPN | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| On-Demand VPN | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| ZTNA | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - N/A?] |

## E.3 Secure Communication Matrix

| Communication Type | Protocol Stack | Encryption | Authentication |
|-------------------|----------------|------------|----------------|
| User → Web App | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| App → Database | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Service → Service | [YOUR INPUT - mTLS?] | [YOUR INPUT] | [YOUR INPUT] |
| Admin → Server | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT → Cloud | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Office → Office | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION F: WIRELESS SECURITY

## F.1 Wireless Architecture

### Corporate Wireless

| SSID | Purpose | Security | Auth | Network |
|------|---------|----------|------|---------|
| NordicShield-Corp | [YOUR INPUT] | [YOUR INPUT - WPA3-Enterprise] | [YOUR INPUT - 802.1X] | [YOUR INPUT - Corp VLAN] |
| NordicShield-IoT | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| NordicShield-Guest | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Wireless Security Standards

| Setting | Requirement | Justification |
|---------|-------------|---------------|
| Protocol | [YOUR INPUT - WPA3, WPA2-only if necessary] | [YOUR INPUT] |
| Authentication | [YOUR INPUT - EAP-TLS, PEAP] | [YOUR INPUT] |
| Encryption | [YOUR INPUT - AES-256, CCMP] | [YOUR INPUT] |
| PMF (802.11w) | [YOUR INPUT] | [YOUR INPUT] |
| Client Isolation | [YOUR INPUT] | [YOUR INPUT] |
| Rogue AP Detection | [YOUR INPUT] | [YOUR INPUT] |

## F.2 Wireless Controller Configuration

| Feature | Configuration | Security Impact |
|---------|---------------|-----------------|
| Management Interface | [YOUR INPUT - Dedicated VLAN, HTTPS only] | [YOUR INPUT] |
| AP Authentication | [YOUR INPUT] | [YOUR INPUT] |
| Captive Portal | [YOUR INPUT] | [YOUR INPUT] |
| WIDS/WIPS | [YOUR INPUT] | [YOUR INPUT] |
| RF Management | [YOUR INPUT] | [YOUR INPUT] |

## F.3 Wireless Security Diagram

```
[YOUR INPUT - Design wireless architecture]

┌─────────────────────────────────────────────────────────────────┐
│                    WIRELESS ARCHITECTURE                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  AUTHENTICATION                WIRELESS CONTROLLER               │
│  ┌──────────────┐             ┌──────────────────┐              │
│  │   RADIUS     │◄────────────│   Controller     │              │
│  │   + AD/IdP   │             │   [YOUR INPUT]   │              │
│  └──────────────┘             └────────┬─────────┘              │
│                                        │                        │
│              ┌─────────────────────────┼──────────────────────┐ │
│              │                         │                      │ │
│     ┌────────▼────────┐    ┌──────────▼──────────┐   ┌───────▼───────┐│
│     │   AP - Corp     │    │   AP - IoT          │   │   AP - Guest  ││
│     │   [Security]    │    │   [Security]        │   │   [Security]  ││
│     │                 │    │                     │   │               ││
│     │  ○ WPA3-Ent     │    │  ○ [YOUR INPUT]     │   │  ○ [INPUT]    ││
│     │  ○ 802.1X       │    │  ○ [YOUR INPUT]     │   │  ○ [INPUT]    ││
│     │  ○ EAP-TLS      │    │  ○ [YOUR INPUT]     │   │  ○ [INPUT]    ││
│     └────────┬────────┘    └──────────┬──────────┘   └───────┬───────┘│
│              │                        │                      │       │
│              ▼                        ▼                      ▼       │
│     ┌─────────────────┐    ┌───────────────────┐   ┌─────────────────┐│
│     │  Corp VLAN      │    │    IoT VLAN       │   │   Guest VLAN   ││
│     │  [Policies]     │    │    [Policies]     │   │   [Policies]   ││
│     └─────────────────┘    └───────────────────┘   └─────────────────┘│
│                                                                       │
└───────────────────────────────────────────────────────────────────────┘
```

---

# SECTION G: PORT SECURITY & ACCESS LAYER

## G.1 Switch Port Security

| Feature | Configuration | Purpose |
|---------|---------------|---------|
| Port Security | [YOUR INPUT - Max MAC addresses] | [YOUR INPUT] |
| MAC Limiting | [YOUR INPUT] | [YOUR INPUT] |
| DHCP Snooping | [YOUR INPUT] | [YOUR INPUT] |
| Dynamic ARP Inspection | [YOUR INPUT] | [YOUR INPUT] |
| IP Source Guard | [YOUR INPUT] | [YOUR INPUT] |
| Storm Control | [YOUR INPUT] | [YOUR INPUT] |
| BPDU Guard | [YOUR INPUT] | [YOUR INPUT] |
| Root Guard | [YOUR INPUT] | [YOUR INPUT] |

## G.2 Port Security Violation Actions

| Violation Type | Action | Notification |
|----------------|--------|--------------|
| MAC Limit Exceeded | [YOUR INPUT - Shutdown, Restrict, Protect] | [YOUR INPUT] |
| Unknown MAC | [YOUR INPUT] | [YOUR INPUT] |
| Rogue DHCP | [YOUR INPUT] | [YOUR INPUT] |
| BPDU on Access Port | [YOUR INPUT] | [YOUR INPUT] |

## G.3 Physical Port Standards

| Port Type | Configuration | Security Controls |
|-----------|---------------|-------------------|
| User Access Ports | [YOUR INPUT] | [YOUR INPUT] |
| Server Ports | [YOUR INPUT] | [YOUR INPUT] |
| Uplink/Trunk Ports | [YOUR INPUT] | [YOUR INPUT] |
| Management Ports | [YOUR INPUT] | [YOUR INPUT] |
| Unused Ports | [YOUR INPUT - Disabled, VLAN blackhole] | [YOUR INPUT] |

---

# SECTION H: DEVICE HARDENING

## H.1 Server Hardening Baseline

### Windows Server Hardening

| Category | Hardening Control | CIS Benchmark Ref |
|----------|------------------|-------------------|
| Services | [YOUR INPUT - Disable unnecessary services] | [YOUR INPUT] |
| Network | [YOUR INPUT - Windows Firewall, IPsec] | [YOUR INPUT] |
| Authentication | [YOUR INPUT - Credential Guard, LSA] | [YOUR INPUT] |
| Audit | [YOUR INPUT - Advanced audit policy] | [YOUR INPUT] |
| Software | [YOUR INPUT - AppLocker, WDAC] | [YOUR INPUT] |
| Updates | [YOUR INPUT - WSUS configuration] | [YOUR INPUT] |
| Remote Access | [YOUR INPUT - RDP hardening] | [YOUR INPUT] |

### Linux Server Hardening

| Category | Hardening Control | CIS Benchmark Ref |
|----------|------------------|-------------------|
| Services | [YOUR INPUT] | [YOUR INPUT] |
| Network | [YOUR INPUT - iptables/nftables] | [YOUR INPUT] |
| Authentication | [YOUR INPUT - PAM, sudo] | [YOUR INPUT] |
| File Permissions | [YOUR INPUT] | [YOUR INPUT] |
| Audit | [YOUR INPUT - auditd] | [YOUR INPUT] |
| SSH | [YOUR INPUT - Key auth, no root login] | [YOUR INPUT] |
| SELinux/AppArmor | [YOUR INPUT] | [YOUR INPUT] |

## H.2 Network Device Hardening

| Category | Hardening Control | Devices |
|----------|------------------|---------|
| Physical Access | [YOUR INPUT - Console password, no USB] | [YOUR INPUT] |
| Remote Management | [YOUR INPUT - SSH only, ACL] | [YOUR INPUT] |
| Authentication | [YOUR INPUT - AAA, RADIUS/TACACS+] | [YOUR INPUT] |
| Logging | [YOUR INPUT - Syslog, timestamps] | [YOUR INPUT] |
| SNMP | [YOUR INPUT - v3 only, complex community] | [YOUR INPUT] |
| Unused Services | [YOUR INPUT - Disable HTTP, Telnet] | [YOUR INPUT] |
| Firmware | [YOUR INPUT - Signed, current] | [YOUR INPUT] |
| Passwords | [YOUR INPUT - Enable secret, type 8/9] | [YOUR INPUT] |

## H.3 Endpoint Hardening

### Workstation Hardening

| Category | Control | Implementation |
|----------|---------|----------------|
| Disk Encryption | [YOUR INPUT - BitLocker with TPM] | [YOUR INPUT] |
| Local Admin | [YOUR INPUT - LAPS, no shared password] | [YOUR INPUT] |
| USB Control | [YOUR INPUT] | [YOUR INPUT] |
| Application Control | [YOUR INPUT] | [YOUR INPUT] |
| Browser Hardening | [YOUR INPUT] | [YOUR INPUT] |
| Firewall | [YOUR INPUT] | [YOUR INPUT] |
| Auto-Updates | [YOUR INPUT] | [YOUR INPUT] |

## H.4 Hardening Verification

| System Type | Verification Method | Frequency | Tool |
|-------------|--------------------| ----------|------|
| Windows Servers | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - CIS-CAT, Nessus] |
| Linux Servers | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Network Devices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Workstations | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION I: GLOBAL OFFICE SECURITY

## I.1 Regional Office Network Design

### Amsterdam Office

| Component | Configuration | Security Controls |
|-----------|---------------|-------------------|
| Internet Connection | [YOUR INPUT] | [YOUR INPUT] |
| WAN Connectivity | [YOUR INPUT - SD-WAN to HQ] | [YOUR INPUT] |
| Local Firewall | [YOUR INPUT] | [YOUR INPUT] |
| Local Switches | [YOUR INPUT] | [YOUR INPUT] |
| Wireless | [YOUR INPUT] | [YOUR INPUT] |
| Security Stack | [YOUR INPUT - Local vs cloud] | [YOUR INPUT] |

### Austin Office

| Component | Configuration | Security Controls |
|-----------|---------------|-------------------|
| Internet Connection | [YOUR INPUT] | [YOUR INPUT] |
| WAN Connectivity | [YOUR INPUT] | [YOUR INPUT] |
| Local Firewall | [YOUR INPUT] | [YOUR INPUT] |
| Local Switches | [YOUR INPUT] | [YOUR INPUT] |
| Wireless | [YOUR INPUT] | [YOUR INPUT] |
| Security Stack | [YOUR INPUT] | [YOUR INPUT] |

### Kigali Office

| Component | Configuration | Security Controls |
|-----------|---------------|-------------------|
| Internet Connection | [YOUR INPUT] | [YOUR INPUT] |
| WAN Connectivity | [YOUR INPUT] | [YOUR INPUT] |
| Local Firewall | [YOUR INPUT] | [YOUR INPUT] |
| Local Switches | [YOUR INPUT] | [YOUR INPUT] |
| Wireless | [YOUR INPUT] | [YOUR INPUT] |
| Security Stack | [YOUR INPUT] | [YOUR INPUT] |

## I.2 Global SD-WAN Architecture

```
[YOUR INPUT - Design SD-WAN architecture]

                        ┌─────────────────┐
                        │   CLOUD (AWS)   │
                        │  [YOUR INPUT]   │
                        └────────┬────────┘
                                 │
     ┌───────────────────────────┼───────────────────────────┐
     │                           │                           │
┌────▼────┐                ┌────▼────┐                ┌────▼────┐
│  TURKU  │                │AMSTERDAM│                │  AUSTIN │
│   HQ    │◄──────────────►│  OFFICE │◄──────────────►│  OFFICE │
│         │  [SD-WAN]      │         │  [SD-WAN]      │         │
└────┬────┘                └────┬────┘                └────┬────┘
     │                          │                          │
     └──────────────────────────┼──────────────────────────┘
                                │
                         ┌──────▼──────┐
                         │   KIGALI    │
                         │   OFFICE    │
                         └─────────────┘

SD-WAN Security Features:
- [YOUR INPUT]
- [YOUR INPUT]
- [YOUR INPUT]
```

---

# SECTION J: INFRASTRUCTURE SECURITY METRICS

## J.1 Security KPIs

| Metric | Current | Target | Measurement |
|--------|---------|--------|-------------|
| Firewall Rule Compliance | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Device Hardening Score | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Patch Compliance | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Segmentation Effectiveness | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Unauthorized Access Attempts | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Mean Time to Contain | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## J.2 Infrastructure Review Schedule

| Review Type | Scope | Frequency | Responsible |
|-------------|-------|-----------|-------------|
| Firewall Rule Review | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Hardening Assessment | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Network Diagram Update | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Penetration Test | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Configuration Backup | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 3.2 - Enterprise Infrastructure Security Design |
| **Phase** | 3 - Security Architecture |
| **Exam Objective** | 3.2 - Apply security principles to secure enterprise infrastructure |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
