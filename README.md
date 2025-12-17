# Enterprise Active Directory Network Infrastructure Lab

## Overview

This repository documents the design, implementation, validation, and security posture of an **enterprise-style Active Directory network environment** built using VMware, pfSense, and Windows Server technologies.

The focus of this project is **architecture and security reasoning**, not step-by-step instruction.

---

## Lab at a Glance

| Component | Details |
|--------|--------|
| Domain | `ad.enterprise.lab` |
| Internal Network | `192.168.81.0/24` |
| Hypervisor | VMware Workstation |
| Firewall | pfSense (Edge-FW01) |
| Domain Controller | Windows Server 2022 (DC01) |
| Client | Windows 11 (Client1) |
| Identity Model | RBAC + AGDLP |
| Policy Enforcement | Group Policy |
| Validation | Evidence-backed |

---

## What This Lab Demonstrates

- Enterprise-aligned Active Directory design
- Secure network boundary enforcement
- Role-Based Access Control (RBAC)
- Group Policy–driven security baselines
- Identity-centric logging and audit strategy
- Risk-aware architectural decision-making
- Evidence-based validation

---

## High-Level Architecture
![Enterprise AD Network Architecture](architecture/network-diagram.png)

- **Internal Network:** Isolated enterprise subnet
- **Firewall:** Single controlled egress point
- **Identity Services:** Active Directory with AD-integrated DNS
- **Clients:** Domain-joined Windows systems

See [`/architecture/architecture-overview.md`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Architecture/architecture-overview.md) for details.

---

## Repository Structure

- [`architecture/`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/tree/main/Architecture):  System design and trust boundaries  
- [`identity/`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/tree/main/Identity):  AD, OU, group, RBAC design  
- [`security/`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/tree/main/Security):  GPO baselines, logging, admin tiering  
- [`planning/`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/tree/main/Planning):  Assumptions, risks, scope, roadmap  
- [`build-guides/`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/tree/main/Build%20Guides):  Component-focused build documentation  
- [`validation/`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/tree/main/Validation):  Acceptance criteria and validation tests  
- [`evidence/`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/tree/main/Evidence):  Proof artifacts supporting validation  

---

## Validation and Evidence

All architectural and security claims are validated through:
- Command output
- Configuration artifacts
- Screenshots where visual confirmation adds value

Evidence is stored separately and referenced explicitly.

---

## Disclaimer

This environment is:
- Non-production
- Isolated
- Intended for educational and demonstration purposes

No real organizational data is used.

---

## Summary

This project reflects how **enterprise identity and security environments are designed, documented, and reviewed**.

It prioritizes:
- Clarity over complexity
- Security over convenience
- Evidence over assumption
