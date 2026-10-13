Day 3 — Computer Hardware & Architecture

1. What does 32-bit vs 64-bit mean?

A bit is a binary digit: either 0 or 1. A processor's architecture defines how it handles instructions, registers, memory addresses and data.

In simple terms, 32-bit and 64-bit architectures differ in how they represent and process certain values and addresses.

32-bit
- Uses 32-bit general-purpose registers in a typical 32-bit architecture.
- Has a smaller address space.
- Common in older systems and some embedded devices.

64-bit
- Uses 64-bit general-purpose registers in a typical 64-bit architecture.
- Supports a much larger theoretical address space.
- Common in modern computers.

How much memory can they address?

In a simplified byte-addressable model:
- 32-bit addresses can represent \(2^{32}\) distinct addresses, or 4 GiB of address space.
- 64-bit addresses can represent \(2^{64}\) distinct addresses, or 16 EiB of theoretical address space.

Actual usable memory depends on the processor, operating system, hardware and implementation. Modern 64-bit CPUs typically support fewer than 64 bits of virtual address space.

Remember: A 64-bit processor doesn't automatically make every program faster. Performance depends on the program, hardware and operating system.

2. What is an instruction set?

An Instruction Set Architecture (ISA) defines the machine instructions a processor understands, along with related rules such as registers and data types.

Think of it as a language that software uses to communicate with the processor.

Two important examples are:

x86 / x86-64

Used by many desktop and laptop computers. x86-64 is the 64-bit extension of the x86 instruction-set family.

ARM / AArch64

Used in many smartphones, tablets and other devices. AArch64 is the 64-bit execution state of the AArch64 architecture.

A program compiled for one architecture may not run natively on another without recompilation, translation or emulation.

3. What is machine code?

Computers execute machine instructions represented as binary data. Assembly language gives humans a more readable representation of those instructions.

For example, a simplified assembly instruction might look like:

MOV EAX, 5

ADD EAX, 3

Conceptually:
- MOV EAX, 5 places the value 5 in a register named EAX.
- ADD EAX, 3 adds 3 to that register's value, making it 8.

This example uses x86-style assembly syntax. Actual instructions and register names vary by architecture and execution mode.

4. Why does this matter in cybersecurity?

This topic is especially important for reverse engineering and digital forensics.

Malware analysis: Analysts may inspect machine code or assembly to understand what a suspicious executable does.

Executable compatibility: Knowing whether a file targets x86, x86-64 or ARM helps determine which environment can execute it.

Reverse engineering: Analysts trace instructions, register changes, function calls and branches to understand a program's behaviour.

Memory forensics: The operating system and processor architecture influence process memory layouts, pointer sizes and how memory structures are interpreted.

For example, if a suspicious executable is built for x86-64, an analyst can select appropriate disassembly settings and tools to examine its instructions.

5. Practical exercise — check your Windows architecture

On your Windows computer:
1. Open Settings.
2. Select System → About.
3. Find System type.
4. Check whether it says a 64-bit or 32-bit operating system and which processor architecture is listed.

You can also open Command Prompt and run:

Look for the System Type field. It may show x64-based PC or x86-based PC.

This is a read-only check; you don't need to install anything.

6. Quick quiz — 5 questions

1. How many distinct addresses can a 32-bit address represent?

256

2³²

2⁶⁴

Correct! A 32-bit address has 2³² possible bit patterns.


2. What does an instruction set architecture define?

Only the computer's screen resolution

The machine instructions and related architectural rules a CPU supports

The size of the computer's hard disk

Correct! The ISA defines the instruction interface and other architectural details.


3. Which is a 64-bit architecture used in many smartphones?

AArch64

HTML

NTFS

Correct! AArch64 is the 64-bit execution state of the ARM architecture.


4. What is assembly language?

A readable representation of machine instructions

A type of RAM

A network encryption protocol

Correct! Assembly represents machine instructions using readable mnemonics.


5. Why does architecture matter during malware analysis?

It determines the colour of the application

It helps an analyst interpret instructions and executable compatibility

It guarantees malware cannot run

Correct! The target architecture helps analysts choose suitable disassembly settings and understand program behaviour.

Your score: 5/5
