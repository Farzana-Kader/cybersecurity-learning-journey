Day 23 — Introduction to Identity and Access Management (IAM)


1. Learning — Detailed study notes

1.1 What is Identity and Access Management?

Identity and Access Management (IAM) is the collection of policies, processes and technologies used to manage digital identities and control access to systems, applications, networks and data.

IAM answers four important questions:

1. Who are you? — Identity
2. Can you prove it? — Authentication
3. What can you access? — Authorization
4. What did you do? — Accountability and auditing

Example: Imagine a university portal.

- A student logs in using their university credentials.
- The system verifies the student's identity.
- The system allows the student to view their own marks.
- The system records relevant activity in audit logs.

The student should not automatically be allowed to edit marks or access another student's private records.

1.2 What is a digital identity?

A digital identity is the information and attributes used to represent a person, device, service or application within a digital system.

An identity may contain:

- A unique username or identifier
- An email address
- Group memberships and assigned roles
- Authentication methods
- Account status
- Permissions or access assignments

Different identities have different purposes.

Identity type	Example	Typical purpose

Human identity	Student or employee	Access applications and services

Privileged identity	System administrator	Perform authorized administrative tasks

Service identity	Application service account	Allow a service to interact with other systems

Device identity	Company laptop	Identify and authenticate a device

Guest identity	External collaborator	Provide limited access to approved resources

Security concern: Service and administrator accounts can be especially valuable targets. If compromised, they may provide access beyond that of an ordinary user.

1.3 The identity lifecycle

IAM is not limited to logging in. It manages identities throughout their lifecycle.

1. Provisioning

Create an account and grant approved access.


2. Maintenance

Update roles and permissions when responsibilities change.

3. Review

Confirm that access is still necessary and appropriate.

4. Deprovisioning

Disable or remove access when it is no longer required.


For example, when an employee leaves a company, their account and active access must be handled promptly according to the organization's offboarding procedure.

If the account remains active, it could become an entry point for unauthorized access.

1.4 Identification, authentication, authorization and accounting

These terms are related but not interchangeable.

Concept	Meaning	Example

Identification	Claiming an identity	Entering a username

Authentication	Proving the claimed identity	Entering a password and approving a security key

Authorization	Checking permitted actions	Allowing access to an approved folder

Accounting / auditing	Recording relevant activity	Logging when a user accesses a resource

A common security mistake is confusing authentication with authorization.

Authentication does not mean unlimited access. A successfully authenticated user may still be denied access to a particular file or application.

1.5 Authentication versus authorization: a practical example

Suppose a digital forensics laboratory has three users:

- Trainee: Can view assigned case files.
- Investigator: Can view and update authorized case records.
- Administrator: Can manage user accounts and system configuration.

All three may successfully authenticate. However, their authorization differs.

If a trainee tries to change another investigator's case record, the application should deny the action even if the trainee has entered the correct password.

This demonstrates why systems must check permissions for protected resources and actions, not just whether a user has logged in.

1.6 The principle of least privilege

The principle of least privilege (PoLP) means granting users, applications and services only the permissions required to perform their legitimate tasks.

Consider this example:

User	Appropriate access

Student	View their own academic information

Lecturer	Manage authorized course records

Finance staff	Access relevant financial records

IT administrator	Perform approved technical administration

Giving everyone administrator access creates unnecessary risk.

If an account is compromised, an attacker may inherit all permissions assigned to that account. Restricting permissions reduces the potential impact.

Least privilege applies to more than people. It also applies to automated scripts, services, applications and cloud workloads.

1.7 IAM and cybersecurity attacks

IAM helps reduce the impact of several common attacks:

- Credential theft: An attacker steals passwords or session credentials.
- Brute-force attack: Repeatedly tries password combinations against an account.
- Password spraying: Tries a small number of common passwords against many accounts.
- Privilege escalation: Gains permissions beyond those originally granted.
- Account takeover: Gains unauthorized control of a legitimate account.
- Insider misuse: A person abuses access they legitimately possess.
- Orphaned-account abuse: An attacker uses an account that remains active after it should have been disabled.

Controls such as MFA, least privilege, timely deprovisioning, access reviews and audit logging help reduce these risks.

No single control prevents every attack, so IAM should work alongside endpoint security, network controls and monitoring.

1.8 IAM, authentication and access-control systems

You will encounter several related terms during this module:

- IAM: The overall identity and access-management discipline.
- Directory service: Stores and organizes identity information, groups and related attributes.
- Single sign-on (SSO): Allows a user to access multiple supported applications through a shared authentication process.
- Multi-factor authentication (MFA): Uses two or more different authentication-factor categories.
- Privileged Access Management (PAM): Focuses on controlling, monitoring and securing powerful accounts and privileged sessions.

We will study these technologies in more depth in upcoming lessons.

2. Practical — Explore identities on Windows

Time: approximately 25 minutes

For today's lab, we'll inspect your own Windows account and learn how identities and groups relate to access control. These are read-only exercises; you do not need to create accounts or change permissions.

Exercise 1 — Identify your current account

Open PowerShell and run:

whoami


This displays the current account in the form COMPUTERNAME\username or DOMAIN\username.

Then run:

whoami /user


This displays your account's security identifier (SID).

What is a SID? A Security Identifier is a value Windows uses to identify a security principal, such as a user or group. It is not the same thing as the display name or username.

Exercise 2 — Examine group memberships

Run:

whoami /groups


Observe the groups listed for your current security token.

Look for these details:

- Group names and their SIDs
- Whether a group is enabled or marked for a special use
- Whether administrative groups appear

Do not assume that seeing a group name automatically means every administrative action is allowed. Windows also considers token privileges, UAC elevation, access-control rules and other security checks.

Exercise 3 — Review local accounts

Run the following in PowerShell:

Get-LocalUser |
    Select-Object Name, Enabled, LastLogon


This displays local user accounts, their enabled status and the last logon information available.

Some accounts may be disabled or intended for built-in system purposes. Do not disable or delete accounts simply because you do not recognize them.

If the command is unavailable, record the error. Your Windows edition, account permissions or environment may affect which commands are supported.



3. Quiz — Test your understanding

Answer these five questions without looking back at the notes if possible.

Day 23 assessment

5/5 answered

1. What is the primary purpose of IAM?

To scan files for viruses

To manage identities and control access to resources

To replace all network security controls

To increase every user's privileges

Correct!
IAM manages digital identities and ensures access is granted according to approved policies.


2. Which process verifies that a user is who they claim to be?

Authorization

Provisioning

Authentication

Auditing

Correct!
Authentication verifies a claimed identity. Authorization determines what that identity can do.


3. A user changes departments. What should happen to their access?

Keep every old permission permanently

Grant administrator rights automatically

Review and adjust permissions for their new responsibilities

Delete all company accounts

Correct!
IAM should update access when responsibilities change and remove permissions that are no longer needed.


4. What is the principle of least privilege?

Give users access to all files

Grant only the permissions necessary for their tasks

Require everyone to use the same account

Disable audit logging

Correct!
Least privilege reduces unnecessary access and limits the potential damage if an account is compromised.


5. Why should an account be deprovisioned when access is no longer required?

To make the username shorter

To reduce the risk of unauthorized access through that account

To remove all system logs

To bypass authentication

Correct!
Disabling or removing unnecessary access reduces opportunities for misuse or account takeover.

Score: 5/5
