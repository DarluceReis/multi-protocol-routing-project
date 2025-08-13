
# 🌐 Advanced Network Protocols
This repository contains the configuration and a detailed explanation of a complex network topology I designed and implemented in Cisco Packet Tracer. The project demonstrates advanced skills in dynamic routing, protocol redistribution, and network security.

---

## Project Overview
The network is comprised of four main sites, each using a different routing protocol, connected via a central router. The goal was to establish a fully functional and secure network where all terminals could communicate with each other, regardless of the routing protocol used in their zone.

---

## Network Zones
Green Zone (EIGRP): Includes ESPANHA, PORTUGAL, and ITALIA.
Yellow Zone (RIPv2): Includes INDONESIA and JAPÃO.
Pink Zone (OSPF): Includes MEXICO and COLOMBIA.
Central Router: EUA, which connects all zones.

--- 

1. Network Configuration & Services
Subnets
Subnets were configured to meet specific host requirements for each site:

| Subnet       | Supported Hosts |
|--------------|----------------|
| **ESPANHA**   | 126            |
| **COLOMBIA**  | 30             |
| **INDONESIA** | 14             |
| **PORTUGAL**  | 6              |
| **WAN Links** | 2              |

Services
DHCP Service: DHCP was configured on the routers for ESPANHA, PORTUGAL, COLOMBIA, and INDONESIA to dynamically assign IP addresses to hosts.
DNS Service: A DNS server located in PORTUGAL was configured with the domain name www.cesae.wan to provide name resolution for the entire network.

--- 

2. Routing Protocols & Redistribution
The project utilizes a multi-protocol routing environment to demonstrate interoperability and routing management.

Routing Zones
EIGRP (Green Zone):
Configured with Autonomous System 1.
Used for the ESPANHA, PORTUGAL, and ITALIA routers.

OSPF (Pink Zone):
Configured as a single area.
Used for the MEXICO and COLOMBIA routers.
The Router ID for each router is its respective loopback address.

RIPv2 (Yellow Zone):
Used for the INDONESIA and JAPÃO routers.

Redistribution
Full Redistribution: All routing protocols (RIP, EIGRP, and OSPF) were redistributed into each other to ensure all terminals could communicate, creating a fully connected network.
Passive Interfaces: Routing information was configured not to be sent to the LANs to optimize network traffic and security.

Virtual Interfaces
Loopback Interfaces were configured on the following routers to serve as their Router IDs and for testing purposes:
MEXICO: 4.4.4.4
COLOMBIA: 5.5.5.5
EUA: 6.6.6.6

--- 

3. Security & Hardening
Robust security measures were implemented to protect the network's integrity.
Router Passwords: The router in EUA has its passwords configured to be encrypted.
SSH Access: The router in ESPANHA has SSH access enabled for the user "admin" with the password "cisco".

Authentication:
EIGRP: Configured with a key chain. The key name is "AWS", the key number is 10, and the password "cisco" with MD5 type encryption.
OSPF: Configured with password authentication using "cisco" and MD5 encryption.
