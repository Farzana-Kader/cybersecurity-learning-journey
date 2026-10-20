Day 17 — Windows Security








1. Microsoft Defender Antivirus

Microsoft Defender Antivirus is a built-in Windows security component that helps detect, block and remove malware.

Malware includes viruses, ransomware, spyware, trojans and other malicious software.

How does it help protect your computer?
- Real-time protection: Checks files and activity as they are accessed or executed.
- Security intelligence updates: Updates threat information used to recognise malicious software.
- Cloud-delivered protection: Can use cloud-based intelligence to help identify emerging threats, depending on configuration.
- Scheduled and manual scans: Check files and locations for threats.
- Protection history: Shows information about detected threats and actions taken.

Quick example

Imagine downloading a file that contains malware. Defender may detect suspicious content and block or quarantine it before it causes harm.

However, antivirus cannot guarantee detection of every threat. Keeping software updated and avoiding suspicious downloads remain important.

2. Windows Defender Firewall

Windows Defender Firewall controls network traffic according to configured rules.

For example, it can block an unsolicited incoming connection while allowing a permitted application to communicate over the network.

Feature	Defender Antivirus	Windows Firewall

Main purpose	Malware protection	Network traffic control

Examines	Files and potentially malicious activity	Network connections and traffic

Example	Detects a malicious executable	Blocks an unauthorised incoming connection

Remember: Antivirus and firewall protection complement each other. Neither replaces the other.

3. Windows Firewall profiles

Windows has three main firewall profiles:

- Domain: For connections to networks where a computer authenticates to an organisation's domain.
- Private: For trusted networks, such as a properly configured home network.
- Public: For untrusted networks, such as public Wi-Fi.

These profiles can use different rules. Public networks generally call for stricter inbound access.

Do not assume a network is safe merely because it is marked Private. The profile should reflect the actual trust level of the network.

4. What is security hardening?

Security hardening means reducing the ways an attacker could compromise a system.

Common Windows hardening practices include:
1. Install Windows and application security updates.
2. Keep Microsoft Defender and firewall protection enabled.
3. Use a standard user account for everyday tasks when practical.
4. Enable multi-factor authentication where available.
5. Use strong, unique passwords.
6. Remove unnecessary applications and disable unneeded services carefully.
7. Enable device encryption when supported and store recovery keys securely.
8. Back up important files and test recovery procedures.
9. Review account permissions and security logs.

Security hardening is about reducing risk, not making a system completely invulnerable.

5. Practical tasks — inspect your Windows security

We'll inspect your settings without disabling protection or changing firewall rules.

Task A — Open Windows Security

1. Open the Windows Start menu.
2. Search for Windows Security.
3. Open Virus & threat protection.
4. Review the displayed protection status and any warnings.

Check whether real-time protection appears enabled. The exact options may differ depending on your Windows version or whether another antivirus product is installed.

Task B — Inspect Defender status

Open PowerShell. If permitted on your system, run:

Get-MpComputerStatus |
  Select-Object AntivirusEnabled, RealTimeProtectionEnabled,
                AntivirusSignatureLastUpdated


Look for whether antivirus and real-time protection are enabled and when the security intelligence was last updated.

If the command is unavailable or access is restricted, use the Windows Security interface instead.

Task C — Inspect firewall profiles

Run:

Get-NetFirewallProfile |
  Select-Object Name, Enabled, DefaultInboundAction,
                DefaultOutboundAction


Observe the Domain, Private and Public profiles.

Task D — Check Windows updates

Open Settings → Windows Update and review whether updates are pending.

You don't need to install anything immediately for this exercise, but you should understand why security updates matter.


6. Day 17 quiz

Test your understanding

5/5 answered

1. What is the primary purpose of Microsoft Defender Antivirus?

A. Assign IP addresses

B. Detect and help remove malware

C. Route packets between networks

D. Manage file permissions only

Correct! Defender Antivirus helps detect, block and remove malicious software.


2. What does Windows Defender Firewall primarily control?

A. Network traffic according to rules

B. The brightness of the screen

C. The computer's RAM capacity

D. The contents of every document

Correct! A firewall controls network connections and traffic based on its rules.


3. Which firewall profile is generally intended for untrusted networks such as public Wi-Fi?

A. Domain

B. Private

C. Public

D. Administrator

Correct! The Public profile is intended for networks that should be treated as untrusted.


4. What is security hardening?

A. Increasing screen resolution

B. Reducing potential attack paths and unnecessary exposure

C. Disabling all security tools

D. Making every user an administrator

Correct! Hardening reduces attack surface through safer configurations and updates.


5. Why should security intelligence be updated?

A. To help Defender recognise newer threats

B. To disable Windows Firewall

C. To remove the need for backups

D. To guarantee every attack is detected

Correct! Updated threat intelligence helps security tools recognise emerging and changing threats.

Score: 5/5
