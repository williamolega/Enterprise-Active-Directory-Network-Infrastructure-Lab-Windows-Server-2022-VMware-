# Roadmap and Future State

## Purpose

This document outlines the **planned evolution** of the Enterprise Active Directory Network Infrastructure Lab.

The roadmap:
- Demonstrates intentional growth, not one-time configuration
- Aligns technical improvements with security maturity
- Reflects how enterprise environments evolve incrementally
- Provides context for current tradeoffs and limitations

The current state is a foundation, not an endpoint.

---

## Current State Summary

The lab currently provides:
- Single-forest, single-domain Active Directory
- One Domain Controller (DC01)
- AD-integrated DNS and centralized DHCP
- pfSense-based network boundary and egress control
- Role-based access control via groups
- Baseline Group Policy enforcement
- Identity-centric logging and audit strategy
- Documented risks, assumptions, and controls

This establishes a **stable identity core**.

---

## Phase 1: Resilience and Redundancy

### Objectives
- Reduce single points of failure
- Improve availability of identity services

### Planned Enhancements
- Deploy a second Domain Controller (DC02)
- Validate replication and FSMO role placement
- Introduce basic service monitoring

### Security Value
- Increased identity resilience
- Improved fault tolerance
- More realistic enterprise identity topology

---

## Phase 2: Administrative Hardening

### Objectives
- Strengthen protection of privileged identities
- Reduce credential exposure risk

### Planned Enhancements
- Enforce administrative tiering with technical controls
- Introduce dedicated administrative workstations
- Apply stricter logon restrictions for Tier 0 accounts

### Security Value
- Reduced lateral movement risk
- Clear separation of privilege levels
- Stronger identity security posture

---

## Phase 3: Logging and Detection Maturity

### Objectives
- Improve visibility and detection capability
- Enable proactive security monitoring

### Planned Enhancements
- Centralize logs into a SIEM
- Correlate identity, endpoint, and firewall events
- Implement alerting for high-risk identity activity

### Security Value
- Faster incident detection
- Improved forensic capability
- Support for security operations workflows

---

## Phase 4: Network Segmentation and Control

### Objectives
- Reduce lateral movement opportunities
- Improve internal traffic control

### Planned Enhancements
- Introduce additional internal subnets
- Apply inter-subnet firewall rules
- Enforce egress filtering policies

### Security Value
- Smaller blast radius from compromise
- Improved defense-in-depth
- Better alignment with Zero Trust principles

---

## Phase 5: Identity Governance and Access Review

### Objectives
- Formalize access review and lifecycle management
- Improve authorization governance

### Planned Enhancements
- Document recurring access review processes
- Introduce privileged access workflows
- Align on-prem RBAC with cloud identity models

### Security Value
- Reduced privilege creep
- Improved audit readiness
- Stronger identity governance

---

## Phase 6: Hybrid and Cloud Integration (Optional)

### Objectives
- Extend identity controls beyond on-premises
- Align with modern enterprise identity architectures

### Planned Enhancements
- Hybrid identity integration
- Cloud-based access reviews
- Unified RBAC and logging models

### Security Value
- Consistent identity governance across environments
- Improved scalability
- Future-proofed identity design

---

## Guiding Principles for Growth

Future changes should:
- Preserve clear trust boundaries
- Maintain separation of concerns
- Be driven by security or operational need
- Be documented and validated

Complexity is introduced **only when justified**.

---

## Summary

The roadmap defines a **measured progression** from:
- Foundational identity services
- To resilient, governed, and monitored identity infrastructure

This approach mirrors how enterprise environments mature over time.
