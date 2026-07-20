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

![DHCP Server](screenshots/dhcp-server.png)

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

---

## DNS Configuration

A dedicated DNS server was configured to provide hostname resolution for internal services within the enterprise network.

### DNS Record

| Hostname | Record Type | IP Address |
|----------|-------------|------------|
| www.cisco | A Record | 192.168.20.4 |

The DNS server allows clients to access the web server using its hostname instead of the IP address.

### DNS Server

![DNS Server](screenshots/dns-server.png)

---

## HTTP Service

An internal web server was deployed and successfully accessed through DNS hostname resolution.

### Validation

The website was accessed using:

```
http://www.cisco
```

This confirms the successful integration of:

- DNS name resolution
- HTTP service
- End-to-end network connectivity

### HTTP Test

![HTTP Test](screenshots/http-test.png)

---

## SSH Remote Management

Secure Shell (SSH) was configured on **Router R1** to provide secure remote administration.

### Configuration

- Local user authentication
- RSA (2048-bit) encryption keys
- SSH enabled on VTY lines
- Domain name configured: `NETWORK.LOCAL`

### Verification

SSH connectivity was successfully verified by establishing a remote session from **R2** to **R1** using:

```text
ssh -l saja 10.10.1.1
```

Successful authentication confirmed secure remote management between network devices.

### SSH Test

![SSH Login](screenshots/ssh-login.png)

---

## Network Address Translation (NAT)

Static Network Address Translation (Static NAT) was implemented to provide address translation between internal and external networks.

### NAT Translation

| Inside Local | Inside Global |
|--------------|---------------|
| 192.168.4.2 | 192.168.3.10 |

### Verification

The translation table confirmed successful NAT operation during network communication.

### NAT Verification

![NAT Verification](screenshots/nat-verification.png)

---

## Routing Configuration

The enterprise network uses multiple routing techniques to enable communication between different network segments.

### Routing Methods

- Static Routing
- RIP (Routing Information Protocol)
- Default Route

### Static Routes Configured on R1

| Destination Network | Next Hop |
|---------------------|----------|
| 10.10.2.0/24 | 10.10.1.2 |
| 10.10.3.0/24 | 10.10.1.2 |
| 192.168.5.0/24 | 10.10.1.2 |

### Verification

The routing table confirmed successful installation of connected and static routes.

### Routing Table

![R1 Routing Table](screenshots/r1-routing-table.png)

