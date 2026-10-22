
Day 21 — Windows Security: Malware Detection, Processes & Incident Investigation

Part 1 — Learning (20 minutes)

1. What is endpoint security?

An endpoint is a device connected to a network, such as a desktop computer, laptop, or server.

Endpoint security protects these devices against threats such as malware, unauthorized access, suspicious applications, and malicious activity.

For example, imagine you download a file that appears to be a PDF reader. After opening it, your computer starts behaving unusually and an unfamiliar process begins running.

A security analyst would investigate the file, the processes it created, its network connections, and relevant security logs.

Common endpoint security technologies include:

Antivirus: Detects and blocks known or suspicious malware.

Endpoint Detection and Response (EDR): Collects endpoint activity and helps analysts detect, investigate, and respond to threats.

Host-based firewall: Controls network traffic entering or leaving a device according to its rules.

Application control: Restricts which applications or scripts are permitted to run.

Antivirus and EDR overlap in some capabilities, but EDR generally provides more extensive investigation and response capabilities.

2. What is a process, and why do analysts investigate it?

A process is a running instance of a program.

When you open a browser, Windows creates one or more processes to run its components. A process has a unique process identifier called a PID while it exists.

Consider this example:

Process  Possible purpose

explorer.exe  Windows desktop and File Explorer

notepad.exe  Text editing

powershell.exe  Running PowerShell commands and scripts

msedge.exe  Microsoft Edge browser

These are examples of legitimate Windows or application processes. However, a familiar process name alone does not prove that a particular instance is genuine. Malware may imitate a legitimate name.

An analyst may examine:

Process name and PID.

Executable file path.

Parent process.

Command-line arguments.

File signature and hash.

Network connections and related security events.

Example: If a document unexpectedly launches PowerShell, that relationship may deserve investigation. However, PowerShell is also used for legitimate administration, so context is essential.

3. What is a parent process and a child process?

When one process starts another, the first is called the parent process, and the newly launched one is the child process.

A simplified process tree might look like this:

explorer.exe

User opens an application

Application.exe

Child process

powershell.exe

A further child process — investigate if unexpected

This is an illustrative example, not a claim that every application follows this exact process chain.

Why does this matter? An investigator can trace how a suspicious activity began. An unexpected process relationship may help explain how a malicious script or payload was launched.

4. What is malware detection?

Malware is software designed to perform harmful or unauthorized actions. Common types include:

Virus: Attaches to files or programs and can spread when infected content runs.

Worm: Can spread between systems without requiring a host file in the same way a traditional virus does.

Trojan: Disguises itself as legitimate or useful software.

Ransomware: Encrypts or otherwise denies access to data, often demanding payment.

Spyware: Collects information without appropriate authorization.

Security tools may detect malware using several approaches.

Detection method

How it works

Signature-based

Matches files or activity against known malicious patterns

Heuristic

Looks for characteristics associated with malicious software

Behavior-based

Examines actions such as suspicious process creation or attempts to alter protected settings

Reputation-based

Uses information about the trustworthiness or history of a file, publisher, or source

No single method detects every threat. A new or modified malicious program may evade one detection method but be identified by another.

5. What are Indicators of Compromise (IoCs)?

An Indicator of Compromise (IoC) is an observable artifact that may indicate a system has been compromised.

Examples include:

A known malicious file hash.

A suspicious domain or IP address.

An unexpected executable in an unusual directory.

A suspicious persistence mechanism.

Evidence of unauthorized account activity.

A file hash is a digital fingerprint calculated from a file's contents. For example, SHA-256 produces a 256-bit hash, usually represented as 64 hexadecimal characters.

If two files have different SHA-256 hashes, their contents differ. If their hashes match, that is strong evidence that the contents are identical, assuming a reliable hash calculation and no practical collision.

Important forensic point: An IoC is evidence to evaluate, not automatic proof of malicious activity. Analysts correlate multiple indicators with timestamps, logs, file information, and system context.

6. What should an analyst do when malware is suspected?

A security analyst generally follows an incident-response process.

1. Identify

Observe alerts, symptoms, and suspicious activity.

2. Preserve evidence

Record timestamps and relevant details; avoid unnecessary changes.

3. Investigate

Correlate process activity, logs, files, and network indicators.

4. Contain

Follow an authorized response procedure to limit further damage.

5. Recover and review

Restore systems safely, verify their status, and document lessons learned.

If this were a real suspected compromise, do not immediately delete suspicious files or terminate processes just because they look unfamiliar. Those actions can destroy evidence. Follow your organization's incident-response procedures and escalation requirements.

Part 2 — Practical exercises (25 minutes)

We'll use PowerShell to inspect process information and calculate a file hash. These exercises are read-only and do not require intentionally running malware.

Task A — Inspect running processes

Open PowerShell and run:

Get-Process |
    Sort-Object CPU -Descending |
    Select-Object -First 10 Name, Id, CPU

What this does:

Get-Process retrieves running processes.

Sort-Object CPU -Descending places processes with higher reported CPU usage first.

Select-Object displays the first ten entries with their names, PIDs, and CPU values.

Record: One process name, its PID, and its CPU value.

Note that the CPU value is accumulated processor time, not necessarily the percentage of CPU currently being used.

Task B — Inspect parent and child relationships

Run:

Get-CimInstance Win32_Process |
    Select-Object -First 20 ProcessId, ParentProcessId, Name

Find the ProcessId and ParentProcessId columns.

For example, if one process has PID 2400 and another process has parent PID 2400, the second process records the first process as its parent.

Windows PIDs can be reused after a process exits, so PID relationships should be interpreted alongside timestamps and other evidence during a real investigation.

Task C — Calculate a SHA-256 file hash

Choose a harmless file you own, such as a text document. Replace the example path with the actual path of that file.

Get-FileHash "C:\Path\To\Your\File.txt" -Algorithm SHA256

Record the algorithm and the resulting hash.

To see how the hash responds to a file change, you may create a temporary text file, calculate its hash, change its contents, and calculate the hash again. Use only a file you created for this exercise.

Task D — Review Defender's detection history

Open Windows Security.

Select Virus & threat protection.

Open Protection history, if available.

Review whether any detections are listed.

Do not restore quarantined files or change protection settings during this exercise. If the history is empty, simply record that no entries were displayed.


Part 3 — Quiz (5 questions)

Answer without looking back at the lesson if possible.

1. What is the main purpose of an endpoint detection and response (EDR) system?


To collect and investigate endpoint activity and support response to threats

To replace every operating-system update

To guarantee that no malware can run

To manage only user passwords

Correct! To collect and investigate endpoint activity and support response to threats

2. A process has ParentProcessId 3200. What does this information indicate?


Its parent process is recorded with PID 3200

Its CPU usage is 32 percent

Its file has a SHA-256 hash beginning with 3200

The process is automatically malicious

Correct! Its parent process is recorded with PID 3200


3. Which detection approach examines actions performed by a program rather than relying only on a known file signature?


Behavior-based detection

Signature-only detection

File compression

Account identification

Correct! Behavior-based detection

4. What does a SHA-256 file hash primarily help an analyst do?


Compare file contents through a calculated fingerprint

Prove who created the file in every case

Determine the exact physical location of a computer

Automatically remove malicious code

Correct! Compare file contents through a calculated fingerprint


5. You see an unfamiliar process name in Task Manager. What is the most appropriate conclusion?


It must be malware and should immediately be deleted

It is safe because Windows allows it to run

It needs further investigation using context and supporting evidence

Its name alone proves that an attack has occurred

Correct! It needs further investigation using context and supporting evidence

Your score: 5/5
