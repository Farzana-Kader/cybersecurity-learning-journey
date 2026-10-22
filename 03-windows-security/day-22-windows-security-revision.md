Day 22 — Windows Security: Revision & Assessment


1. Learning — Complete revision notes

1.1 Windows accounts and privilege levels

Windows accounts determine who can access a computer and which actions they can perform.
- Standard user: Performs everyday tasks with limited privileges.
- Administrator: Can perform system-wide actions, such as installing software and changing protected settings.
- User Account Control (UAC): Prompts for approval or administrator credentials when an action requires elevated privileges.

Why this matters in cybersecurity: If malware runs under an administrator account, it may have greater ability to change system settings, access sensitive files, or disable security controls.

Best practice: Use a standard account for everyday work and elevate privileges only when necessary.

1.2 File permissions and least privilege

Windows uses access control lists (ACLs) to define which users or groups can perform specific actions on files and folders.

Permission	Meaning

Read	View file contents

Write	Modify file contents

Execute	Run a program or executable file

Modify	Read, write and delete, subject to the applicable permissions

Full control	Includes permission changes and other powerful actions

Principle of least privilege: A user, program or service should receive only the permissions necessary to perform its intended task.

For example, a student account should not need permission to modify Windows system files.

Practical command:

icacls "$env:USERPROFILE\Desktop"


This displays access permissions for your Desktop folder.

1.3 Microsoft Defender and Windows Firewall

These are different security controls that work together.

Feature	Main purpose

Microsoft Defender Antivirus	Detects, blocks and removes malware

Windows Defender Firewall	Controls network traffic according to firewall rules

Real-time protection	Checks files and activity as they occur

Security intelligence updates	Help Defender recognize current threats

A firewall does not replace antivirus protection, and antivirus does not replace a firewall.

Check Defender status:

Get-MpComputerStatus |
    Select-Object AntivirusEnabled, RealTimeProtectionEnabled


Check firewall profiles:

Get-NetFirewallProfile |
    Select-Object Name, Enabled, DefaultInboundAction


The Domain, Private and Public profiles apply to different network environments. A public network generally requires a more restrictive inbound configuration.

1.4 Windows Event Logs and security investigations

Event logs provide evidence of system activity. Investigators use them to establish what happened, when it happened and which account or process may have been involved.

Event ID	Meaning

4624	Successful logon

4625	Failed logon

4634	Account logged off

4648	Logon attempted using explicit credentials

4720	User account created

4722	User account enabled

4724	Attempt to reset an account password

1102	Security audit log cleared

Important: An event is not proof of malicious activity by itself. Investigators correlate timestamps, accounts, source information and other events before drawing conclusions.

View recent System events:

Get-WinEvent -LogName System -MaxEvents 10 |
    Select-Object TimeCreated, Id, LevelDisplayName, ProviderName


For a security investigation, preserve relevant evidence and avoid clearing logs or changing the system unnecessarily.

1.5 Authentication, passwords and MFA

Three concepts must remain clear:
- Identification: Claiming an identity, such as entering a username.
- Authentication: Proving that identity.
- Authorization: Determining what the authenticated identity is allowed to do.

Authentication factors commonly fall into three categories:

1. Something you know: Password or PIN.
2. Something you have: Security key or authenticator device.
3. Something you are: Fingerprint or facial recognition.

Multi-factor authentication (MFA) combines at least two different factor categories. A password plus a security key is MFA; two passwords are not.

Passkeys and FIDO2 security keys provide phishing-resistant authentication when implemented correctly. They use cryptographic credentials rather than relying only on a reusable password.

Password storage also matters: secure systems store password verifiers using appropriate password-hashing methods, with unique salts, rather than storing passwords as plain text.

1.6 Updates, vulnerabilities and hardening

A vulnerability is a weakness that could be exploited. A threat is a potential cause of harm. Risk considers the likelihood and impact of harm occurring.

- CVE: A public identifier assigned to a disclosed vulnerability.
- CVSS: A framework for scoring vulnerability severity.
- Patch management: Identifying, testing, deploying and verifying updates.
- System hardening: Reducing unnecessary services, privileges, software and exposure.

Check recently installed Windows updates:

Get-HotFix |
    Sort-Object InstalledOn -Descending |
    Select-Object -First 10 HotFixID, Description, InstalledOn


A list of installed hotfixes does not prove that a system is fully patched. Some updates may not appear in this output, and the operating system's current update status should also be checked.

1.7 Endpoint investigation and malware detection

An endpoint is a device such as a laptop, desktop or server.

- Antivirus: Primarily detects and blocks malicious files and activity.
- EDR (Endpoint Detection and Response): Collects endpoint telemetry and supports investigation, detection and response.
- PID: Process identifier.
- Parent process: The process that created another process.
- IoC (Indicator of Compromise): An observable clue associated with a possible security incident, such as a malicious file hash or suspicious IP address.

Common detection approaches include signature-based detection, heuristic analysis, behavior monitoring and reputation checks.

View processes:

Get-Process |
    Sort-Object CPU -Descending |
    Select-Object -First 10 Name, Id, CPU


Calculate a file's SHA-256 hash:

Get-FileHash "C:\Path\To\Your\File.txt" -Algorithm SHA256


Replace the example path with a real file you own or are authorized to examine. A hash can help identify whether two files are identical, but a hash alone does not establish that a file is malicious.

1.8 Incident response: what should you do first?

Suppose Defender reports a suspicious executable and you notice an unusual process.

A sensible investigation sequence is:

1. Record the alert, time and affected device.
2. Preserve relevant logs and evidence.
3. Examine the file hash, process details and related events.
4. Follow your organization's incident-response procedure.
5. Contain the threat when authorized and appropriate.
6. Remove the threat, recover safely and document the findings.

Avoid immediately deleting suspicious files or clearing logs if doing so could destroy evidence. In a real incident, follow your organization's approved containment procedures.

2. Practical — Windows Security review lab

Complete these tasks on your own Windows computer. These exercises are intended for observation; do not disable protection, change permissions on system folders, or deliberately execute malware.

Practical checklist

8 of 8



[x] 1. Inspect your account

Run whoami and whoami /groups. Identify your account and review its group memberships.

[x] 2. Review folder permissions

Run icacls "$env:USERPROFILE\Desktop" and identify the listed users/groups and permissions.

[x] 3. Check Defender

Run Get-MpComputerStatus and inspect AntivirusEnabled and RealTimeProtectionEnabled.

[x] 4. Check firewall profiles

Run Get-NetFirewallProfile and record whether each profile is enabled.

[x] 5. Inspect system events

Run the Get-WinEvent command from Section 1.4 and identify the newest event's time and ID.

[x] 6. Review installed updates

Run the Get-HotFix command from Section 1.6 and note the newest listed update.


[x] 7. Explore endpoint evidence

Open Task Manager → Details and observe process names and PIDs. Do not terminate unfamiliar processes.

[x] 8. Review security alerts

Open Windows Security → Virus & threat protection → Protection history. Review any displayed entries without changing their status.

Copy checklist progress

Practical reflection: Write down one security control you checked, what you observed and why that observation matters. If a command is unavailable or access is denied, record that rather than attempting to bypass the restriction.


3. Quiz — Final Windows Security assessment

Answer all 10 questions. Each question is worth one point. Choose the best answer; your score will tell us which areas need revision.

Assessment questions

10/10 answered

1. Which Windows feature requests approval for actions requiring elevated privileges?

DNS

UAC

DHCP

ARP

Correct.
User Account Control helps prevent unauthorized elevation by prompting for approval or credentials.


2. What is the principle of least privilege?

Give everyone administrator access

Disable all user accounts

Grant only the permissions needed

Use the same password everywhere

Correct.
Least privilege limits unnecessary access and reduces the potential impact of compromise.


3. Which control primarily filters network traffic according to rules?

Windows Firewall

Password hashing

Task Manager

Event Viewer

Correct.
Windows Firewall controls permitted and blocked network connections.


4. Which event ID represents a failed Windows logon?

4624

4625

4634

4720

Correct.
4625 records a failed logon; 4624 records a successful logon.


5. A password plus a physical security key is an example of:

Two knowledge factors

Authorization only

Multi-factor authentication

A firewall rule

Correct.
A password is something you know, while a security key is something you have.


6. What is CVE used for?

Identifying publicly disclosed vulnerabilities

Encrypting a hard drive

Listing running processes

Assigning Windows user permissions

Correct.
CVE provides standardized identifiers for publicly disclosed cybersecurity vulnerabilities.


7. What does a process ID (PID) identify?

A network subnet

A particular running process

A Windows update

A firewall profile

Correct.
A PID identifies a process within the operating system while that identifier is in use.


8. What does a SHA-256 file hash tell you most directly?

The user's identity

Whether the file is definitely malicious

A file's computed digest for comparison

Whether the firewall is enabled

Correct.
A hash can support file identification and integrity comparisons, but it does not independently prove maliciousness.


9. You find an unfamiliar process. What is the best first approach?

Delete every unfamiliar executable

Clear all event logs

Investigate its path, parent process and related evidence

Immediately disable Defender

Correct.
Contextual investigation helps distinguish legitimate activity from suspicious behavior without destroying evidence.


10. Why is patch management important?

It guarantees no attacks can occur

It helps address known vulnerabilities

It replaces MFA

It disables unnecessary event logging

Correct.
Patches fix defects and vulnerabilities, reducing exposure while not eliminating every security risk.

Score: 10/10
