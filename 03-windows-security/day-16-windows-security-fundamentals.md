Day 16 — Windows Security Fundamentals

1. What is Windows Security?

Windows Security is the collection of features and controls used to protect a Windows computer from unauthorised access, malware, data theft and other threats.

Some important components are:
- User accounts: Identify who is using the computer.
- Permissions: Control which files and resources a user can access.
- User Account Control (UAC): Helps prevent unauthorised changes requiring administrative privileges.
- Microsoft Defender Antivirus: Detects and helps remove malware.
- Windows Defender Firewall: Controls network traffic according to firewall rules.
- Windows Security logs: Record events useful for troubleshooting and investigations.
- BitLocker: Helps protect data on a supported drive through encryption.

Today, we'll focus on accounts, permissions and administrator privileges.

2. Standard user vs administrator

Windows accounts commonly operate with different levels of privilege.

Standard user

Can use applications, work with permitted files and change many personal settings. System-wide changes and protected resources generally require additional permission.

Lower privilege




Administrator

Can perform system-wide tasks, such as installing certain software, changing security settings and managing user accounts, subject to Windows security controls.

Elevated privilege



Why does this matter in cybersecurity?

Suppose malware runs under a standard user account. Its ability to modify protected system files or change system-wide settings may be limited. If it gains administrative privileges, the potential damage can be much greater.

This is why security professionals follow the principle of least privilege: give each user or process only the permissions necessary to perform its job.

3. What is User Account Control (UAC)?

UAC is a Windows security feature that prompts for approval or administrator credentials when an action requires elevation.

For example, when an application attempts to install software or change a protected system setting, Windows may display a confirmation prompt.

Remember:

- UAC is not an antivirus program.
- Clicking Yes approves the requested elevation; it does not prove that the program is safe.
- You should verify the application and the reason for the prompt before approving it.

4. What are file permissions?

File permissions determine who can access a file or folder and what actions they can perform.

Common permissions include:

Permission	Meaning

Read	View file contents

Write	Modify or create data

Read & execute	Read files and run permitted programs

Modify	Read, write and delete, subject to the applicable permissions

Full control	Includes managing permissions and other extensive actions

Windows commonly uses Access Control Lists (ACLs) to specify which users or groups receive particular permissions.

Example: A student may have permission to read a project report but not modify the original file. An administrator or file owner may have broader access, depending on the configured permissions.

An important distinction: being the owner of a file and having particular permissions are related, but they are not identical concepts.

5. Practical exercises on your computer

These commands inspect your current configuration. You do not need to change any security settings.

Task A — Identify your current account

Open Command Prompt and run:

whoami



This displays the current account in DOMAIN\username or COMPUTERNAME\username format.

Then run:

whoami /groups


This lists the security groups and related information associated with your current security token. An account's group membership alone does not necessarily mean the current process is elevated.

Task B — Inspect a folder's permissions

Run:

icacls "$env:USERPROFILE\Desktop"



This displays access-control entries for your Desktop folder if it exists at that path.

Look for:

- User or group names.
- Permission abbreviations.
- Whether permissions are inherited from a parent folder.

You may see entries such as (F) for Full control, (M) for Modify, (RX) for Read and execute, and (R) for Read.

Task C — Check your account type

Open Settings → Accounts → Your info.

Depending on your Windows version and account setup, this page may indicate whether your account is an Administrator or Standard user.

Do not change account types or grant new permissions for this exercise.

6. Day 16 quiz

Test your understanding

5/5 answered

1. Which account type generally has fewer privileges by default?

A. Administrator

B. Standard user

C. SYSTEM account

D. All have identical privileges

Correct! A standard user generally has fewer privileges for system-wide changes.


2. What is the main purpose of UAC?

A. Scan every file for viruses

B. Help control elevation for administrative changes

C. Encrypt all network traffic

D. Create backups automatically

Correct! UAC prompts for approval or credentials for actions requiring elevation.


3. What does the principle of least privilege mean?

A. Give everyone full control

B. Use no passwords

C. Grant only the permissions needed for a task

D. Disable all user accounts

Correct! Least privilege limits the permissions available to each user or process.


4. Which Windows tool can display file and folder permissions from the command line?

A. ipconfig

B. icacls

C. nslookup

D. ping

Correct! icacls displays or manages Windows discretionary access control lists.


5. Why are file permissions relevant to digital forensics?

A. They show which permissions and access controls apply to evidence

B. They guarantee that malware cannot run

C. They replace the need to preserve evidence

D. They automatically decrypt every file

Correct! Permissions help investigators understand access restrictions and the context of files, though they do not alone establish who accessed a file.

Score: 5/5
