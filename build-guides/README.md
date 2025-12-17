# Build Guides Overview

This directory contains system-specific build documentation for the Enterprise Active Directory Network Infrastructure Lab.

Each guide focuses on a **single component**, its purpose, and its configuration boundaries.  
This mirrors how enterprise environments are documented and maintained, where ownership and responsibility are clearly defined.

The build order below reflects **dependency flow**, not importance.

---

## Build Order & Dependencies

### 1. VMware Networking
**Document:** [`vmware-networking.md`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Build%20Guides/vmware-networking.md)

Purpose:
- Establish isolated internal networking for enterprise systems
- Define trust boundaries between internal and external networks

Key outcomes:
- VMnet2 configured as host-only internal network
- VMnet8 configured for NAT-based internet access
- No direct host access to the enterprise subnet

This layer must exist before any systems are deployed.

---

### 2. Edge Firewall (pfSense)
**Document:** [`edge-fw01-pfsense-build.md`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Build%20Guides/edge-fw01-pfsense-build.md)

Purpose:
- Enforce a single network boundary between internal system and the internet
- Provide routing, NAT, and firewall enforcement

Key outcomes:
- WAN interface connected to VMnet8
- LAN interface connected to VMnet2
- NAT and firewall rules applied at the perimeter

Identity systems should never perform routing or NAT functions.

---

### 3. Domain Controller (DC01)
**Document:** [`dc01-build.md`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Build%20Guides/dc01-build.md)

Purpose:
- Provide centralized identity, authentication, and directory services
- Act as the authoritative DNS and DHCP server for the internal domain

Key outcomes:
- Active Directory Domain Services deployed
- DNS configured as AD-integrated and authoritative
- DHCP scope created for internal clients
- Loopback DNS configured for self-resolution

DC01 depends on both networking and firewall layers being in place.

---

### 4. Client Workstation (Client1)
**Document:** [`client1-build.md`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Build%20Guides/client1-build.md)

Purpose:
- Validate domain services from a consumer perspective
- Serve as a controlled identity endpoint

Key outcomes:
- DHCP-based IP configuration
- Domain join to `ad.enterprise.lab`
- Group Policy application and validation

Clients consume identity services but do not provide infrastructure services.

---

## Documentation Philosophy

Build guides are intentionally:
- **Component-focused**, not phase-based
- **Declarative**, not tutorial-heavy
- **Aligned to system responsibility**

Validation and proof of configuration state are documented separately in the [`/validation`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/tree/main/Validation) and [`/evidence`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/tree/main/Evidence) directories.

This separation ensures:
- Clear ownership boundaries
- Auditable configuration state
- Scalable documentation as the lab grows

---

## Future Expansion

This structure supports future additions without restructuring:
- Additional domain controllers (e.g., DC02)
- Centralized logging and SIEM integration
- Vulnerability management tooling
- Cloud-connected identity extensions

New systems should be documented as standalone build guides.

