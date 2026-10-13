Day 4 — Virtual Memory, Paging and Page Tables

1. What is virtual memory?

Imagine your computer has 8 GB of RAM, and you're running a browser, a music player and several other applications.

How does the operating system keep each application organised and prevent them from freely accessing one another's memory?

It uses virtual memory.

Virtual memory gives each process its own virtual address space. The operating system and CPU's memory-management hardware translate virtual addresses into physical memory addresses.

Think of it like an apartment building:
- Virtual address space: each apartment's own room-numbering system.
- Physical RAM: the actual rooms in the building.
- Memory-management hardware: the system that maps a room number to its actual physical location.
- Operating system: manages the arrangements and permissions.

Each process has its own view of memory, so the same virtual address can refer to different physical memory locations in different processes.

Why is this important for security?

Suppose a browser and a password manager are running at the same time. Memory isolation helps prevent the browser from directly accessing the password manager's private memory.

This protection is not absolute against every possible attack, but it is a fundamental security mechanism.

2. What is paging?

Paging divides virtual memory into fixed-size blocks called pages and physical memory into corresponding blocks called frames.

The operating system can map virtual pages to physical frames without requiring an entire process to occupy one continuous region of RAM.

Simplified example

Virtual pages belonging to one process

Page 0

Page 1

Page 2

Page-table mappings

Physical frames in RAM

Frame 4

Frame 1

Frame 7

Here, Page 0 maps to Frame 4, Page 1 to Frame 1, and Page 2 to Frame 7. The numbers are illustrative.

Notice that the pages don't have to map to adjacent physical frames.

A common page size on modern systems is 4 KiB, although other page sizes are supported.

3. What is a page table?

A page table records how virtual pages map to physical frames, along with information used to control access.

For example, a page-table entry may contain information about:
- The physical frame associated with a virtual page.
- Whether the mapping is present or valid.
- Whether the page can be written to.
- Whether access is permitted in user mode or restricted to privileged code.

The CPU's memory-management unit (MMU) uses these mappings to translate addresses and enforce memory-access permissions.

What happens if access is not permitted?

The CPU may raise a page fault. The operating system then handles the situation.


A page fault does not automatically mean a program has crashed or an attack is happening. It can occur during normal operation, such as when a page must be loaded into RAM or when software accesses memory incorrectly.


4. What is a page fault?

There are two useful situations to distinguish:

A. Valid page not currently resident in RAM

The operating system may retrieve the required data from storage or another backing source and update the mapping before allowing execution to continue.

B. Invalid or prohibited memory access

The operating system may reject the access and report an error to the process. Depending on the situation, the application may crash.


Cybersecurity connection


Unexpected memory faults can appear during debugging or crash investigation. Analysts must examine the address, access type, process context and surrounding evidence before deciding what happened.

A page fault by itself is not proof of malware.


5. Virtual memory and digital forensics

Why should a digital forensic investigator understand this?
- Process isolation: helps explain why one process normally cannot directly read another process's private memory.
- Memory acquisition: a physical memory image and a process's virtual address space are not the same thing.
- Malware investigation: suspicious code or injected memory regions may need to be examined in the context of process memory mappings.
- Crash analysis: invalid accesses and memory faults can help investigators understand a program's behaviour.

For example, suppose an investigator finds suspicious executable memory in a running process. They may examine the process's memory mappings, permissions, loaded modules and execution behaviour to determine whether the region is legitimate or suspicious.

6. Important distinction: RAM vs virtual memory

RAM	Virtual memory

Physical memory hardware	A memory-management abstraction

Limited by installed and supported hardware	Provides processes with virtual address spaces

Holds currently resident data and code	Can map to RAM and, in some circumstances, storage-backed pages

Shared physical resource across the system	Each process has its own virtual address space

Virtual memory is not simply another name for the page file. The page file is one possible backing store used by Windows; virtual memory also includes address-space mappings and memory-resident pages.

7. Quick quiz — test your understanding

1. What does virtual memory provide to a process?

Its own virtual address space

Unlimited physical RAM

A separate CPU chip

Correct! Virtual memory provides a process-specific address space managed by the operating system and hardware.


2. What is a page?

A fixed-size block of virtual memory

A physical CPU core

A file stored only on an SSD

Correct! Virtual memory is divided into fixed-size pages.


3. What does a page table help do?

Translate virtual pages to physical frames

Encrypt every file automatically

Schedule Wi-Fi connections

Correct! Page tables hold mappings and access-control information used for address translation.


4. Does every page fault indicate malware?

Yes

No; page faults can occur during normal operation

Only on 64-bit systems

Correct! Page faults have many ordinary causes and need context to interpret.


5. Why is virtual memory relevant to digital forensics?

It makes all deleted files recoverable

It helps analysts understand process memory, mappings and isolation

It replaces the need to preserve evidence

Correct! Memory mappings and process isolation are important when examining running programs and acquired memory.

Your score: 5/5
