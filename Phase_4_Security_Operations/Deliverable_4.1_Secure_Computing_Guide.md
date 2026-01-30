# Deliverable 4.1: Secure Computing & Hardening Guide
## NordicShield Technologies Oy

---

```
╔══════════════════════════════════════════════════════════════════╗
║          SECURE COMPUTING & HARDENING GUIDE                      ║
║                                                                    ║
║  Document ID: HARD-NS-2026-001                                    ║
║  Version: 1.0                                                     ║
║  Author: [YOUR NAME]                                              ║
║  Classification: Internal Use Only                                ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Document Purpose

This document defines NordicShield's secure computing standards, baseline configurations, and hardening procedures for all computing resources including servers, endpoints, mobile devices, and network equipment.

---

## Instructions

1. Define secure baselines for each system type
2. Create actionable hardening checklists
3. Complete all `[YOUR INPUT]` sections
4. Reference CIS Benchmarks and vendor guides
5. Consider NordicShield's IoT and global context

---

# SECTION A: SECURE BASELINE FRAMEWORK

## A.1 Baseline Hierarchy

```
[YOUR INPUT - Design the baseline hierarchy]

┌─────────────────────────────────────────────────────────────────────────┐
│                    BASELINE CONFIGURATION HIERARCHY                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  LEVEL 1: ORGANIZATIONAL BASELINE                                        │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  [YOUR INPUT - Universal standards across all systems]          │    │
│  │  Examples: Password policy, logging requirements, update policy │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                              │                                           │
│                              ▼                                           │
│  LEVEL 2: PLATFORM BASELINES                                             │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐   │
│  │ Windows      │ │ Linux        │ │ Network      │ │ Cloud        │   │
│  │ Baseline     │ │ Baseline     │ │ Baseline     │ │ Baseline     │   │
│  │ [Controls]   │ │ [Controls]   │ │ [Controls]   │ │ [Controls]   │   │
│  └──────────────┘ └──────────────┘ └──────────────┘ └──────────────┘   │
│                              │                                           │
│                              ▼                                           │
│  LEVEL 3: ROLE-SPECIFIC BASELINES                                        │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐   │
│  │ Web Server   │ │ Database     │ │ Domain       │ │ IoT Gateway  │   │
│  │ Hardening    │ │ Hardening    │ │ Controller   │ │ Hardening    │   │
│  └──────────────┘ └──────────────┘ └──────────────┘ └──────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

## A.2 Baseline Standards Selection

| System Type | Baseline Standard | Version | Compliance Level |
|-------------|------------------|---------|------------------|
| Windows Server | [YOUR INPUT - CIS Benchmark] | [YOUR INPUT] | [YOUR INPUT - Level 1/Level 2] |
| Windows Desktop | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| RHEL/CentOS | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Ubuntu | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Cisco IOS | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Palo Alto | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| AWS | [YOUR INPUT - CIS AWS Foundations] | [YOUR INPUT] | [YOUR INPUT] |
| Kubernetes | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## A.3 Baseline Management Process

| Phase | Activities | Responsible | Frequency |
|-------|------------|-------------|-----------|
| Development | [YOUR INPUT - Create/update baseline documents] | [YOUR INPUT] | [YOUR INPUT] |
| Review | [YOUR INPUT - Security review, change control] | [YOUR INPUT] | [YOUR INPUT] |
| Testing | [YOUR INPUT - Lab validation] | [YOUR INPUT] | [YOUR INPUT] |
| Deployment | [YOUR INPUT - Production rollout] | [YOUR INPUT] | [YOUR INPUT] |
| Monitoring | [YOUR INPUT - Compliance checking] | [YOUR INPUT] | [YOUR INPUT] |
| Updates | [YOUR INPUT - Baseline refresh] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION B: WINDOWS SERVER HARDENING

## B.1 Windows Server 2022 Hardening Checklist

### Account Policies

| Setting | Recommended Value | Justification | Status |
|---------|------------------|---------------|--------|
| Minimum password length | [YOUR INPUT - e.g., 14 characters] | [YOUR INPUT] | ☐ |
| Password complexity | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Account lockout threshold | [YOUR INPUT - e.g., 5 attempts] | [YOUR INPUT] | ☐ |
| Account lockout duration | [YOUR INPUT - e.g., 30 minutes] | [YOUR INPUT] | ☐ |
| Enforce password history | [YOUR INPUT - e.g., 24 passwords] | [YOUR INPUT] | ☐ |
| Maximum password age | [YOUR INPUT - or consider removing] | [YOUR INPUT] | ☐ |
| Guest account | [YOUR INPUT - Disabled] | [YOUR INPUT] | ☐ |
| Administrator account rename | [YOUR INPUT] | [YOUR INPUT] | ☐ |

### Local Policies - User Rights

| Setting | Allowed Users/Groups | Justification | Status |
|---------|---------------------|---------------|--------|
| Access this computer from network | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Allow log on locally | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Allow log on through RDP | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Debug programs | [YOUR INPUT - Administrators only] | [YOUR INPUT] | ☐ |
| Deny log on as a batch job | [YOUR INPUT - Guests] | [YOUR INPUT] | ☐ |
| Act as part of the operating system | [YOUR INPUT - No one] | [YOUR INPUT] | ☐ |
| Create a token object | [YOUR INPUT - No one] | [YOUR INPUT] | ☐ |

### Security Options

| Setting | Value | Justification | Status |
|---------|-------|---------------|--------|
| Accounts: Limit local account use of blank passwords | [YOUR INPUT - Enabled] | [YOUR INPUT] | ☐ |
| Devices: Prevent users from installing printer drivers | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Interactive logon: Don't display last signed-in | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Interactive logon: Machine inactivity limit | [YOUR INPUT - e.g., 900 seconds] | [YOUR INPUT] | ☐ |
| Network access: Do not allow anonymous enumeration of SAM accounts | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Network security: LAN Manager authentication level | [YOUR INPUT - NTLMv2 only] | [YOUR INPUT] | ☐ |
| Shutdown: Allow system to be shut down without logon | [YOUR INPUT - Disabled] | [YOUR INPUT] | ☐ |
| User Account Control: Run all administrators in Admin Approval Mode | [YOUR INPUT] | [YOUR INPUT] | ☐ |

### Windows Firewall Configuration

| Profile | State | Inbound | Outbound | Logging |
|---------|-------|---------|----------|---------|
| Domain | [YOUR INPUT - On] | [YOUR INPUT - Block] | [YOUR INPUT] | [YOUR INPUT - Yes, dropped+successful] |
| Private | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Public | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Services Hardening

| Service | Recommendation | Startup Type | Justification |
|---------|----------------|--------------|---------------|
| Print Spooler | [YOUR INPUT - Disabled unless needed] | [YOUR INPUT] | [YOUR INPUT - PrintNightmare] |
| Remote Registry | [YOUR INPUT - Disabled] | [YOUR INPUT] | [YOUR INPUT] |
| SNMP | [YOUR INPUT - Disabled or v3 only] | [YOUR INPUT] | [YOUR INPUT] |
| Telnet | [YOUR INPUT - Disabled] | [YOUR INPUT] | [YOUR INPUT] |
| Windows Remote Management | [YOUR INPUT - Configure securely if needed] | [YOUR INPUT] | [YOUR INPUT] |
| LLMNR | [YOUR INPUT - Disabled] | [YOUR INPUT] | [YOUR INPUT - Poisoning attacks] |
| NetBIOS | [YOUR INPUT - Disabled] | [YOUR INPUT] | [YOUR INPUT] |
| SMBv1 | [YOUR INPUT - Disabled] | [YOUR INPUT] | [YOUR INPUT - EternalBlue] |

### Advanced Security Features

| Feature | Configuration | Status |
|---------|---------------|--------|
| Credential Guard | [YOUR INPUT - Enable on supported hardware] | ☐ |
| Device Guard/HVCI | [YOUR INPUT] | ☐ |
| LSASS Protection | [YOUR INPUT - Enable] | ☐ |
| WDAC (App Control) | [YOUR INPUT] | ☐ |
| BitLocker | [YOUR INPUT - Enable with TPM] | ☐ |
| Secure Boot | [YOUR INPUT - Enabled] | ☐ |

## B.2 Windows Server Hardening Script Template

```powershell
# [YOUR INPUT - Create a sample hardening script]
# NordicShield Windows Server 2022 Hardening Script
# Version: 1.0
# Created: [DATE]

# ==============================================
# ACCOUNT POLICIES
# ==============================================

# Set minimum password length
# [YOUR INPUT - PowerShell command]

# Disable Guest account
# [YOUR INPUT - PowerShell command]

# ==============================================
# DISABLE UNNECESSARY SERVICES
# ==============================================

# Disable Print Spooler
# [YOUR INPUT - PowerShell command]

# Disable SMBv1
# [YOUR INPUT - PowerShell command]

# ==============================================
# CONFIGURE WINDOWS FIREWALL
# ==============================================

# Enable firewall for all profiles
# [YOUR INPUT - PowerShell command]

# Enable logging
# [YOUR INPUT - PowerShell command]

# ==============================================
# AUDIT POLICY
# ==============================================

# Configure audit policies
# [YOUR INPUT - Commands]
```

---

# SECTION C: LINUX SERVER HARDENING

## C.1 Linux (Ubuntu/RHEL) Hardening Checklist

### Account Security

| Setting | Configuration | File/Command | Status |
|---------|---------------|--------------|--------|
| Minimum password length | [YOUR INPUT - 14 characters] | [YOUR INPUT - /etc/security/pwquality.conf] | ☐ |
| Password complexity | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Password expiration | [YOUR INPUT - or disabled with MFA] | [YOUR INPUT - /etc/login.defs] | ☐ |
| Root login via SSH | [YOUR INPUT - Disabled] | [YOUR INPUT - /etc/ssh/sshd_config] | ☐ |
| Password authentication SSH | [YOUR INPUT - Disabled, use keys] | [YOUR INPUT] | ☐ |
| Sudo configuration | [YOUR INPUT - Wheel/sudo group only] | [YOUR INPUT - /etc/sudoers] | ☐ |
| Account lockout | [YOUR INPUT] | [YOUR INPUT - PAM] | ☐ |
| umask | [YOUR INPUT - 027 or 077] | [YOUR INPUT] | ☐ |

### SSH Hardening

| Setting | Value | File Location | Status |
|---------|-------|---------------|--------|
| Protocol | [YOUR INPUT - 2] | [YOUR INPUT] | ☐ |
| PermitRootLogin | [YOUR INPUT - no] | [YOUR INPUT] | ☐ |
| PasswordAuthentication | [YOUR INPUT - no] | [YOUR INPUT] | ☐ |
| PermitEmptyPasswords | [YOUR INPUT - no] | [YOUR INPUT] | ☐ |
| X11Forwarding | [YOUR INPUT - no] | [YOUR INPUT] | ☐ |
| MaxAuthTries | [YOUR INPUT - 4] | [YOUR INPUT] | ☐ |
| AllowUsers/AllowGroups | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| ClientAliveInterval | [YOUR INPUT - 300] | [YOUR INPUT] | ☐ |
| ClientAliveCountMax | [YOUR INPUT - 0] | [YOUR INPUT] | ☐ |
| Ciphers | [YOUR INPUT - Strong ciphers only] | [YOUR INPUT] | ☐ |
| MACs | [YOUR INPUT - Strong MACs only] | [YOUR INPUT] | ☐ |
| KexAlgorithms | [YOUR INPUT - Strong KEX only] | [YOUR INPUT] | ☐ |

### Filesystem Security

| Control | Configuration | Command/File | Status |
|---------|---------------|--------------|--------|
| /tmp mount options | [YOUR INPUT - noexec,nosuid,nodev] | [YOUR INPUT - /etc/fstab] | ☐ |
| /var mount options | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| /home mount options | [YOUR INPUT - nodev] | [YOUR INPUT] | ☐ |
| World-writable files | [YOUR INPUT - Audit and remediate] | [YOUR INPUT - find command] | ☐ |
| SUID/SGID files | [YOUR INPUT - Audit and remove unnecessary] | [YOUR INPUT] | ☐ |
| Unowned files | [YOUR INPUT - Investigate] | [YOUR INPUT] | ☐ |

### Network Security

| Setting | Configuration | Implementation | Status |
|---------|---------------|----------------|--------|
| IP forwarding | [YOUR INPUT - Disabled unless router] | [YOUR INPUT - sysctl] | ☐ |
| Source routing | [YOUR INPUT - Disabled] | [YOUR INPUT] | ☐ |
| ICMP redirects | [YOUR INPUT - Disabled] | [YOUR INPUT] | ☐ |
| SYN cookies | [YOUR INPUT - Enabled] | [YOUR INPUT] | ☐ |
| Firewall (iptables/nftables) | [YOUR INPUT - Default deny] | [YOUR INPUT] | ☐ |
| IPv6 | [YOUR INPUT - Disable if not used] | [YOUR INPUT] | ☐ |

### Service Hardening

| Service | Recommendation | Status |
|---------|----------------|--------|
| Unnecessary services | [YOUR INPUT - Disable: telnet, rsh, rcp, rlogin, finger] | ☐ |
| NFS | [YOUR INPUT - Disable unless needed, configure securely] | ☐ |
| Samba | [YOUR INPUT - Disable unless needed] | ☐ |
| SNMP | [YOUR INPUT - v3 only or disable] | ☐ |
| Avahi | [YOUR INPUT - Disable] | ☐ |
| CUPS | [YOUR INPUT - Disable unless needed] | ☐ |

### SELinux/AppArmor

| Control | Configuration | Status |
|---------|---------------|--------|
| SELinux Mode | [YOUR INPUT - Enforcing] | ☐ |
| SELinux Policy | [YOUR INPUT - targeted] | ☐ |
| AppArmor Status | [YOUR INPUT - Enabled, profiles enforced] | ☐ |
| Custom Profiles | [YOUR INPUT - For NordicShield apps] | ☐ |

## C.2 Linux Hardening Script Template

```bash
#!/bin/bash
# [YOUR INPUT - Create a sample hardening script]
# NordicShield Linux Server Hardening Script
# Version: 1.0
# Tested on: Ubuntu 22.04 LTS, RHEL 9

# ==============================================
# SSH HARDENING
# ==============================================

# Backup original sshd_config
# [YOUR INPUT]

# Disable root login
# [YOUR INPUT - sed command]

# Disable password authentication
# [YOUR INPUT]

# Set strong ciphers
# [YOUR INPUT]

# ==============================================
# NETWORK HARDENING
# ==============================================

# Disable IP forwarding
# [YOUR INPUT - sysctl command]

# Enable SYN cookies
# [YOUR INPUT]

# ==============================================
# FIREWALL CONFIGURATION
# ==============================================

# Default deny policy
# [YOUR INPUT - iptables/ufw commands]

# Allow SSH from management network only
# [YOUR INPUT]

# ==============================================
# FILESYSTEM SECURITY
# ==============================================

# Mount /tmp with security options
# [YOUR INPUT]
```

---

# SECTION D: ENDPOINT SECURITY

## D.1 Windows Workstation Hardening

### Endpoint Protection Configuration

| Control | Configuration | Tool/Method | Status |
|---------|---------------|-------------|--------|
| Anti-malware | [YOUR INPUT - Real-time protection enabled] | [YOUR INPUT - Defender/CrowdStrike] | ☐ |
| EDR Agent | [YOUR INPUT - Installed and reporting] | [YOUR INPUT] | ☐ |
| Host firewall | [YOUR INPUT - Enabled, default deny inbound] | [YOUR INPUT] | ☐ |
| Disk encryption | [YOUR INPUT - BitLocker with TPM] | [YOUR INPUT] | ☐ |
| Application control | [YOUR INPUT - Whitelisting/WDAC] | [YOUR INPUT] | ☐ |
| USB restrictions | [YOUR INPUT - Block or encrypt only] | [YOUR INPUT - GPO/Intune] | ☐ |
| AutoRun | [YOUR INPUT - Disabled] | [YOUR INPUT] | ☐ |
| Screen lock | [YOUR INPUT - 5 minutes inactivity] | [YOUR INPUT] | ☐ |

### Browser Hardening

| Setting | Chrome | Edge | Firefox | Status |
|---------|--------|------|---------|--------|
| Auto-updates | [YOUR INPUT - Enabled] | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Safe Browsing | [YOUR INPUT - Enhanced] | [YOUR INPUT - SmartScreen] | [YOUR INPUT] | ☐ |
| Password manager | [YOUR INPUT - Disabled, use enterprise] | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Third-party cookies | [YOUR INPUT - Block] | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Pop-ups | [YOUR INPUT - Block] | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Extensions | [YOUR INPUT - Whitelist only] | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Flash/Java | [YOUR INPUT - Disabled] | [YOUR INPUT] | [YOUR INPUT] | ☐ |

### Office Security

| Setting | Configuration | Status |
|---------|---------------|--------|
| Macro execution | [YOUR INPUT - Disable all except signed] | ☐ |
| Protected View | [YOUR INPUT - Enabled for all sources] | ☐ |
| Trusted locations | [YOUR INPUT - Restricted] | ☐ |
| Active content in documents | [YOUR INPUT - Restrict] | ☐ |
| OLE embedding | [YOUR INPUT - Restrict] | ☐ |
| DDE | [YOUR INPUT - Disabled] | ☐ |

## D.2 Endpoint Configuration Profile

```
[YOUR INPUT - Design endpoint configuration for Intune/SCCM/GPO]

NORDICSHIELD WORKSTATION SECURITY PROFILE
=========================================

IDENTITY:
- Azure AD Joined: [YOUR INPUT]
- Conditional Access: [YOUR INPUT]
- MFA Required: [YOUR INPUT]

ENCRYPTION:
- BitLocker Encryption: [YOUR INPUT - Required]
- Recovery Key Storage: [YOUR INPUT - Azure AD]
- Encryption Algorithm: [YOUR INPUT - XTS-AES 256]

FIREWALL:
- Domain Profile: [YOUR INPUT]
- Private Profile: [YOUR INPUT]
- Public Profile: [YOUR INPUT]

DEFENDER:
- Real-time Protection: [YOUR INPUT]
- Cloud-delivered Protection: [YOUR INPUT]
- Automatic Sample Submission: [YOUR INPUT]
- PUA Protection: [YOUR INPUT]
- Tamper Protection: [YOUR INPUT]

ATTACK SURFACE REDUCTION:
- Block Office apps from creating child processes: [YOUR INPUT]
- Block credential stealing from LSASS: [YOUR INPUT]
- Block executable content from email: [YOUR INPUT]
- Block untrusted USB processes: [YOUR INPUT]
```

---

# SECTION E: MOBILE DEVICE SECURITY

## E.1 Mobile Device Management (MDM) Policy

### Device Enrollment Requirements

| Requirement | iOS | Android | Status |
|-------------|-----|---------|--------|
| Minimum OS version | [YOUR INPUT - iOS 16+] | [YOUR INPUT - Android 13+] | ☐ |
| Jailbreak/Root detection | [YOUR INPUT - Block enrollment] | [YOUR INPUT] | ☐ |
| MDM enrollment | [YOUR INPUT - Required for corporate access] | [YOUR INPUT] | ☐ |
| Device encryption | [YOUR INPUT - Required] | [YOUR INPUT - Required] | ☐ |
| Passcode | [YOUR INPUT - 6-digit minimum, biometric allowed] | [YOUR INPUT] | ☐ |

### Device Configuration

| Setting | iOS Configuration | Android Configuration | Status |
|---------|-------------------|----------------------|--------|
| Screen lock timeout | [YOUR INPUT - 2 minutes] | [YOUR INPUT] | ☐ |
| Passcode complexity | [YOUR INPUT] | [YOUR INPUT] | ☐ |
| Max failed attempts | [YOUR INPUT - 10, then wipe] | [YOUR INPUT] | ☐ |
| Camera (optional) | [YOUR INPUT - Allow] | [YOUR INPUT] | ☐ |
| Screenshot | [YOUR INPUT - Block for work apps] | [YOUR INPUT] | ☐ |
| Cloud backup for work data | [YOUR INPUT - Disable] | [YOUR INPUT] | ☐ |
| Copy/paste between work/personal | [YOUR INPUT - Block] | [YOUR INPUT] | ☐ |
| USB file transfer | [YOUR INPUT - Block or MDM controlled] | [YOUR INPUT] | ☐ |

### Application Management

| Control | Configuration | Justification |
|---------|---------------|---------------|
| Required apps | [YOUR INPUT - Authenticator, Outlook, Teams] | [YOUR INPUT] |
| Prohibited apps | [YOUR INPUT - Untrusted app stores, high-risk apps] | [YOUR INPUT] |
| App protection policies | [YOUR INPUT - PIN for work apps, wipe on unenrollment] | [YOUR INPUT] |
| Managed browser | [YOUR INPUT - Edge required for work sites] | [YOUR INPUT] |
| VPN configuration | [YOUR INPUT - Per-app VPN for sensitive apps] | [YOUR INPUT] |

## E.2 BYOD vs Corporate Device Matrix

| Feature | Corporate Device | BYOD | Justification |
|---------|------------------|------|---------------|
| MDM enrollment | [YOUR INPUT - Full device management] | [YOUR INPUT - Work profile only] | [YOUR INPUT] |
| Personal apps visibility | [YOUR INPUT - Yes] | [YOUR INPUT - No] | [YOUR INPUT] |
| Remote wipe scope | [YOUR INPUT - Full device] | [YOUR INPUT - Work profile only] | [YOUR INPUT] |
| App installation | [YOUR INPUT - Restricted] | [YOUR INPUT - Personal unrestricted] | [YOUR INPUT] |
| Access to data | [YOUR INPUT - Full access] | [YOUR INPUT - Limited sensitive data] | [YOUR INPUT] |
| Location tracking | [YOUR INPUT - Optional] | [YOUR INPUT - Not allowed] | [YOUR INPUT] |

## E.3 NordicShield Mobile Security Policy

```
[YOUR INPUT - Write mobile device security policy summary]

NORDICSHIELD MOBILE DEVICE SECURITY POLICY
==========================================

1. SCOPE
   [YOUR INPUT - Which devices, which users]

2. DEVICE REQUIREMENTS
   - [YOUR INPUT]
   - [YOUR INPUT]
   - [YOUR INPUT]

3. ACCEPTABLE USE
   - [YOUR INPUT]
   - [YOUR INPUT]

4. PROHIBITED ACTIVITIES
   - [YOUR INPUT - Jailbreaking/rooting]
   - [YOUR INPUT - Connecting to untrusted networks for work]
   - [YOUR INPUT]

5. DATA PROTECTION
   - [YOUR INPUT]
   - [YOUR INPUT]

6. LOST/STOLEN DEVICE
   - [YOUR INPUT - Report within 1 hour]
   - [YOUR INPUT - Remote wipe procedure]

7. EMPLOYEE DEPARTURE
   - [YOUR INPUT]
```

---

# SECTION F: WIRELESS SECURITY

## F.1 Wireless Security Standards

### Corporate SSID Configuration

| Setting | Recommended Configuration | Justification |
|---------|--------------------------|---------------|
| SSID Name | [YOUR INPUT - Non-identifying] | [YOUR INPUT - Don't advertise company] |
| Security Protocol | [YOUR INPUT - WPA3-Enterprise] | [YOUR INPUT - Strongest available] |
| Authentication | [YOUR INPUT - 802.1X with EAP-TLS] | [YOUR INPUT - Certificate-based] |
| RADIUS Server | [YOUR INPUT - Redundant NPS/FreeRADIUS] | [YOUR INPUT] |
| Encryption | [YOUR INPUT - AES-CCMP/GCMP-256] | [YOUR INPUT] |
| PMF (802.11w) | [YOUR INPUT - Required] | [YOUR INPUT - Management frame protection] |
| Fast Roaming | [YOUR INPUT - 802.11r] | [YOUR INPUT - Session continuity] |
| Client Isolation | [YOUR INPUT - Enabled] | [YOUR INPUT - Prevent lateral movement] |
| VLAN Assignment | [YOUR INPUT - Dynamic based on user group] | [YOUR INPUT - Segmentation] |

### Guest SSID Configuration

| Setting | Configuration | Justification |
|---------|---------------|---------------|
| SSID Name | [YOUR INPUT] | [YOUR INPUT] |
| Security | [YOUR INPUT - WPA3-Personal or OWE] | [YOUR INPUT] |
| Captive Portal | [YOUR INPUT - Terms acceptance required] | [YOUR INPUT] |
| Network Access | [YOUR INPUT - Internet only, no internal] | [YOUR INPUT] |
| Bandwidth Limit | [YOUR INPUT - 10 Mbps per client] | [YOUR INPUT] |
| Session Duration | [YOUR INPUT - 8 hours max] | [YOUR INPUT] |
| VLAN | [YOUR INPUT - Dedicated guest VLAN] | [YOUR INPUT] |

### IoT SSID Configuration

| Setting | Configuration | Justification |
|---------|---------------|---------------|
| SSID Name | [YOUR INPUT - NordicShield-IoT] | [YOUR INPUT] |
| Security | [YOUR INPUT - WPA2/WPA3-Enterprise] | [YOUR INPUT - Device capability varies] |
| Authentication | [YOUR INPUT - 802.1X or MAC auth + profiling] | [YOUR INPUT] |
| Network Access | [YOUR INPUT - IoT VLAN only, specific destinations] | [YOUR INPUT] |
| Client Isolation | [YOUR INPUT - Enabled] | [YOUR INPUT - Prevent IoT-to-IoT attacks] |

## F.2 Wireless Threats & Mitigations

| Threat | Description | Mitigation | Implementation |
|--------|-------------|------------|----------------|
| Evil Twin | [YOUR INPUT - Rouge AP mimicking corporate SSID] | [YOUR INPUT - WIDS, certificate auth] | [YOUR INPUT] |
| Deauthentication Attack | [YOUR INPUT] | [YOUR INPUT - PMF (802.11w)] | [YOUR INPUT] |
| KRACK/Dragonblood | [YOUR INPUT] | [YOUR INPUT - Patching, WPA3] | [YOUR INPUT] |
| Rogue AP | [YOUR INPUT - Unauthorized AP] | [YOUR INPUT - WIDS/WIPS, NAC] | [YOUR INPUT] |
| Credential Harvesting | [YOUR INPUT] | [YOUR INPUT - Certificate auth, no password] | [YOUR INPUT] |
| Wireless Sniffing | [YOUR INPUT] | [YOUR INPUT - Encryption, VPN for sensitive] | [YOUR INPUT] |

## F.3 Wireless IDS/IPS Configuration

| Detection | Response | Priority |
|-----------|----------|----------|
| Rogue AP detected | [YOUR INPUT - Alert + auto-contain] | [YOUR INPUT - High] |
| Deauth flood | [YOUR INPUT - Alert + investigate] | [YOUR INPUT] |
| Evil twin | [YOUR INPUT - Alert + contain + notify users] | [YOUR INPUT - Critical] |
| Unauthorized SSID | [YOUR INPUT] | [YOUR INPUT] |
| MAC Spoofing | [YOUR INPUT] | [YOUR INPUT] |
| Association flood | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION G: APPLICATION SECURITY

## G.1 Application Whitelisting

### Whitelisting Policy

| Environment | Enforcement Level | Allowed Applications |
|-------------|------------------|---------------------|
| Workstations | [YOUR INPUT - Audit → Enforce] | [YOUR INPUT - Corporate apps, signed MS apps] |
| Servers | [YOUR INPUT - Enforce] | [YOUR INPUT - Role-specific apps only] |
| Kiosks | [YOUR INPUT - Strict enforce] | [YOUR INPUT - Single app only] |
| Developer | [YOUR INPUT - Audit mode] | [YOUR INPUT - Expanded with approval] |

### Application Control Rules

| Rule Type | Example | Action |
|-----------|---------|--------|
| Publisher (Certificate) | [YOUR INPUT - Microsoft Corporation] | [YOUR INPUT - Allow] |
| Path | [YOUR INPUT - C:\Program Files\*] | [YOUR INPUT - Allow] |
| Hash | [YOUR INPUT - Specific file hash] | [YOUR INPUT - Allow/Block] |
| Packaged App | [YOUR INPUT - Windows Store apps] | [YOUR INPUT - Controlled] |
| Scripts | [YOUR INPUT - Signed scripts only] | [YOUR INPUT - Allow signed, block unsigned] |

### Exception Management

```
[YOUR INPUT - Design exception process]

APPLICATION WHITELIST EXCEPTION REQUEST

Request Date: ___________
Requestor: ___________
Department: ___________

Application Details:
- Name: [YOUR INPUT]
- Publisher: [YOUR INPUT]
- Version: [YOUR INPUT]
- Business Justification: [YOUR INPUT]

Security Assessment:
- Vulnerability scan: [YOUR INPUT]
- Malware scan: [YOUR INPUT]
- Code review (if applicable): [YOUR INPUT]
- Risk assessment: [YOUR INPUT]

Approval:
- [ ] Security Approved
- [ ] IT Operations Approved
- [ ] Business Owner Approved

Rule Type to Create: [YOUR INPUT]
Expiration: [YOUR INPUT]
```

## G.2 Sandboxing & Isolation

### Sandboxing Technologies

| Technology | Use Case | Implementation |
|------------|----------|----------------|
| Windows Sandbox | [YOUR INPUT - Testing untrusted files] | [YOUR INPUT - Enable, policy for use] |
| Browser Isolation | [YOUR INPUT - High-risk websites] | [YOUR INPUT - Remote browser isolation] |
| Application Containers | [YOUR INPUT - Sensitive apps] | [YOUR INPUT - Microsoft Defender Application Guard] |
| VM Isolation | [YOUR INPUT - Development, testing] | [YOUR INPUT - Hyper-V isolated VMs] |
| Network Isolation | [YOUR INPUT - Untrusted traffic] | [YOUR INPUT - Segmented network] |

### Application Guard Configuration

| Setting | Configuration | Justification |
|---------|---------------|---------------|
| Mode | [YOUR INPUT - Enterprise managed] | [YOUR INPUT] |
| Clipboard | [YOUR INPUT - Disabled or text only] | [YOUR INPUT] |
| Printing | [YOUR INPUT - Disabled] | [YOUR INPUT] |
| File download | [YOUR INPUT - Trust files manually] | [YOUR INPUT] |
| Persistence | [YOUR INPUT - Disabled] | [YOUR INPUT] |

## G.3 Secure Software Configuration

### Default Deny Configuration

```
[YOUR INPUT - Design default deny approach]

DEFAULT DENY SECURITY MODEL
==========================

1. NETWORK LEVEL
   - Default: Block all inbound
   - Allowed: [YOUR INPUT - Explicit whitelist]

2. APPLICATION LEVEL
   - Default: Block unsigned executables
   - Allowed: [YOUR INPUT - Publisher-signed, hash-verified]

3. SCRIPT LEVEL
   - Default: Block all scripts
   - Allowed: [YOUR INPUT - Signed scripts from trusted paths]

4. USER LEVEL
   - Default: Standard user (no admin)
   - Elevation: [YOUR INPUT - JIT, with approval]
```

---

# SECTION H: NETWORK DEVICE HARDENING

## H.1 Router/Switch Hardening

### Management Plane Security

| Control | Configuration | Status |
|---------|---------------|--------|
| SSH (disable Telnet) | [YOUR INPUT - SSH v2 only] | ☐ |
| SSH timeout | [YOUR INPUT - 5 minutes] | ☐ |
| SSH authentication | [YOUR INPUT - RADIUS/TACACS+ with local fallback] | ☐ |
| SSH ACL | [YOUR INPUT - Management network only] | ☐ |
| HTTPS for web management | [YOUR INPUT - TLS 1.2+, or disable web UI] | ☐ |
| Console timeout | [YOUR INPUT - 5 minutes] | ☐ |
| Banner | [YOUR INPUT - Legal warning banner] | ☐ |
| Password encryption | [YOUR INPUT - Type 8/9 hashes] | ☐ |
| SNMP | [YOUR INPUT - v3 only with auth/priv, ACL] | ☐ |
| NTP | [YOUR INPUT - Authenticated NTP] | ☐ |
| Logging | [YOUR INPUT - Syslog to SIEM, timestamps] | ☐ |

### Control Plane Security

| Control | Configuration | Status |
|---------|---------------|--------|
| CoPP (Control Plane Policing) | [YOUR INPUT - Rate limit management traffic] | ☐ |
| Routing protocol authentication | [YOUR INPUT - MD5/SHA for OSPF, BGP] | ☐ |
| DHCP snooping | [YOUR INPUT - Enabled on access ports] | ☐ |
| Dynamic ARP Inspection | [YOUR INPUT - Enabled] | ☐ |
| IP Source Guard | [YOUR INPUT - Enabled] | ☐ |
| BPDUGuard | [YOUR INPUT - Enabled on access ports] | ☐ |
| Root Guard | [YOUR INPUT - On appropriate ports] | ☐ |
| Storm Control | [YOUR INPUT - Configure thresholds] | ☐ |

### Data Plane Security

| Control | Configuration | Status |
|---------|---------------|--------|
| Unused ports | [YOUR INPUT - Shutdown, blackhole VLAN] | ☐ |
| Port security | [YOUR INPUT - MAC limiting, sticky] | ☐ |
| Private VLANs | [YOUR INPUT - Where appropriate] | ☐ |
| ACLs | [YOUR INPUT - Block RFC1918 from internet, etc.] | ☐ |
| uRPF (Unicast Reverse Path Forwarding) | [YOUR INPUT - Enable where applicable] | ☐ |

## H.2 Network Device Hardening Checklist

```
[YOUR INPUT - Create comprehensive checklist]

CISCO IOS/IOS-XE HARDENING CHECKLIST
===================================

MANAGEMENT ACCESS:
[ ] no ip http server
[ ] ip http secure-server
[ ] ip ssh version 2
[ ] transport input ssh (on vty lines)
[ ] access-class applied to vty lines
[ ] exec-timeout 5 0
[ ] [YOUR INPUT - Additional commands]

SERVICES TO DISABLE:
[ ] no ip source-route
[ ] no ip finger
[ ] no ip bootp server
[ ] no service tcp-small-servers
[ ] no service udp-small-servers
[ ] no cdp run (or per-interface on untrusted)
[ ] no ip proxy-arp (per interface)
[ ] [YOUR INPUT]

LOGGING:
[ ] service timestamps log datetime msec localtime show-timezone
[ ] logging buffered 32768 informational
[ ] logging host [SIEM IP]
[ ] logging trap informational
[ ] [YOUR INPUT]

AUTHENTICATION:
[ ] aaa new-model
[ ] aaa authentication login default group tacacs+ local
[ ] aaa authorization exec default group tacacs+ local
[ ] aaa accounting commands 15 default start-stop group tacacs+
[ ] [YOUR INPUT]
```

---

# SECTION I: CLOUD RESOURCE HARDENING

## I.1 AWS Security Configuration

### EC2 Instance Hardening

| Control | Configuration | Status |
|---------|---------------|--------|
| IMDSv2 | [YOUR INPUT - Required (disable v1)] | ☐ |
| Instance metadata | [YOUR INPUT - Restrict to authorized roles] | ☐ |
| Security groups | [YOUR INPUT - Least privilege, no 0.0.0.0/0] | ☐ |
| EBS encryption | [YOUR INPUT - Default encryption enabled] | ☐ |
| Instance profile | [YOUR INPUT - Minimal IAM permissions] | ☐ |
| SSM Agent | [YOUR INPUT - Installed for patching] | ☐ |
| Public IP | [YOUR INPUT - Avoid unless necessary] | ☐ |
| AMI hardening | [YOUR INPUT - CIS-hardened AMIs] | ☐ |

### S3 Bucket Security

| Control | Configuration | Status |
|---------|---------------|--------|
| Block public access | [YOUR INPUT - Enabled at account and bucket level] | ☐ |
| Encryption | [YOUR INPUT - SSE-S3 or SSE-KMS default] | ☐ |
| Versioning | [YOUR INPUT - Enabled for critical buckets] | ☐ |
| Object lock | [YOUR INPUT - For compliance/backup] | ☐ |
| Access logging | [YOUR INPUT - Enabled] | ☐ |
| Bucket policy | [YOUR INPUT - Explicit deny for non-HTTPS] | ☐ |
| Cross-account access | [YOUR INPUT - Restricted, use resource policies] | ☐ |

### IAM Security

| Control | Configuration | Status |
|---------|---------------|--------|
| Root account MFA | [YOUR INPUT - Hardware MFA required] | ☐ |
| Root account usage | [YOUR INPUT - No access keys, alerts on use] | ☐ |
| Password policy | [YOUR INPUT - 14 char, complexity, 90-day rotation] | ☐ |
| MFA enforcement | [YOUR INPUT - Required for console access] | ☐ |
| Access keys rotation | [YOUR INPUT - 90 days max] | ☐ |
| Unused credentials | [YOUR INPUT - Disable after 90 days] | ☐ |
| Permission boundaries | [YOUR INPUT - Implemented for delegated admins] | ☐ |
| Service control policies | [YOUR INPUT - Restrict risky actions] | ☐ |

## I.2 Azure Security Configuration

### Azure VM Hardening

| Control | Configuration | Status |
|---------|---------------|--------|
| Azure Disk Encryption | [YOUR INPUT - Enabled with Key Vault key] | ☐ |
| NSG | [YOUR INPUT - Attached, least privilege] | ☐ |
| Just-in-Time VM access | [YOUR INPUT - Enabled for management ports] | ☐ |
| Guest configuration | [YOUR INPUT - Azure Policy for compliance] | ☐ |
| Update management | [YOUR INPUT - Azure Update Management] | ☐ |
| Diagnostic settings | [YOUR INPUT - Enabled, sent to Log Analytics] | ☐ |
| Managed identity | [YOUR INPUT - Use instead of credentials] | ☐ |

### Azure AD Security

| Control | Configuration | Status |
|---------|---------------|--------|
| Security defaults | [YOUR INPUT - Enabled or Conditional Access] | ☐ |
| MFA enforcement | [YOUR INPUT - All users, risk-based] | ☐ |
| Conditional Access | [YOUR INPUT - Block legacy auth, require compliant device] | ☐ |
| Privileged Identity Management | [YOUR INPUT - Enabled for admin roles] | ☐ |
| Identity Protection | [YOUR INPUT - Risk policies configured] | ☐ |
| Access reviews | [YOUR INPUT - Quarterly for privileged roles] | ☐ |

---

# SECTION J: IOT/OT DEVICE HARDENING

## J.1 IoT Gateway Hardening

| Control | Configuration | Justification | Status |
|---------|---------------|---------------|--------|
| Firmware | [YOUR INPUT - Signed, verified, current] | [YOUR INPUT] | ☐ |
| Default credentials | [YOUR INPUT - Changed immediately] | [YOUR INPUT] | ☐ |
| Secure boot | [YOUR INPUT - Enabled] | [YOUR INPUT] | ☐ |
| Unnecessary services | [YOUR INPUT - Disabled] | [YOUR INPUT] | ☐ |
| Remote management | [YOUR INPUT - SSH only from management network] | [YOUR INPUT] | ☐ |
| Automatic updates | [YOUR INPUT - Enabled with testing] | [YOUR INPUT] | ☐ |
| Certificate authentication | [YOUR INPUT - Device certificates] | [YOUR INPUT] | ☐ |
| Logging | [YOUR INPUT - Forward to SIEM] | [YOUR INPUT] | ☐ |
| Physical security | [YOUR INPUT - Tamper detection] | [YOUR INPUT] | ☐ |

## J.2 OT/SCADA Security

| Control | Configuration | Safety Consideration |
|---------|---------------|---------------------|
| Network isolation | [YOUR INPUT - Air gap or strict firewall] | [YOUR INPUT - Critical for safety] |
| Change management | [YOUR INPUT - Formal process, testing required] | [YOUR INPUT - Prevent production impact] |
| Protocol security | [YOUR INPUT - Modbus/TCP monitoring, DNP3 authentication] | [YOUR INPUT] |
| Patch management | [YOUR INPUT - Vendor-approved, tested in lab first] | [YOUR INPUT - Longer cycles acceptable] |
| Remote access | [YOUR INPUT - Jump server, MFA, session recording] | [YOUR INPUT] |
| Antivirus | [YOUR INPUT - Whitelisting preferred over signature] | [YOUR INPUT - Performance impact] |
| USB policy | [YOUR INPUT - Disabled or kiosk scanning] | [YOUR INPUT - Common malware vector] |

---

# SECTION K: COMPLIANCE VERIFICATION

## K.1 Hardening Compliance Dashboard

| System Category | Total Systems | Compliant | Non-Compliant | Compliance % | Target |
|----------------|---------------|-----------|---------------|--------------|--------|
| Windows Servers | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT - 95%] |
| Linux Servers | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Workstations | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Network Devices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Cloud Resources | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Devices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## K.2 Compliance Scanning Schedule

| Scan Type | Scope | Frequency | Tool | Owner |
|-----------|-------|-----------|------|-------|
| CIS Benchmark - Windows | All Windows systems | [YOUR INPUT - Weekly] | [YOUR INPUT - CIS-CAT, Qualys] | [YOUR INPUT] |
| CIS Benchmark - Linux | All Linux systems | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| AWS Security Benchmark | AWS accounts | [YOUR INPUT] | [YOUR INPUT - Prowler, AWS Config] | [YOUR INPUT] |
| Custom baseline | All systems | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## K.3 Exception Management

| Exception ID | System | Control | Justification | Compensating Control | Expiration | Approver |
|--------------|--------|---------|---------------|---------------------|------------|----------|
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 4.1 - Secure Computing & Hardening Guide |
| **Phase** | 4 - Security Operations |
| **Exam Objectives** | 4.1, 4.5 - Security techniques, enterprise capabilities |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
