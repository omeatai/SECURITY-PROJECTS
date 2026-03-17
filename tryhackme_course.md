# TRYHACKME.COM | [ONLINE](https://tryhackme.com/paths)

# A. PRE-SECURITY COURSE

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

<details>
  <summary>Intro to LAN</summary>

## Introduction

The **Intro to LAN** TryHackMe room builds on basic networking concepts by focusing on Local Area Networks (LANs). You learn about common LAN topologies (star, bus, ring), key devices like switches and routers, how subnetting divides a network into smaller pieces, and how ARP and DHCP support communication and address assignment. The room also uses interactive labs to show how topology flaws and misconfigurations can cause failures or be abused.

## Detailed Explanation

- [x] **LAN Topologies Overview**
  - A **topology** is the design or layout of a network—how devices are connected.
  - Different topologies have different costs, performance characteristics, and failure modes.
  - The room focuses on star, bus, and ring topologies.
- [x] **Star Topology**
  - Devices are individually connected to a central networking device (usually a switch or hub).
  - Advantages:
    - Very common in modern networks due to reliability and scalability.
    - Easy to add more devices as demand grows.
  - Disadvantages:
    - More expensive because it uses more cabling and dedicated equipment.
    - Increased size leads to more maintenance and harder troubleshooting.
    - The central device is a single point of failure—if it fails, connected devices cannot communicate.
- [x] **Bus Topology**
  - All devices connect to a single **backbone cable**, like leaves on a tree branch.
  - Advantages:
    - Cost-efficient and relatively simple to set up.
    - Requires less cabling and fewer dedicated devices than star topologies.
  - Disadvantages:
    - All data travels along the same cable, making it prone to bottlenecks when many devices send data at once.
    - Troubleshooting is difficult because all traffic shares one path.
    - The backbone cable is a single point of failure; if it breaks, all communication stops.
- [x] **Ring Topology**
  - Devices are connected in a loop, each attached to two neighbours.
  - Often called a **token** topology because a token can circulate to control whose turn it is to send.
  - Advantages:
    - Requires less cabling and less dependence on central hardware than star.
    - Easier to troubleshoot because there is only one direction for data flow.
    - Less prone to bottlenecks than a bus, as traffic is controlled and distributed.
  - Disadvantages:
    - Data may need to pass through many devices before reaching its destination, making it less efficient.
    - A single cut cable or failed device can break the entire loop and bring the network down.
- [x] **Switches**
  - Switches aggregate multiple devices (computers, printers, other networked equipment) using Ethernet.
  - Common in larger networks (businesses, schools) where many ports (4, 8, 16, 24, 32, 64, etc.) are needed.
  - Unlike hubs, switches learn which device is on which port and send packets only to the intended destination, reducing unnecessary traffic.
- [x] **Routers and Routing**
  - A **router** connects different networks and passes data between them.
  - The verb for what routers do is **routing**.
  - Routing is the process of creating and using paths so data can travel across multiple networks.
  - Routers are especially useful in environments with multiple possible paths, enabling resilience and controlled traffic flows.
  - Switches and routers can be connected together to increase redundancy by providing multiple paths; if one path fails, another can carry the traffic (with a potential performance trade-off).
- [x] **Interactive Topology Lab**
  - An interactive lab lets you explore how each topology can break.
  - You intentionally introduce failures (like cutting cables) to see their impact and retrieve the flag `THM{TOPOLOGY_FLAWS}`.
- [x] **Subnetting Basics**
  - **Subnetting** is dividing a larger network into smaller subnetworks (subnets).
  - Analogy: slicing a cake into pieces to share among friends; subnetting decides who gets which slice of address space.
  - Example organisational departments that might get distinct subnets:
    - Accounting
    - Finance
    - Human Resources
  - Subnetting is represented by a **subnet mask**, also made of four octets (32 bits), each ranging from 0–255.
  - Subnets use IP addresses in three main ways:
    - **Network Address** – identifies the start of the network (e.g. `192.168.1.0`).
    - **Host Address** – identifies individual devices on the network (e.g. `192.168.1.100`).
    - **Default Gateway** – a device that can send data to other networks (often `192.168.1.1` or `192.168.1.254`).
  - In small home networks, one subnet is usually enough (up to ~254 hosts).
  - Larger environments (offices, campuses) need subnetting for:
    - Efficiency
    - Security
    - Administrative control
  - Example: a café might have one subnet for internal devices (employees, cash registers) and another for public Wi‑Fi users.
- [x] **ARP (Address Resolution Protocol)**
  - ARP links IP addresses (logical identifiers) to MAC addresses (physical identifiers).
  - Each device keeps an ARP **cache** with mappings of IP addresses to MAC addresses.
  - ARP uses two packet types:
    - **ARP Request** – broadcast asking “Who has this IP address? Tell me your MAC.”
    - **ARP Reply** – unicast response from the device that owns the IP, providing its MAC.
  - This process allows devices to discover each other’s physical identifiers and communicate on the LAN.
- [x] **DHCP (Dynamic Host Configuration Protocol)**
  - DHCP automatically assigns IP addresses instead of requiring manual configuration.
  - When a device joins a network, it follows a 4-step exchange:
    - **DHCP Discover** – the device broadcasts to find a DHCP server.
    - **DHCP Offer** – the server offers an available IP address.
    - **DHCP Request** – the device requests to use the offered address.
    - **DHCP ACK** – the server acknowledges and confirms the lease.
  - This automation simplifies IP management, especially in large LANs.

## Terminal Commands

This room is mostly conceptual and uses interactive labs through the browser. There are no specific command-line tools emphasised beyond what you have learned previously; the focus is on understanding topologies, devices, and protocols like ARP and DHCP.

```bash
# No primary terminal commands highlighted in this LAN topology and subnetting room.
```

## Code

There is no programming component in this room. Instead, you work with visual diagrams, interactive labs, and conceptual models of how LAN devices and protocols operate.

```py
# No code snippets for the Intro to LAN room.
```

## Questions and Answers

### Question 1: What does LAN stand for?

<details>
<summary>Answer</summary>
LAN stands for **Local Area Network**.
</details>

### Question 2: What is the verb used to describe the job routers perform?

<details>
<summary>Answer</summary>
Routers perform **routing**.
</details>

### Question 3: Which device is used to centrally connect multiple devices on a local network and send data only to the correct destination?

<details>
<summary>Answer</summary>
A **switch** is used to centrally connect multiple devices and forward data intelligently to the correct port.
</details>

### Question 4: Which topology is described as cost-efficient to set up?

<details>
<summary>Answer</summary>
The **bus** topology is cost-efficient to set up.
</details>

### Question 5: Which topology is more expensive to set up and maintain, but offers scalability and reliability?

<details>
<summary>Answer</summary>
The **star** topology.
</details>

### Question 6: What is a major disadvantage of a bus topology in terms of reliability?

<details>
<summary>Answer</summary>
The backbone cable is a single point of failure; if it breaks, all devices on the bus lose connectivity.
</details>

### Question 7: Why can troubleshooting be difficult in a bus topology?

<details>
<summary>Answer</summary>
Because all devices share the same cable and path, making it hard to pinpoint which device or segment is causing issues.
</details>

### Question 8: What is one advantage and one disadvantage of a ring topology?

<details>
<summary>Answer</summary>
Advantage: relatively easy to troubleshoot and less prone to bottlenecks; Disadvantage: a single break or failed device can disrupt the whole ring.
</details>

### Question 9: What is the technical term for dividing a network into smaller pieces?

<details>
<summary>Answer</summary>
The term is **subnetting**.
</details>

### Question 10: How many bits are in a subnet mask, and what is the range of each octet?

<details>
<summary>Answer</summary>
A subnet mask is 32 bits long, split into four octets, each ranging from 0 to 255.
</details>

### Question 11: What address identifies the start of a network, and what address identifies devices within that network?

<details>
<summary>Answer</summary>
The **Network Address** identifies the start of the network; the **Host Address** identifies devices within the network.
</details>

### Question 12: What is the role of the default gateway?

<details>
<summary>Answer</summary>
The default gateway is the device responsible for sending data to other networks when the destination is not on the local subnet.
</details>

### Question 13: What does ARP stand for, and what is its purpose?

<details>
<summary>Answer</summary>
ARP stands for **Address Resolution Protocol**; it maps IP addresses to MAC addresses so devices can communicate on a LAN.
</details>

### Question 14: Which type of ARP packet asks devices whether they own a specific IP address?

<details>
<summary>Answer</summary>
An **ARP Request** asks which device has a particular IP address.
</details>

### Question 15: Which address acts as a physical identifier, and which acts as a logical identifier on a network?

<details>
<summary>Answer</summary>
The **MAC address** is the physical identifier, and the **IP address** is the logical identifier.
</details>

### Question 16: What DHCP packet does a device send to discover available DHCP servers?

<details>
<summary>Answer</summary>
It sends a **DHCP Discover** packet.
</details>

### Question 17: After receiving an offer from a DHCP server, what packet does the device send to accept the IP address?

<details>
<summary>Answer</summary>
The device sends a **DHCP Request** packet.
</details>

### Question 18: What is the last DHCP packet sent by the server to complete the IP assignment?

<details>
<summary>Answer</summary>
The final packet is **DHCP ACK**, acknowledging that the device may use the assigned IP address.
</details>

### Question 19: What flag do you receive at the end of the LAN topology lab when you successfully break the topologies as instructed?

<details>
<summary>Answer</summary>
You receive the flag `THM{TOPOLOGY_FLAWS}`.
</details>

## Summary

The Intro to LAN room explains how local area networks are structured using different topologies, and how devices like switches and routers move traffic efficiently and reliably. You learn the trade-offs between star, bus, and ring designs, and see how topology flaws can cause failures. The room also introduces subnetting, ARP, and DHCP, showing how networks are divided, how devices discover each other’s hardware addresses, and how IP addresses are automatically assigned. Together, these concepts form the core of how LANs are built, managed, and kept functioning.

## References

- [Intro to LAN – TryHackMe](https://tryhackme.com/room/introtolan)
- [Intro to LAN - Youtube](https://www.youtube.com/watch?v=csYtPidvvFQ)

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
- [What is Networking? - Youtube Networking Basics](https://www.youtube.com/watch?v=42u_2e6eNF4)

</details>

<details>
  <summary>Intro to LAN</summary>

## Introduction

The **Intro to LAN** TryHackMe room explores how Local Area Networks (LANs) are designed and operated. It focuses on common topologies (star, bus, ring), key devices like switches and routers, and concepts such as subnetting, ARP, and DHCP. You also complete an interactive lab where you intentionally break LAN topologies to understand their weaknesses and retrieve the flag `THM{TOPOLOGY_FLAWS}`.

## Detailed Explanation

- [x] **LAN Topologies Overview**
  - A **topology** is the design or layout of a network—how devices are physically and logically connected.
  - LANs can be built using different topologies, each with unique advantages, costs, and failure modes.
- [x] **Star Topology**
  - Devices are individually connected to a central networking device, such as a switch or hub.
  - This is the most commonly found topology today because of its reliability and scalability.
  - More cabling and dedicated equipment make it more expensive than other topologies.
  - As the network grows, maintenance and troubleshooting become more complex.
  - The central device is a single point of failure: if it fails, connected devices can no longer communicate.
- [x] **Bus Topology**
  - All devices share a single **backbone cable** from which they branch, like leaves off a tree.
  - Because all data travels along the same cable, the network can become slow and **bottlenecked** when many devices send data at once.
  - Troubleshooting is harder because all traffic shares one path, making it difficult to isolate issues.
  - It is cost‑efficient and relatively simple to set up, using less cabling and fewer dedicated devices.
  - A break in the backbone cable is a critical single point of failure; if it breaks, no devices can communicate.
- [x] **Ring Topology**
  - Devices are connected in a closed loop, each connected directly to two neighbours.
  - Sometimes called a **token** topology because devices pass control in turn.
  - Data circulates around the ring until it reaches the destination; a device forwards traffic if it has none of its own to send.
  - Because data flows in one direction, faults are relatively easy to troubleshoot.
  - However, traffic may have to traverse many devices before reaching the target, which is inefficient.
  - The design is less prone to bottlenecks than a bus, but a single cut cable or failed device can break the entire ring.
- [x] **Switches**
  - Switches are dedicated devices that aggregate multiple networked devices (PCs, printers, etc.) via Ethernet.
  - Common in larger environments (businesses, schools) where many ports (4, 8, 16, 24, 32, 64, etc.) are required.
  - Unlike hubs, switches keep track of which device is on which port (MAC learning) and send packets only to the intended destination.
  - This selective forwarding reduces unnecessary traffic and improves overall network efficiency.
- [x] **Routers and Routing**
  - A **router** connects different networks and passes data between them.
  - **Routing** is the process of creating and using paths between networks so data can be delivered end‑to‑end.
  - Routing becomes especially useful when multiple paths exist between networks, enabling redundancy and resilience.
  - Switches and routers can be combined to create multiple paths; if one path fails, another can still carry traffic, trading some performance for reliability.
- [x] **Subnetting Basics**
  - **Subnetting** is splitting a larger network into smaller subnetworks (subnets), like slicing a cake into pieces for different groups.
  - Organisations may subnet for departments such as Accounting, Finance, and Human Resources.
  - A subnet is described by a **subnet mask**, also made up of four octets (32 bits), each in the range 0–255.
  - IP addresses in a subnet are used in three main ways:
    - **Network Address** – identifies the start of the network (e.g. `192.168.1.0`).
    - **Host Address** – identifies individual devices (e.g. `192.168.1.100`).
    - **Default Gateway** – a device that can send data to other networks (commonly `192.168.1.1` or `192.168.1.254`).
  - Small home networks typically live on a single subnet, but larger networks use subnetting for:
    - **Efficiency** – better use of address space and traffic control.
    - **Security** – segmenting sensitive systems from general users.
    - **Full control** – administrative separation of departments or functions.
  - Example: a café may use one subnet for internal devices (staff, tills) and another for public Wi‑Fi.
- [x] **ARP (Address Resolution Protocol)**
  - Devices have two identifiers: a logical **IP address** and a physical **MAC address**.
  - **ARP** maps IP addresses to MAC addresses so devices can communicate on a LAN.
  - Each device maintains an **ARP cache**, a ledger of IP‑to‑MAC mappings.
  - ARP uses two key packet types:
    - **ARP Request** – broadcast: “Who has this IP address? Tell me your MAC.”
    - **ARP Reply** – unicast response from the device that owns the IP, returning its MAC.
  - Once learned, mappings are stored in the cache for future use.
- [x] **DHCP (Dynamic Host Configuration Protocol)**
  - Devices can be assigned IP addresses manually or automatically using **DHCP**.
  - When a device joins a network without a configured IP, it follows a four‑step DHCP exchange:
    - **DHCP Discover** – the device broadcasts to find DHCP servers.
    - **DHCP Offer** – a server responds with an available IP address and configuration.
    - **DHCP Request** – the device requests to use the offered address.
    - **DHCP ACK** – the server acknowledges the assignment so the device can begin using the IP.
- [x] **Interactive Topology Lab**
  - The attached lab lets you interact with star, bus, and ring topologies and intentionally break them.
  - You explore how single points of failure and design weaknesses cause outages.
  - Completing the lab and breaking the topologies as instructed yields the flag `THM{TOPOLOGY_FLAWS}`.

## Terminal Commands

This room is primarily conceptual and uses interactive browser‑based labs rather than CLI tools. There is no specific terminal command focus beyond your existing networking knowledge.

```bash
# No primary terminal commands for the Intro to LAN room.
```

## Code

There is no programming component in this room. The focus is on network design, behaviour, and protocols rather than writing or analysing code.

```py
# No code snippets for the Intro to LAN room.
```

## Questions and Answers

### Question 1: What does LAN stand for?

<details>
<summary>Answer</summary>
LAN stands for **Local Area Network**.
</details>

### Question 2: In simple terms, what is a network topology?

<details>
<summary>Answer</summary>
A network topology is the design or layout of how devices are connected and how data flows between them in a network.
</details>

### Question 3: Why is the star topology so common in modern networks?

<details>
<summary>Answer</summary>
Because it is reliable and scalable—devices are individually connected to a central device, making it easy to add more devices as demand grows.
</details>

### Question 4: What is the main cost‑related disadvantage of a star topology?

<details>
<summary>Answer</summary>
It requires more cabling and dedicated networking equipment, making it more expensive to set up and maintain than simpler topologies.
</details>

### Question 5: What is the central single point of failure in a star topology?

<details>
<summary>Answer</summary>
The central device (such as a switch or hub); if it fails, all connected devices lose connectivity.
</details>

### Question 6: Why can a bus topology quickly become slow or bottlenecked?

<details>
<summary>Answer</summary>
Because all devices share a single backbone cable, so simultaneous data transmissions compete for the same path and create congestion.
</details>

### Question 7: What makes troubleshooting a bus topology difficult?

<details>
<summary>Answer</summary>
All traffic travels along one cable, so pinpointing which device or segment is causing problems is challenging.
</details>

### Question 8: What is the critical single point of failure in a bus topology?

<details>
<summary>Answer</summary>
The backbone cable itself—if it breaks, devices can no longer send or receive data along the bus.
</details>

### Question 9: How are devices connected in a ring topology?

<details>
<summary>Answer</summary>
Each device is connected directly to two neighbours, forming a closed loop through which data circulates.
</details>

### Question 10: Why is a ring topology relatively easy to troubleshoot but potentially inefficient?

<details>
<summary>Answer</summary>
Data travels in a single direction, simplifying fault location, but it may have to pass through many devices before reaching its destination, which is inefficient.
</details>

### Question 11: What is the primary job of a switch on a LAN?

<details>
<summary>Answer</summary>
To connect multiple devices and intelligently forward packets only to the correct destination port, reducing unnecessary traffic.
</details>

### Question 12: What is the verb used to describe the job that routers perform?

<details>
<summary>Answer</summary>
Routers perform **routing**, creating and using paths so data can travel between different networks.
</details>

### Question 13: What is the technical term for dividing a network into smaller pieces?

<details>
<summary>Answer</summary>
The term is **subnetting**.
</details>

### Question 14: How many bits are in a subnet mask, and what is the valid range for each octet?

<details>
<summary>Answer</summary>
A subnet mask is 32 bits long, made up of four octets, each ranging from 0 to 255.
</details>

### Question 15: What address identifies the start of a network, and what address identifies devices within that network?

<details>
<summary>Answer</summary>
The **Network Address** identifies the start of the network, while **Host Addresses** identify individual devices within that network.
</details>

### Question 16: What is the role of the default gateway on a subnet?

<details>
<summary>Answer</summary>
It is the device responsible for sending data to other networks when the destination is not on the local subnet.
</details>

### Question 17: What does ARP stand for, and what problem does it solve?

<details>
<summary>Answer</summary>
ARP stands for **Address Resolution Protocol**; it maps IP addresses to MAC addresses so devices can find each other’s physical identifiers and communicate on a LAN.
</details>

### Question 18: Which ARP packet asks “Who has this IP address?” and which packet responds?

<details>
<summary>Answer</summary>
An **ARP Request** asks who owns a specific IP address, and an **ARP Reply** responds with the MAC address of the device that owns that IP.
</details>

### Question 19: Which address is the physical identifier for a device, and which is the logical identifier?

<details>
<summary>Answer</summary>
The **MAC address** is the physical identifier, and the **IP address** is the logical identifier.
</details>

### Question 20: What are the four main DHCP packet types involved in automatic IP assignment?

<details>
<summary>Answer</summary>
They are **DHCP Discover**, **DHCP Offer**, **DHCP Request**, and **DHCP ACK**.
</details>

### Question 21: What flag do you receive at the end of the LAN topology lab when you successfully break the topologies?

<details>
<summary>Answer</summary>
You receive the flag `THM{TOPOLOGY_FLAWS}`.
</details>

## Summary

The Intro to LAN room explains how local area networks can be built using different topologies—star, bus, and ring—and what trade‑offs each design introduces in terms of cost, scalability, and reliability. It shows how switches and routers move traffic efficiently, how subnetting divides a larger network into smaller, manageable pieces, and how ARP and DHCP help devices discover each other and automatically obtain IP addresses. Through an interactive lab, you see how single points of failure and design weaknesses can break networks and practice reasoning about resilience. Together, these concepts give you a solid foundation for understanding and troubleshooting LANs.

## References

- [Intro to LAN – TryHackMe](https://tryhackme.com/room/introtolan)
- [Intro to LAN – YouTube](https://www.youtube.com/watch?v=csYtPidvvFQ)

</details>

<details>
  <summary>OSI Model</summary>

## Introduction

The **OSI Model** (Open Systems Interconnection Model) is a fundamental networking framework that standardises how devices send, receive, and interpret data. It defines seven distinct layers, from the physical transmission of bits up to the user-facing application layer, so that diverse hardware and software can interoperate reliably. As data passes down and up these layers, additional information is added and removed in a process called **encapsulation**.

## Detailed Explanation

- [x] **OSI Model Overview**
  - OSI stands for **Open Systems Interconnection**.
  - The model has **7 layers**, numbered from Layer 1 (Physical) to Layer 7 (Application).
  - Each layer has specific responsibilities and interacts only with adjacent layers.
  - **Encapsulation** is the process of adding layer‑specific information (headers, trailers) to data as it descends through the stack.
- [x] **Layer 1 – Physical**
  - Concerned with the **physical components** and media that carry bits (0s and 1s).
  - Uses electrical, optical, or radio signals to represent the binary **numbering system** (1s and 0s).
  - Examples include **Ethernet cables** and other cabling/hardware that physically connect devices.
- [x] **Layer 2 – Data Link**
  - Handles **physical addressing** and framing for data on the same network.
  - Adds the **MAC address** of the receiving endpoint to frames.
  - Every networked device has a **Network Interface Card (NIC)** with a unique burned‑in MAC address (though it can be spoofed).
  - Responsible for presenting data in a format suitable for physical transmission.
- [x] **Layer 3 – Network**
  - Responsible for **routing** and reassembly of packets across multiple networks.
  - Works with **IP addresses** (e.g. `192.168.1.100`), deciding how packets traverse routers.
  - Protocols such as **OSPF (Open Shortest Path First)** and **RIP (Routing Information Protocol)** help determine optimal paths based on:
    - Shortest path (fewest hops).
    - Reliability (loss history).
    - Link speed (e.g. copper vs fibre).
  - Devices like routers that operate here are called **Layer 3 devices**.
- [x] **Layer 4 – Transport**
  - Manages end‑to‑end transport of data using **TCP** or **UDP**.
  - **TCP (Transmission Control Protocol)**:
    - Connection‑oriented and focused on **reliability and accuracy**.
    - Maintains a reserved connection while data is sent and received.
    - Performs **error checking** and ensures packets are received and reassembled in order.
    - Used by applications that require complete and correct data, such as file downloads, web browsing, and email.
    - Disadvantages: slower and more resource‑intensive; can bottleneck if the connection is unreliable.
  - **UDP (User Datagram Protocol)**:
    - Connectionless and **faster** than TCP.
    - No guarantee or error correction—data may be lost without retransmission.
    - Leaves rate control and reliability to the application, making it flexible but less safe.
    - Used where some loss is acceptable, e.g. **video streaming** or small discovery protocols like **ARP** and **DHCP**.
- [x] **Layer 5 – Session**
  - Creates, manages, and terminates **sessions** between devices.
  - A **session** exists while a connection is successfully established and active.
  - Can use **checkpoints** so that if a connection drops, only the most recent data needs to be resent.
  - Sessions are **unique**, and data does not cross between different sessions.
- [x] **Layer 6 – Presentation**
  - Acts as a **translator** for data between the Application layer and lower layers.
  - Ensures that data is formatted in a standard way so different software (e.g. different email clients) can interpret it consistently.
  - Handles **data encryption and decryption**, such as HTTPS for secure web traffic.
- [x] **Layer 7 – Application**
  - Closest to the **end user**, defining how users interact with networked data.
  - Everyday software like **email clients**, **web browsers**, and **FTP clients** (e.g. FileZilla) live here.
  - Provides a **Graphical User Interface (GUI)** and uses protocols like **DNS** to translate domain names into IP addresses.
- [x] **OSI Dungeon Practical**
  - A gamified exercise where you climb layers of the OSI model in the correct order.
  - Escaping the dungeon rewards you with the flag `THM{OSI_DUNGEON_ESCAPED}` and reinforces layer ordering.

## Terminal Commands

This room focuses on conceptual understanding of OSI layers and protocol behaviour rather than specific command‑line tools. Any practical elements are delivered through interactive labs (such as the OSI dungeon game) rather than CLI usage.

```bash
# No primary terminal commands for the OSI Model room.
```

## Code

There is no direct programming component in this room. Instead, you focus on how network protocols and layers interact, which underpins how applications and services are implemented in code elsewhere.

```py
# No code snippets for the OSI Model room.
```

## Questions and Answers

### Question 1: What does “OSI” in OSI Model stand for?

<details>
<summary>Answer</summary>
It stands for **Open Systems Interconnection**.
</details>

### Question 2: How many layers does the OSI model have?

<details>
<summary>Answer</summary>
The OSI model has **7** layers.
</details>

### Question 3: What is the key term for when pieces of information get added to data as it passes through OSI layers?

<details>
<summary>Answer</summary>
This process is called **encapsulation**.
</details>

### Question 4: Which OSI layer deals with physical components like cables and electrical signals?

<details>
<summary>Answer</summary>
The **Physical layer (Layer 1)**.
</details>

### Question 5: What numbering system consisting of 0s and 1s is used at the Physical layer?

<details>
<summary>Answer</summary>
The **binary** numbering system.
</details>

### Question 6: Which cables are commonly used to physically connect devices in a LAN at the Physical layer?

<details>
<summary>Answer</summary>
**Ethernet cables**.
</details>

### Question 7: Which layer adds MAC addresses and focuses on physical addressing?

<details>
<summary>Answer</summary>
The **Data Link layer (Layer 2)**.
</details>

### Question 8: What piece of hardware in every networked device contains a burned‑in MAC address?

<details>
<summary>Answer</summary>
The **Network Interface Card (NIC)**.
</details>

### Question 9: Which layer is responsible for routing packets between networks?

<details>
<summary>Answer</summary>
The **Network layer (Layer 3)**.
</details>

### Question 10: Name two routing protocols mentioned that can help determine optimal paths at the Network layer.

<details>
<summary>Answer</summary>
**OSPF (Open Shortest Path First)** and **RIP (Routing Information Protocol)**.
</details>

### Question 11: What type of addresses are handled at the Network layer?

<details>
<summary>Answer</summary>
**IP addresses**.
</details>

### Question 12: At the Transport layer, which protocol guarantees the accuracy and correct ordering of data?

<details>
<summary>Answer</summary>
**TCP (Transmission Control Protocol)**.
</details>

### Question 13: Which Transport‑layer protocol does not care whether data arrives or not?

<details>
<summary>Answer</summary>
**UDP (User Datagram Protocol)**.
</details>

### Question 14: Which protocol would an email client or file download application typically use: TCP or UDP?

<details>
<summary>Answer</summary>
They would typically use **TCP**.
</details>

### Question 15: Which protocol is better suited for video streaming where some data loss is acceptable?

<details>
<summary>Answer</summary>
**UDP**, because it is faster and tolerates some packet loss.
</details>

### Question 16: What is the name of the OSI layer that creates, maintains, and terminates sessions between devices?

<details>
<summary>Answer</summary>
The **Session layer (Layer 5)**.
</details>

### Question 17: What is the technical term used when a connection between two devices is successfully established at the Session layer?

<details>
<summary>Answer</summary>
It is called a **session**.
</details>

### Question 18: Which OSI layer acts as a translator and is responsible for data formats and encryption like HTTPS?

<details>
<summary>Answer</summary>
The **Presentation layer (Layer 6)**.
</details>

### Question 19: What is the main purpose of the Application layer (Layer 7)?

<details>
<summary>Answer</summary>
It defines how users interact with networked data via software (e.g. email clients, web browsers) by providing **protocols and interfaces** such as GUIs.
</details>

### Question 20: What does GUI stand for, and where is it relevant in the OSI model?

<details>
<summary>Answer</summary>
GUI stands for **Graphical User Interface**, and it is relevant at the **Application layer**, where users interact with applications.
</details>

### Question 21: What is the flag obtained when you successfully escape the OSI dungeon game?

<details>
<summary>Answer</summary>
The flag is `THM{OSI_DUNGEON_ESCAPED}`.
</details>

## Summary

The OSI Model organises networking into seven logical layers, from the physical movement of bits up to the user‑facing applications. Each layer has a specific role: the Physical and Data Link layers handle signals and local addressing, the Network and Transport layers route and reliably deliver data using IP, TCP, and UDP, and the Session, Presentation, and Application layers manage sessions, translation, security, and user interaction. By understanding how encapsulation works and what happens at each layer, you can reason about where problems occur, why certain protocols are used, and how different systems interoperate. Hands‑on activities like the OSI dungeon reinforce layer order and responsibilities through practice.

## References

- [OSI Model – TryHackMe](https://tryhackme.com/room/osimodelzi)

</details>

<details>
  <summary>Packets & Frames</summary>

## Introduction

The **Packets & Frames** TryHackMe room explains how data is broken into smaller units for transmission and how different protocols and models describe this process. At Layer 3 of the OSI model, **packets** carry IP information, while at Layer 2, **frames** encapsulate packets with MAC addressing. The room also introduces the TCP/IP model, TCP vs UDP behaviour (including the three‑way handshake), port numbers, and a few hands‑on challenges with flags.

## Detailed Explanation

- [x] **Packets vs Frames**
  - A **packet** is a unit of data at **Layer 3 (Network)** and includes IP addressing information plus a payload.
  - A **frame** is a unit of data at **Layer 2 (Data Link)** that encapsulates a packet and adds MAC addresses and other link‑layer details.
  - Analogy: the **frame** is the envelope that carries the letter (the **packet**) through the postal system; once opened, the letter can be processed or forwarded.
  - The process of adding these headers as data moves through layers is **encapsulation**.
  - When the encapsulating information is stripped off, you are looking at the underlying packet or data itself.
- [x] **Why Packets Are Useful**
  - Data is split into smaller pieces (packets) instead of being sent as one large message.
  - This reduces the chance of **bottlenecks** and improves efficiency when many devices share a network.
  - Example: when loading an image from a website, the image is broken into several packets and then **reconstructed** on the receiving device.
- [x] **IP Packet Headers**
  - Packets using the Internet Protocol (IP) have standardised headers that help devices handle and route data.
  - Important IP headers include:
    - **Time to Live (TTL)** – sets an expiry for the packet so it does not circulate indefinitely and clog the network.
    - **Checksum** – provides integrity checking; if the computed value on receipt differs, the packet is considered corrupt.
    - **Source Address** – the IP address of the sending device so responses know where to return.
    - **Destination Address** – the IP address of the target device so routers know where to forward the packet.
- [x] **TCP/IP Model Overview**
  - The **TCP/IP model** is a four‑layer model that parallels the OSI model in a simplified form:
    - **Application**
    - **Transport**
    - **Internet**
    - **Network Interface**
  - Like the OSI model, information is added at each layer as packets traverse the stack (encapsulation) and removed in reverse (decapsulation).
- [x] **TCP Basics and Reliability**
  - **TCP (Transmission Control Protocol)** is connection‑based and emphasises reliability.
  - Before data is sent, TCP must establish a connection between client and server.
  - Because of this, TCP **guarantees** that data sent will be received in order at the other end, or it will be retransmitted.
  - Advantages:
    - Integrity of data is guaranteed.
    - Can synchronise devices to avoid flooding or reordering issues.
  - Disadvantages:
    - Requires a reliable connection; if small chunks are lost, larger units may need to be resent.
    - Slower than UDP due to extra processing and connection maintenance.
- [x] **TCP Headers**
  - Key TCP header fields include:
    - **Source Port** – random high port on the sender used to send the packet.
    - **Destination Port** – the port where a service is listening on the receiver (e.g. port 80 for a web server).
    - **Source IP** – IP address of the sender.
    - **Destination IP** – IP address of the receiver.
    - **Sequence Number** – initial random number assigned to the first piece of data to track ordering.
    - **Acknowledgement Number** – used to confirm receipt; typically previous sequence number + 1.
    - **Checksum** – integrity check; if recalculated value differs, data is corrupt.
    - **Data** – the actual payload being transferred.
    - **Flag** – indicates how to handle the packet during connection setup and teardown (e.g. SYN, ACK, FIN, RST).
- [x] **TCP Three‑Way Handshake**
  - The **three‑way handshake** establishes a reliable TCP connection:
    - **SYN** – client initiates connection and proposes an Initial Sequence Number (ISN).
    - **SYN/ACK** – server responds with its own ISN and acknowledges the client’s.
    - **ACK** – client acknowledges the server’s ISN; the connection is established.
  - After this, **DATA** packets carry the payload, and finally:
    - **FIN** – used to close the connection cleanly.
    - **RST** – used to abruptly terminate communication when something goes wrong.
- [x] **TCP Closing a Connection**
  - When a device determines that all data has been successfully sent and received, it should close the TCP connection to free resources.
  - A **FIN** packet is sent to initiate closure and must be acknowledged by the other side.
  - Both sides exchange FIN and ACK as part of a graceful shutdown.
- [x] **UDP Basics**
  - **UDP (User Datagram Protocol)** is **stateless** and does not require a three‑way handshake.
  - There is no synchronisation, acknowledgement, or built‑in integrity checking beyond basic mechanisms.
  - UDP is useful where:
    - Some data loss is acceptable (e.g. video streaming, voice chat).
    - High speed and low overhead are more important than guaranteed delivery.
  - Trade‑offs:
    - Faster and simpler than TCP.
    - Does not care whether data is received; unstable connections can cause poor user experience.
- [x] **UDP Headers**
  - UDP packets have fewer headers but share some with IP:
    - **Time to Live (TTL)** – expiry timer.
    - **Source Address** – IP of the sender.
    - **Destination Address** – IP of the receiver.
    - **Source Port** – randomly chosen port used by the sender.
    - **Destination Port** – port where the application or service is listening.
    - **Data** – payload.
- [x] **Ports and Services**
  - Ports are numeric identifiers (0–65535) that allow multiple applications to share a single IP address.
  - Common ports (0–1024) are reserved for standard services:
    - **FTP (21)** – File Transfer Protocol for client‑server file sharing.
    - **SSH (22)** – Secure Shell for remote text‑based management.
    - **HTTP (80)** – unencrypted web traffic.
    - **HTTPS (443)** – encrypted web traffic.
    - **SMB (445)** – file and printer sharing.
    - **RDP (3389)** – Remote Desktop Protocol for graphical remote access.
  - Services can run on non‑standard ports (e.g. HTTP on 8080), but clients must know and specify the port (often using `:<port>` in URLs).
- [x] **Practical Challenges and Flags**
  - One challenge has you reconstruct a TCP handshake conversation between Alice and Bob to understand the sequence of SYN, SYN/ACK, and ACK messages, yielding the flag `THM{TCP_CHATTER}`.
  - Another challenge involves connecting to IP `8.8.8.8` on port `1234`, which returns the flag `THM{YOU_CONNECTED_TO_A_PORT}`.
  - Additional tasks reinforce concepts of TCP vs UDP, and using ports in practice.

## Terminal Commands

This room is primarily conceptual and uses static or browser‑based labs rather than heavy command‑line interaction. You may, however, conceptually work with tools like `netcat` or similar to connect to specific IP:port combinations in practical challenges.

```bash
# Example (conceptual) usage to connect to a host and port:
nc 8.8.8.8 1234
```

## Code

There is no dedicated programming component; instead, you focus on how network protocols structure and move data. Any code‑like interactions are typically done through network tools or lab interfaces.

```py
# No direct code samples for the Packets & Frames room.
```

## Questions and Answers

### Question 1: What is the name for a piece of data when it has IP addressing information?

<details>
<summary>Answer</summary>
It is called a **packet**.
</details>

### Question 2: What is the name for a piece of data when it does not have IP addressing information and is used at Layer 2?

<details>
<summary>Answer</summary>
It is called a **frame**.
</details>

### Question 3: Which OSI layer uses packets, and which uses frames?

<details>
<summary>Answer</summary>
Packets are used at **Layer 3 (Network)**, and frames are used at **Layer 2 (Data Link)**.
</details>

### Question 4: What IP header field prevents packets from living forever on a network?

<details>
<summary>Answer</summary>
The **Time to Live (TTL)** field.
</details>

### Question 5: What is the purpose of the checksum field in IP or TCP headers?

<details>
<summary>Answer</summary>
It provides **integrity checking**; if the computed checksum at the receiver differs from the sender’s value, the data is considered corrupt.
</details>

### Question 6: Name the four layers of the TCP/IP model.

<details>
<summary>Answer</summary>
They are **Application**, **Transport**, **Internet**, and **Network Interface**.
</details>

### Question 7: Is TCP connection‑based or stateless, and what does that imply?

<details>
<summary>Answer</summary>
TCP is **connection‑based**, meaning it must establish and maintain a connection between client and server to reliably deliver data.
</details>

### Question 8: What is the correct order of a normal TCP three‑way handshake?

<details>
<summary>Answer</summary>
The order is **SYN, SYN/ACK, ACK**.
</details>

### Question 9: Which TCP header field ensures the integrity of data?

<details>
<summary>Answer</summary>
The **checksum** field.
</details>

### Question 10: What is the role of the Sequence Number and Acknowledgement Number in TCP?

<details>
<summary>Answer</summary>
The **Sequence Number** labels each piece of data so it can be reassembled in order, and the **Acknowledgement Number** confirms receipt and indicates the next expected sequence value.
</details>

### Question 11: What does the FIN flag in TCP signify?

<details>
<summary>Answer</summary>
It indicates that a device wants to **cleanly close** the TCP connection.
</details>

### Question 12: What is the purpose of the RST flag in TCP?

<details>
<summary>Answer</summary>
It abruptly **resets** the connection, usually when there is a problem or the service is unavailable.
</details>

### Question 13: What does “UDP” stand for, and what type of connection is it?

<details>
<summary>Answer</summary>
UDP stands for **User Datagram Protocol**, and it is a **stateless** connectionless protocol.
</details>

### Question 14: In general, which protocol would you use to transfer a file reliably: TCP or UDP?

<details>
<summary>Answer</summary>
You would use **TCP**.
</details>

### Question 15: Which protocol is more appropriate for a video call: TCP or UDP?

<details>
<summary>Answer</summary>
**UDP**, because it tolerates some data loss while prioritising speed and low latency.
</details>

### Question 16: How many possible port numbers are there on a host?

<details>
<summary>Answer</summary>
There are **65,535** possible port numbers (0–65535).
</details>

### Question 17: What port does HTTP typically use, and what about HTTPS?

<details>
<summary>Answer</summary>
HTTP typically uses port **80**, and HTTPS uses port **443**.
</details>

### Question 18: Which port is commonly used by SSH, and what is it for?

<details>
<summary>Answer</summary>
SSH commonly uses port **22** and is used for secure remote login over a text‑based interface.
</details>

### Question 19: What is the flag obtained after helping Alice and Bob complete a TCP handshake conversation in the lab?

<details>
<summary>Answer</summary>
The flag is `THM{TCP_CHATTER}`.
</details>

### Question 20: What flag do you receive after connecting to `8.8.8.8` on port `1234` in the practical challenge?

<details>
<summary>Answer</summary>
You receive the flag `THM{YOU_CONNECTED_TO_A_PORT}`.
</details>

## Summary

The Packets & Frames room deepens your understanding of how data is structured and transported on networks. You learn the distinction between packets and frames across OSI layers, see how IP and TCP/UDP headers support routing and reliability, and explore how the TCP/IP model maps to practical networking. By comparing TCP and UDP, examining key headers, and working with common ports and simple labs, you build intuition for how real‑world traffic is formed, transmitted, and interpreted. This knowledge is essential for analysing network behaviour and troubleshooting connectivity issues in later security work.

## References

- [Packets & Frames – TryHackMe](https://tryhackme.com/room/packetsframes)
- [Packets & Frames – YouTube](https://www.youtube.com/watch?v=vzcLrE0SfiQ)

</details>