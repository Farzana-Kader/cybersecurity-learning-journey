Day 15 — Secure Networks: Revision & Assessment

1. Quick revision — Days 8–14

Day 8 — Networking fundamentals

Networks connect devices. Switches connect devices within local networks; routers forward traffic between networks; firewalls enforce traffic rules.

Remember: IP identifies a network interface logically; MAC addresses operate at the data-link layer.




Day 9 — IP addressing and subnetting

IPv4 uses 32 bits; IPv6 uses 128 bits. Private IPv4 ranges include 10.0.0.0/8, 172.16.0.0/12 and 192.168.0.0/16. CIDR notation represents network-prefix length.




Day 10 — DNS, DHCP, ARP and ICMP

DNS resolves names to IP addresses. DHCP assigns network configuration. ARP resolves IPv4 addresses to local-link MAC addresses. ICMP supports diagnostic messages, including those used by ping.




Day 11 — TCP, UDP and ports

TCP provides reliable, ordered delivery. UDP has lower protocol overhead and does not guarantee delivery or ordering. Ports identify application endpoints.

Common ports: HTTP 80, HTTPS 443, DNS 53, SSH 22.




Day 12 — TLS, HTTPS and certificates

TLS protects data in transit. Certificates help authenticate server identity. Browsers validate certificate trust, validity and hostname.




Day 13 — Firewalls, IDS and IPS

Firewalls enforce traffic rules. IDS detects suspicious activity and alerts. IPS can actively block suspicious traffic.




Day 14 — VPNs, proxies and privacy

VPNs create encrypted tunnels to VPN servers. Proxies forward requests. Split tunneling routes selected traffic differently; zero trust requires verification instead of implicit trust.



2. Practical recall challenge



Command	Purpose

ipconfig	Displays local network configuration

nslookup example.com	Queries DNS

arp -a	Displays the local ARP cache

ping example.com	Tests reachability using ICMP where permitted

netstat -ano	Shows connections, listening ports and associated PIDs

tracert example.com	Attempts to identify network hops

Test-NetConnection example.com -Port 443	Tests TCP connectivity to port 443

Get-NetFirewallProfile	Displays Windows Firewall profile configuration


3. Final assessment — 10 questions

Secure Networks test


1. Which device forwards packets between different networks?

A. Switch

B. Router

C. Keyboard

D. Repeater only

Correct! Routers forward traffic between networks.


2. Which is a private IPv4 address?

A. 8.8.8.8

B. 1.1.1.1

C. 192.168.1.20

D. 203.0.113.10

Correct! 192.168.0.0/16 is a private IPv4 range.


3. Which protocol commonly resolves a domain name to an IP address?

A. DHCP

B. DNS

C. ARP

D. SSH

Correct! DNS resolves domain names to records such as IP addresses.


4. Which statement about TCP is correct?

A. It guarantees all networks are secure

B. It provides reliable, ordered byte-stream delivery

C. It is used only for video calls

D. It never retransmits data

Correct! TCP provides reliable, ordered delivery of a byte stream.


5. Which port is the standard default for HTTPS?

A. 21

B. 25

C. 80

D. 443

Correct! HTTPS commonly uses TCP port 443.


6. What does a TLS certificate help a browser verify?

A. That the website has no malware

B. The server's identity, subject to certificate validation

C. That the Wi-Fi is private

D. That every page is trustworthy

Correct! Certificate validation helps authenticate the server; it does not prove a site is harmless.


7. Which system detects suspicious activity and raises alerts?

A. IDS

B. DHCP

C. DNS

D. Proxy only

Correct! IDS detects and alerts; an IPS may block traffic.


8. What is the main purpose of a firewall?

A. To assign every device an IP

B. To enforce network traffic rules

C. To replace antivirus software

D. To guarantee anonymity

Correct! A firewall allows or blocks traffic according to rules.


9. What does a VPN primarily provide between your device and the VPN server?

A. Guaranteed anonymity

B. An encrypted tunnel

C. Protection from every phishing email

D. A guarantee that the provider cannot see metadata

Correct! A VPN encrypts traffic across its tunnel but does not guarantee complete anonymity.


10. What does the principle of zero trust mean?

A. Trust every device inside the office

B. Disable all user accounts

C. Verify access and grant only the permissions needed

D. Allow access once a VPN connects

Correct! Zero trust avoids implicit trust and applies verification and least privilege.

Final score: 10/10
