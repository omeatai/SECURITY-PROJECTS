## 1-Introduction to Cyber Security

<details>
  <summary>Offensive Security Intro</summary>

## Introduction

"To outsmart a hacker, you need to think like one." This is the core of **Offensive Security**. It involves breaking into computer systems, exploiting software bugs, and finding loopholes in applications to gain unauthorized access. The goal is to understand hacker tactics and enhance system defences.

In this TryHackMe lesson, you are guided through hacking your first website in a legal and safe environment to see how an ethical hacker operates. The room uses a fake bank application (FakeBank) that you can safely attack using tools like Gobuster to find hidden pages and perform a simulated bank transfer.

## Detailed Explanation

- [x] **What is Offensive Security?**
  - Simulating a hacker's actions to find vulnerabilities in a system
  - Breaking into systems, exploiting bugs, and finding loopholes to gain unauthorized access
  - Goal: understand attacker tactics to improve defences
- [x] **TryHackMe and Virtual Machines**
  - VMs create simulated environments as practical complements to lessons
  - FakeBank is a prepared fake bank application for safe, legal practice
  - Start the machine via "Start Machine" (or "Show Split View" if needed)
- [x] **Your First Hack – Tool and Steps**
  - **Gobuster**: command-line tool to brute-force a website for hidden directories and pages
  - Takes a wordlist and tries each word against the site; reports existing pages (e.g. Status 200)
- [x] **Step 1: Open a terminal**
  - Terminal (command line) lets you interact with the computer without a GUI
  - On the room machine, open the terminal from the Terminal icon
- [x] **Step 2: Use Gobuster to find hidden pages**
  - Many sites have admin or internal pages (e.g. admin portal, bank transfers)
  - Human error or negligence can leave these pages reachable; attackers look for them
  - Gobuster scans the target URL with a wordlist to discover existing paths
- [x] **Step 3: Hack the bank**
  - Use Gobuster results (e.g. `/bank-transfer`) and visit the hidden page in the browser
  - From there, an attacker could abuse functionality (e.g. transfer money)
  - Ethical hackers find and report such issues so the organisation can fix them
  - Room task: transfer $2000 from account 2276 to 8881, then confirm balance on your account page (refresh if needed)
- [x] **Learning path and careers**
  - Break topics down, focus on an area you like, and practice regularly (e.g. daily on TryHackMe)
  - Example offensive roles: Penetration Tester (find exploitable vulnerabilities), Red Teamer (simulate adversary), Security Engineer (design and maintain security controls)

## Terminal Commands

Gobuster is used to discover hidden directories and pages on a target website. `-u` sets the target URL and `-w` specifies the wordlist; `dir` runs directory/file brute-force mode.

```bash
gobuster -u http://fakebank.thm -w wordlist.txt dir
```

Example output:

```text
=====================================================
Gobuster v2.0.1              OJ Reeves (@TheColonial)
=====================================================
[+] Mode         : dir
[+] Url/Domain   : http://fakebank.thm/
[+] Threads      : 10
[+] Wordlist     : wordlist.txt
[+] Status codes : 200,204,301,302,307,403
[+] Timeout      : 10s
=====================================================
/images (Status: 301)
/bank-transfer (Status: 200)
=====================================================
```

Status 200 indicates a page that exists and was successfully accessed. Use discovered paths (e.g. `/bank-transfer`) in the browser to continue the exercise.

## Code

No code sections in this room; the activity uses terminal commands (Gobuster) and the web interface only.

## Questions and Answers

### Question 1: Which process involves simulating a hacker's actions to find vulnerabilities in a system?

<details>
<summary>Answer</summary>
Offensive Security.
</details>

### Question 2: What is the main goal of offensive security?

<details>
<summary>Answer</summary>
To understand hacker tactics and enhance system defences by finding and exploiting vulnerabilities in a controlled way.
</details>

### Question 3: What role do Virtual Machines play in this TryHackMe room?

<details>
<summary>Answer</summary>
They provide simulated environments that complement the lesson so you can practice hacking (e.g. FakeBank) in a legal, safe setting.
</details>

### Question 4: What is Gobuster used for in this room?

<details>
<summary>Answer</summary>
Gobuster is a command-line tool used to brute-force a website for hidden directories and pages by trying words from a wordlist against the target URL.
</details>

### Question 5: What do the flags `-u` and `-w` mean in the Gobuster command?

<details>
<summary>Answer</summary>
`-u` specifies the target website URL to scan; `-w` specifies the path to the wordlist file used for brute-forcing directory/page names.
</details>

### Question 6: What does Status 200 in Gobuster output indicate?

<details>
<summary>Answer</summary>
The page or directory exists and returned a successful HTTP response (OK), so it is a valid, reachable path on the target.
</details>

### Question 7: Why might hidden pages like admin or bank-transfer be dangerous if left exposed?

<details>
<summary>Answer</summary>
They can give attackers access to sensitive functions (e.g. admin controls or money transfers) due to human error or negligence in access control.
</details>

### Question 8: What is the hidden page you are directed to find and use in the FakeBank task?

<details>
<summary>Answer</summary>
The secret bank transfer page: `/bank-transfer`.
</details>

### Question 9: In the room task, which accounts are involved in the transfer?

<details>
<summary>Answer</summary>
Transfer $2000 from account 2276 to your account (account number 8881).
</details>

### Question 10: How should an ethical hacker use a vulnerability like an exposed bank-transfer page?

<details>
<summary>Answer</summary>
With permission, find the vulnerability, demonstrate impact, and report it to the organisation (e.g. the bank) so they can fix it before a malicious hacker exploits it.
</details>

### Question 11: What is a Penetration Tester's main responsibility?

<details>
<summary>Answer</summary>
Testing technology products to find exploitable security vulnerabilities.
</details>

### Question 12: How does a Red Teamer differ from a typical penetration tester?

<details>
<summary>Answer</summary>
A Red Teamer acts as an adversary, attacking the organisation and providing feedback from an attacker’s perspective, often in broader, more realistic scenarios.
</details>

### Question 13: What does a Security Engineer typically focus on?

<details>
<summary>Answer</summary>
Designing, monitoring, and maintaining security controls, networks, and systems to help prevent cyberattacks.
</details>

### Question 14: What is the recommended way to start learning cybersecurity on TryHackMe?

<details>
<summary>Answer</summary>
Break topics down, choose an area of interest, and practice regularly with hands-on exercises—for example, building a habit of learning a little each day on TryHackMe.
</details>

### Question 15: Where do you confirm that your FakeBank transfer succeeded?

<details>
<summary>Answer</summary>
On your account page; refresh the page if needed to see the updated balance.
</details>

## Summary

Offensive Security is about thinking like an attacker to find and fix weaknesses. This room introduces the idea by having you use Gobuster to find a hidden bank-transfer page on FakeBank, then perform a simulated transfer. You use the terminal (Gobuster with `-u` and `-w`), interpret results (e.g. Status 200), and complete the task in the browser. The room also briefly covers learning habits and offensive roles such as Penetration Tester, Red Teamer, and Security Engineer.

## References

- [Offensive Security Intro – TryHackMe](https://tryhackme.com/room/offensivesecurityintro)

</details>

<details>
  <summary>Defensive Security Intro</summary>

## Introduction

In the previous lesson, you focused on offensive security: identifying and exploiting vulnerabilities to strengthen defences. This lesson introduces **defensive security**, which is primarily concerned with **preventing intrusions** and **detecting and responding to them** when they occur. Blue teams operate on the defensive side, using processes, tools, and analysis to protect systems and data.

Defensive security spans tasks such as user awareness training, asset management, patching, deploying firewalls and IPS, enabling logging and monitoring, and running specialised functions like SOC operations, threat intelligence, DFIR, and malware analysis.

## Detailed Explanation

- [x] **What is Defensive Security?**
  - Focused on preventing intrusions from occurring
  - Detecting intrusions when they occur and responding properly
  - Typically associated with blue teams and defence-focused roles
- [x] **Core Defensive Tasks**
  - User cyber security awareness: training users to resist attacks targeting their systems
  - Documenting and managing assets: knowing what systems/devices you must protect
  - Updating and patching systems: closing known vulnerabilities across endpoints and servers
  - Setting up preventative devices: firewalls and IPS to filter and block malicious traffic
  - Logging and monitoring: collecting logs and monitoring for suspicious or unauthorized activity
- [x] **Security Operations Center (SOC)**
  - Team of security professionals monitoring networks and systems for malicious events
  - Watches for vulnerabilities, policy violations, unauthorized activity, and intrusions
  - Often uses SIEM tools to aggregate events and generate alerts
- [x] **Threat Intelligence**
  - Intelligence = information about current and potential adversaries and threats
  - Collects data from local (e.g. network logs) and public (e.g. forums) sources
  - Processes and analyzes data to understand adversaries’ tactics, techniques, and procedures (TTPs)
  - Outputs recommendations and actionable steps to achieve threat‑informed defence
- [x] **Digital Forensics and Incident Response (DFIR)**
  - Digital forensics: investigates evidence of attacks and related crimes
  - Key evidence sources: file system images, memory dumps, system logs, network logs
  - Incident response: methodology to handle cyber incidents to reduce damage and recover quickly
  - Four main IR phases: Preparation; Detection and Analysis; Containment, Eradication and Recovery; Post‑Incident Activity
- [x] **Malware and Malware Analysis**
  - Malware = malicious software (virus, trojan horse, ransomware, etc.)
  - Viruses attach to programs and spread, altering/overwriting/deleting files
  - Trojans appear legitimate but hide malicious functionality
  - Ransomware encrypts files and demands payment for decryption
  - Static analysis: study malware without running it (often at assembly level)
  - Dynamic analysis: run malware in a controlled environment and observe behaviour
- [x] **Defensive Work in Practice (SOC Scenario)**
  - SOC analysts triage SIEM alerts, distinguishing benign from malicious activity
  - Examples: multiple failed logins (possibly user error or brute force), connections from unknown IPs
  - Analysts investigate, correlate events, and identify indicators such as flags (e.g. `THM{THREAT-BLOCKED}`) during exercises

## Terminal Commands

This room is largely conceptual and interface‑driven (SIEM simulation, dashboards) rather than command‑line heavy; there are no specific terminal commands required beyond interacting with the training environment.

```bash
# No primary terminal command focus in this defensive room
```

## Code

There is no code implementation focus in this lesson. Instead, it emphasises processes (SOC, DFIR, IR phases) and analysis of alerts, logs, and malware behaviour.

```py
# No code samples for this defensive security introduction
```

## Questions and Answers

### Question 1: Which team focuses on defensive security?

<details>
<summary>Answer</summary>
The blue team focuses on defensive security.
</details>

### Question 2: What are the two primary goals of defensive security?

<details>
<summary>Answer</summary>
To prevent intrusions from occurring and to detect and respond properly when intrusions do occur.
</details>

### Question 3: Why is user cyber security awareness important for defence?

<details>
<summary>Answer</summary>
Because many attacks target end users; training them reduces risks from phishing, unsafe downloads, and other user‑driven threats.
</details>

### Question 4: Why must assets be documented and managed in defensive security?

<details>
<summary>Answer</summary>
You can only adequately protect systems and devices if you know what you own, where they are, and how critical they are.
</details>

### Question 5: What is the role of firewalls and intrusion prevention systems (IPS) in defence?

<details>
<summary>Answer</summary>
Firewalls control what traffic can enter or leave a network; IPS blocks network traffic that matches rules or attack signatures to stop malicious activity.
</details>

### Question 6: Why are logging and monitoring critical in defensive security?

<details>
<summary>Answer</summary>
They enable detection of malicious activities and intrusions, such as new unauthorized devices or suspicious connections, by providing visibility into network and system events.
</details>

### Question 7: What is a Security Operations Center (SOC)?

<details>
<summary>Answer</summary>
A team of cyber security professionals that monitors networks and systems to detect and respond to malicious events, often supported by tools like SIEMs.
</details>

### Question 8: Give an example of a policy violation a SOC might care about.

<details>
<summary>Answer</summary>
For example, users uploading confidential company data to an online storage service in violation of security policy.
</details>

### Question 9: What is threat intelligence in the context of defensive security?

<details>
<summary>Answer</summary>
Threat intelligence is the collection, processing, and analysis of data about adversaries and threats to inform better defences and response strategies.
</details>

### Question 10: Why does threat intelligence need data from both local and public sources?

<details>
<summary>Answer</summary>
Local sources (like logs) show what is happening in your environment, while public sources (like forums and reports) reveal wider adversary behaviour and emerging threats; together, they give a fuller picture.
</details>

### Question 11: What are some key evidence sources used in digital forensics?

<details>
<summary>Answer</summary>
File system images, system memory dumps, system logs, and network logs.
</details>

### Question 12: What is the main aim of incident response?

<details>
<summary>Answer</summary>
To reduce damage from an incident and recover affected systems as quickly and effectively as possible.
</details>

### Question 13: Name the four main phases of the incident response process.

<details>
<summary>Answer</summary>
Preparation; Detection and Analysis; Containment, Eradication and Recovery; Post‑Incident Activity.
</details>

### Question 14: What is ransomware and how does it impact victims?

<details>
<summary>Answer</summary>
Ransomware is malware that encrypts a user’s files and demands payment (a ransom) in exchange for the decryption key, denying access to data until the ransom is paid or recovery is performed.
</details>

### Question 15: How does a trojan horse differ from a typical virus?

<details>
<summary>Answer</summary>
A trojan horse appears to offer a legitimate or desirable function but secretly performs malicious actions, whereas a virus attaches to other programs and replicates by infecting additional files or systems.
</details>

### Question 16: What is static malware analysis?

<details>
<summary>Answer</summary>
It is analysing malware without executing it, often by examining its code or binary, and typically requires knowledge of low‑level instructions like assembly.
</details>

### Question 17: What is dynamic malware analysis?

<details>
<summary>Answer</summary>
Running malware in a controlled environment and monitoring its behaviour, such as file changes, network connections, and process activity.
</details>

### Question 18: In the SIEM simulation scenario, what is the purpose of the flag `THM{THREAT-BLOCKED}`?

<details>
<summary>Answer</summary>
It serves as proof that you successfully followed the investigation steps in the simulated SIEM environment and identified the correct malicious activity or outcome.
</details>

## Summary

This lesson shifts from attacking to defending, showing how blue teams work to prevent, detect, and respond to threats. You learned about defensive tasks such as awareness, asset management, patching, firewalls and IPS, logging and monitoring, and specialised areas like SOC operations, threat intelligence, DFIR, and malware analysis. The scenario with a SIEM and alerts illustrates how analysts triage events and identify real threats. Together, these concepts form the foundation of a robust, threat‑informed defensive posture.

## References

- [Defensive Security Intro – TryHackMe](https://tryhackme.com/room/defensivesecurityintro)

</details>

<details>
  <summary>Defensive Security Intro 2</summary>

## Introduction

This TryHackMe room introduces defensive security from the defender’s point of view. Rather than attacking systems, you focus on monitoring, detecting suspicious activity, and responding to potential attacks before damage occurs. In this exercise, you work with a simulated monitoring dashboard to review alerts, identify malicious behaviour, and take action to stop an attack against a fake bank.

## Detailed Explanation

- [x] **Goal of Defensive Security**
  - Defensive security is the process of defending and securing devices and systems.
  - The main goal is to detect and respond to attacks before they cause harm.
  - Unlike offensive security, you do not attack systems; you monitor and protect them.
- [x] **Understanding Suspicious Activity and Alerts**
  - Activity that does not look normal is considered suspicious and is captured as alerts.
  - Defenders review alerts to decide what needs deeper investigation.
  - The monitoring dashboard in this room represents a real-world tool used in SOC environments.
- [x] **Working with the Monitoring Dashboard**
  - You open the monitoring dashboard on the provided virtual machine.
  - You review recent alerts to spot unusual traffic patterns or IPs.
  - One of the core tasks is identifying the suspicious source IP address.
- [x] **Identifying the Attack**
  - After spotting suspicious activity, defenders determine what kind of attack is taking place.
  - The room provides a “URL Discovery Attempts” list where you can see what URLs the attacker is probing.
  - By reviewing the latest entry, you learn which sensitive URL the attacker is trying to access.
- [x] **Stopping and Containing the Attack**
  - Once the attack is understood, defenders can block the attacker’s IP address.
  - Additional measures include applying rate limits so no one can overwhelm the system.
  - Updating security rules and adding defensive controls help prevent similar attacks in the future.
  - Stopping the attacker while you investigate and fix vulnerabilities is known as containment.

## Terminal Commands

This room is primarily focused on using a graphical monitoring dashboard and simulated controls rather than running terminal commands. You interact with the interface to view alerts, identify the malicious IP, and apply blocking and rate-limiting actions.

```bash
# No primary terminal command focus in this defensive room;
# actions are taken via the monitoring dashboard UI.
```

## Code

There is no specific code implementation in this exercise. The emphasis is on understanding alerts, recognising suspicious behaviour, and applying defensive actions (blocking IPs, rate limiting, updating rules) through the simulated environment.

```py
# No code samples for this defensive security exercise
```

## Questions and Answers

### Question 1: What is the main goal of defensive security?

<details>
<summary>Answer</summary>
The main goal of defensive security is to detect and respond to attacks before they cause damage to systems or data.
</details>

### Question 2: How does defensive security differ from offensive security in this context?

<details>
<summary>Answer</summary>
In defensive security you monitor and protect systems, focusing on detection and response, whereas in offensive security you actively attempt to exploit systems to find weaknesses.
</details>

### Question 3: What type of information is stored as an alert in the monitoring system?

<details>
<summary>Answer</summary>
Alerts store pieces of information about suspicious or unusual activity observed on the system or network.
</details>

### Question 4: Which source IP address is generating the suspicious traffic in this room?

<details>
<summary>Answer</summary>
The suspicious traffic is generated by the source IP address `32.122.195.63`.
</details>

### Question 5: Where in the dashboard do you look to understand what URLs the attacker is trying to access?

<details>
<summary>Answer</summary>
You look at the “URL Discovery Attempts” list and review the latest entry.
</details>

### Question 6: What is the latest URL that the attacker has attempted to access?

<details>
<summary>Answer</summary>
The latest URL the attacker tried to find is `https://fakebank.com/admin`.
</details>

### Question 7: Why do defenders care about URLs like `/admin` on a banking site?

<details>
<summary>Answer</summary>
Such URLs often expose administrative or sensitive functionality; if attackers discover and exploit them, they may gain powerful access or control over the system.
</details>

### Question 8: What defensive actions do you take once the attack has been identified?

<details>
<summary>Answer</summary>
You block the attacker’s IP address, apply rate limits to prevent overwhelming traffic, update security rules, and add additional measures to prevent the attack from recurring.
</details>

### Question 9: What is meant by containment in the context of this exercise?

<details>
<summary>Answer</summary>
Containment means stopping the attacker from continuing (for example, by blocking their IP and limiting traffic) while you investigate and remediate underlying vulnerabilities.
</details>

### Question 10: What flag do you receive after successfully applying the defensive measures?

<details>
<summary>Answer</summary>
You receive the flag `THM{FAKEBANK-SECURED}` once the success message appears after stopping the attack.
</details>

### Question 11: Why is reviewing recent alerts an important first step for defenders?

<details>
<summary>Answer</summary>
Reviewing recent alerts helps defenders quickly spot abnormal activity that may indicate an ongoing or emerging attack, allowing them to prioritise investigations and responses.
</details>

### Question 12: How does this room simulate real-world defensive work?

<details>
<summary>Answer</summary>
It uses a virtual machine and monitoring dashboard to replicate how defenders review alerts, investigate suspicious IPs and URLs, and apply controls like blocking and rate limiting to protect a production-like system.
</details>

## Summary

In this TryHackMe room, you approach security from the defender’s perspective. You monitor a simulated banking environment, review alerts, identify a suspicious source IP and an attacker probing an admin URL, and then apply defensive actions such as IP blocking, rate limiting, and updating rules. The exercise reinforces the core idea that defensive security is about early detection, investigation, and containment of attacks to keep systems secure.

## References

- [Defensive Security Intro – TryHackMe](https://tryhackme.com/room/defensivesecurityintro)

</details>

<details>
  <summary>Careers in Cyber</summary>

## Introduction

The **Careers in Cyber** TryHackMe room gives an overview of key cyber security roles and why this field is attractive. Cyber security careers are in high demand, offer competitive salaries, and span a wide range of roles—from defending systems and responding to incidents, to analysing malware and legally hacking systems. This room outlines what different roles do, their responsibilities, and suggested learning paths and career resources.

## Detailed Explanation

- [x] **Why get a career in cyber?**
  - High pay: security roles often have high starting salaries.
  - Exciting work: can include legally hacking systems or defending against live cyber attacks.
  - Strong demand: there are over 3.5 million unfilled cyber positions globally.
  - This room links to learning paths that help you build the skills needed for these roles.
- [x] **Security Analyst**
  - Responsible for maintaining the security of an organisation’s data.
  - Works with stakeholders to understand security requirements and the threat landscape.
  - Analyses networks and systems to identify weaknesses and inform defensive improvements.
  - Compiles ongoing reports about network safety, security issues, and responses.
  - Develops security plans based on research into new attack tools, trends, and required controls.
  - Learning Paths:
    - Pre Security
    - Cyber Security 101
    - SOC Level 1
  - Career Guides: Becoming a Cyber Security Analyst, How to Become a Level 1 SOC Analyst, A Day in the Life of a SOC Analyst, The Ultimate SOC L1 Analyst Interview Guide, Hayden’s Success Story.
- [x] **Security Engineer**
  - Designs, monitors, and maintains security controls, networks, and systems to help prevent cyberattacks.
  - Uses threat and vulnerability data from across the security team to build and tune defences.
  - Tests and screens security measures across software and infrastructure.
  - Monitors networks and reports to update systems and mitigate vulnerabilities.
  - Identifies and implements systems needed for optimal security posture.
  - Learning Paths:
    - SOC Level 1
    - Jr Penetration Tester
    - Offensive Pentesting
  - Career Guides: Becoming a Security Engineer, How to Become a Security Engineer, A Day in the Life of a Security Engineer, Preparing for a Security Engineering Interview, Richárd’s Success Story.
- [x] **Incident Responder**
  - Identifies and mitigates attacks while the attacker’s operations are still unfolding.
  - Creates and maintains incident response plans, policies, and procedures.
  - Works under pressure, assessing and responding to security breaches in real time.
  - Uses metrics such as MTTD (Mean Time To Detect), MTTA (Mean Time To Acknowledge), and MTTR (Mean Time To Recover) to measure effectiveness.
  - Aims to minimise damage, protect data and reputation, and support rapid recovery.
  - Learning Paths:
    - SOC Level 1
- [x] **Digital Forensics Analyst**
  - Uses digital forensics to investigate incidents and crimes.
  - In law enforcement contexts, collects and analyses evidence to help solve crimes, charge the guilty, and exonerate the innocent.
  - In corporate contexts, investigates policy violations and internal incidents.
  - Responsibilities include:
    - Collecting digital evidence while following legal and procedural requirements.
    - Analysing digital evidence to answer case-related questions.
    - Documenting findings and reporting on the case for legal or internal use.
- [x] **Malware Analyst**
  - Analyses all types of malware to understand how they work and what they do.
  - Often called a reverse engineer, focusing on converting compiled programs into readable low-level code.
  - Requires strong programming skills, especially in low-level languages like assembly and C.
  - Responsibilities include:
    - Performing static analysis (reverse engineering) of malicious programs.
    - Conducting dynamic analysis by running malware samples in a controlled environment.
    - Documenting and reporting findings, including detection and mitigation recommendations.
- [x] **Penetration Tester**
  - Tests technology products for security loopholes; also known as a pentester or ethical hacker.
  - Attempts to uncover and exploit vulnerabilities in systems, networks, and applications.
  - Helps organisations understand risk so they can fix weaknesses before real attackers exploit them.
  - Responsibilities include:
    - Conducting tests on computer systems, networks, and web-based applications.
    - Performing security assessments, audits, and policy reviews.
    - Evaluating and reporting findings with recommended remediation steps.
  - Learning Paths:
    - Jr Penetration Tester
    - Offensive Pentesting
  - Career Guides: Becoming a Penetration Tester, How to Become a Penetration Tester, Junior Penetration Tester Interview prep, Tom’s Success Story from IT Support to Pentester.
- [x] **Red Teamer**
  - Plays the role of an adversary, attacking an organisation and providing feedback from an enemy’s perspective.
  - Similar to pentesters but with a more targeted focus on detection and response capabilities.
  - Emulates real-world adversaries: gaining access, maintaining persistence, and avoiding detection.
  - Assessments can run for weeks and are often performed by external specialist teams.
  - Best suited to organisations with mature security programs that want to test incident response and monitoring.
  - Responsibilities include:
    - Emulating threat actors to uncover exploitable weaknesses and test detection.
    - Assessing security controls, threat intelligence, and incident response processes.
    - Reporting insights with actionable recommendations to strengthen defences.
  - Learning Paths:
    - Jr Penetration Tester
    - Offensive Pentesting
    - Red Teamer
  - Career Guides: Red Teaming roles, salaries, and opportunities.

## Terminal Commands

This room is informational and career-focused; it does not centre on specific terminal commands. Instead, it introduces you to roles and suggests learning paths and resources that will later involve hands-on labs and command-line work.

```bash
# No primary terminal commands for this careers overview room.
```

## Code

There is no code to write or analyse in this room. The emphasis is on understanding job roles, not on implementing technical solutions directly within the exercise.

```py
# No code snippets for the Careers in Cyber room.
```

## Questions and Answers

### Question 1: Why are cyber security careers considered attractive?

<details>
<summary>Answer</summary>
They offer high starting pay, involve exciting work such as legally hacking systems or defending against attacks, and are in very high demand with millions of unfilled roles.
</details>

### Question 2: What is the main responsibility of a Security Analyst?

<details>
<summary>Answer</summary>
A Security Analyst maintains the security of an organisation’s data by analysing networks and systems, working with stakeholders, and recommending or supporting defensive measures.
</details>

### Question 3: Name two key responsibilities of a Security Analyst.

<details>
<summary>Answer</summary>
Compiling ongoing reports about network and data safety, and developing security plans based on research into new attack tools and trends.
</details>

### Question 4: What is the primary focus of a Security Engineer?

<details>
<summary>Answer</summary>
Designing, monitoring, and maintaining security controls, networks, and systems to help prevent cyberattacks.
</details>

### Question 5: How does an Incident Responder measure the effectiveness of their response?

<details>
<summary>Answer</summary>
Using metrics like MTTD (Mean Time To Detect), MTTA (Mean Time To Acknowledge), and MTTR (Mean Time To Recover) to track how quickly and effectively incidents are handled.
</details>

### Question 6: What is the core work of a Digital Forensics Analyst?

<details>
<summary>Answer</summary>
Collecting, analysing, and reporting on digital evidence related to incidents or crimes, while following legal and procedural requirements.
</details>

### Question 7: Why does a Malware Analyst need strong low-level programming skills?

<details>
<summary>Answer</summary>
Because they reverse engineer compiled malware into readable low-level code (often assembly or C) to understand exactly how it behaves.
</details>

### Question 8: What is the main goal of a Penetration Tester’s work?

<details>
<summary>Answer</summary>
To identify and safely exploit vulnerabilities in systems and applications so organisations can understand their risk and fix weaknesses before real attackers abuse them.
</details>

### Question 9: How does a Red Teamer differ from a typical Penetration Tester?

<details>
<summary>Answer</summary>
Red Teamers focus on emulating realistic adversaries to test an organisation’s detection and response capabilities over longer, more covert engagements, while pentesters typically focus on finding as many technical vulnerabilities as possible in a defined scope.
</details>

### Question 10: Why are Red Team assessments usually better suited to organisations with mature security programs?

<details>
<summary>Answer</summary>
Because they are designed to test and refine existing detection, intelligence, and incident response capabilities, which require a baseline of monitoring and processes already in place.
</details>

### Question 11: Which learning paths are suggested for someone aiming to become a Penetration Tester?

<details>
<summary>Answer</summary>
The Jr Penetration Tester and Offensive Pentesting learning paths.
</details>

### Question 12: What is one benefit of reading real-world career guides and success stories linked in this room?

<details>
<summary>Answer</summary>
They provide practical insight into what the roles are like day to day and concrete steps others took to break into the field, helping you plan your own path.
</details>

## Summary

The Careers in Cyber room outlines why cyber security is a high-opportunity field and introduces key roles such as Security Analyst, Security Engineer, Incident Responder, Digital Forensics Analyst, Malware Analyst, Penetration Tester, and Red Teamer. For each role, you learn the core responsibilities and how they contribute to defending organisations or understanding threats. The room also points you to TryHackMe learning paths and career guides so you can start building the practical skills and knowledge required for your target role.

## References

- [Careers in Cyber – TryHackMe](https://tryhackme.com/room/careersincyber)

</details>

## 2-Network Fundamentals


<details>
  <summary>What is Networking?</summary>

## Introduction

The **What is Networking?** TryHackMe room introduces networking from first principles and ties it to everyday examples. You learn that networks are simply things that are connected—whether that is a city’s transport system, the power grid, or computing devices like phones and laptops. The room then scales up to explain the Internet, IP and MAC addressing, IPv4 vs IPv6, and basic tools like `ping`, all of which are foundational for later cyber security work.

## Detailed Explanation

- [x] **What is a Network?**
  - A network is a collection of things that are connected.
  - Everyday examples include public transport systems, power grids, postal systems, and social circles.
  - In computing, the same concept applies to technological devices that communicate and share data.
  - Networks in computing can range from 2 devices to billions (laptops, phones, cameras, traffic lights, farming sensors, etc.).
  - Because networks underpin so many aspects of modern life, understanding networking is essential in cyber security.
- [x] **The Internet as a Giant Network**
  - The Internet is a giant network made up of many smaller networks.
  - The room uses an example of Alice, Bob, Jim, and new friends Zayn and Toby to show how someone who can speak multiple “languages” can connect groups together.
  - Historically, ARPANET in the late 1960s was an early network funded by the U.S. Defence Department.
  - In 1989, Tim Berners-Lee created the World Wide Web (WWW), transforming the Internet into a global information repository.
  - The Internet can be seen as many small **private networks** interconnected by **public networks**.
- [x] **Private vs Public Networks**
  - A **private network** is a smaller network (e.g. your home or office network) where devices communicate with one another.
  - A **public network** (the Internet) connects many private networks together.
  - Devices use labels to identify themselves, enabling ordered communication.
  - The room emphasises that devices must be identifiable, similar to how people are identified by names and fingerprints.
- [x] **IP Addresses**
  - Devices have two main identifiers:
    - An **IP address** (Internet Protocol address) that can change over time.
    - A **MAC address** that is more permanent (like a serial number).
  - An IPv4 address is made up of four sections called **octets**.
  - IP addressing & subnetting determine how these numbers are allocated, but the key idea is that one IP cannot be active on more than one device inside the same network at the same time.
  - IP addresses follow protocols so that devices can “speak the same language”.
  - Devices can have:
    - A **private IP address** used within a local network.
    - A **public IP address** used on the Internet, typically assigned by an ISP.
- [x] **Public and Private IP Examples**
  - Example devices:
    - `DESKTOP-KJE57FD` with private `192.168.1.77` and public `86.157.52.21`.
    - `CMNatic-PC` with private `192.168.1.74` and the same public `86.157.52.21`.
  - Both devices can communicate privately using their private IP addresses.
  - When either device accesses the Internet, the public IP (from the ISP) is what outside services see.
  - Public IPs are scarce and managed because of the huge number of connected devices.
- [x] **IPv4 vs IPv6**
  - IPv4 supports about \(2^{32}\) addresses (~4.29 billion), which is not enough for the projected number of devices.
  - Cisco estimated tens of billions of devices would be online, making address exhaustion a real problem.
  - IPv6 is a newer protocol version providing up to \(2^{128}\) addresses (340 trillion-plus), solving the exhaustion issue.
  - IPv6 also introduces more efficient methodologies, though the addressing format looks more complex.
- [x] **MAC Addresses**
  - Every network interface has a physical network interface card (NIC) with a factory-assigned **MAC address**.
  - A MAC address is a 12-character hexadecimal number split by colons (e.g. `a4:c3:f0:85:ac:2d`).
  - The first half (OUI) identifies the manufacturer; the second half is a unique identifier.
  - MAC addresses can be **spoofed**, where a device pretends to be another by copying its MAC.
  - Poor security that relies only on MAC-based trust can be bypassed by spoofing.
- [x] **MAC Filtering and Guest Wi-Fi Scenario**
  - Cafes, hotels, and similar locations often use MAC address control on guest/public Wi‑Fi.
  - They may grant better service or access only to paid devices.
  - In the lab scenario, a router allows Alice’s paid device while discarding Bob’s packets.
  - Spoofing Bob’s MAC to match Alice’s shows how MAC control can be abused if used alone.
- [x] **Ping and ICMP**
  - `ping` is a fundamental network tool using ICMP (Internet Control Message Protocol).
  - It tests if a connection exists and how reliable it is by sending ICMP echo requests and waiting for echo replies.
  - Ping measures round-trip time and packet loss between devices.
  - It can be run against local devices (private IPs) or public resources (websites).
  - Example: pinging `192.168.1.254` and seeing multiple ICMP packets sent and received with an average time.
  - In the lab, you ping `8.8.8.8` to reveal a flag.

## Terminal Commands

The main command-line tool introduced is `ping`, which tests connectivity and latency between devices using ICMP.

```bash
# Basic ping syntax
ping 10.10.10.10

# Example from the room
ping 8.8.8.8
```

On most systems, `ping` will send multiple packets and show statistics including packets sent/received and average round-trip time.

## Code

This room focuses on conceptual networking foundations and simple command-line usage rather than programming. There are no specific code samples to implement; instead you practice using built-in tools like `ping` and visualise IP and MAC addressing.

```py
# No programming examples in this networking fundamentals room.
```

## Questions and Answers

### Question 1: In simple terms, what is a network?

<details>
<summary>Answer</summary>
A network is a collection of things that are connected—such as devices, people, or systems—that can communicate with each other.
</details>

### Question 2: What is the key term for devices that are connected together in computing?

<details>
<summary>Answer</summary>
The key term is a **network**.
</details>

### Question 3: Who invented the World Wide Web?

<details>
<summary>Answer</summary>
Tim Berners-Lee.
</details>

### Question 4: What are the two broad types of networks mentioned in the room?

<details>
<summary>Answer</summary>
Private networks and public networks (the Internet).
</details>

### Question 5: What does the term “IP” stand for?

<details>
<summary>Answer</summary>
Internet Protocol.
</details>

### Question 6: What is each section of an IPv4 address called, and how many sections are there?

<details>
<summary>Answer</summary>
Each section is called an **octet**, and there are 4 octets in an IPv4 address.
</details>

### Question 7: What is the difference between a private and a public IP address?

<details>
<summary>Answer</summary>
A private IP address identifies a device within a local/private network, while a public IP address identifies the network to the wider Internet and is assigned by an ISP.
</details>

### Question 8: Why was IPv6 introduced?

<details>
<summary>Answer</summary>
To provide a vastly larger address space and new efficiencies because IPv4’s ~4.29 billion addresses are insufficient for the growing number of connected devices.
</details>

### Question 9: What does the term “MAC” stand for and what is its purpose?

<details>
<summary>Answer</summary>
MAC stands for Media Access Control; it is a hardware address assigned to a device’s network interface to uniquely identify it on the data link layer.
</details>

### Question 10: What security risk is associated with relying solely on MAC addresses for access control?

<details>
<summary>Answer</summary>
MAC addresses can be spoofed, so an attacker can impersonate a trusted device and bypass simple MAC-based access controls.
</details>

### Question 11: In the hotel Wi‑Fi scenario, what happens when Bob spoofs Alice’s MAC address?

<details>
<summary>Answer</summary>
The router treats Bob’s traffic as if it were Alice’s paid device, allowing his packets through and granting him access he did not pay for.
</details>

### Question 12: What protocol does `ping` use, and what does it measure?

<details>
<summary>Answer</summary>
`ping` uses the Internet Control Message Protocol (ICMP) and measures connectivity and round‑trip time between devices.
</details>

### Question 13: What is the correct syntax to ping the IP address `10.10.10.10`?

<details>
<summary>Answer</summary>
The syntax is: `ping 10.10.10.10`.
</details>

### Question 14: What flag do you get when you ping `8.8.8.8` in the lab?

<details>
<summary>Answer</summary>
You receive the flag `THM{I_PINGED_THE_SERVER}`.
</details>

### Question 15: What is the flag obtained by spoofing your MAC address in the interactive Wi‑Fi lab?

<details>
<summary>Answer</summary>
The flag is `THM{YOU_GOT_ON_TRYHACKME}`.
</details>

## Summary

This room explains networking in both everyday and technical terms, showing that networks are simply collections of connected things. You learn how the Internet is a giant network made of many private and public networks, and how devices identify themselves using IP and MAC addresses. The room introduces IPv4 vs IPv6, demonstrates why MAC spoofing can undermine weak access controls, and shows how `ping` and ICMP are used to test connectivity. These fundamentals provide a base for understanding more advanced networking and cyber security concepts.

## References

- [What is Networking? – TryHackMe](https://tryhackme.com/room/whatisnetworking)
- [What is Networking? - Youtube Networking Basics] (https://www.youtube.com/watch?v=42u_2e6eNF4)

</details>
