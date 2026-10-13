Day 8 — Networking Fundamentals

1. What is a computer network?

A computer network is a group of connected devices that communicate and share information.

Examples include:
- Your phone connected to Wi-Fi.
- Computers connected in a college laboratory.
- A bank's computers communicating with its servers.
- Your browser connecting to a website.

Important network devices

Router

Connects different networks and forwards packets between them. Your home router typically connects your local network to the internet.

Switch

Connects devices within a local network and forwards Ethernet frames to the appropriate device.

Firewall

Applies security rules to allow or block network traffic.

2. IP address vs MAC address

These are two different types of network addresses.

IP address

An address used to identify a device's network interface logically so traffic can be routed between networks.

Example: 192.168.1.10

MAC address

A link-layer address used for communication on a local network.

Example: 00:1A:2B:3C:4D:5E

Remember: An IP address can change when a device joins another network. A MAC address is generally associated with a network interface, but it can be changed or randomized by software.

Cybersecurity connection: IP addresses can help investigators examine network traffic, while MAC addresses can sometimes help identify devices on a local network. Neither address alone proves who was using a device.

3. TCP vs UDP

TCP and UDP are transport-layer protocols that carry data between applications.

Feature	TCP	UDP

Connection	Connection-oriented	Connectionless

Delivery	Provides reliable, ordered delivery	No built-in guarantee of delivery or order

Overhead	Generally higher	Generally lower

Common uses	HTTPS, SSH, email	DNS queries, voice/video traffic, online gaming

TCP uses mechanisms such as acknowledgements and retransmissions to provide reliable delivery. UDP does not provide those guarantees at the transport layer.

Cybersecurity example: Investigators may examine TCP connections to understand communication with a suspicious server. UDP traffic can also reveal DNS queries or other activity associated with malware.

4. What are ports?

A port number helps a computer deliver network traffic to the correct application or service.

Think of an IP address as a building's address and a port as the particular entrance or service inside it.

Common port numbers:

Port	Common service

22	SSH — secure remote login

53	DNS — domain name lookup

80	HTTP — web traffic without TLS

443	HTTPS — web traffic protected by TLS

3389	RDP — Windows Remote Desktop

Ports don't automatically make a service secure. For example, an exposed remote-login service can be risky if it is poorly configured or uses weak credentials.

5. What happens when you open a website?

Imagine you enter https://example.com into your browser.

1. DNS lookup

Find the IP address associated with the domain.

2. Network connection

Your device connects to the server, commonly using TCP or QUIC.

3. TLS security

HTTPS establishes or resumes a secure session and authenticates the server.

4. HTTP request

The browser requests the webpage.

5. Response

The server returns data for the browser to display.

Note: Modern HTTPS can use HTTP/3 over QUIC, which uses UDP, rather than TCP. The exact connection process depends on the browser and server.

Why does this matter in cybersecurity?

A security analyst might investigate:
- DNS requests to suspicious domains.
- Connections to unexpected IP addresses.
- Traffic to exposed or unusual ports.
- Unencrypted HTTP traffic.
- Connections between a compromised computer and a command-and-control server.

Practical task — Explore your own computer

On your Windows computer, open Command Prompt (cmd) and run these commands one at a time.

1. View your IP configuration

ipconfig

Look for IPv4 Address and Default Gateway under your active adapter.


2. View your MAC address

getmac

3. View active network connections

netstat -ano

This shows connections, local and remote endpoints, connection states, and process IDs. Some entries may be listening services rather than active remote connections.

Keep your output private if it contains network details you don't want to share. You do not need to scan any external systems.

Day 8 quiz

1. Which device forwards packets between different networks?

Switch

Router

Keyboard

RAM

Correct! Router


2. Which address is used for logical network addressing and routing?

MAC address

File path

IP address

Process ID

Correct! IP Address


3. Which protocol provides reliable, ordered delivery?

UDP

TCP

ARP

ICMP

Correct! TCP


4. Which port is commonly used for HTTPS?

22

53

80

443

Correct! 443


5. What is the main purpose of DNS?

Encrypt every file

Translate domain names to resource records such as IP addresses

Block all malware

Assign MAC addresses

Correct! Translate domain names to resource records such as IP addresses

Score: 5/5
