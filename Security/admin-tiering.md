# Administrative Tiering Strategy

## Purpose

This document defines the **administrative tiering strategy** for the Enterprise Active Directory Network Infrastructure Lab.

The goal of administrative tiering is to:
- Protect high-value identity assets
- Limit credential exposure
- Reduce lateral movement risk
- Enforce least privilege across administrative roles

Administrative access is treated as a **security boundary**, not a convenience.

---

## Tiering Model Overview

The environment follows a **tiered administration model**, where administrative access is segmented based on the sensitivity of systems being managed.

Each tier:
- Has distinct credentials
- Uses separate access paths
- Is isolated from lower-trust systems

This model prevents compromise at one level from cascading upward.

---

## Tier Definitions

### Tier 0 — Identity & Core Infrastructure

**Scope**
- Domain Controllers
- Active Directory
- Identity services
- Domain-level configuration

**Examples**
- Domain Admins
- Enterprise Admins
- AD-related service accounts

**Controls**
- Highly restricted membership
- No interactive logon to workstations
- Access only from trusted administrative systems

Tier 0 is the **highest trust level** and must be protected above all others.

---

### Tier 1 — Server Administration

**Scope**
- Member servers
- Application servers
- Infrastructure services

**Examples**
- Server operators
- Application administrators

**Controls**
- Separate credentials from Tier 0
- No access to Domain Controllers
- Limited administrative scope

Tier 1 administrators cannot manage identity infrastructure.

---

### Tier 2 — Workstation & User Support

**Scope**
- User workstations
- End-user support activities

**Examples**
- Helpdesk staff
- Desktop support

**Controls**
- Lowest privilege level
- No access to servers or identity systems
- Separate credentials from higher tiers

Tier 2 is treated as **high-risk** due to user interaction.

---

## Credential Separation

Key rules:
- One account per tier per administrator
- No credential reuse across tiers
- Tier 0 credentials never touch Tier 1 or Tier 2 systems

This reduces the risk of credential theft and reuse.

---

## Access Enforcement

Administrative tiering is enforced through:
- OU placement
- Group membership
- Logon restrictions via Group Policy
- Explicit deny policies where appropriate

Access paths are **designed**, not assumed.

---

## Group Strategy Alignment

Administrative access is granted via:
- Dedicated admin groups
- Role-based membership
- Clear naming conventions

Permissions are never assigned directly to user accounts.

---

## Logging and Monitoring

Administrative activity is:
- Logged centrally
- Monitored for anomalies
- Subject to review

High-risk actions (Tier 0) receive the highest scrutiny.

---

## Future Enhancements

This strategy supports:
- Privileged Access Workstations (PAWs)
- Just-in-Time (JIT) administration
- Privileged Access Management (PAM)
- Cloud-based privileged identity extensions

Tiering is designed to evolve with maturity.

---

## Summary

The administrative tiering strategy prioritizes:
- Protection of identity over convenience
- Explicit trust boundaries
- Reduced blast radius from compromise

This mirrors how enterprise environments protect their most critical identity assets.

