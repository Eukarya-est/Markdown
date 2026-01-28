# 1-2 Information Security Systems

[toc]

## I. Information Security Organizations

### 1. CTI

Cyber Threat Intelligence (CTI) is <u>the process of collecting, analyzing, and sharing data</u> about current and potential cyber threats to help organizations proactively defend against attacks, moving from reactive to predictive security.

### 2. ISAC

Information Sharing and Analysis Center (ISAC) is collaborative organizations for sharing cyber threat info in critical sectors like electricity, telecom , finance, etc., helping protect infrastructure.

### 3. Information Sharing in Cybersecurity

In order to share threat intelligence, it is necessary to establish a format for describing information and procedures for exchange.

#### 1) Structured Threat Information eXpression (STIX)

STIX is a XML specification that standardizes how to describe threats, attacks, vulnerabilities, and actions. a STIX consists of:

- Campaigns
- Threat Actors
- Tactics, Techniques, and Procedures (TTPs)
- Indicators
- Observables
- Incidents
- Courses Of Action
- Exploit Targets

#### 2) Trusted Automated eXchange of Indicator Information (TAXII)

TAXII provides the secure transport protocol (over HTTPS) for sharing it.

#### 3) Automates Indicator Sharing (AIS)

Cybersecurity and Infrastructure Security Agency's (CISA's) program for real-time, machine-readable exchange of threat indicators and countermeasures.

#### 4) Malware Attribute Enumeration and Correlation (MAEC)

MAES standardizes malware descriptions for better analysis an collaboration.

### 4. Information Security Committee

The Information Security Committee is the management decision-making organization, including the Chief Information Security Officer (CISO).

### 5. Security Operations Center (SOC)

SOC is a security monitoring hub. IT companies providing security management services are providing SOCs to focus on multiple customers, monitoring customer security equipment, detecting and responding to cyberattacks.

### 6. Computer Security Incident Response Team (CSIRT)

CSIRT is Organization that monitor computers and networks primarily for security purposes, analyze and investigate the causes of problems.

- Internal CSIRT
  - Organization that respond to incidents for companies or public organizations.
- National CSIRT
  - Organization representing a country or region, collaborating with internal CIRST and serving as contact points.
- CERT Coordination Center (CERT/CC)
  - Organization that coordinates and coordinates information with other CSIRTs

A internal CSIRT is in charge of incident management such as preparation and follow-up, and the process of handling incidents from from occurrence to resolution is called <u>Incident handling</u>.

1. Preparation
   - Proactive measures like creating an Incident Response Plan (IRP), training staff, and setting up necessary tools and resources.
2. Detection & Analysis
   - Identifying potential incidents via alerts, user reports, and monitoring, then analyzing them to confirm and assess severity.
3. Containment
   - Isolating affected systems to prevent the attack from spreading further, like quarantining malware or blocking IPs.
4. Eradication
   - Removing the root cause, such as deleting malware, patching vulnerabilities, or resetting compromised accounts.
5. Recovery
   - Restoring systems to normal operation, potentially from backups, and ensuring security is restored.
6. Lessons Learned
   - Reviewing the incident to find gaps, update plans, and improve overall security posture to prevent recurrence. 

### 7. Open CSIRT Foundation (OCF)

OSF is a non-profit organization dedicated to improving global cyber resilience by fostering cooperation, research, training, and standardization for CSIRTs

Legally based in the Netherlands, the OCF promotes best practices, maintains the <u>Security Incident Management Maturity Model (SIM3)</u> for evaluating CSIRT performance (process, techniques, human resource, organizational structure,  etc), and supports communities like the TF-CSIRT, all while working to enhance internet security and personal freedom. 

### 8. Open Web Application Security Project (OWASP)

OWASP is a non-profit organization that studies web application security, creates guidelines, and develops vulnerability diagnostic tools.

- OWASP Top 10
  - A regularly updated report outlining security concerns for web application security, focusing on the 10 most critical risks. 
- OWASP Zed Attack Proxy (OWASP ZAP)
  - It is a free tool to investigate vulnerabilities. Designed to facilitate vulnerability diagnosis by web application developers.
- OWASP Application Security Verification Standard (OWASP ASVS)
  - Standard for web application security verification. It summarizes the security requirements required for web application design, development, and vulnerability diagnosis.

### 9. National Institute of Standards and Technology (NIST)

NIST is a non-regulatory agency within the U.S. Department of Commerce that promotes innovation and industrial competitiveness by advancing measurement science, standards, and technology for the nation. It develops <u>crucial standards</u>, like the widely used NIST CyberSecurity Framework (NIST CSF) and NIST SP800 series, to help businesses and government improve security, quality of life, and economic growth in areas from atomic clocks and encryption to IT and nanomaterials. 

### 10. Japan Security Organization and Management

#### 1) IPA Security Center

IPA Security Center is a security center located within IPA (Information-technology Promotion Agency, Japan).

It operates the Information Security Early Warning Partnership, and also provides various information on information security, recommendations to prevent recurrence, and educational activities.

1. Guidelines for SME information security measures
   - https://www.ipa.go.jp/security/guide/sme/about.html
2. Internal Rogue Access Guidelines for Organizations
   - https://www.ipa.go.jp/security/guide/insider.html
3. How to create a secure website
   - https://www.ipa.go.jp/security/vuln/websecurity/about.html

#### 2) Japan Vulnerability Database

Japan Vulnerability Notes (JVN) is a portal site provides vulnerability-related information such as software used in Japan and countermeasures. It is operated jointly by JPCERT/CC and IPA.

JVN uses three different numbering schemes to assign vulnerability identification numbers to identify vulnerabilities.

- JVN# + 8-digit
  - Vulnerability information coordinated and published under the Information Security Early Warning Partnership
- JVNVU# + 8-digit
  - Collaboration with other overseas adjustment agencies and overseas product developers
- JVNTA# + 8-digit
  - Attention seeking information issued by JPCERT/CC if necessary, with or without adjustment

#### 3) National center of Incident readiness and Strategy for Cybersecurity, Japan (NISC)

In accordance with the Basic Act on Japanese Cyber Security, the Cyber Security Strategy Headquarters was established in the Japanese Cabinet, and at the same time, NISC was established in the Japanese Cabinet Secretariat.

NISC plans and implements cybersecurity strategies.

- Basic principles of cybersecurity strategy
  1. Ensuring free circulation of Information
     - In cyberspace, a world should be created and maintained in which the information sent is not unreasonably censored and unduly altered along the way to reach the intended recipient.
  2. Rule of law
     - As in real space, the rule of law should be carried out in cyberspace.
  3. Openness
     - Cyberspace should not be occupied by some actors and should always be open to those seeking participation
  4. Autonomy
     - Even if cyberspace threats become a task that needs to be addressed nationwide, it is impossible and inappropriate for the state to replace all the maintenance of order in cyberspace.
  5. Collaboration of diverse actors
     - All stakeholders involved in cyberspace, such as key infrastructure operators, businesses, and individuals, need to strengthen their cybersecurity vision, fulfill their roles and responsibilities, and strive for themselves

#### 4) CRYPTography Research and Evaluation Committees (CRYPTREC)

CRYPTREC is a project to evaluate and monitor the safety of e-Government recommended ciphers and to investigate and examine the appropriate implementation and operation of cryptographic technology. CRYPTREC publishes three types of "List of Ciphers to Reference for Procurement in E-Government".

1. e-Government Recommended Cryptography List
   - This is a list of cryptographic technologies that CRYPTREC has confirmed safety and implementation performance, and it is considered that they have sufficient experience in the market or are expected to spread in the future.
2. Recommended Candidate Cryptography List
   - This is a list of cryptographic technologies that CRYPTREC has confirmed for safety and implementation performance and may appear on the e-Government recommended cipher list in the future.
3. Operational Monitoring Cryptography List
   - This is a list of cryptographic technologies that are no longer recommended to allow continuous use for compatibility.

#### 5) Initiative for Cyber Security Information sharing Partnership of Japan (J-CSIP)

J-CSIP is an initiative that IPA established with the cooperation of the Ministry of Economy, Trade and Industry as a place for information sharing and early response, focusing on manufacturers of equipment used in critical infrastructure such as heavy construction and heavy electricity. Overall, J-SCIP has established an information sharing system with eight Special Interest Group (SIG) and is in production.

#### 6) Cyber Rescue and Advice Team against targeted attack of Japan (J-CRAT)

J-CRAT is a cyber rescue team founded by IPA in 2014 to prevent damage from targeted cyberattacks. It is engaged in activities to help reduce damage to the organization and block the chain of attacks.

#### 7) Cyber Physical Security Framework

Cyber Physical Security Framework is a framework formulated by the Ministry of Economy, Trade and Industry that summarizes the overall security measures required by the industry.

It is designed to secure cybersecurity across the new supply chain in line with the concept of Society 5.0, which is realized by highly converging cyberspace and physical space, and Connected Industries, which creates new values by connecting people, goods, technologies, and organizations.

#### 8) NOTICE

NOTICE is a collaboration between the Ministry of Internal Affairs and Communications, NICT, and Internet providers to investigate devices that may be abused in cyberattacks by accessing IoT devices and to alert users of those devices.

#### 9) Network Incident analysis Center for Tactical Emergency Response (NICTER)

NICTER is a cyber attack observation and analysis system aimed at understanding the general trend of indiscriminate cyber attacks. It observes a large scale of unused, unallocated IP addresses called dark-net.

## II. Security Assessment

### 1. ISO/IEC 15408

ISO/IEC 15408 is an international standard for evaluating the security of IT-related products and information systems.

<u>Common Criteria (CC)</u> provides evaluation results that are useful for procurers to make decisions and enables comparison between independent security evaluation results, CC is mainly based on the following concept.

1. Securtiy Target (ST)
   - Basic security design document
   - Creating an ST is of paramount importance when developing a product or system.
2. Evaluation Assurance Level (EAL)
   - EAL provides warranty requirements for the product and is an objective measure of the security level of the product or system.
   - From EAL1 (guarantee of functional testing) to EAL7 (guarantee of formal design verification and testing), the higher the number, the more strict the degree of guarantee.

### 2. Payment Card Industry Data Security Standard (PCI DSS)

PCI DSS is a security standard in the credit card industry that aims to safely handle the data of credit card members.

PCI DSS certification can be obtained by obtaining certification after receiving examination and vulnerability inspection by an examination agency certified by PCI Security Standard Council (PCI SSC).

PCI DSSprovides a baseline of technical and operational controls, including 12 core requirements, for merchants and service providers to safeguard sensitive data, with compliance validated through assessments like scans or Self-Assessment Questionnaire (SAQ). 

1. **Build and Maintain a Secure Network & Systems:** 
   1. <u>Req 01.</u> Install and maintain firewall construction to protect card membership data.
   2. <u>Req 02.</u> Do not use vendor-provided default values for system passwords and other security parameters.
2. **Protect Cardholder Data:**
   1. <u>Req 03.</u> Protect stored card membership data
   2. <u>Req 04.</u> In the case of transmitting card member data via a public network, the data are encrypted.
3. **Maintain a Vulnerability Management Program:** 
   1. <u>Req 05.</u> Protect all systems from malware and regularly update antivirus software or programs
   2. <u>Req 06.</u> Develop and maintain secure systems and applications
4. **Implement Strong Access Control Measures:** 
   1. <u>Req 07.</u> To restrict access of card member data within a business necessary range.
   2. <u>Req 08.</u> Limit access to system components to the extent necessary for business purposes.
   3. <u>Req 09.</u> Restrict physical access to card membership data
5. **Regularly Monitor & Test Networks:**
   1. <u>Req 10.</u> Track and monitor all access to network resources and card membership data
   2. <u>Req 11.</u> Periodically test security systems and processes
6. **Maintain an Information Security Policy:**
   1. Req 12. Maintain comprehensive policies for all personnel. 

### 3. Security Content Automation Protocol (SCAP)

SCAP is a framework for automating security scanning, vulnerability management, and policy compliance, developed by NIST.

SCAP consists of six standard specifications.

1. Common Vulnerabilities and Exposures (CVE)
   - It is an identifier assigned by MITRE, a non-profit organization supported by the U.S. government, for vulnerabilities in individual products. 
   - Many of the vulnerability countermeasure information provision services use CVE.
2. Common Configuration Enumeration (CCE)
   - The CCE assigns a common identification number CCE-ID to the system setting information and identifies system information setting items related to security.
   - Using the identification number, data linkage between the vulnerability countermeasure information source and security export is realized.
3. Common Platform Enumeration (CPE)
   - Common name criteria for identifying hardware, software, and other information systems.
4. Common Vulnerability Scoring System (CVSS)
   - An open, comprehensive, and generic approach to assessment of vulnerabilities information systems.
   - CVSS allows quantitative comparisons of vulnerability severity under the same criteria. 
   - CVSS is v4.0 (released Nov 2023) as of Jan 2026.
     1. Base Metrics
        - point of view that evaluates the characteristics of the vulnerability itself
     2. Temporal Metrics
        - Find the CVSS AS-IS value from the perspective of assessing the current severity of the vulnerability.
        - In addition to the base values, use three criteria for evaluating the status quo: Exploitability (E), Remendiation (RL), and Report Confidence (RC).
     3. Environmental Metrics
        - Obtain CVSS environment values from a perspective that assesses the severity of the final vulnerability, including the user environment.
        - In addition to the AS-IS value, the calculation is based on values such as Collateral Damage Potential (CD) and Target Distribution (TD).
5. eXtensible Configuration Checklist Description Format (XCCDF)
   - XCCDF is a specification language for describing security checklists, benchmarks, etc.
6. Open Vulnerability and Assessment Language (OVAL)
   - OVAL is a specification for checking computer security settings.

### 4. Common Weakness Enumeration (CWE)

CWE is a common criterion for identifying types of security weaknesses (vulnerabilities) in software.A wide variety of vulnerabilities are classified and systematized in a hierarchical structure by granting CWE identifiers (CWE-IDs).It is classified into the following four categories.

- View
- Category
- Weakness
- Compound Element

### 5. Exploit Prediction Scoring System (EPSS)

EPSS has a scoring system for predicting the possibility of vulnerabilities being exploited. ESPP aggregates information on vulnerability abuse and calculates scores in the 0-1 range using machine learning algorithms.

### 6. Known Exploited Vulnerabilities Catalog (KEV Catalog)

KEV catalog is a list of known exploited vulnerabilities provided by the CISA. KEV catalog is linked to the CVE database and is used to identify registered vulnerabilities that have been identified for exploitation.

### 7. Knowledge Base

Knowledge base is a database or source of information that aggregates cybersecurity knowledge, know-how, examples, and best practices. Organizations are systematically organized so that they can quickly find and utilize information to help them with their security measures from Knowledge base.

1. Adversarial Tactics, Techniques, and Common Knowledge (MITRE ATT&CK)
   - MITRE ATT&CK is a knowledge base run by MITRE. It systematically classifies attack methods, tactics, and technologies for various cyber attacks and publishes them globally as a framework.
2. NIST SP800 Series
   - The NIST SP800 series is a set of security guidelines and standardized documents issued by the NIST. It summarizes information security best practices and risk management methods, and how security controls are implemented.

### 8. Vulnerability test

1. Penetration test
   - Penetration testing is a method of performing vulnerability testing by actually attacking and attempting to invade a system.
   - This test should be prepared with permission to attack and not impact the system from the attack
2. Port scanner
   - Port scanner is a tool for verifying unnecessary services among services running on a Web server.
3. Fuzzing
   - Fuzzing is an inspection method for vulnerabilities that developers do not recognize in software products. A vulnerability is detected by sending a large amount of problem-causing data and monitoring its response and behavior.

### 9.  Japan Security Assessment

#### 1) Information Security Management System (ISMS) Conformity Assessment System

ISMS Conformity Assessment System is the evaluation system of the Japan Institute for Promotion of Digital Economy and Community
(JIPDEC) that evaluates and certifies that a company's ISMS complies with JIS Q27001 (ISO/IEC27001). When an organization obtains ISMS certification, it can prove the reliability of information security externally.

- Certificate Authority: Check for ISMS compliance and register
- Personnel Certificate Authority: Qualifying ISMS Judges
- Recognized agency: an organization whose operational capabilities are recognized by the above two organizations

#### 2) Cyber Security Management System (CSMS) Conformity Assessment System

CSMS Conformity Assessment System is a cybersecurity management system for Industrial Automation and Control System (IACS). CSMS Conformity Assessment System  is a security management certification standard established to protect systems that control critical infrastructure and Compared to ISMS Conformity Assessment System, CSMS Conformity Assessment System requires specialization of control system.

#### 3) Japan Information Technology Security Evaluation and Certification Scheme (JISEC)

JISEC is a system that evaluates and certifies the appropriateness and certainty of security functions of IT-related products in accordance with ISO/IEC15408. There is a third-party evaluation agency for evaluation, and certification is performed through IPA.

#### 4) Japan Cryptographic Module Validation Program (JCMVP)

JCMVP is a cryptographic module authentication system and one of the product authentication systems operated by IPA. JCMVP evaluates and authenticates whether cryptographic modules consisting of hardware and software equipped with security functions such as encryption, hash, and signature functions properly protect security functions and important internal information.

#### 5) Security Action

Security Action is a system that self-declares countermeasures in line with SME information security measures.

## Reference

1. インプレス [徹底攻略 情報処理安全確保支援士教科書 令和8年度] ISBN 978-4295022893
2. Google Gemini
3. Wikipedia
   - https://www.wikipedia.org/
4. Cloud Flare [What is OWASP? What is the OWASP Top 10?]
   - https://www.cloudflare.com/learning/security/threats/owasp-top-10/