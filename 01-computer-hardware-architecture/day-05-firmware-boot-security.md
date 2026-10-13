Day 5 — BIOS/UEFI, Bootloaders, Secure Boot & TPM

1. What happens when you switch on a computer?

When you press the power button, Windows doesn't appear instantly. The computer must initialise its hardware, identify a bootable device and load the operating system.

The process can be simplified into these stages:

1.Power on

The CPU begins executing firmware instructions.

2.UEFI firmware

Initialises hardware and identifies a boot option.

3.Boot manager / bootloader

Selects and starts the operating system's boot components.

4.Windows kernel

The operating system kernel and required components begin loading.

5.Login screen

Windows completes startup and presents the sign-in interface.

This is a simplified Windows startup sequence; the exact steps vary by device, configuration and boot mode.

2. What is BIOS?

BIOS stands for Basic Input/Output System.

It is traditional firmware that helps initialise hardware and begin the boot process.

Older computers commonly used legacy BIOS booting. Most modern computers use UEFI instead.

3. What is UEFI?

UEFI stands for Unified Extensible Firmware Interface.

UEFI is a modern firmware interface that supports features such as boot management, firmware configuration and Secure Boot.

BIOS (legacy)	UEFI

Traditional firmware approach	Modern firmware interface

Commonly associated with MBR booting	Commonly used with GPT-partitioned disks

Does not provide UEFI Secure Boot	Can support Secure Boot

Important: BIOS and UEFI are often compared informally, but UEFI is not simply a newer version of the old BIOS code. They use different firmware interfaces and boot mechanisms.

4. What is a bootloader?

A bootloader is software involved in loading or starting an operating system.

On a typical Windows system, Windows Boot Manager helps select the Windows boot entry, and Windows OS loader (winload.efi on UEFI systems) loads the Windows kernel and essential components.

Why is this important?

Imagine an attacker modifies the startup process so that malicious code runs before Windows security tools start. This could allow the attacker to interfere with the system at a very early stage.

This is one reason boot integrity matters.

5. What is Secure Boot?

Secure Boot is a UEFI security feature that checks the digital signatures of boot components against trusted keys and policies.

Its purpose is to help prevent unauthorised or untrusted boot software from running during startup.

For example:
- A trusted, properly signed boot component may pass verification.
- An unauthorised or modified component that fails verification may be blocked.

Secure Boot is not a guarantee that a computer is completely safe. It doesn't stop every form of malware, and its effectiveness depends on configuration, trusted keys and the security of the boot components themselves.

Cybersecurity connection: bootkits

A bootkit is malware that targets the boot process or early startup components to gain persistence or interfere with system security.

Secure Boot helps defend against some boot-level threats by verifying boot components before execution.

For a forensic investigator, suspicious boot settings, unexpected firmware changes and unusual boot components may be important evidence.

6. What is TPM?

TPM stands for Trusted Platform Module.

It is a security component that can securely store or protect cryptographic keys and record certain platform measurements.

A TPM can support features such as:
- BitLocker: disk encryption, including protecting key material.
- Measured boot: recording measurements of components involved in startup.
- Device integrity checks: allowing software to evaluate evidence about a device's boot state.

Secure Boot vs TPM

Feature	Main purpose

Secure Boot	Verifies boot components against firmware trust policies.

TPM	Provides protected key operations and platform measurement capabilities.

Measured boot	Records measurements of startup components, often using TPM platform configuration registers.

BitLocker	Protects data through volume encryption; TPM can help protect its encryption keys.

A useful way to remember it:

Secure Boot checks; TPM protects keys and stores measurements; measured boot records evidence about startup.

These technologies can work together, but they perform different functions.

7. Practical exercise on your Windows computer

Let's check your current settings without changing anything.

Task A — Check Secure Boot status
1. Press Win + R.
2. Type msinfo32 and press Enter.
3. In System Information, find BIOS Mode.
4. Find Secure Boot State.

You might see:
- BIOS Mode: UEFI
- Secure Boot State: On

Your result may differ depending on your computer and configuration.

Task B — Check TPM
1. Press Win + R.
2. Type tpm.msc and press Enter.
3. Check whether a compatible TPM is detected.
4. If it is available, look for the Specification Version, commonly 2.0 on modern Windows 11 systems.

Safety note: Only inspect these settings today. Don't change firmware settings, clear the TPM or modify Secure Boot keys. Those changes can affect startup or encrypted-data access.

8. Why this matters in digital forensics

Consider a computer suspected of being compromised.

An investigator might ask:
- Was Secure Boot enabled?
- Was the boot configuration changed?
- Are there signs of a bootkit or unauthorised boot component?
- Does the system provide relevant boot-integrity measurements?
- Could disk encryption affect evidence acquisition?

These questions help establish the system's security state. Investigators should preserve evidence and document findings rather than assuming that a disabled Secure Boot setting proves an attack occurred.

9. Day 5 quiz — five questions
  
1. What is UEFI primarily responsible for in this context?

Editing documents

Providing firmware services and starting the boot process

Scanning every downloaded file

Correct! UEFI initialises hardware and helps select and start boot components.


2. What does Secure Boot help do?

Verify boot components against trusted keys and policies

Guarantee that all malware is blocked

Encrypt every file on the computer

Correct! Secure Boot verifies boot components according to configured trust policies.


3. What does TPM stand for?

Trusted Platform Module

Total Protection Manager

Trusted Processing Memory

Correct! TPM stands for Trusted Platform Module.


4. What is a bootkit?

A normal computer accessory

Malware that targets the boot process or early startup components

A backup file format

Correct! Bootkits target the startup chain and may attempt to establish early persistence.


5. How can you inspect Secure Boot status in Windows?

Open msinfo32 and check Secure Boot State

Delete the bootloader

Clear the TPM

Correct! System Information lets you inspect BIOS Mode and Secure Boot State without changing them.

Your score: 5/5
