# Evidence Overview

## Purpose

This directory contains **validation artifacts** that prove the environment was configured as described in the design and architecture documentation.

Evidence is separated from narrative documentation to:
- Improve auditability
- Reduce ambiguity
- Mirror enterprise validation practices

Each artifact corresponds to a specific validation claim.

---

## Evidence Categories

### Clients
Artifacts validating client configuration and identity context, including:
- Network configuration (DHCP, DNS, gateway)
- Domain membership
- Group Policy application
- Authentication context

---

### DHCP
Artifacts validating centralized IP address assignment, including:
- Scope configuration
- DHCP options (router, DNS, domain name)

---

### Firewall
Artifacts validating network boundary enforcement, including:
- Interface assignments
- NAT configuration
- Firewall rule behavior

---

### VMware
Artifacts validating virtual networking configuration, including:
- Internal network isolation
- External NAT-based egress

---

## Evidence Handling Notes

- Evidence represents **point-in-time validation**
- Screenshots are used only where visual confirmation adds value
- Command output is preserved verbatim
- No sensitive production data is included

---

## Relationship to Validation

Evidence artifacts are referenced explicitly in:
- [`validation/acceptance-criteria.md`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/validation/acceptance-criteria.md)
- [`validation/validation-tests.md`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/validation/validation-tests.md)

Evidence supports **claims**, not instructions.
