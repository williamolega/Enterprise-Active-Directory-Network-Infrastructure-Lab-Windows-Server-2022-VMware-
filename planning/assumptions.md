# Assumptions

## Purpose

This document outlines the **assumptions** made during the design and implementation of the Enterprise Active Directory Network Infrastructure Lab.

Explicitly documenting assumptions:
- Clarifies design intent
- Prevents misinterpretation of scope
- Reduces ambiguity during review
- Mirrors enterprise architecture and risk practices

Assumptions are not requirements. They are **accepted constraints**.

---

## Environment Assumptions

- The lab operates in an **isolated, non-production environment**
- All systems are deployed using **VMware Workstation**
- No existing enterprise infrastructure is integrated
- Internet access is available only via a controlled egress path

The environment is intentionally self-contained.

---

## Identity Assumptions

- A **single forest, single domain** model is sufficient
- The domain represents a small-to-mid enterprise
- Active Directory is the authoritative identity provider
- No external identity federation is required at this stage

Identity complexity is introduced only when justified.

---

## Network Assumptions

- Internal systems do not require inbound internet access
- All outbound traffic is routed through a single firewall
- No segmentation beyond the internal subnet is required
- Firewall rules are default-deny for inbound traffic

Network design prioritizes clarity over micro-segmentation.

---

## Security Assumptions

- Administrative access is limited and role-based
- Least privilege is enforced through groups and RBAC
- Identity systems are treated as high-value assets
- Logging and auditing requirements are identity-centric

Threat modeling is focused on identity compromise and lateral movement.

---

## Operational Assumptions

- Administrative actions are intentional and documented
- Group membership changes are reviewable
- Configuration drift is minimized through centralized policy
- Manual intervention is acceptable for lab-scale operations

Automation is out of scope unless explicitly introduced later.

---

## Tooling Assumptions

- Native Windows and pfSense tooling is sufficient
- No third-party SIEM or EDR is required initially
- GitHub serves as the primary documentation repository

Tooling is selected for transparency and learning value.

---

## Growth and Future State Assumptions

- Additional systems may be added incrementally
- Security maturity may increase over time
- Cloud or hybrid integration is a future consideration
- Current design should not block future enhancements

Design favors extensibility without premature optimization.

---

## Summary

The assumptions documented here:
- Define the boundaries of this lab
- Explain why certain design decisions were made
- Provide context for reviewers and future maintainers

Any change to these assumptions should prompt a **design review**.

