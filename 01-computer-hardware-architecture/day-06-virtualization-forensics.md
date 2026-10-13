Day 6 — Virtualization, Hardware Security & Digital Forensics

1. What is virtualization?

Virtualization allows one physical computer to run multiple isolated computing environments called virtual machines (VMs).

For example, you could run Windows on your laptop and create a virtual machine running Kali Linux for cybersecurity practice.

A virtual machine can have its own virtual CPU, memory, storage and network interface, even though these resources ultimately come from the same physical computer.

What is a hypervisor?

A hypervisor is software or firmware that creates and manages virtual machines.


There are two common types:

Type	Description	Example

Type 1	Runs directly on the physical hardware	VMware ESXi, Microsoft Hyper-V

Type 2	Runs as an application on a host operating system	Oracle VirtualBox, VMware Workstation

The exact classification can depend on the product's architecture and configuration, but this distinction is useful for introductory study.

Why do cybersecurity students use VMs?
- Safe testing environments: investigate suspicious files in an isolated lab.
- Penetration testing practice: practise security tools against authorised test systems.
- Digital forensics: examine copies of systems and disk images.
- Snapshots: save a VM's state so you can return to it later.

Important: A VM is not automatically perfectly secure. Malware may escape through vulnerabilities or misconfiguration. Use isolated networks, trusted VM software and snapshots, and never assume a snapshot alone protects your host computer.

2. What is hardware-assisted virtualization?

Modern processors provide features that help hypervisors run virtual machines efficiently and isolate them.

Examples include:
- Intel VT-x
- AMD-V

These features allow a hypervisor to manage guest operating systems with hardware support.

Another important feature is IOMMU, which helps restrict how devices using direct memory access (DMA) can access system memory.

Cybersecurity connection

If a VM is poorly isolated, an attacker may attempt to exploit a hypervisor vulnerability to access the host or other VMs. This is commonly called a VM escape.

Hardware-assisted virtualization and correct configuration help strengthen isolation, but updates and secure configuration are still essential.

3. Hardware security threats

Not all attacks target applications or network services. Some target the hardware, firmware or low-level mechanisms of a computer.

A. Firmware attacks
Attackers may attempt to modify firmware so malicious behaviour persists even after the operating system is reinstalled.
Defence: Secure Boot where appropriate, firmware updates and controlled firmware settings.

B. Memory-related attacks
Some attacks exploit weaknesses in how hardware stores or protects data. Rowhammer, for example, can cause bit flips in certain DRAM conditions.
Defence: supported hardware mitigations, system updates and appropriate memory protections.

C. Side-channel attacks
Attackers infer information from indirect signals, such as execution timing or cache behaviour, rather than directly reading the protected data.
Defence: appropriate hardware and software mitigations, secure implementation and timely updates.

You don't need to master the technical details of these attacks today. For admission preparation, focus on recognising the threat, explaining its impact and identifying sensible defences.

4. What is volatile memory?

Volatile memory loses its contents when power is removed. RAM is the most familiar example.

Non-volatile storage, such as an SSD or HDD, retains stored data without continuous power.

This distinction is critical in digital forensics.

Imagine a computer is switched on and suspected of running malware.

Its RAM might contain:
- Running processes and threads.
- Network connections and related state.
- Decrypted data or encryption keys held in memory.
- Injected code or other suspicious memory regions.

If the computer is powered off, much of that volatile evidence will be lost.

Live forensics vs dead-box forensics

Live forensics	Dead-box forensics

Examines a running system	Examines a powered-off system or acquired storage

Can capture volatile information	Focuses more on persistent evidence

May reveal running processes and active connections	May reveal files, logs and other stored artefacts

Collection can alter system state	Acquisition and analysis must still preserve evidence carefully

Key principle: Investigators should follow an appropriate evidence-collection plan. They must consider the risk of losing volatile evidence, the risks of interacting with a compromised machine, and the need to document every action.

Don't automatically power off a suspected compromised computer without considering the incident-response procedure and forensic requirements.

5. How does memory forensics work?

A simplified workflow looks like this:

1. Assess

Document the machine's state and determine what evidence may be lost.

2. Acquire

Use an appropriate, trusted tool to collect memory where authorised.

3. Preserve

Record collection details and protect the acquired evidence.

4. Analyse

Examine processes, memory regions, loaded modules and relevant connections.

5. Correlate

Compare findings with system logs, disk artefacts and network evidence.

A memory image is a snapshot of memory acquired at a particular time. It is not necessarily a complete record of everything that ever happened on the machine.

For example, finding a suspicious process in a memory image can be a useful lead, but an investigator should correlate it with command-line arguments, process relationships, file activity and other evidence.

6. Practical exercise — check virtualization on Windows

Let's inspect your computer without changing any settings.

Task A: Check whether virtualization is enabled
1. Press Ctrl + Shift + Esc to open Task Manager.
2. Select Performance → CPU.
3. Look for Virtualization.
4. Note whether it says Enabled or Disabled.

If the field isn't visible, your Task Manager version or system configuration may differ.

Task B: Think like a forensic investigator


Imagine you discover a running process that is communicating with an unknown external server.

Write down three things you would want to investigate. Good starting points include:
- The process name, PID and parent process.
- The remote IP address and connection details.
- The process executable's location, signature and hash.

These are investigative leads, not proof that the process is malicious.

7. Day 6 quiz — five questions


1. What does a hypervisor do?

Creates and manages virtual machines

Encrypts all network traffic automatically

Replaces the CPU

Correct! A hypervisor manages virtual machines and their access to computing resources.


2. Which is an example of a Type 2 hypervisor application?

Oracle VirtualBox

The ALU

A page table

Correct! VirtualBox commonly runs as an application on a host operating system.


3. Why is RAM important in live forensics?

It permanently retains all evidence after power loss

It may contain volatile evidence such as running process state

It stores only photographs

Correct! RAM may hold evidence that disappears when power is removed.


4. What is a side-channel attack?

An attack that infers information through indirect signals such as timing

A normal computer shutdown

A type of disk partition

Correct! Side-channel attacks exploit indirect information leakage rather than necessarily reading protected data directly.


5. Why shouldn't an investigator automatically power off a suspected compromised machine?

It would increase the CPU clock speed

It could destroy volatile evidence needed for the investigation

It guarantees that malware spreads

Correct! Powering off loses much volatile memory evidence, so the response must consider evidence preservation and safety.

Your score: 5/5
