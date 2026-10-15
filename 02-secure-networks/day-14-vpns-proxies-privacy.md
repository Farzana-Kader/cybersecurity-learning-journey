Day 14 — VPNs, Proxies & Network Privacy, the final lesson in our Secure Networks module.

1. What is a VPN?

A VPN (Virtual Private Network) creates an encrypted tunnel between your device and a VPN server over a network such as the internet.

Imagine sending a confidential letter through a locked delivery service. Someone observing the journey may see that a package is travelling, but encryption helps prevent them from reading its contents.

Your device


Encrypted VPN tunnel

Traffic protected in transit

VPN server → Destination website


What does a VPN protect?
- Encrypts traffic between your device and the VPN server, helping protect it from local network observers.
- Websites generally see the VPN server's public IP address instead of your original public IP address.
- Can help protect traffic on untrusted Wi-Fi networks.

What does a VPN NOT guarantee?
- Complete anonymity or immunity from malware.
- Protection against phishing or unsafe downloads.
- That the VPN provider cannot see any information about your activity.
- End-to-end encryption for every connection beyond the VPN tunnel.

Cybersecurity insight: A VPN changes whom you trust. You may reduce what your local network can observe, but you must also consider the VPN provider's privacy and logging practices.

2. What is a proxy server?

A proxy server acts as an intermediary between your device and a destination server. Instead of connecting directly, your request goes through the proxy.

Your device

Proxy server

Forwards requests and responses

Destination website


Proxies are commonly used for:

- Filtering websites in schools and workplaces.
- Caching content to reduce repeated downloads.
- Routing requests through another server.
- Hiding the client's IP address from the destination in many proxy configurations.

However, a proxy does not automatically encrypt all your traffic. Its protection depends on the proxy type and the connection being used.

3. VPN vs Proxy

Feature	VPN	Proxy

Main purpose	Protects network traffic through an encrypted tunnel	Forwards traffic through an intermediary

Traffic coverage	Often device-wide or configured applications	Often a particular application or protocol

Encryption	Encrypts the VPN tunnel	Not guaranteed

IP visibility	Destination usually sees VPN server IP	Destination usually sees proxy IP

Common use	Safer network access and remote work	Filtering, caching and routing

Remember: an HTTPS connection can remain encrypted between your browser and the website even when you use a proxy. The proxy itself does not necessarily decrypt HTTPS traffic.

4. Other important privacy concepts

Public IP vs private IP

- Private IP: Used within a local network, such as 192.168.1.10.

- Public IP: Used to identify a network's internet-facing address.

A VPN usually changes the public IP address that destination websites observe, but it does not necessarily change the private IP assigned to your device.

Split tunneling

Split tunneling allows some traffic to travel through a VPN while other traffic uses your normal internet connection.

For example, a work application might use the company VPN while personal browsing goes directly to the internet. This can improve efficiency, but traffic outside the VPN does not receive its tunnel protection.

DNS leaks

DNS translates domain names, such as example.com, into IP addresses. A DNS leak can occur when DNS requests travel outside the intended VPN tunnel or use an unexpected resolver.

A VPN's protection depends on its configuration, operating system, DNS settings and possible leaks.

Zero trust

Zero trust is a security approach based on the principle “never trust automatically; always verify.” Being connected to a company VPN does not mean every user or device should automatically gain access to every internal resource. Identity, device health and permissions still matter.


5. Practical exercises — Windows

Use your own computer and trusted services. These checks do not require changing your network settings.

Task A — Check your IP configuration

Open Command Prompt and run:

ipconfig


Identify your active network adapter and note its IPv4 address, default gateway and DNS server if shown.


Task B — Check proxy settings

In PowerShell, run:

netsh winhttp show proxy


This shows the proxy configuration for Windows HTTP services. It does not necessarily show every browser's proxy settings.

Task C — Inspect your route

tracert example.com


This attempts to show the network hops between your computer and the destination. Some routers may not respond, so timeouts do not automatically mean your connection is broken.

For your notes, record what each command reveals. Don't share public IP addresses or other network details publicly if you prefer to keep them private.

6. Quiz — Day 14



1. What is the primary purpose of a VPN tunnel?

A. To guarantee complete anonymity

B. To encrypt traffic between your device and the VPN server

C. To remove all malware

D. To eliminate the need for HTTPS

Correct! A VPN protects traffic across its tunnel, but it does not guarantee anonymity or replace HTTPS.


2. What does a proxy server do?

A. Always encrypts every packet on your device

B. Acts as an intermediary for requests and responses

C. Replaces your computer's operating system

D. Prevents every phishing attack

Correct! A proxy forwards traffic between a client and a destination.


3. What is split tunneling?

A. Dividing a hard drive into partitions

B. Sending all traffic through two firewalls

C. Routing some traffic through a VPN and other traffic outside it

D. Splitting a password into two parts

Correct! Split tunneling routes selected traffic through the VPN while other traffic uses another route.


4. What is a DNS leak in the VPN context?

A. A website loading slowly

B. DNS requests escaping the intended VPN protection

C. A router running out of power

D. A certificate expiring

Correct! DNS requests may go outside the intended tunnel or use an unexpected resolver.


5. Which statement best describes zero trust?

A. Trust every device on the company VPN

B. Allow every user once they sign in

C. Verify identity and access continuously according to policy

D. Block all internet connections

Correct! Zero trust requires verification and least-privilege access rather than implicit trust.

Score: 5/5
