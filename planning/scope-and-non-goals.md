# Scope and Non-Goals

## Purpose

This document defines the **scope** and **explicit non-goals** of the Enterprise Active Directory Network Infrastructure Lab.

Clearly documenting scope:
- Sets accurate expectations for reviewers
- Prevents misinterpretation of design intent
- Demonstrates architectural discipline
- Mirrors enterprise project governance practices

What is not included is as important as what is included.

---

## In-Scope Objectives

The following capabilities are **intentionally within scope** of this lab.

### Identity Infrastructure
- Single-forest, single-domain Active Directory
- Centralized authentication and authorization
- AD-integrated DNS
- Group-based RBAC and AGDLP patterns

---

### Network Boundary and Segmentation
- Isolated internal enterprise network
- Single controlled egress point
- Firewall-enforced internal/external boundary
- No direct internet exposure of identity systems

---

### Security Baseline
- Group Policy–enforced security baselines
- Identity-focused logging and auditing
- Administrative tiering strategy (conceptual and partial enforcement)
- Least-privilege access via groups

---

### Validation and Evidence
- Configuration validation via authoritative commands
- Evidence artifacts stored and referenced separately
- Clear mapping of claims to proof

---

### Documentation and Design
- Architecture-first documentation
- Explicit assumptions, risks, and tradeoffs
- Future-state roadmap aligned to security maturity

---

## Explicit Non-Goals

The following items are **intentionally out of scope** for this lab.

### High Availability and Disaster Recovery
- No multi-site deployment
- No automated failover
- No backup or recovery orchestration

These are deferred to future maturity phases.

---

### Full Network Micro-Segmentation
- No per-application VLANs
- No east-west firewall enforcement between all systems

The lab prioritizes identity architecture over network complexity.

---

### Advanced Threat Detection
- No fully integrated SIEM
- No EDR or UEBA tooling
- No real-time alerting pipelines

Logging is foundational, not fully operationalized.

---

### Automation and Infrastructure-as-Code
- No DSC, Terraform, or Ansible
- No automated build pipelines
- Manual configuration is intentional

The focus is on understanding and validation, not speed.

---

### Compliance Certification
- No formal alignment to a specific compliance framework
- No audit attestation or certification claims

Controls are **inspired by**, not certified against, standards.

---

### Production Hardening
- No real-world uptime guarantees
- No patch management lifecycle
- No enterprise support tooling

The environment is educational and demonstrative.

---

## Scope Control Principles

Scope decisions are guided by the following principles:

- Prioritize **identity and access control**
- Avoid premature optimization
- Introduce complexity only when it provides security value
- Document tradeoffs transparently

Any change to scope should be intentional and documented.

---

## Summary

The scope of this lab is intentionally focused on:
- Identity architecture
- Security design reasoning
- Enterprise-aligned documentation and validation

By clearly defining non-goals, this lab avoids overreach and maintains architectural clarity.

