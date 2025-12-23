# Domain Controller Build (DC01 – Windows Server 2022)

## Purpose

This document defines the configuration of **DC01**, the primary Domain Controller for the Enterprise Active Directory Network Infrastructure Lab.

DC01 is responsible for:
- Centralized identity and authentication
- Authoritative DNS for the domain
- DHCP for internal clients

DC01 does **not** perform routing, NAT, or perimeter security functions.

---

## System Overview

- **Hostname:** DC01
- **Operating System:** Windows Server 2022
- **Domain:** `ad.enterprise.lab`
- **Role:** Primary Domain Controller

DC01 is the first identity system deployed and serves as the foundation for all directory-dependent services.

---

## Network Configuration

DC01 is connected only to the **internal network**.

- **Interface:** Internal (VMnet2)
- **IP Address:** `192.168.81.10`
- **Subnet Mask:** `255.255.255.0`
- **Default Gateway:** `192.168.81.1` (Edge-FW01)
- **DNS Server:** `127.0.0.1`

### Design Rationale
- Loopback DNS ensures self-resolution of AD records
- Gateway points to the firewall, not another Windows system
- Static IP provides consistent identityand reliable service resolution

---

## Active Directory Domain Services (AD DS)

### Domain Creation
- New forest created
- Domain name: `ad.enterprise.lab`
- Functional level aligned with Windows Server 2016 for compatibility

DC01 holds all FSMO roles in this lab.

---

## DNS Configuration

DNS is installed as an **AD-integrated service**.

Key characteristics:
- DC01 is authoritative for `ad.enterprise.lab`
- SRV records are automatically registered
- Secure dynamic updates are enabled

### Forwarders
- External DNS resolution is handled via configured forwarders
- DNS recursion remains centralized through DC01

---

## DHCP Configuration

DC01 provides DHCP services for the internal network.

### DHCP Scope
- **Scope Name:** Internal-Lan-Scope
- **Range:** `192.168.81.100 – 192.168.81.200`
- **Subnet Mask:** `255.255.255.0`

### DHCP Options
- **Option 003 (Router):** `192.168.81.1`
- **Option 006 (DNS Servers):** `192.168.81.10`
- **Option 015 (DNS Domain Name):** `ad.enterprise.lab`

Running DHCP on DC01 keeps IP assignment closely integrated with Active Directory.

---

## Time Synchronization

DC01 serves as the authoritative time source for the domain.

- Domain members synchronize time from DC01
- Time accuracy is critical for Kerberos authentication

---

## Security Considerations

- DC01 is not exposed to the internet
- Administrative access is restricted to domain admins
- No non-essential services are installed
- Identity services are isolated from network security controls

This configuration aligns with least privilege and separation of duties principles.

---

## Validation

The following artifacts validate correct configuration:

- Active Directory health  
  **Evidence:** [`/evidence/ad/dcdiag-dc01.txt`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/edit/main/evidence/AD/dcdiag-dc01.txt)

- Network configuration  
  **Evidence:** [`/evidence/ad/ipconfig-all-dc01.txt`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/evidence/AD/ipconfig-all-dc01.txt)

- DNS configuration and forwarders  
  **Evidence:** [`/evidence/ad/dns-forwarders-dc01.png`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/evidence/AD/dns-forwarders.dc01.png)

- FSMO role ownership  
  **Evidence:** [`/evidence/ad/netdom-query-fsmo.txt`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/evidence/AD/netdom-query-fsmo.txt)
  
- DHCP Scope  
  **Evidence:** [`/evidence/dhcp/dhcp-scope-dc01.png`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/evidence/DHCP/dhcp-scope-dc01.png)
  
- DHCP Options  
  **Evidence:** [`/evidence/dhcp/dhcp-options-dc01.png`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/evidence/DHCP/dhcp-options-dc01.png)  

---
## Notes

- `dcdiag` reports no critical errors. Observed warnings relate to optional LDAP hardening, WinRM configuration, and external DNS/time resolution, which are common in isolated lab environments and do not impact Active Directory functionality.

---

## Future Enhancements

This design supports:
- Additional Domain Controllers (DC02)
- Tiered administrative models
- Enhanced logging and auditing
- Integration with SIEM and security tooling

All future identity systems should follow this baseline.

