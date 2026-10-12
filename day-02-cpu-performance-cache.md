Day 2: Computer Hardware & Architecture

Topic: CPU cores, clock speed, registers and cache

1. CPU cores — how many tasks can a CPU handle?

A CPU core is an individual processing unit inside a processor. Each core can execute instructions independently, subject to the CPU's architecture and available resources.

Imagine a supermarket:

- One cashier handles one customer's checkout at a time.
- Multiple cashiers can serve different customers concurrently.
- Similarly, multiple CPU cores can work on different tasks at the same time.

Example: Suppose your computer has a four-core CPU. One core might work on your browser, another on a background task, while others handle additional work. The operating system schedules processes and threads across the available cores.

Why does this matter in cybersecurity?

Security tools often perform multiple operations, such as scanning files, analysing logs and processing network data. Multiple cores can help these workloads run concurrently.

Remember: a process is a running program, while a thread is an execution path within a process. A program does not automatically become four times faster just because the CPU has four cores.

2. Clock speed — how fast does a CPU operate?

Clock speed describes the frequency of a processor's clock, measured in hertz (Hz). Modern CPU speeds are commonly expressed in gigahertz (GHz).
- 1 GHz = 1 billion clock cycles per second.
- 3 GHz = 3 billion clock cycles per second.

However, a clock cycle is not necessarily equal to one completed instruction. Some instructions need multiple cycles, while modern CPUs can execute parts of several instructions during overlapping cycles.

Important: A higher GHz number does not automatically mean a faster CPU. Performance also depends on CPU design, core count, cache, memory and workload.

Cybersecurity connection

When a forensic tool scans a large disk image or a malware-analysis tool processes many files, CPU performance can affect the time required. Investigators must distinguish a genuinely suspicious slowdown from normal resource-intensive work.

3. Registers — the CPU's tiny, fast storage

Registers are small storage locations inside the CPU. They hold values the CPU needs immediately, such as operands, addresses and intermediate results.

Examples include:
- Program Counter (PC): tracks the address of the next instruction to fetch.
- Instruction Register (IR): a traditional architectural model for holding the current instruction being decoded or executed.
- General-purpose registers: hold data, addresses and intermediate results.

Think of registers as items in your hand while working. They're immediately accessible, but there is very little space.

4. Cache — keeping frequently needed data nearby

CPU cache stores copies of data and instructions that the processor may need again. It is generally faster to access than RAM, helping reduce delays.

Simplified storage hierarchy

Registers

Very small · Extremely fast

CPU Cache — L1, L2, L3

Fast storage close to the CPU

RAM

Larger working memory

SSD / HDD

Persistent storage for programs and files

This is a conceptual hierarchy; actual CPU designs vary, and not every access follows a simple step-by-step path.

L1, L2 and L3 cache

Cache	  Typical characteristic

L1	    Usually the smallest and fastest cache, close to each core

L2	    Usually larger than L1, but somewhat slower

L3	    Often larger and shared among multiple cores

Cache levels and sharing arrangements vary by processor model.

What happens when data is missing from cache?
- Cache hit: the required data is found in cache.
- Cache miss: the data isn't found there, so the CPU must fetch it from another level of the memory hierarchy, often a slower one.

Cache misses can reduce performance because the CPU may have to wait for data.

Cybersecurity connection

Cache is also relevant to advanced hardware security. Certain side-channel attacks can infer information by observing indirect effects such as timing or cache behaviour. They may reveal information even when the attacker cannot directly read the protected data.

You do not need to learn the attack mechanics today. Just remember that hardware behaviour can sometimes leak information.

5. Put the concepts together

Imagine you're running a malware scanner on your computer.
1. The operating system schedules the scanner's threads on available CPU cores.
2. Each core executes machine instructions using the CPU instruction cycle.
3. Registers hold immediate values and intermediate results.
4. Cache helps the CPU access frequently needed data and instructions quickly.
5. RAM holds the scanner's active working data, while the SSD or HDD stores files being examined.

If the computer becomes slow, you would investigate CPU utilisation, memory pressure, disk activity and process behaviour before deciding what caused it.

6. Your practical exercise

On Windows, open Task Manager with Ctrl + Shift + Esc.
1. Select Performance → CPU.
2. Look for Cores, Logical processors and Speed.
3. Select Memory and observe how much RAM is in use.
4. Select Processes and compare CPU usage for a few applications.

This is read-only observation; you don't need to install anything or change system settings.

Notice that logical processors may be greater than physical cores because some CPUs support simultaneous multithreading. The cache sizes shown in Task Manager depend on your processor and Windows version.
