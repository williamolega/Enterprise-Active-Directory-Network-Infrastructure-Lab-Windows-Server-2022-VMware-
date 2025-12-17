# Group Policy Baseline

## Purpose

This document defines the **Group Policy (GPO) baseline strategy** for the Enterprise Active Directory Network Infrastructure Lab.

The objective of this baseline is to:
- Establish consistent security posture across systems
- Reduce configuration drift
- Centralize enforcement of security controls
- Reflect real-world enterprise hardening practices

Group Policy is the primary mechanism for enforcing security standards at scale.

---

## Baseline Philosophy

The GPO baseline follows these principles:

- **Security by default**
- **Centralized enforcement**
- **Minimal exceptions**
- **Auditability over convenience**

Local configuration is avoided wherever possible in favor of domain-level policy.

---

## Scope of the Baseline

The baseline applies to:
- Domain Controllers
- Member servers
- Domain-joined workstations
- User accounts

Policies are scoped via **OUs and security filtering**, not applied indiscriminately at the domain root.

---

## Domain Controller Baseline

### Objectives
- Protect the identity authority
- Reduce attack surface
- Increase visibility into authentication activity

### Key Control Areas
- Account lockout policies
- Kerberos policy enforcement
- Audit policy configuration
- Secure LDAP and authentication settings
- Restricted local logon rights

Domain Controllers receive **stricter controls** than other systems.

---

## Workstation Baseline

### Objectives
- Harden user endpoints
- Reduce lateral movement risk
- Enforce consistent user experience

### Key Control Areas
- Password and lock screen policies
- Local administrator restrictions
- Firewall enforcement
- Security auditing
- Removal of insecure legacy protocols

Workstations are treated as **untrusted by default**.

---

## User Policy Baseline

### Objectives
- Protect user credentials
- Enforce secure behavior
- Reduce identity misuse

### Key Control Areas
- Credential protection settings
- Logon restrictions
- Policy-based security controls
- User environment consistency

User policies are scoped to **user OUs**, not computers.

---

## Audit and Logging Baseline

### Objectives
- Ensure visibility into identity-related activity
- Support incident investigation and access review

### Key Control Areas
- Logon and logoff events
- Account management events
- Group membership changes
- Policy changes
- Authentication failures

Audit policies are defined centrally and applied consistently.

---

## Policy Application Strategy

- GPOs are applied at the **lowest reasonable OU level**
- Inheritance blocking is used sparingly and explicitly
- Security filtering is preferred over OU sprawl
- Policy names clearly indicate scope and intent

This reduces unintended policy impact and simplifies troubleshooting.

---

## Exception Handling

Exceptions to baseline policy:
- Must be explicitly documented
- Should be temporary whenever possible
- Must not weaken core identity security

Exceptions are handled via **additional GPOs**, not by modifying the baseline.

---

## Validation

Baseline enforcement is validated using:
- `gpresult` reports
- Event logs
- Configuration review

Evidence is stored separately in the [`/evidence`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/tree/main/Evidence) directory.

---

## Scalability and Future State

This baseline supports future enhancements such as:
- Tiered administration
- Privileged access workstations (PAWs)
- Centralized logging and SIEM integration
- Cloud-based policy extensions

Baseline policies should evolve with threat landscape changes.

---

## Summary

The Group Policy baseline in this lab prioritizes:
- Consistency over customization
- Security over convenience
- Visibility over implicit trust

This approach reflects how enterprise security baselines are designed, enforced, and reviewed.

