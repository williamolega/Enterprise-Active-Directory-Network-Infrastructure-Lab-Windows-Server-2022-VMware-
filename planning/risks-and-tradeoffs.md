# Risks and Tradeoffs

## Purpose

This document outlines the **key risks and tradeoffs** associated with the design and implementation of the Enterprise Active Directory Network Infrastructure Lab.

Documenting risks and tradeoffs:
- Demonstrates intentional decision-making
- Shows awareness of security and operational impact
- Mirrors enterprise risk management practices
- Prevents false assumptions about “perfect” designs

Every architecture involves tradeoffs.

---

## Single Domain Controller Risk

### Risk
The environment currently relies on a **single Domain Controller (DC01)**.

### Impact
- DC failure results in loss of authentication and directory services
- No built-in redundancy for identity services

### Tradeoff Rationale
- Acceptable for a lab-scale environment
- Reduces complexity and resource usage
- Enables focused learning on core identity concepts

### Mitigation (Future State)
- Introduce a secondary Domain Controller (DC02)
- Distribute FSMO roles as appropriate

---

## Co-hosting AD, DNS, and DHCP

### Risk
Multiple critical services run on a single system.

### Impact
- Increased blast radius if DC01 is compromised or unavailable
- Service contention in resource-constrained environments

### Tradeoff Rationale
- Common in small enterprises
- Simplifies architecture for learning and documentation
- Reflects realistic entry-level enterprise deployments

### Mitigation (Future State)
- Separate DHCP or DNS if scale or risk increases
- Introduce role separation as maturity grows

---

## Flat Internal Network

### Risk
All internal systems share a single subnet.

### Impact
- Limited east-west traffic isolation
- Reduced ability to contain lateral movement

### Tradeoff Rationale
- Simplifies troubleshooting and design
- Appropriate for initial identity-focused lab
- Avoids premature segmentation complexity

### Mitigation (Future State)
- Introduce subnet segmentation

---

## Limited Centralized Logging

### Risk
Logs are stored locally and reviewed manually.

### Impact
- Reduced detection capability
- Slower incident response
- Limited historical analysis

### Tradeoff Rationale
- Keeps tooling simple and transparent
- Avoids introducing SIEM complexity prematurely
- Focuses learning on identity signal

### Mitigation (Future State)
- Centralize logs into a SIEM
- Implement alerting and correlation
- Retain logs for compliance and investigation

---

## Administrative Model Maturity

### Risk
Administrative tiering is defined but not fully enforced with dedicated PAWs or JIT access.

### Impact
- Increased exposure of privileged credentials
- Reduced defense-in-depth for Tier 0 assets

### Tradeoff Rationale
- Allows conceptual understanding before technical enforcement
- Reduces lab resource requirements
- Mirrors transitional enterprise environments

### Mitigation (Future State)
- Implement Privileged Access Workstations
- Introduce Just-In-Time administration
- Enforce stricter logon restrictions

---

## Firewall Simplicity

### Risk
Firewall rules are minimal and permissive for outbound traffic.

### Impact
- Reduced visibility into malicious egress
- Limited application-level control

### Tradeoff Rationale
- Focuses on identity and boundary enforcement
- Avoids policy sprawl in early stages
- Maintains clarity for learning and validation

### Mitigation (Future State)
- Introduce egress filtering
- Enable IDS/IPS
- Add logging and alerting

---

## Documentation vs Automation

### Risk
Manual configuration increases the risk of human error.

### Impact
- Configuration drift
- Reduced repeatability

### Tradeoff Rationale
- Emphasizes understanding over automation
- Improves transparency of decisions
- Appropriate for a learning-focused lab

### Mitigation (Future State)
- Introduce Infrastructure-as-Code
- Automate validation checks
- Version control configurations

---

## Summary

The risks and tradeoffs documented here:
- Are intentional and understood
- Reflect realistic enterprise constraints
- Provide a roadmap for future hardening

No architecture is risk-free, only risk-aware.
