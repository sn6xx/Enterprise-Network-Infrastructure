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