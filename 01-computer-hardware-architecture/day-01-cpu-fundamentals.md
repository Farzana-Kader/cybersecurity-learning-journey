Day 1 — Computer Hardware & Architecture
Topic: The CPU Instruction Cycle
Study time: 1 hour · MSc Cybersecurity & Digital Forensics preparation
Today, we'll learn how a CPU executes instructions, why this matters in cybersecurity, and how an investigator can use this knowledge when analysing suspicious programs.
1. What happens when you run a program?
Imagine you double-click a calculator app. The computer must read the program's instructions, understand them, and perform the required operations.
The CPU generally repeats three main steps:
1. FETCH
Get the instruction

2. DECODE
Understand the instruction

3. EXECUTE
Perform the operation

The cycle repeats for subsequent instructions.


Step 1: Fetch
The CPU retrieves the next instruction from memory, often through its cache.
Two important components help:
- Program Counter (PC): Holds the address of the next instruction to be fetched.
- Registers: Small, fast storage locations inside the CPU used to hold instructions, addresses, and data.
Step 2: Decode
The CPU's control logic interprets the instruction to determine what operation is required.
For example, it may need to add two numbers, compare values, or move data between registers and memory.
Step 3: Execute
The CPU performs the operation. Depending on the instruction, it might calculate a result, access memory, or change the program's execution flow.
The Program Counter is then updated so the CPU can continue with the appropriate next instruction. Branches and jumps can change which instruction comes next.
2. A simple example
Suppose a program needs to calculate 5 + 3.
Stage	What happens
Fetch	CPU retrieves the instruction to add two values.
Decode	CPU identifies the addition operation and its operands.
Execute	The arithmetic logic unit (ALU) calculates \(5+3=8\).
Store result	The result 8 is placed in a register or written to memory as needed.
This is a simplified example; real machine instructions are encoded in binary and can involve several internal CPU operations.
3. Why does this matter in cybersecurity?
The CPU does not inherently know whether a program is good or malicious. It executes instructions according to the machine's architecture and security controls.
Consider a suspicious program:
1. It starts running.
2. Its instructions execute through the CPU.
3. It attempts to read a sensitive file.
4. It attempts to contact an external server.
An investigator needs to understand what the program did and whether it was permitted to do it.
- Malware analysis: Analysts examine instructions and observe program behaviour.
- Memory forensics: Investigators may inspect processes, memory contents, and execution state.
- Incident response: Analysts correlate process activity with file changes and network connections.
- Security controls: Operating-system protections and hardware features can restrict certain operations; the CPU is not simply allowed to do everything a program requests.
Important distinction: Fetch–decode–execute explains how instructions are processed. It does not, by itself, explain why a program is malicious. That requires examining its behaviour, intent, and effects.
4. Three important terms to remember

Program Counter (PC)
Holds the memory address of the next instruction to fetch.




Registers
Very small, very fast storage locations inside the CPU.




ALU (Arithmetic Logic Unit)
Performs arithmetic operations and logical comparisons.
