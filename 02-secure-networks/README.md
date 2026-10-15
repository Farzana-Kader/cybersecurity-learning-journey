# Secure Networks

## Module Overview

**Status:** Completed ✅  
**Study Days:** Day 8–Day 15  
**Duration:** 8 study days, approximately 1 hour per day  
**Final Assessment Score:** 10/10 (100%)

## Learning Objectives

The goal of this module was to understand computer networking fundamentals, network communication protocols, and the security technologies used to protect network traffic.

## Topics Covered

### Day 8 — Networking Fundamentals
- Understanding computer networks and network communication.
- Roles of routers, switches, and firewalls.
- Difference between IP and MAC addresses.
- Introduction to TCP, UDP, DNS, and HTTPS.

### Day 9 — IP Addressing and Subnetting
- IPv4 and IPv6 addressing.
- Public and private IP addresses.
- Subnet masks and CIDR notation.
- Subnetting and network segmentation.
- Importance of segmentation in network security.

### Day 10 — DNS, DHCP, ARP, and ICMP
- DNS resolution and common DNS record types.
- DHCP and the DORA process.
- ARP address resolution and ARP spoofing.
- ICMP and network connectivity testing.

### Day 11 — TCP, UDP, and Ports
- Differences between TCP and UDP.
- TCP three-way handshake.
- Common network ports and their services.
- Understanding network connection states.
- Inspecting active connections and listening ports.

### Day 12 — TLS, HTTPS, and Digital Certificates
- How TLS protects data in transit.
- HTTPS communication and digital certificates.
- Certificate authorities and certificate validation.
- Symmetric and asymmetric encryption.
- Understanding the metadata that may remain visible when using HTTPS.

### Day 13 — Firewalls, IDS, and IPS
- Firewall rules and traffic filtering.
- Stateful and stateless firewall concepts.
- Intrusion Detection Systems (IDS).
- Intrusion Prevention Systems (IPS).
- Signature-based and anomaly-based detection.
- Understanding false positives.

### Day 14 — VPNs, Proxies, and Network Privacy
- How VPNs create encrypted tunnels.
- Proxy servers and their uses.
- VPN versus proxy.
- Split tunneling and DNS leaks.
- Introduction to zero-trust security.

### Day 15 — Revision and Assessment
- Reviewed the concepts covered throughout the module.
- Revised common networking commands.
- Completed the final assessment.
- Achieved a score of 10/10.

## Practical Exercises

The following commands were studied or used to understand network configuration, connectivity, and security.

| Command | Purpose |
|---|---|
| `ipconfig` | View local network configuration |
| `nslookup example.com` | Query DNS |
| `arp -a` | View the local ARP cache |
| `ping example.com` | Test connectivity using ICMP where permitted |
| `netstat -ano` | View network connections and associated process IDs |
| `tracert example.com` | Trace network hops |
| `Test-NetConnection example.com -Port 443` | Test TCP connectivity to port 443 |
| `Get-NetFirewallProfile` | Inspect Windows Firewall profiles |

**Practical learning note:** These commands help investigate network configuration and connectivity. Their results depend on system settings, network conditions, and security policies.

## Cybersecurity Relevance

Understanding secure networks is essential for identifying suspicious communication, investigating network incidents, and protecting systems from unauthorised access.

This module established the foundation for understanding:

- Network reconnaissance and traffic analysis.
- Common network-based attacks.
- Secure communication using TLS.
- Firewall configuration and intrusion detection.
- Network privacy and access control.
- Basic network troubleshooting during security investigations.

## Assessment Results

| Assessment | Score |
|---|---:|
| Day 8 — Networking Fundamentals | 5/5 |
| Day 9 — IP Addressing and Subnetting | 5/5 |
| Day 10 — DNS, DHCP, and ARP | 5/5 |
| Day 11 — TCP, UDP, and Ports | 5/5 |
| Day 12 — TLS, HTTPS, and Certificates | 5/5 |
| Day 13 — Firewalls, IDS, and IPS | 5/5 |
| Day 14 — VPNs, Proxies, and Privacy | 5/5 |
| Day 15 — Final Revision Assessment | 10/10 |

**Final assessment result: 100%**

## Key Takeaways

- Network protocols define how devices communicate.
- IP addressing and subnetting help organise and segment networks.
- DNS, DHCP, ARP, and ICMP perform different network functions.
- TCP and UDP serve different communication requirements.
- TLS and HTTPS help protect data in transit.
- Firewalls, IDS, and IPS provide complementary security controls.
- VPNs and proxies have different privacy and traffic-routing capabilities.
- No single security technology guarantees complete protection.

## Reflection

Completing this module improved my understanding of networking fundamentals and the security mechanisms used to protect communication between devices. I learned how to recognise common protocols and ports, inspect basic network configuration, understand encrypted communication, and distinguish between firewall, IDS, and IPS functions.

The practical exercises helped connect theoretical concepts with real-world Windows networking commands. This knowledge provides a foundation for further study in Windows security, network monitoring, and digital forensics.

