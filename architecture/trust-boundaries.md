# Trust Boundaries

## Purpose

This document defines the **trust boundaries** enforced within the Enterprise Active Directory Network Infrastructure Lab.

Trust boundaries represent points where:
- Trust levels change
- Access must be explicitly controlled
- Security assumptions no longer hold

Making trust boundaries explicit prevents implicit trust and reduces security risk.

---

## Trust Boundary Philosophy

This lab follows these principles:

- Trust is **never assumed**
- Boundaries are **explicit and enforced**
- Identity systems are treated as **high-value assets**
- Compromise in one zone should not automatically grant access to another

Trust boundaries are architectural controls, not just network rules.

---

## External Network Boundary

### Boundary
**External Network <-> Internal Network**

### Enforcement
- pfSense firewall (Edge-FW01)
- NAT and firewall rules
- Default-deny inbound policy

### Trust Model
- External networks are **untrusted**
- No inbound access to internal systems
- All outbound traffic is explicitly routed through the firewall

This boundary prevents direct exposure of identity infrastructure.

---

## Internal Network Boundary

### Boundary
**Firewall <-> Internal Enterprise Network**

### Enforcement
- Single internal subnet
- Firewall as the default gateway
- No routing or NAT on identity systems

### Trust Model
- Internal systems are trusted relative to external networks
- Trust is still limited and monitored
- Internal compromise does not imply administrative privilege

---

## Identity Trust Boundary (Tier 0)

### Boundary
**Identity Systems <-> All Other Systems**

### Enforcement
- Administrative tiering
- Group-based access control
- Logon restrictions
- Group Policy enforcement

### Trust Model
- Domain Controllers represent **Tier 0**
- Compromise of Tier 0 is considered catastrophic
- Administrative access is tightly restricted and audited

Identity trust boundaries are enforced logically, not just physically.

---

## Administrative Trust Boundaries

### Boundary
**Administrative Accounts ↔ Standard User Accounts**

### Enforcement
- Separate admin groups
- Role-based access control
- Administrative tiering model

### Trust Model
- Administrative identities are higher trust
- Credentials are protected from exposure to lower-tier systems
- Privilege escalation paths are minimized

---

## Client Trust Boundary

### Boundary
**User Workstations <-> Identity Infrastructure**

### Enforcement
- Authentication via Active Directory
- Authorization via group membership
- Policy enforcement via Group Policy

### Trust Model
- Workstations are treated as **potentially compromised**
- Users consume identity services but do not administer them
- Client compromise does not imply identity compromise

---

## Trust Boundary Validation

Trust boundaries are validated through:
- Firewall configuration evidence
- Group Policy application
- RBAC and group strategy
- Administrative access controls

Evidence artifacts are stored in the [`/evidence`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/tree/main/evidence) directory.

---

## Summary

The trust boundaries in this lab:
- Are explicitly defined and enforced
- Separate untrusted, trusted, and high-trust systems
- Align with Zero Trust and enterprise identity security principles

Explicit trust boundaries are foundational to secure system design.

