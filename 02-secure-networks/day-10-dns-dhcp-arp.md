Day 10 — DNS, DHCP, ARP and Network Discovery

1. DNS — Domain Name System

DNS translates domain names into information used to locate internet services, commonly including IP addresses.

Imagine typing example.com into your browser. Your computer needs to discover the appropriate IP address before it can contact the server.

Your computer

Requests a DNS lookup


DNS resolver

Finds the relevant DNS record

IP address returned

Your device can contact the destination


Common DNS record types:

Record	Purpose

A	Maps a name to an IPv4 address

AAAA	Maps a name to an IPv6 address

MX	Identifies mail servers for a domain

CNAME	Creates an alias for another domain name

TXT	Stores text data, often used for domain verification and email security

Cybersecurity connection: Attackers may use malicious domains for phishing or command-and-control communication. Analysts investigate DNS logs to identify unusual queries, suspicious domains, or patterns that could indicate malware.

2. DHCP — Dynamic Host Configuration Protocol

DHCP automatically provides network configuration to devices joining a network.

Without DHCP, you might have to configure your IP address, subnet mask, gateway, and DNS server manually.

A common DHCP process is called DORA:

D — Discover

The device looks for a DHCP server.

O — Offer

A server offers an IP configuration.

R — Request

The device requests the offered configuration.

A — Acknowledge

The server confirms the lease.


DHCP usually assigns a leased address, meaning the assignment is valid for a period of time and can be renewed.

Cybersecurity connection: A rogue DHCP server could give devices a malicious gateway or DNS server. This could redirect traffic or interfere with communications.

3. ARP — Address Resolution Protocol

ARP helps an IPv4 device discover the MAC address associated with a local IPv4 address on the same local network.

For example, your laptop wants to send data to a device at 192.168.1.20. It knows the destination IP address but needs the corresponding local-link MAC address to send an Ethernet frame.

Laptop

“Who has 192.168.1.20?”

Local network

The device with that IPv4 address replies with its MAC address.

Ethernet frame sent

The laptop can send the frame to the destination MAC.


If the destination is outside the local subnet, your computer normally resolves the MAC address of its default gateway, rather than the remote server's MAC address.

What is ARP spoofing?

ARP spoofing occurs when an attacker sends deceptive ARP messages to associate their MAC address with another device's IP address, potentially redirecting local network traffic.

Possible consequences include:
- Man-in-the-middle attacks.
- Traffic interception.
- Communication disruption.

Defenses include network segmentation, encrypted protocols, and protections such as Dynamic ARP Inspection where supported.

4. ICMP and ping

ICMP is used for network-layer messages, including error reporting and diagnostics.

The ping command commonly uses ICMP Echo Request and Echo Reply messages to test whether a destination responds.

For example:

ping 192.168.1.1


A response suggests the destination is reachable and responding to those requests. However, no response does not necessarily mean the device is offline; a firewall may block ICMP.

Cybersecurity professionals use network diagnostics to investigate connectivity problems and gather clues about network behaviour. They must interpret the results carefully.

5. Practical lab — Investigate your own Windows network

Run these commands in Command Prompt, one at a time.

1. Look up a domain

nslookup example.com

Shows DNS lookup results, including the responding DNS server and returned records.


2. Inspect the ARP cache

arp -a

Displays cached IPv4-to-MAC mappings for local network interfaces.


3. Test connectivity

ping example.com

Tests whether the destination responds to ICMP Echo Requests.


4. Inspect DNS cache

ipconfig /displaydns

Displays cached DNS resolver records available on your computer.



These are basic diagnostic commands for your own computer. You don't need to scan other devices or networks.

Day 10 quiz

1. What is the primary purpose of DNS?

Assign MAC addresses

Translate domain names into DNS records such as IP addresses

Encrypt all network traffic

Assign IP addresses automatically

Correct! Translate domain names into DNS records such as IP addresses


2. What does DHCP provide to a device?

Automatic network configuration

Malware removal

File encryption

A permanent MAC address

Correct! Automatic network configuration


3. What does ARP help resolve on a local IPv4 network?

Domain name to website content

Process ID to application name

IPv4 address to MAC address

Password to username

Correct! IPv4 address to MAC address


4. What is ARP spoofing?

Changing a DNS record legitimately

Sending deceptive ARP messages to mislead local devices

Blocking every ICMP packet

Assigning an IPv6 address

Correct! Sending deceptive ARP messages to mislead local devices


5. If ping receives no reply, what can you conclude?

The device is definitely powered off

The IP address does not exist

The device may be offline or ICMP may be blocked

DNS is always broken

Correct! The device may be offline or ICMP may be blocked

Score: 5/5
