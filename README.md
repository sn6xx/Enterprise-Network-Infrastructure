# Enterprise Network Infrastructure

## Overview

This project demonstrates the design and implementation of a secure enterprise network using Cisco Packet Tracer.

The network was designed to simulate a real enterprise environment with multiple LANs, routing protocols, network services, remote management, and security features.

---

## Project Topology

![Network Topology](screenshots/topology.png)
--- 

## Features

- Multi-router enterprise network topology
- VLAN segmentation (VLAN 10 & VLAN 20)
- Inter-VLAN Routing
- Static Routing
- RIP Routing
- Default Route
- DHCP Server
- DNS Server
- HTTP Server
- Network Address Translation (NAT)
- SSH Remote Management
- Telnet Remote Access
- Switch Port Security
- End-to-End Connectivity Testing
---

## VLAN Configuration

The enterprise network was segmented using Virtual LANs (VLANs) to improve security and reduce broadcast traffic.

| VLAN | Purpose | Connected Devices |
|------|---------|-------------------|
| VLAN 10 | User Network | PC3, PC4 |
| VLAN 20 | Server Network | HTTP Server, DNS Server, DHCP Server, PC1, PC2 |

A trunk link was configured between SW1 and SW2 to allow VLAN traffic between switches.
---

## VLAN & Inter-VLAN Routing

The enterprise network was segmented using VLANs to improve network organization and security.

| VLAN | Purpose |
|------|---------|
| VLAN 10 | User Network |
| VLAN 20 | Server Network |

Inter-VLAN Routing was implemented using the Router-on-a-Stick technique.

Two IEEE 802.1Q trunk links were configured:

- SW1 ↔ SW2
- SW2 ↔ R1

Router R1 was configured with subinterfaces for VLAN 10 and VLAN 20 to enable communication between VLANs.
---

## DHCP Configuration

A dedicated DHCP server was configured to automatically assign IP addresses to devices in the Server Network.

### DHCP Settings

| Setting | Value |
|---------|-------|
| Pool Name | serverPool |
| Network | 192.168.20.0/24 |
| Default Gateway | 192.168.20.1 |
| DNS Server | 192.168.20.3 |
| Start IP Address | 192.168.20.5 |
| Maximum Users | 251 |

The DHCP service automatically assigns network configuration to client devices, reducing manual configuration and improving network management.

