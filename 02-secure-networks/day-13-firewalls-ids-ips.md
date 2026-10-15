Day 13 — Firewalls, IDS and IPS

1. What is a firewall?

A firewall is a security system that monitors network traffic and allows or blocks connections according to predefined rules.

Think of it like a security guard at a building entrance: it checks who can enter and who must be denied.

Incoming and outgoing traffic


Firewall checks its rules

IP address · Port · Protocol · Connection state


Allow

Permitted traffic


Block

Denied traffic



Types of firewall
- Packet-filtering firewall: Checks information such as source IP, destination IP, port and protocol.
- Stateful firewall: Tracks active connections and considers their connection state when deciding whether to allow traffic.
- Application-layer firewall: Inspects application-level traffic, such as HTTP requests.
- Next-generation firewall (NGFW): Can combine traditional firewall rules with capabilities such as application awareness and intrusion prevention.

Example: A firewall rule may allow outgoing HTTPS connections on TCP port 443 while blocking unsolicited incoming connections.

Remember: a firewall reduces exposure, but it does not automatically detect every malicious file or attack.

2. What are IDS and IPS?

These are security systems that look for suspicious activity in network traffic.









IDS — Intrusion Detection System

Detects suspicious activity and alerts the security team. It generally does not block traffic automatically.

Example: It detects repeated login attempts from one IP address and raises an alert.












IPS — Intrusion Prevention System

Detects suspicious activity and can automatically block or prevent it.

Example: It identifies a known attack pattern and drops the malicious network packets.



IDS vs IPS

Feature	IDS	IPS

Full form	Intrusion Detection System	Intrusion Prevention System

Main purpose	Detects and alerts	Detects and blocks

Typical placement	Monitors a network copy of traffic	Often placed inline with traffic

Main risk	Alert may not be acted on quickly	False positives can block legitimate traffic

Easy way to remember: IDS = Intruder Detected! IPS = Intruder Prevented!

3. How do IDS and IPS detect attacks?

They commonly use two approaches:
- Signature-based detection: Looks for known attack patterns. Effective against recognised threats, but may miss new variations.
- Anomaly-based detection: Looks for activity that differs from normal behaviour. Can identify unusual attacks, but may produce false alarms.

A false positive occurs when normal activity is incorrectly flagged as malicious.

4. How these systems work together

Imagine a company server receives thousands of unusual requests.
1. The firewall checks whether the connections meet its rules.
2. The IDS analyses traffic for suspicious patterns and alerts the security team.
3. The IPS can block traffic matching attack patterns.
4. Security analysts investigate alerts, review logs and improve the rules.

These systems complement each other. None guarantees complete protection, so patching, authentication, monitoring and secure configuration remain important.

5. Practical task — Windows Firewall

We'll inspect your existing firewall configuration without changing any settings.

Task A: Check firewall profiles

Open PowerShell and run:

Get-NetFirewallProfile |
  Select-Object Name, Enabled, DefaultInboundAction, DefaultOutboundAction


This displays the firewall profiles (Domain, Private and Public), whether each is enabled, and its default traffic actions.

Task B: Inspect firewall rules

Get-NetFirewallRule |
  Select-Object -First 10 DisplayName, Enabled, Direction, Action


Look for these fields:
- Enabled — whether the rule is enabled.
- Direction — inbound or outbound.
- Action — allow or block.

These commands only read configuration. Keep your firewall enabled and don't change rules just for practice.


6. Quiz — Day 13

1. What is the primary purpose of a firewall?

A. To store passwords

B. To allow or block traffic based on rules

C. To recover deleted files

D. To encrypt every file

Correct! A firewall enforces rules governing network traffic.


2. Which system primarily detects suspicious activity and alerts?

A. IDS

B. IPS

C. DHCP

D. DNS

Correct! An IDS detects and alerts; an IPS can actively prevent traffic.


3. A system automatically blocks traffic matching a known attack pattern. Which system might be doing this?

A. A passive IDS only

B. An IPS

C. A DNS resolver

D. A DHCP server

Correct! An IPS can block malicious traffic automatically.


4. What is signature-based detection?

A. Detecting only unknown behaviour

B. Matching activity against known attack patterns

C. Checking a user's password length

D. Encrypting network traffic

Correct! Signature-based systems look for known indicators or patterns.


5. What is a false positive?

A. A real attack that was blocked

B. A failed network cable

C. Normal activity incorrectly flagged as malicious

D. A firewall with no rules

Correct! A false positive is a benign event incorrectly classified as a threat.

Score: 5/5
