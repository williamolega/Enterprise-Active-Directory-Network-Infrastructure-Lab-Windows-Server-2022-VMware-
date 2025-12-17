# Executive Summary

## Overview

This project documents the design, implementation, and validation of an **enterprise-style Active Directory network environment**.

The lab is intentionally designed to demonstrate:
- Identity-first architecture
- Secure network boundary enforcement
- Role-based access control
- Enterprise-aligned documentation and validation practices

This is not just a tutorial lab. It is an **architectural and security exercise**.

---

## Key Objectives

- Build a secure and isolated identity environment
- Separate identity services from network security functions
- Enforce least privilege through RBAC and group strategy
- Validate design claims with authoritative evidence
- Document assumptions, risks, and future state intentionally

---

## Architecture Summary

- **Hypervisor:** VMware Workstation
- **Network Boundary:** pfSense (Edge-FW01)
- **Identity Services:** Active Directory (DC01)
- **Clients:** Domain-joined Windows workstations
- **Domain:** `ad.enterprise.lab`

All external connectivity is mediated through a firewall.  
Identity services are never internet-facing.

---

## Security Posture

The environment enforces:
- Centralized authentication and authorization
- Group-based access control
- Administrative tiering strategy
- Policy-driven configuration via Group Policy
- Identity-centric logging and auditing

Security decisions are explicit, documented, and validated.

---

## Validation Approach

Validation is performed using:
- Authoritative command output
- System configuration artifacts
- Targeted screenshots where visual proof adds value

Evidence is separated from narrative and stored for auditability.

---

## Intended Audience

This project is intended for:
- Security engineers
- Identity and IAM practitioners
- Cloud and infrastructure security professionals
- Hiring managers evaluating architectural thinking

---

## Summary

This lab demonstrates the ability to:
- Design secure identity infrastructure
- Reason about risk and tradeoffs
- Document decisions professionally
- Validate outcomes like an enterprise engineer

It represents a **foundational identity and security architecture**, not a finished production system.

