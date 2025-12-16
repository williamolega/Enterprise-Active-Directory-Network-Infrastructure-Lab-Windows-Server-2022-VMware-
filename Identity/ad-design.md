# Active Directory Design

## Purpose

This document describes the **Active Directory (AD) design decisions** for the Enterprise Active Directory Network Infrastructure Lab.

The goal of this design is to:
- Provide a secure and reliable identity authority
- Support authentication, authorization, and policy enforcement
- Mirror real-world enterprise AD patterns, not lab-only shortcuts

---

## Forest and Domain Design

### Forest
- Single forest
- Serves as the ultimate security boundary

Rationale
- Simplifies trust and administration
- Most common enterprise deployment model
- Appropriate for small-to-mid enterprise environments

---

### Domain
- Single domain: `ad.enterprise.lab`

Rationale
- Centralized identity and policy management
- Avoids unnecessary complexity
- Aligns with modern best practice (domains are not organizational boundaries)

---

## Domain Controller Design

### Domain Controllers
- **DC01** (Windows Server 2022)

**Roles**
- Active Directory Domain Services (AD DS)
- DNS (AD-integrated)
- DHCP (single scope)

**Key Decisions**
- Domain Controller is not internet-facing
- Domain Controller performs no routing or NAT
- DNS on DC01 points to loopback (127.0.0.1) for self-resolution

This ensures AD services remain authoritative and resilient.

---

## DNS Integration

- DNS is AD-integrated
- Zone replication occurs within the domain
- Clients resolve DNS exclusively through the Domain Controller

Rationale
- Active Directory relies on DNS for authentication and service discovery
- Centralized DNS ensures consistency and integrity
- External name resolution is handled via DNS forwarders, not public DNS on clients

---

## Identity Scope

### Objects Managed in Active Directory
- Users
- Computers
- Groups
- Group Policy Objects (GPOs)

### Objects Not Managed in Active Directory
- Network routing
- Firewall enforcement
- Internet egress policy

This enforces **least responsibility** for identity infrastructure.

---

## Security Considerations

This AD design supports:
- Strong authentication boundaries
- Centralized policy enforcement
- Auditable identity operations
- Future tiered administration models

**Guiding principles**
- Identity systems are isolated
- Authentication is centralized
- Authorization is group-based
- Policy is enforced via GPO, not local configuration

---

## Scalability and Future State

This design intentionally supports future expansion, including:
- Additional Domain Controllers (e.g., DC02)
- Administrative tiering
- Centralized logging and monitoring
- Hybrid identity or cloud extensions

Changes to the AD design should be driven by **security or business requirements**, not convenience.

---

## Summary

The Active Directory design in this lab prioritizes:
- Clarity over complexity
- Security over shortcuts
- Scalability over one-off configuration

This mirrors how enterprise identity environments are designed, operated, and reviewed.

