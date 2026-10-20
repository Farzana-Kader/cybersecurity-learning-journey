Day 19 — Authentication & Account Security

1. What is authentication?

Authentication is the process of verifying that a user or system is who or what it claims to be.

For example, when you sign in to Windows, the system checks your credentials before granting access.

Don't confuse these three concepts:

Concept	Meaning	Example

Identification	Claiming an identity	Entering a username

Authentication	Proving the identity	Providing a password or security key

Authorization	Determining permitted actions	Permission to open a protected folder

Authentication answers: Who are you?

Authorization answers: What are you allowed to do?

2. The three authentication factors

Authentication factors generally fall into three categories.









1. Something you know

A password, PIN or passphrase.

Risk: It may be guessed, stolen or disclosed.












2. Something you have

A hardware security key, smart card or authenticator device.

Risk: The device may be lost or stolen.












3. Something you are

A biometric characteristic, such as a fingerprint or facial feature.

Risk: Biometric systems can make errors and require secure handling of biometric data.



What is multi-factor authentication (MFA)?

MFA requires two or more different authentication factors.

Examples:
- Password + authenticator approval.
- PIN + a separate hardware security key.
- Password + a biometric factor, when implemented as separate factors.

Two passwords are not MFA because both are something you know.

MFA makes account compromise harder even if a password is stolen. Phishing-resistant methods, such as properly configured FIDO2 security keys or passkeys, can provide stronger protection against fake login pages.

3. Password security

A secure password should be difficult to guess and unique to each account.

Good practices include:
- Use long, unique passwords or passphrases.
- Avoid names, birthdays and common patterns.
- Never reuse important passwords across websites.
- Use a reputable password manager.
- Enable MFA wherever possible.
- Change a password promptly if it is compromised.

A password's length and unpredictability are important. Complexity rules alone do not make a weak, predictable password secure.

How Windows stores passwords

Windows does not normally store user passwords as readable plain text. Windows authentication uses credential-verification mechanisms, including password-derived hashes in relevant account stores.

A hash is a one-way transformation used to verify a value without storing the original password in plain text. Password security depends on the storage method, salting, computational cost and other protections.

Forensic relevance: investigators may encounter credential stores or authentication artefacts. These are sensitive evidence and should be handled only through authorised forensic procedures.

4. Account lockout and brute-force attacks

A brute-force attack repeatedly tries possible passwords until one succeeds.

A password-spraying attack tries a small number of common passwords against many accounts to avoid triggering some per-account controls.

Organisations may use account lockout policies, throttling and monitoring to limit repeated authentication attempts.

However, overly strict lockout settings can allow attackers to deny legitimate users access by deliberately triggering lockouts. Security teams must balance protection and availability.

Useful defensive controls include:
- MFA.
- Strong, unique passwords.
- Rate limiting and account lockout policies.
- Monitoring failed logons.
- Alerts for unusual authentication patterns.

Remember the Windows Event Viewer lesson: Event ID 4625 commonly represents a failed logon. A pattern of failures may deserve investigation, but it does not prove an attack on its own.

5. Practical exercises — inspect your Windows account

These exercises are read-only. Don't attempt to recover passwords or change account security policies.

Task A — Identify your current account

Open Command Prompt:

whoami


Then run:

whoami /groups


Observe your account identity and group memberships. These commands don't reveal your password.

Task B — Inspect local account information

In PowerShell, run:

Get-LocalUser |
  Select-Object Name, Enabled, LastLogon


This lists local Windows accounts and selected properties. Depending on your edition, permissions and environment, the command may be unavailable or return limited information.

Do not share account details publicly if you prefer to keep them private.

Task C — Review sign-in security

Open Settings → Accounts → Sign-in options.

Review which sign-in methods are available on your computer, such as Windows Hello PIN, fingerprint or facial recognition. Availability depends on your device and configuration.

Also consider whether the Microsoft account or other online accounts you use have MFA enabled.

6. Day 19 quiz

Test your understanding

5/5 answered

1. What does authentication verify?

A. Which files a user can delete

B. The identity a user or system claims to have

C. The computer's screen resolution

D. Whether a network is public

Correct! Authentication verifies claimed identity.


2. Which combination is an example of MFA?

A. Password + another password

B. Two security questions

C. Password + a separate hardware security key

D. Username + password

Correct! A password and a hardware security key are different factor types.


3. What is password spraying?

A. Trying many passwords against one account only

B. Trying a small set of common passwords across multiple accounts

C. Encrypting a password manager

D. Disabling account authentication

Correct! Password spraying distributes a few guesses across multiple accounts.


4. Which Windows Security event commonly records a failed logon?

A. 4624

B. 4625

C. 4634

D. 4720

Correct! Event ID 4625 commonly records failed logons.


5. Why can a strict account lockout policy create a security problem?

A. It automatically disables MFA

B. An attacker may deliberately lock out legitimate users

C. It encrypts files too strongly

D. It makes every password public

Correct! Repeated malicious attempts can trigger lockouts and disrupt legitimate access.

Score: 5/5
