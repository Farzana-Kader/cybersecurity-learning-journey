Day 11 — TCP, UDP, Ports and Network Traffic

1. Understand the TCP three-way handshake

TCP establishes a connection using a process called the three-way handshake.

Client

Server


1. SYN

Client requests a connection.


2. SYN-ACK

Server acknowledges and responds.


3. ACK

Client acknowledges the response.



TCP connection established


Why is this important?
- It helps explain how TCP connections begin.
- Analysts can examine connection attempts in packet captures.
- Unusual patterns of connection attempts may indicate scanning or other suspicious activity.

Security example: A SYN flood attack sends many TCP connection requests in an attempt to exhaust server resources.

2. TCP vs UDP — a deeper comparison

Feature	TCP	UDP

Connection setup	Handshake	No transport-level handshake

Reliability	Reliable, ordered byte stream	No built-in delivery or ordering guarantee

Retransmission	Supported	Not built into UDP itself

Common examples	SSH, HTTPS over TCP, email protocols	DNS queries commonly, voice/video, QUIC transport

Main concern	Connection abuse, SYN floods	Spoofed traffic, amplification abuse, application-specific risks

Remember that UDP is not inherently insecure, and TCP is not inherently secure. Encryption and authentication depend on protocols and configurations above the transport layer, such as TLS or SSH.

3. Ports and network services

A port number helps identify the destination application or service on a host.

22
SSH

Remote administration. Weak passwords or exposed services can create security risks.



53
DNS

Domain name resolution. Investigators may look for unusual DNS traffic.



80
HTTP

Web traffic without TLS protection at the HTTP layer.



443
HTTPS

HTTP protected using TLS.



3389
RDP

Commonly used for Windows Remote Desktop. Exposing it without appropriate protections can increase risk.



A port being open does not automatically mean a system is compromised. It means a service may be listening or accepting traffic, depending on the observation and network conditions.

4. Understand network connection states

When you run netstat, you may see these TCP states:

State	Meaning

LISTENING	A service is waiting for incoming connections.

ESTABLISHED	A TCP connection is active.

TIME_WAIT	A recently closed connection is being kept briefly for TCP cleanup.

CLOSE_WAIT	The remote side closed its connection; the local application has not fully closed it yet.

SYN_SENT	A connection request was sent, and the client is waiting for a response.

These states are not proof of malicious activity. Analysts interpret them alongside process details, destination addresses, timestamps, and other evidence.

5. Practical investigation on Windows

Open Command Prompt and try these commands on your own device.

A. List connections and process IDs

netstat -ano

Look for local addresses, remote addresses, states and PIDs.


B. Find which process owns a PID

tasklist /FI "PID eq 1234"

Replace 1234 with a PID you observed. The result may require elevated permissions for some details.


C. View listening and established TCP connections in PowerShell

Get-NetTCPConnection

You can inspect fields such as State, LocalPort, RemoteAddress and OwningProcess.


Investigation exercise: Choose one connection you recognise, find its PID, and identify the owning process. Don't assume an unfamiliar connection is malicious just because you don't recognise it.

Day 11 quiz

1. What is the correct TCP three-way handshake order?

ACK → SYN → FIN

SYN → SYN-ACK → ACK

SYN-ACK → FIN → ACK

SYN → ACK → RST

Correct! SYN → SYN-ACK → ACK



2. Which port is commonly used for SSH?

21

22

80

443

Correct! 22


3. What does ESTABLISHED usually mean in netstat for TCP?

The service is waiting for connections

The connection is active

The computer is offline

The process has been deleted

Correct! The connection is active


4. What does the -o option in netstat -ano show?

Only open files

Owning process IDs

Only UDP traffic

Encrypted passwords

Correct! Owning process IDs


5. Which is the best way to assess a suspicious connection?

Assume every unfamiliar port is malicious

Immediately delete the process

Correlate the PID, process, destination, timing and other evidence

Ignore all outbound traffic

Correct! Correlate the PID, process, destination, timing and other evidence


Score: 5/5
