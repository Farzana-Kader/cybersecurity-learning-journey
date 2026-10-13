Day 7 — Hardware & Architecture Revision

1.Your revision map

Day 1 — CPU instruction cycle

Fetch → Decode → Execute. The Program Counter tracks the next instruction address, and the ALU performs arithmetic and logical operations.

Day 2 — Cores, clock speed, registers and cache

Cores execute work, clock speed measures frequency, registers hold immediate values, and cache helps the CPU access frequently needed data quickly.

Day 3 — 32-bit, 64-bit and instruction sets

Architecture affects registers, addressing and instruction execution. x86-64 and AArch64 are examples of 64-bit architectures.

Day 4 — Virtual memory and paging

Virtual pages map to physical frames using page tables. Memory protection helps isolate processes.

Day 5 — Boot security

UEFI starts the boot process, Secure Boot verifies boot components against trust policies, and TPM supports protected keys and platform measurements.

Day 6 — Virtualization and forensics

Hypervisors manage VMs. RAM may contain volatile evidence, so investigators must plan evidence acquisition carefully.

2. Practical assessment — investigate a suspicious computer

Imagine you are a junior digital forensic analyst.

A company reports that an employee's computer became unusually slow. An unknown program was running, and the employee noticed unexpected network activity.

Your task is to identify what you would investigate first.

Read the scenario and answer the questions below. There may be more than one useful investigation step, but select the best answer for each question.

3. Final quiz — 10 questions

Assessment

10/10 answered

1. What is the correct basic CPU instruction cycle?

Execute → Fetch → Decode

Fetch → Decode → Execute

Decode → Execute → Fetch

Correct! — The CPU fetches an instruction, decodes it and executes the operation.

2. Which CPU component performs arithmetic and logical operations?

ALU

SSD

Program Counter

Correct! — The ALU performs arithmetic and logical operations.

3. A CPU has a 3 GHz clock. What does this describe?

Exactly 3 billion completed instructions per second

Three billion clock cycles per second

Three gigabytes of memory

Correct! — Clock frequency measures cycles per second, not a guaranteed instruction count.

4. Which statement about 64-bit architecture is correct?

It guarantees every program runs faster

It supports a much larger theoretical address space than 32-bit addressing

It prevents all malware

Correct! — A 64-bit address can represent many more distinct addresses than a 32-bit address.

5. What maps virtual pages to physical memory frames?

Page tables

The Windows desktop

A firewall rule

Correct! — Page tables contain mappings used by the memory-management hardware.

6. What is the primary role of Secure Boot?

Verify boot components against configured trust policies

Scan every email attachment

Replace disk encryption

Correct! — Secure Boot helps prevent unauthorised boot components from running.

7. Which statement about a TPM is correct?

It is a type of web browser

It supports protected cryptographic key operations and platform measurements

It replaces system RAM

Correct! — TPMs provide hardware-backed security capabilities.

8. What manages virtual machines?

A hypervisor

A page fault

A network packet

Correct! — A hypervisor creates and manages virtual machines.

9. Why might an investigator collect RAM from a running computer?

RAM may contain volatile evidence such as process and connection state

RAM permanently preserves every deleted file

RAM proves who committed an offence

Correct! — Volatile memory can contain useful evidence that may disappear after shutdown.

10. A computer has an unknown process and unexpected network activity. What is the best initial approach?

Immediately declare the process malicious

Document the state and correlate process, file, network and relevant log evidence

Delete the process and erase its files

Correct! — Preserve evidence and correlate multiple sources before drawing conclusions.

10/10
You've demonstrated a strong understanding of the core concepts.
