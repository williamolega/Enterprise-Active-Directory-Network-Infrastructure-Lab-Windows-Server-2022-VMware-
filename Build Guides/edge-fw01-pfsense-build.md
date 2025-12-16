# Edge Firewall Configuration (Edge-FW01 – pfSense)

## Purpose

This document defines the configuration of **Edge-FW01**, the firewall for the Enterprise Active Directory Network Lab.

Edge-FW01 is responsible for:
- Enforcing a single network boundary
- Controlling egress traffic
- Providing routing and NAT
- Preventing direct internet exposure of identity systems

Identity infrastructure must never perform perimeter security functions.

---

## Role & Responsibility

Edge-FW01 is the only system in the lab that:
- Has connectivity to both trusted and untrusted networks
- Performs NAT
- Acts as the default gateway for internal systems

It does **not**:
- Host identity services
- Provide DNS or DHCP
- Authenticate users

This strict separation mirrors enterprise design principles.

---

## Network Interfaces

### WAN Interface (Untrusted)
- Connected to **VMnet8 (NAT)**
- IP assignment: **DHCP (from host router)**

Purpose:
- Provide controlled egress
- Prevent inbound connections to internal systems

---

### LAN Interface (Trusted)
- Connected to **VMnet2 (Host-only)**
- IP address: `192.168.81.1/24`

Purpose:
- Serve as the default gateway for internal systems
- Enforce firewall policy between internal and external networks

---

## Routing & NAT

### Default Gateway
- Internal systems use `192.168.81.1` as their default gateway
- All outbound traffic must go through Edge-FW01

### NAT Configuration
- Outbound NAT is enabled
- Internal private addresses are translated before egress
- No inbound NAT or port forwarding is configured

This ensures identity services are never directly reachable from the internet.

---

## Firewall Policy

### LAN Rules
- Allow internal systems to initiate outbound connections
- Block unsolicited inbound traffic by default

### WAN Rules
- Default deny
- No inbound services exposed

Firewall policy follows a **deny-by-default** model.

---

## DNS Considerations

Edge-FW01 does not act as a DNS server for internal systems.

- Clients and servers resolve DNS via **DC01**
- Any external DNS resolution occurs via DC01 forwarders
- Edge-FW01 only facilitates packet transit

This preserves DNS authority within Active Directory.

---

## Validation

The following artifacts validate correct configuration:

- LAN/WAN interface assignments  
  **Evidence:** [`/evidence/firewall/interfaces-edge-fw01.png`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Evidence/Firewall/interfaces-edge-fw01.png)

- Outbound NAT enforcement  
  **Evidence:** [`/evidence/firewall/nat-outbound.png`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Evidence/Firewall/nat-outbound.png)

- LAN firewall policy  
  **Evidence:** [`/evidence/firewall/firewall-rules-lan.png`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Evidence/Firewall/firewall-rules-lan.png)

---

## Security Considerations

This design:
- Eliminates direct exposure of identity systems
- Enforces least privilege at the network level
- Provides a single point for monitoring and control
- Supports future enhancements (IDS, VPN, logging)

Any changes to firewall behavior must be documented and validated.

---

## Future Enhancements

This firewall design supports:
- VPN termination for remote access
- IDS/IPS enablement
- Additional internal segments
- Cloud connectivity extensions

All enhancements must preserve the principle of explicit trust boundaries.

