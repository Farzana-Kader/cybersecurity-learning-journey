# 🛡️ Windows Security

**Cybersecurity Learning Journey | Days 16–22**

## 📌 Overview

This module focuses on Windows operating system security, defensive security controls, authentication, system monitoring, vulnerability management, and endpoint investigation. It combines theoretical learning with practical PowerShell exercises to develop foundational skills for cybersecurity and digital forensics.

## 🎯 Learning Objectives

- Understand Windows user accounts, privileges, and access permissions.
- Examine Microsoft Defender Antivirus and Windows Defender Firewall.
- Analyze Windows Event Logs for security-relevant activity.
- Understand authentication, password security, and multi-factor authentication (MFA).
- Learn vulnerability management, patching, and system hardening.
- Investigate processes, indicators of compromise (IoCs), and file hashes.
- Apply basic evidence-preservation and incident-response principles.

## 📚 Daily Learning Progress

| Day | Topic | Key Concepts |
|---|---|---|
| 16 | Windows Security Fundamentals | User accounts, UAC, ACLs, least privilege |
| 17 | Defender and Firewall | Antivirus, real-time protection, firewall profiles |
| 18 | Windows Event Logs | Event Viewer, security events, log analysis |
| 19 | Authentication and MFA | Password security, authentication factors, passkeys |
| 20 | Patch Management and Hardening | CVE, CVSS, updates, vulnerabilities, risk |
| 21 | Endpoint Investigation | Processes, PIDs, parent processes, IoCs, SHA-256 |
| 22 | Revision and Assessment | Module revision, practical review, final assessment |

## 🧪 Practical Exercises

### 1. Inspect the Current User

```powershell
whoami
whoami /groups
```

Purpose: Identify the current account and examine its group memberships.

### 2. Review Folder Permissions

```powershell
icacls "$env:USERPROFILE\Desktop"
```

Purpose: Examine access control entries for a user folder.

### 3. Check Microsoft Defender

```powershell
Get-MpComputerStatus |
    Select-Object AntivirusEnabled, RealTimeProtectionEnabled
```

Purpose: Review selected Defender protection status indicators.

### 4. Inspect Firewall Profiles

```powershell
Get-NetFirewallProfile |
    Select-Object Name, Enabled, DefaultInboundAction
```

Purpose: Review the status and inbound-action configuration of Windows Firewall profiles.

### 5. Examine Recent System Events

```powershell
Get-WinEvent -LogName System -MaxEvents 10 |
    Select-Object TimeCreated, Id, LevelDisplayName, ProviderName
```

Purpose: Review recent System log entries and their timestamps.

### 6. Review Installed Updates

```powershell
Get-HotFix |
    Sort-Object InstalledOn -Descending |
    Select-Object -First 10 HotFixID, Description, InstalledOn
```

Purpose: Review recently listed Windows hotfixes. This output alone does not establish whether the system is fully patched.

### 7. Investigate Running Processes

```powershell
Get-Process |
    Sort-Object CPU -Descending |
    Select-Object -First 10 Name, Id, CPU
```

Purpose: Observe running processes, process identifiers, and reported CPU usage.

### 8. Calculate a SHA-256 Hash

```powershell
Get-FileHash "C:\Path\To\Your\File.txt" -Algorithm SHA256
```

Purpose: Calculate a file hash that can support file identification and integrity comparisons. Replace the example path with an appropriate file you own or are authorized to examine.

## 🔎 Important Windows Security Event IDs

| Event ID | Description |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4634 | Account logged off |
| 4648 | Logon using explicit credentials |
| 4720 | User account created |
| 4722 | User account enabled |
| 4724 | Attempt to reset an account password |
| 1102 | Security audit log cleared |

**Investigation note:** Individual events should be interpreted in context and correlated with other evidence before deciding that suspicious activity occurred.

## 🧠 Skills Developed

- Windows security configuration and inspection
- User and permission management fundamentals
- Defensive security monitoring
- Basic event-log analysis
- Authentication and access-security concepts
- Vulnerability and patch-management fundamentals
- Process inspection and file-hash analysis
- Introductory endpoint investigation
- Evidence preservation and incident-response awareness
- PowerShell command-line practice

## 📝 Module Assessment

- **Assessment:** Day 22 — Windows Security Revision
- **Score:** To be recorded after completing the assessment
- **Practical work:** Windows security checks and PowerShell exercises
- **Status:** In progress until the final assessment and documentation are completed

## 🔐 Ethical and Safety Considerations

All practical exercises are intended for systems that I own or have explicit permission to examine. Investigations should follow applicable authorization, privacy, and evidence-handling requirements. Security controls should not be disabled, logs should not be cleared, and suspicious files should not be executed as part of these exercises.

## 🚀 Learning Outcome

By completing this module, I have developed a foundation in Windows security controls, authentication, event monitoring, system hardening, and endpoint investigation. These skills provide a starting point for further study in **Identity and Access Management (IAM), incident response, and digital forensics**.
