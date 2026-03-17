<!-- Paste the TryHackMe/Let's Defend page URL at the top -->
<!-- Then paste your raw notes, explanations, commands, and code below -->

https://tryhackme.com/room/defensivesecurityintro

# Defensive Security Intro

Think like a Defenderdepicting a person sitting at a desk, with multiple monitors stacked on one another showing various cybersecurity and data iconograhpy such as a map, bar charts, etc.
Defensive security is the process of defending and securing devices and systems.

Before you can defend a system, you need to understand what defenders are responsible for. Defensive security focuses on detecting and investigating attacks, and responding before damage occurs.

Unlike offensive security, you do not attack systems, instead, you monitor and protect them.

Answer the questions below
What is the main goal of defensive security?
ANS: Detect and respond to attacks

Detect Suspicious Activity
The first step in defensive security is spotting activity that doesn't look normal. This activity is stored in pieces of information known as alerts.


View Site
This room uses a virtual machine to simulate a real system.

You'll need to...
1. Open the monitoring dashboard
2. Review recent alerts
3. Identify the suspicious source IP.
Why you're doing this

Defenders use tools similar to this monitoring dashboard to decide what activity needs investigating.

Answer the questions below
Which source IP address is generating the suspicious traffic?
32.122.195.63

Identify the Attack
Once suspicious activity is determined, defenders need to understand what kind of attack it is.


View Site
This room uses a virtual machine to simulate a real system.

You'll need to...
1. Investigate the attack that has occured.
2. View the "URL Discovery Attempts" list.
3. Look at the latest "URL Discovery Attempts" entry to answer the question.
Why you're doing this

The monitoring dashboard shows what the attacker is trying to find. We can use this information to better secure our systems, stop the attacker and prevent this attack from occuring again.

Answer the questions below
Copy the latest URL that the attacker has tried to find and paste it below.
https://fakebank.com/admin


Stop the Attack
Now that the attack has been identified, defenders can take steps to stop it.


View Site
This room uses a virtual machine to simulate a real system.

You'll need to...
1. Block the attacker's IP address
2. Apply rate limits, so any one else cannot overwhelm the system
3. Update security rules
4. Apply additional security measures to prevent this occuring again.
Why you're doing this

We can stop the attacker from continuing on immediately while we investigate and fix any security vulnerabilities. This is known as containment.

Answer the questions below
When the success message apears, copy the flag and paste it below.
THM{FAKEBANK-SECURED}