# Deliverable 2.1: Threat Actor Analysis & Intelligence Report
## NordicShield Technologies Oy

---

```
╔══════════════════════════════════════════════════════════════════╗
║                   THREAT INTELLIGENCE REPORT                      ║
║                                                                    ║
║  Classification: INTERNAL USE ONLY - TLP:AMBER                    ║
║  Report ID: TI-NS-2026-001                                        ║
║  Date: [YOUR DATE]                                                ║
║  Analyst: [YOUR NAME]                                             ║
║  Distribution: Security Team, IT Leadership, Executive Team       ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Document Purpose

This Threat Intelligence Report profiles threat actors relevant to NordicShield Technologies Oy, analyzes their motivations, capabilities, and tactics, and provides actionable intelligence for defensive operations.

---

## Instructions

1. Research each threat actor category in the context of NordicShield's operations
2. Complete all `[YOUR INPUT]` sections with your analysis
3. Use MITRE ATT&CK framework for TTP mapping
4. Provide concrete recommendations based on your analysis

---

# SECTION A: EXECUTIVE INTELLIGENCE SUMMARY

## A.1 Threat Landscape Overview

```
[YOUR INPUT - Write a 200-250 word executive summary]

Current Threat Environment:
- Key threat trends affecting the industry
- Specific relevance to NordicShield
- Overall risk assessment

Priority Threats:
1. [#1 threat and why]
2. [#2 threat and why]  
3. [#3 threat and why]

Recommended Immediate Actions:
1.
2.
3.
```

## A.2 Threat Severity Matrix

| Threat Actor Type | Likelihood | Impact | Risk Level | Trend |
|-------------------|------------|--------|------------|-------|
| Nation-State (IP Theft) | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | ↑ Increasing |
| Ransomware Groups | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Supply Chain Attackers | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Insider Threats | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Hacktivists | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Competitors | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

**Rating Scale:** Very Low | Low | Medium | High | Critical

---

# SECTION B: THREAT ACTOR PROFILES

## B.1 Nation-State Actors

### Profile: "Arctic Fox" (Primary Threat)

| Attribute | Assessment |
|-----------|------------|
| **Actor Type** | Nation-State / State-Sponsored |
| **Suspected Origin** | [YOUR INPUT - Which nation-state might target Nordic green-tech?] |
| **Sophistication** | [YOUR INPUT - Low / Medium / High / Advanced] |
| **Resources** | [YOUR INPUT - Limited / Moderate / Significant / Unlimited] |
| **Targets** | Nordic technology companies, energy sector, critical infrastructure |
| **Primary Motivation** | [YOUR INPUT] |
| **Active Since** | [YOUR INPUT] |

#### Motivations Analysis

| Motivation | Relevance to NordicShield | Evidence/Reasoning |
|------------|---------------------------|-------------------|
| **Intellectual Property Theft** | [YOUR INPUT - High/Medium/Low] | [YOUR INPUT - Why would they want NordicShield's IP?] |
| **Economic Espionage** | [YOUR INPUT] | [YOUR INPUT] |
| **Competitive Advantage** | [YOUR INPUT] | [YOUR INPUT] |
| **Pre-positioning** | [YOUR INPUT] | [YOUR INPUT - Access for future disruption?] |
| **Supply Chain Access** | [YOUR INPUT] | [YOUR INPUT - Use NordicShield to reach their customers?] |

#### Tactics, Techniques, and Procedures (TTPs)

Map to MITRE ATT&CK Framework:

| Tactic | Technique | Technique ID | NordicShield Relevance |
|--------|-----------|--------------|----------------------|
| **Initial Access** | Spear Phishing | T1566 | [YOUR INPUT - Who would be targeted?] |
| **Initial Access** | Supply Chain Compromise | T1195 | [YOUR INPUT - Which suppliers?] |
| **Initial Access** | Exploit Public-Facing Application | T1190 | [YOUR INPUT - Which applications?] |
| **Execution** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Persistence** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Privilege Escalation** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Defense Evasion** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Credential Access** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Discovery** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Lateral Movement** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Collection** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Exfiltration** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

#### Targeted Assets

| Asset Category | Specific Targets | Value to Attacker | Risk Rating |
|----------------|------------------|-------------------|-------------|
| Intellectual Property | [YOUR INPUT - Cooling algorithms] | [YOUR INPUT] | [YOUR INPUT] |
| R&D Systems | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| IoT Device Firmware | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Customer Data | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Strategic Plans | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

#### Historical Incidents (Industry Context)

Research and document real-world incidents involving similar threat actors targeting similar industries:

| Date | Incident | Target | TTPs Used | Relevance |
|------|----------|--------|-----------|-----------|
| [YOUR INPUT] | [YOUR INPUT - Research a real APT attack] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

### Profile: Generic Nation-State (Secondary Threats)

Complete profiles for 2-3 additional nation-state concerns:

| Actor Profile | Origin | Motivation | Key TTPs | NordicShield Risk |
|---------------|--------|------------|----------|-------------------|
| [YOUR INPUT - Economic Espionage Actor] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| [YOUR INPUT - Destructive Actor] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## B.2 Cybercriminal Threat Actors

### Profile: Ransomware-as-a-Service (RaaS) Groups

| Attribute | Assessment |
|-----------|------------|
| **Actor Type** | Organized Cybercrime |
| **Sophistication** | [YOUR INPUT] |
| **Resources** | [YOUR INPUT] |
| **Motivation** | Financial Gain |
| **Typical Ransom Demand** | [YOUR INPUT - What might NordicShield face?] |

#### Ransomware Group Analysis

| Group Archetype | Characteristics | Targeting Criteria | NordicShield Match |
|-----------------|-----------------|-------------------|-------------------|
| **Big Game Hunters** | Target large enterprises, high ransoms | Revenue >$50M, critical operations | [YOUR INPUT - Does NordicShield match?] |
| **Opportunistic** | Exploit vulnerabilities of convenience | Unpatched systems, weak RDP | [YOUR INPUT] |
| **Data Exfiltration Focus** | Double extortion model | Sensitive data holders | [YOUR INPUT] |

#### Attack Chain Analysis

```
[YOUR INPUT - Map a typical ransomware attack against NordicShield]

Phase 1 - Initial Access:
- Vector: [YOUR INPUT]
- Likely entry point: [YOUR INPUT]

Phase 2 - Establish Foothold:
- Persistence mechanism: [YOUR INPUT]
- C2 communication: [YOUR INPUT]

Phase 3 - Privilege Escalation:
- Target accounts: [YOUR INPUT]
- Techniques: [YOUR INPUT]

Phase 4 - Lateral Movement:
- Key systems targeted: [YOUR INPUT]
- Movement methods: [YOUR INPUT]

Phase 5 - Data Collection/Exfiltration:
- Target data: [YOUR INPUT]
- Exfiltration method: [YOUR INPUT]

Phase 6 - Ransomware Deployment:
- Deployment method: [YOUR INPUT]
- Encryption targets: [YOUR INPUT]

Phase 7 - Extortion:
- Ransom communication: [YOUR INPUT]
- Double extortion tactics: [YOUR INPUT]
```

#### Business Impact Assessment

| Scenario | Impact Description | Financial Impact | Recovery Time |
|----------|-------------------|------------------|---------------|
| IoT Platform Encrypted | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Corporate Systems Encrypted | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Data Exfiltrated & Leaked | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Full Environment Compromise | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

### Profile: Business Email Compromise (BEC) Actors

| Attribute | Assessment |
|-----------|------------|
| **Actor Type** | Organized Crime / Solo Operators |
| **Sophistication** | [YOUR INPUT - Low-Medium] |
| **Primary Technique** | Social Engineering, Email Compromise |
| **Typical Target** | Finance, HR, Executive Assistants |

#### BEC Scenario Analysis for NordicShield

| Scenario | Target | Pretext | Potential Loss |
|----------|--------|---------|---------------|
| Invoice Fraud | [YOUR INPUT - Finance team?] | [YOUR INPUT - Vendor impersonation?] | [YOUR INPUT] |
| Gift Card Scam | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Payroll Diversion | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Wire Transfer Fraud | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## B.3 Supply Chain Threat Actors

### Profile: Supply Chain Attackers

| Attribute | Assessment |
|-----------|------------|
| **Actor Type** | State-Sponsored or Criminal (varies) |
| **Sophistication** | High |
| **Method** | Compromise trusted third parties |
| **Impact Multiplier** | Very High (affects multiple victims) |

#### NordicShield Supply Chain Analysis

| Supply Chain Element | Vendor/Source | Trust Level | Compromise Risk | Impact if Compromised |
|---------------------|---------------|-------------|-----------------|----------------------|
| IoT Hardware Components | [YOUR INPUT - From company profile] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Software Libraries | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Cloud Services (AWS) | Amazon Web Services | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| SaaS Applications | [YOUR INPUT - From company profile] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Development Tools | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Security Tools | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

#### Supply Chain Attack Scenarios

| Scenario | Attack Vector | Threat Actor | Detection Difficulty | Mitigation |
|----------|--------------|--------------|---------------------|------------|
| Compromised IoT Firmware | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Malicious NPM Package | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| SaaS Provider Breach | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## B.4 Insider Threats

### Profile: Malicious Insiders

| Attribute | Assessment |
|-----------|------------|
| **Actor Type** | Current/Former Employee, Contractor |
| **Access Level** | Legitimate (makes detection difficult) |
| **Motivation Factors** | Varies (financial, grievance, ideology, recruitment) |

#### Insider Threat Indicators

| Indicator Category | Specific Behaviors | Detection Method |
|-------------------|-------------------|------------------|
| **Technical Indicators** | [YOUR INPUT - Unusual data access, off-hours activity] | [YOUR INPUT] |
| **Behavioral Indicators** | [YOUR INPUT - Disgruntlement, financial stress] | [YOUR INPUT] |
| **Organizational Indicators** | [YOUR INPUT - Resignation, termination notice] | [YOUR INPUT] |

#### High-Risk Insider Scenarios for NordicShield

| Scenario | Insider Type | Target | Motivation | Risk Level |
|----------|-------------|--------|------------|------------|
| R&D Engineer Departure | [YOUR INPUT] | [YOUR INPUT - Cooling algorithms?] | [YOUR INPUT - Competitor recruitment?] | [YOUR INPUT] |
| Disgruntled IT Admin | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Finance Employee | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Contractor with Access | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Third-Party Vendor Staff | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Profile: Negligent Insiders (Unintentional)

| Risk Factor | Description | Likelihood | Impact |
|-------------|-------------|------------|--------|
| Phishing Susceptibility | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Shadow IT | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Poor Password Practices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Misconfiguration | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Lost/Stolen Devices | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## B.5 Hacktivists

### Profile: Environmental/Political Hacktivists

| Attribute | Assessment |
|-----------|------------|
| **Actor Type** | Ideologically Motivated Groups/Individuals |
| **Sophistication** | [YOUR INPUT - Usually Low-Medium] |
| **Typical Targets** | Companies perceived as harmful to causes |
| **Common Tactics** | DDoS, Defacement, Data Leaks, Doxing |

#### Hacktivist Risk Assessment

| Factor | Assessment | Reasoning |
|--------|------------|-----------|
| Does NordicShield have a controversial position? | [YOUR INPUT] | [YOUR INPUT] |
| Does green-tech attract positive or negative attention? | [YOUR INPUT] | [YOUR INPUT] |
| Are there any potential controversy triggers? | [YOUR INPUT - Partnerships, customers?] | [YOUR INPUT] |
| Public profile/visibility | [YOUR INPUT] | [YOUR INPUT] |

#### Potential Hacktivist Scenarios

| Trigger Event | Actor Type | Likely Action | Business Impact |
|---------------|------------|---------------|-----------------|
| Partnership with controversial company | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Environmental controversy | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Political association | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

## B.6 Competitive Threats

### Profile: Corporate Espionage

| Attribute | Assessment |
|-----------|------------|
| **Actor Type** | Competitors, Industrial Spies |
| **Methods** | Recruitment, Theft, Social Engineering, Technical Exploitation |
| **Targets** | Trade secrets, pricing, strategic plans, customer lists |

#### Competitive Intelligence Risks

| Information Asset | Value to Competitors | Protection Level | Risk |
|-------------------|---------------------|------------------|------|
| Cooling Algorithms | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Customer List | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Pricing Models | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Expansion Plans | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Partnership Details | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION C: THREAT ACTOR COMPARISON MATRIX

## C.1 Comprehensive Comparison

| Factor | Nation-State | Ransomware | Supply Chain | Insider | Hacktivist | Competitor |
|--------|-------------|------------|--------------|---------|------------|------------|
| **Sophistication** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Resources** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Persistence** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Primary Goal** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Attack Timeline** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **Detection Difficulty** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| **NordicShield Priority** | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## C.2 Motivation Comparison

| Motivation | Nation-State | Ransomware | Supply Chain | Insider | Hacktivist | Competitor |
|------------|-------------|------------|--------------|---------|------------|------------|
| Financial | ☐ | ☑ | ☐ | ☐ | ☐ | ☐ |
| Espionage | ☑ | ☐ | ☐ | ☐ | ☐ | ☑ |
| Disruption | ☐ | ☐ | ☐ | ☐ | ☑ | ☐ |
| Ideology | ☐ | ☐ | ☐ | ☐ | ☑ | ☐ |
| Revenge | ☐ | ☐ | ☐ | ☑ | ☐ | ☐ |
| Access Resale | ☐ | ☐ | ☐ | ☐ | ☐ | ☐ |

```
[YOUR INPUT - Complete the matrix above with checkboxes]
```

---

# SECTION D: INTELLIGENCE-DRIVEN DEFENSE RECOMMENDATIONS

## D.1 Priority Actions by Threat Actor

### Against Nation-State Actors (Arctic Fox)

| Priority | Recommendation | Rationale | Effort | Impact |
|----------|---------------|-----------|--------|--------|
| 1 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 2 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 3 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 4 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 5 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Against Ransomware Actors

| Priority | Recommendation | Rationale | Effort | Impact |
|----------|---------------|-----------|--------|--------|
| 1 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 2 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 3 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Against Supply Chain Threats

| Priority | Recommendation | Rationale | Effort | Impact |
|----------|---------------|-----------|--------|--------|
| 1 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 2 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 3 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

### Against Insider Threats

| Priority | Recommendation | Rationale | Effort | Impact |
|----------|---------------|-----------|--------|--------|
| 1 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 2 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| 3 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## D.2 Detection Capabilities Required

| Threat Actor | Detection Capability Needed | Current State | Gap |
|--------------|---------------------------|---------------|-----|
| Nation-State | [YOUR INPUT - EDR, NDR, threat hunting] | [YOUR INPUT] | [YOUR INPUT] |
| Ransomware | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Supply Chain | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Insider | [YOUR INPUT - UEBA, DLP] | [YOUR INPUT] | [YOUR INPUT] |
| Hacktivist | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION E: THREAT INTELLIGENCE PROGRAM RECOMMENDATIONS

## E.1 Intelligence Sources

| Source Type | Examples | Value for NordicShield | Recommended |
|-------------|----------|----------------------|-------------|
| Commercial Threat Intel | [YOUR INPUT - Recorded Future, Mandiant, etc.] | [YOUR INPUT] | [YOUR INPUT] |
| Government Sources | [YOUR INPUT - NCSC-FI, CISA, ENISA] | [YOUR INPUT] | [YOUR INPUT] |
| ISACs | [YOUR INPUT - Industry specific] | [YOUR INPUT] | [YOUR INPUT] |
| Open Source | [YOUR INPUT - VirusTotal, AlienVault, etc.] | [YOUR INPUT] | [YOUR INPUT] |
| Dark Web Monitoring | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## E.2 Intelligence Requirements (PIRs)

Define Priority Intelligence Requirements for NordicShield:

| PIR # | Requirement | Threat Actor | Collection Source |
|-------|-------------|--------------|-------------------|
| PIR-1 | [YOUR INPUT - e.g., TTPs targeting IoT manufacturers] | [YOUR INPUT] | [YOUR INPUT] |
| PIR-2 | [YOUR INPUT - e.g., Ransomware groups targeting Nordic companies] | [YOUR INPUT] | [YOUR INPUT] |
| PIR-3 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| PIR-4 | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

## E.3 Threat Intelligence Sharing

| Sharing Partner | Information to Share | Information to Receive | Mechanism |
|-----------------|---------------------|----------------------|-----------|
| NCSC-FI | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Industry Peers | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |
| Customers | [YOUR INPUT] | [YOUR INPUT] | [YOUR INPUT] |

---

# SECTION F: APPENDICES

## F.1 MITRE ATT&CK Reference

```
[YOUR INPUT - List key ATT&CK techniques relevant to NordicShield]

Reconnaissance (TA0043):
- 

Resource Development (TA0042):
-

Initial Access (TA0001):
-

Execution (TA0002):
-

Persistence (TA0003):
-

[Continue for other tactics...]
```

## F.2 Indicators of Compromise (IOCs) - Arctic Fox Campaign

**Note:** These are fictional IOCs for training purposes.

| Indicator Type | Value | Confidence | Context |
|----------------|-------|------------|---------|
| IPv4 | 185.159.xxx.xxx | High | C2 Server |
| Domain | update-nordic[.]com | High | Phishing infrastructure |
| File Hash (SHA256) | [YOUR INPUT] | Medium | Malicious document |
| Email Address | service@nord-update[.]com | High | Phishing sender |
| User Agent | [YOUR INPUT] | Low | Reconnaissance |

## F.3 Glossary

| Term | Definition |
|------|------------|
| APT | [YOUR INPUT] |
| TTP | [YOUR INPUT] |
| IOC | [YOUR INPUT] |
| C2/C&C | [YOUR INPUT] |
| TLP | [YOUR INPUT] |
| RaaS | [YOUR INPUT] |
| BEC | [YOUR INPUT] |

---

## Document Information

| Field | Value |
|-------|-------|
| **Deliverable** | 2.1 - Threat Actor Analysis & Intelligence Report |
| **Phase** | 2 - Threats, Vulnerabilities, and Mitigations |
| **Exam Objective** | 2.1 - Compare and contrast common threat actors and motivations |
| **Status** | ⬜ Not Started / 🟡 In Progress / ✅ Complete |
| **Completed By** | [YOUR NAME] |
| **Completion Date** | [DATE] |
| **Classification** | TLP:AMBER - Internal Use Only |

---

**Developed by Allyship Security Labs (AllySecLabs)**
*Security+ SY0-701 Capstone Project*
