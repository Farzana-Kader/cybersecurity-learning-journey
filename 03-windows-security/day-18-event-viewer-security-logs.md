Day 18 — Windows Event Logs & Investigation


1. What is Windows Event Viewer?

Event Viewer is a built-in Windows utility that displays records of system, application and security-related events.

Windows records many events automatically. Investigators can examine these records to understand errors, account activity, service changes and potential security incidents.

For example, if someone repeatedly enters an incorrect password, Windows may record failed logon events, depending on the system configuration and auditing policy.

The four main event categories


Application

Events from applications, including crashes and errors.




System

Windows system components, drivers, services and startup-related events.




Security

Audited security events such as logons and account-management activity, when auditing is enabled.




Setup

Windows installation, setup and update-related events.



2. Understanding event severity

Windows events may have different levels of severity.

Level	Meaning

Information	An operation completed or an event was recorded.

Warning	A condition may require attention.

Error	A problem affected an operation.

Critical	A serious failure occurred.

Audit Success	An audited security action succeeded.

Audit Failure	An audited security action failed.

Audit Success and Audit Failure are audit outcomes rather than ordinary severity levels.

Important: An error isn't necessarily a cyberattack, and a successful audit event isn't automatically evidence of malicious activity. Investigators need context.

3. Important Windows Security Event IDs

An Event ID identifies a particular type of event within a Windows event provider or log.

Here are several useful Security log IDs:

Event ID	What it commonly records

4624	Successful logon

4625	Failed logon

4634	Logoff

4648	Logon attempted using explicit credentials

4720	User account created

4722	User account enabled

4724	Attempt to reset an account password

1102	Security audit log cleared

These events are useful investigation leads, but their availability depends on the system, audit policy and Windows version.

Example: investigating failed logons

Suppose you find many Event ID 4625 records within a short period.

Possible explanations include:

- A user repeatedly entering an incorrect password.
- An application or service using outdated credentials.
- Automated password guessing.
- Another authentication problem.

You should examine the timestamps, account names, logon types, source network address when available, and surrounding events before drawing conclusions.

4. Practical task — open Event Viewer

Task A — Explore the logs

1. Press Windows + R.
2. Type eventvwr.msc.
3. Press Enter.
4. Expand Windows Logs.
5. Open Application, then System.
6. Select a recent event and inspect its General and Details tabs.

Notice the event source, ID, level, date/time and description.

Task B — Inspect Security logs

Navigate to:

Event Viewer → Windows Logs → Security

Look for logon events such as 4624 or 4625 if they are present.

You may need administrator permissions to view the Security log. If access is denied, don't change permissions or auditing settings just for this exercise.

Task C — Read recent system events with PowerShell

Open PowerShell and run:

Get-WinEvent -LogName System -MaxEvents 10 |
  Select-Object TimeCreated, Id, LevelDisplayName, ProviderName


This displays ten recent System log events with their timestamps, IDs, levels and providers.

To inspect a few recent Application events:

Get-WinEvent -LogName Application -MaxEvents 10 |
  Select-Object TimeCreated, Id, LevelDisplayName, ProviderName


These commands read existing logs; they do not modify them.

5. How to approach a basic incident investigation

Imagine a user reports that someone may have tried to access their computer.

A basic investigation might follow this process:


1.Preserve

Avoid clearing logs or changing the evidence.

2.Collect

Identify relevant logs and record the time range.

3.Correlate

Compare failed logons, successful logons and nearby events.

4.Interpret

Consider normal explanations as well as malicious ones.

5.Document

Record findings, limitations and timestamps.


For real forensic work, follow the organisation's incident-response procedures and evidence-handling requirements. Preserve original evidence and work from appropriate copies where possible.

6. Day 18 quiz

Test your understanding

5/5 answered

1. Which Windows tool is used to view application, system and security events?

A. Device Manager

B. Event Viewer

C. Disk Cleanup

D. Task Scheduler only

Correct! Event Viewer provides access to Windows event logs.


2. Which Event ID commonly represents a failed logon?

A. 4624

B. 4625

C. 4634

D. 4720

Correct! Event ID 4625 commonly records a failed logon.


3. What does Event ID 4624 commonly indicate?

A. A successful logon

B. A failed logon

C. A cleared Security log

D. A newly created account

Correct! 4624 commonly records a successful logon.


4. You find many failed logons. What is the best first conclusion?

A. A cyberattack definitely occurred

B. The computer is infected

C. The events need further investigation and context

D. The logs should be deleted

Correct! Failed logons have several possible causes, so correlate the evidence before deciding.


5. Why should investigators avoid clearing logs during an investigation?

A. It makes the computer faster

B. It can destroy relevant evidence

C. It automatically disables encryption

D. It fixes account permissions

Correct! Clearing logs can remove useful evidence and affect an investigation.

Score: 5/5
