# Known Limitations

## Purpose

This document outlines the **known limitations** of the validation performed for the Enterprise Active Directory Network Lab.

Documenting limitations:
- Sets accurate expectations for reviewers
- Prevents over-interpretation of validation results
- Reflects mature engineering and audit practices
- Complements acceptance criteria and validation tests

Validation confirms **intentional outcomes**, not absolute guarantees.

---

## Scope of Validation

Validation focuses on:
- Correct configuration state
- Architectural alignment with design intent
- Identity and access control functionality
- Boundary enforcement at a logical level

Validation does **not** attempt to prove:
- Production readiness
- Resilience under failure conditions
- Long-term operational stability

---

## Single-Instance Validation

### Limitation
Validation is performed against a **single instance** of each system.

### Impact
- No redundancy testing
- No replication validation
- No failover scenarios exercised

### Context
This is consistent with the lab’s single-DC, single-firewall design and documented tradeoffs.

---

## Point-in-Time Validation

### Limitation
All validation artifacts represent a **point-in-time snapshot**.

### Impact
- Configuration drift after validation is not detected
- No continuous compliance monitoring exists

### Context
Ongoing monitoring and drift detection are out of scope for this lab.

---

## Manual Validation Methods

### Limitation
Validation relies on **manual commands and screenshots**.

### Impact
- Human error is possible
- Validation is not automatically repeatable

### Context
Manual validation is intentional to prioritize transparency and understanding over automation.

---

## Limited Security Testing

### Limitation
Validation does not include:
- Adversarial testing
- Penetration testing
- Exploit simulation
- Red team activity

### Impact
- Security posture is inferred from configuration, not attack resistance

### Context
The lab focuses on **preventive and architectural controls**, not offensive testing.

---

## Logging and Detection Coverage

### Limitation
Logging validation confirms **log generation**, not:
- Alert fidelity
- Correlation accuracy
- Detection coverage against real threats

### Impact
- Detection effectiveness is not fully measured

### Context
Advanced detection and SIEM validation are planned future enhancements.

---

## Environmental Constraints

### Limitation
Validation occurs in a **virtualized lab environment**.

### Impact
- Performance characteristics differ from production
- Hardware-level behaviors are not represented

### Context
The lab is designed for architectural learning, not performance benchmarking.

---

## Dependency on Assumptions

### Limitation
Validation assumes:
- Assumptions documented in [`/planning/assumptions.md`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/planning/assumptions.md) hold true
- No undocumented changes exist

### Impact
- Violated assumptions may invalidate validation results

### Context
Assumptions are explicitly documented to manage this risk.

---

## Summary

The known limitations documented here:
- Are intentional and understood
- Do not invalidate the design or validation outcomes
- Reflect realistic constraints of a lab-scale environment

Validation confirms **architectural correctness and intent**, not production assurance.

