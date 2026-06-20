---
source: https://en.wikipedia.org/wiki/Defense_in_depth_(computing)
fetched: 2026-06-19
---

Concept in information security 

**Defense in depth** is a concept used in [information security](./Information_security) in which multiple layers of security controls (defense) are placed throughout an [information technology](./Information_technology) (IT) system. Its intent is to provide [redundancy](./Redundancy_(engineering)) in the event a [security control](./Security_controls) fails or a vulnerability is exploited.[[1]](./Defense_in_depth_(computing)#cite_note-1)

 

## Background

 

The idea behind the defense in depth approach is to defend a system against any particular attack using several independent methods.[[2]](./Defense_in_depth_(computing)#cite_note-schneier2006-2) It is a layering tactic, conceived by the [National Security Agency](./National_Security_Agency) (NSA) as a comprehensive approach to information and electronic security.[[3]](./Defense_in_depth_(computing)#cite_note-nsa1-3)[[4]](./Defense_in_depth_(computing)#cite_note-owasp1-4)

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/4/4c/Defense_In_Depth_-_Onion_Model.svg/250px-Defense_In_Depth_-_Onion_Model.svg.png)](./File:Defense_In_Depth_-_Onion_Model.svg)The [onion model](./Onion_model) of defense in depth

Defense in depth is sometimes thought of as forming the layers of an onion, with data at the core of the onion, people the next outer layer of the onion, and [network security](./Network_security), host-based security, and [application security](./Application_security) forming the outermost layers of the onion.[[5]](./Defense_in_depth_(computing)#cite_note-5)

 

## Tiers

 

Defense in depth can be divided into three overarching areas: Physical, Technical, and Administrative.[[6]](./Defense_in_depth_(computing)#cite_note-6)

 

### Physical

 

[Physical controls](./Physical_security) are anything that physically limits or prevents access to IT systems. Examples of physical defensive security are: fences, guards, dogs, and [CCTV](./Closed-circuit_television) systems.[[3]](./Defense_in_depth_(computing)#cite_note-nsa1-3)

 

### Technical

 

Technical controls are hardware or software whose purpose is to protect systems and resources. Examples of technical controls include disk encryption, file integrity software, authentication,[[7]](./Defense_in_depth_(computing)#cite_note-:0-7) [network security controls](./Network_security), [antiviruses](./Antivirus_software), and [behavioural analysis software](./Behavioral_analytics).[[8]](./Defense_in_depth_(computing)#cite_note-8)

 

In the event that one layer of defence fails, defense in depth aims to ensure network security via a second-line of defence.[[3]](./Defense_in_depth_(computing)#cite_note-nsa1-3) For example, if an attacker penetrates a computer system at a given OSI layer (e.g. [Layer 3](./Network_layer)), a redundancy should exist at another layer ([Layer 7](./Application_layer)) to ensure layered defense.[[3]](./Defense_in_depth_(computing)#cite_note-nsa1-3)

 
- Authentication, authorization, and accounting
- Confidentiality, integrity, and availability
- Authentication and password security

 
- Encryption
- Hashing

 

#### Application security

 
- [Application security](./Application_security)
- [Web application firewalls](./Web_application_firewall)[[7]](./Defense_in_depth_(computing)#cite_note-:0-7)

 

#### Host security

 
- [Vulnerability scanners](./Vulnerability_scanner)
- [Sandboxing](./Sandbox_(computer_security))
- [Endpoint detection and response](./Endpoint_detection_and_response)[[7]](./Defense_in_depth_(computing)#cite_note-:0-7)

 

#### Network security

 
- [Logging](./Data_logger)
- [Intrusion detection systems](./Intrusion_detection_system)[[7]](./Defense_in_depth_(computing)#cite_note-:0-7)
- [Firewalls](./Firewall_(computing))[[7]](./Defense_in_depth_(computing)#cite_note-:0-7)
- [Demilitarized zones](./DMZ_(computing))
- [Network segmentation](./Network_segmentation)[[9]](./Defense_in_depth_(computing)#cite_note-:1-9)
- [Virtual private network](./Virtual_private_network)

 

### Administrative and operational

 

[Administrative controls](./Administrative_controls) are the organization's policies and procedures and govern the organisation's [human resources](./Human_resources), [technology](./Technology), and [operations](./Operations_research).[[3]](./Defense_in_depth_(computing)#cite_note-nsa1-3)

 

#### People

 
- [Multi-factor authentication](./Multi-factor_authentication)[[9]](./Defense_in_depth_(computing)#cite_note-:1-9)
- [Password policies](./Password_policy)[[9]](./Defense_in_depth_(computing)#cite_note-:1-9)[[3]](./Defense_in_depth_(computing)#cite_note-nsa1-3)
- [Internet Security Awareness Training](./Internet_Security_Awareness_Training)[[7]](./Defense_in_depth_(computing)#cite_note-:0-7)[[3]](./Defense_in_depth_(computing)#cite_note-nsa1-3)

 

#### Technology

 
- [Patch management](./Patch_management)[[9]](./Defense_in_depth_(computing)#cite_note-:1-9)
- [Risk assessment](./Risk_assessment)[[3]](./Defense_in_depth_(computing)#cite_note-nsa1-3)
- [Information assurance](./Information_assurance)[[3]](./Defense_in_depth_(computing)#cite_note-nsa1-3)

 

#### Operations

 
- [Principle of least privilege](./Principle_of_least_privilege)[[9]](./Defense_in_depth_(computing)#cite_note-:1-9)

 

## Regulatory alignment

 

Defense in depth principles align with multiple regulatory frameworks that require layered security controls rather than reliance on single protective measures.

 

The [Health Insurance Portability and Accountability Act](./Health_Insurance_Portability_and_Accountability_Act) (HIPAA) Security Rule implicitly mandates a defense in depth approach by requiring covered entities to implement administrative safeguards (45 CFR 164.308), physical safeguards (45 CFR 164.310), and technical safeguards (45 CFR 164.312) as complementary layers protecting [protected health information](./Protected_health_information).["Summary of the HIPAA Security Rule"](https://www.hhs.gov/hipaa/for-professionals/security/laws-regulations/index.html). U.S. Department of Health and Human Services. Retrieved April 1, 2026. The December 2024 HIPAA Security Rule notice of proposed rulemaking (90 FR 898) would further codify layered defenses by simultaneously mandating network segmentation, encryption, multi-factor authentication, anti-malware deployment, and continuous monitoring as distinct but overlapping security controls.["HIPAA Security Rule To Strengthen the Cybersecurity of Electronic Protected Health Information"](https://www.federalregister.gov/documents/2025/01/06/2024-30983/hipaa-security-rule-to-strengthen-the-cybersecurity-of-electronic-protected-health-information). Federal Register. January 6, 2025. Retrieved April 1, 2026.

 

[NIST Special Publication 800-53](./NIST_Special_Publication_800-53) organizes security controls into 20 control families spanning management, operational, and technical domains, providing a comprehensive defense in depth framework for federal information systems.["NIST SP 800-53 Rev. 5: Security and Privacy Controls"](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final). National Institute of Standards and Technology. September 2020. Retrieved April 1, 2026. The [NIST Cybersecurity Framework](./NIST_Cybersecurity_Framework) 2.0 similarly structures protective measures across the Identify, Protect, Detect, Respond, and Recover functions, reinforcing the layered security approach.["NIST Cybersecurity Framework 2.0"](https://www.nist.gov/cyberframework). National Institute of Standards and Technology. February 2024. Retrieved April 1, 2026.

 

## See also

 
- [Defense strategy (computing)](./Defense_strategy_(computing))
- [Swiss cheese model](./Swiss_cheese_model)

 

## References

  
1. [↑](./Defense_in_depth_(computing)#cite_ref-1) ["Secure Product Design - OWASP Cheat Sheet Series"](https://cheatsheetseries.owasp.org/cheatsheets/Secure_Product_Design_Cheat_Sheet.html#2-the-principle-of-defense-in-depth). *cheatsheetseries.owasp.org*. Retrieved 2025-10-02.
2. [↑](./Defense_in_depth_(computing)#cite_ref-schneier2006_2-0) ["Security in the Cloud"](https://www.schneier.com/blog/archives/2006/02/security_in_the.html). *Schneier on Security*. 2006-02-15. Retrieved 2025-10-02.
3. [1](./Defense_in_depth_(computing)#cite_ref-nsa1_3-0) [2](./Defense_in_depth_(computing)#cite_ref-nsa1_3-1) [3](./Defense_in_depth_(computing)#cite_ref-nsa1_3-2) [4](./Defense_in_depth_(computing)#cite_ref-nsa1_3-3) [5](./Defense_in_depth_(computing)#cite_ref-nsa1_3-4) [6](./Defense_in_depth_(computing)#cite_ref-nsa1_3-5) [7](./Defense_in_depth_(computing)#cite_ref-nsa1_3-6) [8](./Defense_in_depth_(computing)#cite_ref-nsa1_3-7) [9](./Defense_in_depth_(computing)#cite_ref-nsa1_3-8) [National Security Agency](./National_Security_Agency), [Defense in Depth: A practical strategy for achieving Information Assurance in today’s highly networked environments.](https://web.archive.org/web/20121002051613/https://www.nsa.gov/ia/_files/support/defenseindepth.pdf)
4. [↑](./Defense_in_depth_(computing)#cite_ref-owasp1_4-0) [OWASP CheatSheet: Defense in depth](https://cheatsheetseries.owasp.org/cheatsheets/Secure_Product_Design_Cheat_Sheet.html#2-the-principle-of-defense-in-depth)
5. [↑](./Defense_in_depth_(computing)#cite_ref-5) ["Security Onion Control Scripts"](https://dx.doi.org/10.1016/b978-0-12-417208-1.09986-4). *Applied Network Security Monitoring*. Elsevier. 2014. pp. 451–456. [doi](./Doi_(identifier)):[10.1016/b978-0-12-417208-1.09986-4](https://doi.org/10.1016%2Fb978-0-12-417208-1.09986-4). [ISBN](./ISBN_(identifier)) [978-0-12-417208-1](./Special:BookSources/978-0-12-417208-1). Retrieved 2021-05-29.
6. [↑](./Defense_in_depth_(computing)#cite_ref-6) Stewart, James Michael; Chapple, Mike; Gibson, Darril (2015). [*CISSP (ISC)2 Certified Information Systems Security Professional Official Study Guide*](https://books.google.com/books?id=xSvdCQAAQBAJ). John Wiley & Sons. [ISBN](./ISBN_(identifier)) [978-1-119-04271-6](./Special:BookSources/978-1-119-04271-6).
7. [1](./Defense_in_depth_(computing)#cite_ref-:0_7-0) [2](./Defense_in_depth_(computing)#cite_ref-:0_7-1) [3](./Defense_in_depth_(computing)#cite_ref-:0_7-2) [4](./Defense_in_depth_(computing)#cite_ref-:0_7-3) [5](./Defense_in_depth_(computing)#cite_ref-:0_7-4) [6](./Defense_in_depth_(computing)#cite_ref-:0_7-5) ["What is defense in depth? | Layered security"](https://www.cloudflare.com/learning/security/glossary/what-is-defense-in-depth/). *www.cloudflare.com*. Retrieved 2025-10-02.
8. [↑](./Defense_in_depth_(computing)#cite_ref-8) ["What is Defense in Depth? Defined and Explained"](https://www.fortinet.com/resources/cyberglossary/defense-in-depth). *Fortinet*. Retrieved 2025-10-02.
9. [1](./Defense_in_depth_(computing)#cite_ref-:1_9-0) [2](./Defense_in_depth_(computing)#cite_ref-:1_9-1) [3](./Defense_in_depth_(computing)#cite_ref-:1_9-2) [4](./Defense_in_depth_(computing)#cite_ref-:1_9-3) [5](./Defense_in_depth_(computing)#cite_ref-:1_9-4) ["Cybersecurity Spotlight - Defense in Depth (DiD)"](https://www.cisecurity.org/spotlight/cybersecurity-spotlight-defense-in-depth-did/). *CIS*. Retrieved 2025-10-02.