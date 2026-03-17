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
  <summary>Defensive Security Intro</summary>

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
