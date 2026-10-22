Day 20 — Windows Updates, Patch Management & Vulnerabilities

1. What is a vulnerability?

A vulnerability is a weakness in software, hardware, or configuration that an attacker could exploit.

Examples:
- An operating system with a known, unpatched security flaw.
- An application using an outdated library.
- A system allowing unnecessary administrator privileges.
- A server exposed to a vulnerable network service.

Threat vs. vulnerability vs. risk

Term	Meaning	Example

Threat	Something that could cause harm	A cybercriminal

Vulnerability	A weakness that could be exploited	An unpatched Windows flaw

Risk	The likelihood and impact of harm	The attacker exploits the flaw and steals data

B. What is patch management?

A patch is an update that fixes a bug, security weakness, or other software issue.

Patch management is the process of identifying, testing, deploying, and verifying updates.

1. Identify updates and vulnerabilities

2. Prioritize by severity and exposure

3. Test updates where practical

4. Install updates

5. Verify installation and monitor


Why is patch management important?

- Closes known security weaknesses.
- Reduces opportunities for malware and ransomware attacks.
- Improves stability and reliability.
- Helps organizations meet security requirements.

Important: Updating software reduces risk, but it does not guarantee that a system is completely secure.

C. What are CVE and CVSS?

- CVE — Common Vulnerabilities and Exposures: A standardized identifier assigned to a publicly disclosed vulnerability. Example format: CVE-YYYY-NNNN.
- CVSS — Common Vulnerability Scoring System: A framework for rating vulnerability severity, usually on a scale from 0.0 to 10.0.

Typical CVSS severity bands:

Score	Severity

0.0	None

0.1–3.9	Low

4.0–6.9	Medium

7.0–8.9	High

9.0–10.0	Critical

A CVSS score helps prioritize work, but teams must also consider whether the vulnerability is actively exploited, whether the system is exposed, and how important its data is.

2. Practical 

Today’s task is to inspect your own Windows system safely. We will check update status and installed updates without changing system settings.

Practical A — Check Windows Update

1. Open Settings.

2. Go to Windows Update.

3. Check whether updates are available, pending, or whether Windows reports that you're up to date.

4. Note the date of the last update check, if displayed.

Do not interrupt an update that is already installing.

Practical B — Inspect installed updates using PowerShell

Open PowerShell. A normal, non-administrator window should be sufficient for these read-only checks.

Command 1 — View Windows version and build

Get-ComputerInfo |
    Select-Object WindowsProductName, WindowsVersion, OsBuildNumber


Command 2 — View recently installed hotfixes

Get-HotFix |
  Sort-Object InstalledOn -Descending |
  Select-Object -First 10 HotFixID, Description, InstalledOn


Command 3 — Check the Windows Update service

Get-Service -Name wuauserv |
  Select-Object Name, Status, StartType


The service may not always be running; that alone does not prove Windows Update is broken. Windows can start services when needed.

Write down:

- Your Windows version and build.
- One recently installed update ID, if available.
- Your Windows Update status from Settings.

If a command returns an error, record the message rather than changing permissions or service settings.

Day 20 quiz — 5 questions

1. What is a vulnerability?

A security weakness that could be exploited

A guaranteed successful attack

A software update

A type of firewall

Correct! A security weakness that could be exploited


2. What does CVE provide?

A computer's IP address

A standardized identifier for a disclosed vulnerability

A password encryption algorithm

A Windows update schedule

Correct! A standardized identifier for a disclosed vulnerability


3. What is CVSS used for?

Creating user accounts

Installing drivers

Rating vulnerability severity

Scanning only Wi-Fi networks

Correct! Rating vulnerability severity


4. Which is a sensible patch-management practice?

Install every update without any planning in every environment

Ignore updates if the computer seems to work

Identify, prioritize, deploy and verify updates

Disable security updates permanently

Correct! Identify, prioritize, deploy and verify updates


5. What should influence vulnerability prioritization besides CVSS?

The computer's wallpaper

Whether it is actively exploited and how exposed the system is

The user's favorite browser color

The number of desktop icons

Correct! Whether it is actively exploited and how exposed the system is

Score: 5/5
