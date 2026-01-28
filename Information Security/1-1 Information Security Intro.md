# 1-1 Information Security Intro; Definition

[toc]

## I. Information Security Definition

### 1. Definition

Basically, the Information Security is to maintain Confidentiality, Integrity, Availability (<u>CIA Triad</u>).  Additionally, the Information Security contains Authenticity, Accountability, Non-Repudiation, Reliability.

#### 1) Confidentiality 

**Keeping data secret from unauthorized eyes**

Protecting information from unauthorized disclosure; only authorized users can view it, often achieved with encryption and access controls.

#### 2) Integrity

**Ensuring data is accurate and unaltered**

Ensuring data is trustworthy, complete, and hasn't been changed, corrupted, or tampered with, using methods like hashing and version control.

#### 3) Availability

**Guaranteeing authorized access when needed**

Making sure systems and data are accessible and usable by authorized entities when required, preventing disruptions thru backups, redundancy, and disaster recovery. 

#### 4) Authenticity

Ensuring data or communication is genuine and comes from the claimed source.

#### 5) Accountability

The ability to trace actions and events back to a specific entity, often thru logging and auditing.

#### 6) Non-Repudiation

Preventing users from falsely denying they sent or received data or performed an action, providing proof of origin or delivery.

#### 7) Reliability

Being consistent with the intended behavior and result.

### 2. Information Security Management System (ISMS)

A systematic framework of policies, processes, and controls (like those in ISO 27001) that helps organizations manage and protect their sensitive data, ensuring its CIA Triad.![pdca-cycle](.\imgs\pdca-cycle.jpg)

## II. Types and Framework of Information Security

### 1. Information security measure

#### 1) Technical security measure

- Entry point security: Measures to prevent unauthorized access and malware intrusion from outside
- Exit point Security: Final defense line measures to prevent leakage of confidential information after entry or from inside
- Defense in Depth: Tiered combination of security measures

#### 2) Human Security measure

The "human element," focusing on employee behavior, awareness, and training to mitigate risks like social engineering, insider threats, and accidental data breaches. 

#### 3)  Physical Security measure

To protect tangible assets—premises, equipment, and personnel—from physical threats like theft, vandalism, or environmental hazards. Securing offices, locking up laptops, and safe disposal of sensitive data...

### 2. 4 method of Information security measure

#### 1) Prevention

- Information security training
- Back-up
- Updates measures before and after accidents

#### 2) Defense

- Preventing incidents from threats
- Defending against real attacks

#### 3) Detection/Tracking: 

- Access Log Check
- IDS (Intrusion Detection System)
- Introduction of forensics Systems

#### 4) Recovery

- Quick Response to Accidents
- BCP (Business Continuity Planning)

### 3. Information assets

#### 1) Definition

Valuable data, knowledge, or information resources (digital or physical) that an organization owns, manages, and uses for operations, decision-making, and strategy.

#### 2) Threats

Threats are potential causes of accidents that are likely to damage systems or organizations.

- Intentional man-made threats: eavesdropping, falsification, unauthenticated access, theft, spoofing, inaction, virus infection, ...

- Accidental man-made threats: bugs, file misdeletion, Careless, ...

- Environmental threats: earthquakes, floods, lightning strikes, fires, typhoons, ...

#### 3) Vulnerability

Vulnerability is a weakness of an asset that a threat can penetrate.

#### 4) Risk

Risk is the possibility that a threat will cause damage by exploiting vulnerability.

R: Size of Information Security Risk 

A: Value of Information Assets / T: Size of Threats / V: Degree of Vulnerability
$$
R = A \times T \times V
$$

## III. Fraud and Attack Mechanism

### 1. Fraud Mechanism (Fraud Triangle Theory)

The Fraud Triangle Theory, developed by Donald Cressey, explains that fraud occurs when three elements converge:

- Opportunity:  Weak internal controls allowing the act.
- Pressure: Financial or emotional incentive or motivation to commit fraud.
- Rationalization: The ability to justify the dishonest behavior as acceptable.

![fraud-triad](.\imgs\fraud-triad.png)

### 2. Situational Crime Prevention (SCP)

1. **Increase Effort:** Make it harder (e.g., stronger locks, ID cards).
2. **Increase Risk:** Make detection more likely (e.g., CCTV, guards, good lighting).
3. **Reduce Rewards:** Make the loot less valuable (e.g., marking property, removable car stereos).
4. **Reduce Provocations:** Remove triggers (e.g., managing crowds, reducing temptation).
5. **Remove Excuses:** Eliminate justifications (e.g., clear signage about rules). 

### 3. Types of Attackers

1. **Script kiddie**: An unskilled individual who uses malicious scripts or programs developed by others.
2. **Bot herder**: A hacker who use automated techniques to scan specific network ranges and find vulnerable systems, such as machines without current security patches, on which to install their bot program.
3. **Insider**:  a trusted individual (employee, contractor, partner) misusing authorized access to harm an organization's data or systems, either maliciously (theft, sabotage) or unintentionally (phishing, errors).
4. Criminal: one's own pleasure purpose or phishing, extortion such as fraud or intentional crimes, etc.

### 4. motive of attack

1. Extortion: An attack for ill-gotten gains.
2. Hacktivism: Hacking as a form of civil disobedience to promote a political agenda or social change.
3. Cyberterrorism: Using computer networks to cause destruction, fear, or significant harm, often for political or ideological reasons, targeting critical infrastructure like utilities, financial systems, or government networks.

### 5. White hat Hacker

A white hat hacker, or ethical hacker is a cybersecurity expert who uses hacking skills legally and with permission to find and fix security vulnerabilities in systems, networks, and software, protecting organizations from malicious (black hat) hackers by identifying weaknesses before they can be exploited.

### 6. Security Framework; The Cyber Kill Chain

The Cyber Kill Chain is developed by Lockheed Martin, that breaks down cyberattacks into seven distinct stages—<u>Reconnaissance, Weaponization, Delivery, Exploitation, Installation, Command & Control (C&C), and Actions on Objectives</u>—to help organizations understand, detect, and prevent intrusions by disrupting the attack at any point.

| #    | Stage                 | Concept                                                      |
| ---- | --------------------- | ------------------------------------------------------------ |
| 1    | Reconnaissance        | The attacker gathers information about the target (e.g., public records, social media, network scanning). |
| 2    | Weaponization         | Coupling exploit with backdoor into deliverable payload.     |
| 3    | Delivery              | Delivering weaponized bundle to the victim via e-mail, web, USB, etc. |
| 4    | Exploitation          | Exploiting a vulnerability to execute code on victim's system. |
| 5    | Installation          | Installing malware on the asset.                             |
| 6    | Command & Control     | Command channel for remote manipulation of victim            |
| 7    | Actions on Objectives | With 'Hands on Keyboard' access, Intruders accomplish their original goals. |

## Reference

1. インプレス [徹底攻略 情報処理安全確保支援士教科書 令和8年度] ISBN 978-4295022893
2. Google Gemini
3. Wikipedia
   - https://www.wikipedia.org/
4. Lockheed Martin [Cyber Kill Chain]
   - https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html

