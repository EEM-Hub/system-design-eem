---
source: sources/wiki-Defense_in_depth_computing.md
source_url: https://en.wikipedia.org/wiki/Defense_in_depth_(computing)
---

## Defense in Depth (Layered Security Strategy)

Defense in depth is an information security strategy that deploys multiple, independent layers of security controls throughout an IT system. Conceived by the NSA, the approach provides redundancy so that if any single control fails or a vulnerability is exploited, other layers continue to protect the system. It is often visualized as an "onion model" with data at the core surrounded by concentric layers of people, network security, host-based security, and application security.

## Key Concepts

- **Core principle**: No single security control is sufficient; multiple independent methods must defend each asset so that failure of one does not compromise the system.
- **Onion model**: Layers radiate outward from data (core) through people, network security, host-based security, and application security.
- **Three overarching tiers**: Physical, Technical, and Administrative/Operational controls.
- **Physical controls**: Fences, guards, dogs, CCTV — anything that physically limits access to IT systems.
- **Technical controls**: Hardware or software protections — disk encryption, authentication, firewalls, antivirus, intrusion detection, endpoint detection and response, sandboxing, vulnerability scanners, web application firewalls, VPNs, DMZs, network segmentation.
- **Administrative/Operational controls**: Policies and procedures governing people, technology, and operations — MFA, password policies, security awareness training, patch management, risk assessment, information assurance, principle of least privilege.
- **OSI layer redundancy**: If an attacker penetrates at one OSI layer (e.g., Layer 3 / Network), a defense should exist at another layer (e.g., Layer 7 / Application).
- **Swiss cheese model**: Related concept — each layer has holes, but the holes in different layers don't align, so threats are caught by at least one layer.

## Commands and Syntax

No specific CLI commands. This is a strategy/architecture concept. Implementation involves deploying and configuring controls at each tier:

- **Network layer**: Firewalls, IDS/IPS, network segmentation, DMZs, VPNs, logging
- **Host layer**: Endpoint detection and response (EDR), vulnerability scanners, sandboxing
- **Application layer**: Web application firewalls (WAF), application security testing
- **Data layer**: Encryption (at rest and in transit), hashing, file integrity monitoring
- **People layer**: MFA enrollment, password policy enforcement, security awareness training
- **Operations**: Patch management schedules, risk assessments, least-privilege access reviews

## Relationships

- **Information Security**: Defense in depth is a foundational strategy within information security architecture.
- **Network Security**: Network-layer controls (firewalls, IDS, segmentation, DMZs) form one of the outermost defensive layers.
- **Application Security**: WAFs and secure coding practices represent the application defense layer.
- **Physical Security**: Physical controls (fences, guards, CCTV) are the first tier of defense.
- **Principle of Least Privilege**: An operational control that limits blast radius when a layer is breached.
- **Multi-Factor Authentication**: A people-layer control that strengthens authentication beyond passwords alone.
- **Redundancy (Engineering)**: Defense in depth applies the redundancy principle to security — no single point of failure.
- **Regulatory Frameworks**: HIPAA, NIST SP 800-53, and NIST CSF 2.0 all mandate or align with layered security controls.

## Exam-Relevant Points

- Defense in depth uses **multiple independent layers** — know this definition precisely; it is about redundancy of controls, not just having many controls.
- The three tiers are **Physical, Technical, and Administrative/Operational** — a common exam categorization (CISSP, Security+).
- The **onion model** layers from inside out: Data → People → Network Security → Host-Based Security → Application Security.
- Technical controls span multiple OSI layers; redundancy should exist across layers (e.g., Layer 3 and Layer 7).
- Key technical sub-categories to memorize: **Application security** (WAF), **Host security** (EDR, sandboxing, vulnerability scanning), **Network security** (firewalls, IDS, DMZ, segmentation, VPN, logging).
- Administrative controls include **MFA, password policies, security awareness training, patch management, risk assessment, least privilege**.
- **HIPAA Security Rule** implicitly requires defense in depth through administrative (45 CFR 164.308), physical (45 CFR 164.310), and technical (45 CFR 164.312) safeguards. The December 2024 proposed rulemaking would explicitly codify layered defenses (network segmentation + encryption + MFA + anti-malware + continuous monitoring).
- **NIST SP 800-53** organizes controls into 20 families across management, operational, and technical domains.
- **NIST CSF 2.0** structures measures across five functions: **Identify, Protect, Detect, Respond, Recover**.
- The concept was developed by the **NSA** as a comprehensive approach to information and electronic security.
- Related to the **Swiss cheese model** — each layer has weaknesses, but overlapping layers prevent threats from passing through all of them.
