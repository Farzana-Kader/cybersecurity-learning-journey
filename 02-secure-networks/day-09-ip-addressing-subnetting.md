Day 9 — IP Addressing & Subnetting

1. What is an IP address?

An IP address identifies a network interface so devices can communicate across networks.

There are two main versions:

IPv4

Uses 32 bits and is usually written as four decimal numbers separated by dots.

192.168.1.10

Each number ranges from 0 to 255.

IPv6

Uses 128 bits and is written in hexadecimal groups separated by colons.

2001:db8::1

Provides a much larger address space than IPv4.

2. Public IP vs private IP

Private IPv4 range	Typical use

10.0.0.0 – 10.255.255.255	Large private networks

172.16.0.0 – 172.31.255.255	Private organizational networks

192.168.0.0 – 192.168.255.255	Common home and small-office networks

Private IP addresses are used inside private networks and aren't directly routed across the public internet. Routers commonly use Network Address Translation (NAT) to let multiple private devices share a public IPv4 address.

Public IP addresses are globally routable, subject to routing and filtering policies.

Cybersecurity connection: An investigator needs to understand whether an observed address is private or public before interpreting network logs. An IP address alone doesn't prove who was responsible for an activity.

3. What is a subnet mask?

A subnet mask tells a device which bits of an IPv4 address identify the network and which identify the host.

For example:

IP address

192.168.1.10/24

Network portion

192.168.1

Host portion

10

/24 means the first 24 bits identify the network.

Equivalent subnet mask: 255.255.255.0

In a conventional /24 IPv4 subnet, there are 256 total addresses, typically 254 usable host addresses because the network and broadcast addresses are reserved.

4. What is subnetting?

Subnetting divides a larger IP network into smaller networks.

Imagine a college with separate networks for students, staff and administration. Subnetting helps organize traffic and manage address allocation.

192.168.1.0/24

Original network

Students

192.168.1.0/26

Staff

192.168.1.64/26

Admin

192.168.1.128/26

Servers

192.168.1.192/26

Illustrative network segmentation into four equal subnets.

Each /26 subnet contains 64 total addresses, typically 62 usable host addresses. Notice how the network ranges don't overlap.

Important: Subnetting alone doesn't guarantee security. Firewalls, access-control rules and proper network configuration are needed to restrict traffic between subnets.

5. Why subnetting matters in cybersecurity
- Network segmentation: Separates sensitive systems from ordinary user devices.
- Incident response: Helps analysts understand which network a suspicious IP belongs to.
- Firewall configuration: Supports rules based on network ranges.
- Attack investigation: Helps correlate logs from different network segments.

Practical task — Find your own IP configuration

On Windows, open Command Prompt and run:

ipconfig

Find your active adapter's IPv4 address, subnet mask and default gateway. For example, your computer might show an address such as 192.168.1.10, but your actual values may differ.

You can also use:

ipconfig /all


This displays more detailed adapter information. You don't need to share your actual network details here.

Day 9 quiz

1. How many bits does IPv4 use?

16 bits

32 bits

64 bits

128 bits

Correct! 32 bits


2. Which of these is a private IPv4 address?

8.8.8.8

1.1.1.1

192.168.1.20

203.0.113.10

Correct! 192.168.1.20


3. What does /24 represent in an IPv4 CIDR address?

24 host bits

24 network-prefix bits

24 total addresses

24 routers

Correct! 24 network-prefix bits


4. How many total IPv4 addresses are in a /26 subnet?

32

64

128

256

Correct! 64


5. What is one security benefit of network segmentation?

It removes the need for passwords

It guarantees no malware can spread

It can restrict communication between groups of systems

It encrypts every packet automatically

Correct! It can restrict communication between groups of systems

Score: 5/5
