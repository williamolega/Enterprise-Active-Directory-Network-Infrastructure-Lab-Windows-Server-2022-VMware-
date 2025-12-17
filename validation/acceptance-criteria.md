# Acceptance Criteria

## Purpose

This document defines the **acceptance criteria** for the Enterprise Active Directory Network Infrastructure Lab.

Acceptance criteria establish the minimum conditions required for the environment to be considered:
- Correctly implemented
- Secure by design
- Architecturally consistent
- Ready for validation and review

These criteria focus on **outcomes**, not implementation steps.

---

## Identity and Authentication

The environment is considered acceptable when:

- Active Directory is deployed and functional
- A domain (`ad.enterprise.lab`) exists and is authoritative
- Domain Controller (DC01) can authenticate users and computers
- Clients successfully join and authenticate to the domain

---

## DNS and Name Resolution

Acceptance criteria:

- DNS is AD-integrated and authoritative for the domain
- Clients resolve domain and DC records via DC01
- Domain Controller resolves its own records via loopback
- External DNS resolution occurs only through forwarders

---

## DHCP and Client Configuration

The environment meets criteria when:

- DHCP issues addresses from a defined internal scope
- Clients receive:
  - Correct IP address
  - Correct subnet mask
  - Correct default gateway
  - Correct DNS server
- No DHCP is provided by the hypervisor or firewall

---

## Network Boundary Enforcement

Acceptance criteria:

- Internal systems have no direct internet exposure
- All egress traffic traverses the firewall (Edge-FW01)
- Firewall enforces NAT and default-deny inbound policy
- Identity systems do not perform routing or NAT

---

## Authorization and Access Control

The environment is acceptable when:

- Permissions are granted via groups only
- Role-based access control (RBAC) is enforced
- No permissions are assigned directly to users
- Administrative access is separated by tier and role

---

## Policy Enforcement

Acceptance criteria:

- Group Policy is applied successfully to clients
- Security baselines are enforced via GPO
- Policy scope aligns with OU design
- No reliance on local configuration drift

---

## Logging and Audit

The environment meets criteria when:

- Identity-related events are logged
- Audit policies are centrally defined
- Logs support authentication, authorization, and change tracking
- Evidence of logging configuration exists

---

## Documentation and Evidence

Acceptance requires:

- Design decisions are documented
- Risks, assumptions, and tradeoffs are explicit
- Evidence artifacts exist for all critical claims
- Evidence is traceable, reproducible, and reviewable

---

## Summary

The lab is considered **complete and acceptable** when all criteria above are met and validated through documented evidence.

