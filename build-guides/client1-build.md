# Client Workstation Build (Client1 – Windows 11 Pro)

## Purpose

This document defines the build and configuration of **Client1**, a domain-joined workstation used to validate identity, DNS, DHCP, and Group Policy functionality within the Enterprise Active Directory Network Lab.

Client1 represents a standard enterprise endpoint and is intentionally limited to a **consumer role** of directory services.

---

## System Overview

- **Hostname:** Client1
- **Operating System:** Windows 11 Pro
- **Domain Membership:** `ad.enterprise.lab`
- **Role:** Domain-joined client workstation

Client1 does not host infrastructure services and does not perform routing, DNS, or DHCP functions.

---

## Network Configuration

Client1 is connected only to the **internal network**.

- **Interface:** Internal (VMnet2)
- **IP Assignment:** DHCP (from DC01)
- **DNS Server:** `192.168.81.10`
- **Default Gateway:** `192.168.81.1`

### Design Rationale
- DHCP ensures centralized IP assignment
- DNS resolution is enforced through Active Directory
- The client has no direct awareness of external DNS or routing

---

## Domain Join

Client1 is joined to the `ad.enterprise.lab` domain using domain credentials.

### Expected Outcomes
- Computer account created in Active Directory
- Trust established with DC01
- Secure channel created for authentication and policy delivery

---

## Group Policy

Client1 receives Group Policy from DC01.

This validates:
- Directory connectivity
- DNS resolution
- SYSVOL availability
- Client-side policy processing

Client1 receives Group Policy from the domain and applies it locally; it does not create or manage policies.

---

## Identity Context

User and computer authentication occurs via Active Directory.

- Logons are authenticated by DC01
- Kerberos is used as the primary authentication protocol
- Authorization decisions are centrally enforced

---

## Validation

The following artifacts validate correct configuration:

- DHCP assignment and DNS configuration  
  **Evidence:** [`/evidence/clients/ipconfig-all-client1.txt`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/evidence/Clients/ipconfig-all-client1.txt)

- Domain membership confirmation and Group Policy application  
  **Evidence:** [`/evidence/clients/gpresult-client1.html`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/evidence/Clients/gpresult-client1.html)

- Identity context verification  
  **Evidence:** [`/evidence/clients/whoami-client1.txt`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/evidence/Clients/whoami-client1.txt)

- System Domain Membership  
  **Evidence:** [`/evidence/clients/system-domain-membership-client1.png`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/evidence/Clients/system-domain-membership-client1.png)


---

## Security Considerations

- Client1 has no local administrative authority over domain services
- Network access is constrained by firewall policy
- Identity and policy enforcement is centralized

This aligns with least privilege and endpoint isolation principles.

---

## Future Enhancements

Client1 can later be used to validate:
- Additional GPOs
- Endpoint logging and auditing
- Security tooling integration (Defender, EDR)
- Conditional access and identity-based controls

All future endpoint configurations should follow this baseline.

