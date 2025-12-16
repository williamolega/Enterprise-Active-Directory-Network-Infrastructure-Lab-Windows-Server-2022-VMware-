# VMware Networking Configuration

## Purpose

This document defines the virtual networking layer used by the Enterprise Active Directory Network Lab.

The goal of this layer is to:
- Provide a **fully isolated internal enterprise network**
- Establish a **controlled egress path** to the internet
- Enforce clear trust boundaries before any identity or client systems are deployed

All higher-level systems depend on this networking foundation.

---

## Design Principles

The VMware networking configuration follows these principles:

- Internal identity systems must **never** be directly exposed to the host or internet
- Network boundaries must be explicit and enforceable
- Routing and NAT are handled by a dedicated edge system, not by identity infrastructure
- Virtual networking should mirror real enterprise segmentation patterns

---

## Virtual Network Overview

Two VMware virtual networks are used:

| Network | Purpose | Trust Level |
|------|--------|------------|
| VMnet2 | Internal enterprise network | Trusted |
| VMnet8 | Internet egress via NAT | Untrusted |

---

## VMnet2 – Internal Enterprise Network

**Type:** Host-only  
**Subnet:** `192.168.81.0/24`  
**DHCP:** Disabled  

### Purpose
VMnet2 represents the internal enterprise network where the following reside:
- Domain controllers
- Domain-joined clients
- Internal services


### Design Decisions
- DHCP is disabled to ensure **centralized address management** via Active Directory
- The host system has no direct route into this network
- All internal traffic must pass through the firewall for egress

### Systems Attached
- Edge-FW01 (pfSense) Internal (LAN) interface
- DC01 (Domain Controller)
- Client1 (Domain-joined workstation)

---

## VMnet8 – External Network (NAT)

**Type:** NAT  
**IP Address:** DHCP (from host computer)  

### Purpose
VMnet8 provides controlled egress while preventing inbound exposure.

### Design Decisions
- Only the firewall’s WAN interface is attached
- No internal systems are connected directly
- Internet access is mediated by pfSense NAT and firewall rules

---

## Traffic Flow Summary

```text
Client1 / DC01
     │
     ▼
VMnet2 (Internal)
     │
     ▼
Edge-FW01
     │
     ▼
VMnet8 (NAT)
     │
     ▼
Internet
