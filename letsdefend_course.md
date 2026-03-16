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
