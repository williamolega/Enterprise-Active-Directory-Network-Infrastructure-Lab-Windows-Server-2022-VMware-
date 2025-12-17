# Architecture Overview

## Purpose

This document describes the **high-level architecture** of the Enterprise Active Directory Network Infrastructure Lab.

The objective of this architecture is to:
- Establish a secure and isolated identity environment
- Enforce clear trust boundaries between systems
- Separate identity services from network security functions
- Reflect real-world enterprise design principles rather than lab shortcuts

This architecture is intentionally simple, controlled, and extensible.

---

## Architectural Principles

The design follows these guiding principles:

- **Identity is a protected control plane**
- **Network boundaries are explicit and enforced**
- **Separation of concerns is maintained**
- **Single points of trust are clearly defined**
- **Complexity is introduced only when justified**

These principles inform all design decisions in this lab.

---

## High-Level Architecture

The environment is composed of the following core components:

- **Hypervisor Layer:** VMware Workstation
- **Network Boundary:** pfSense (Edge-FW01)
- **Identity Services:** Active Directory (DC01)
- **Client Systems:** Domain-joined workstations (Client1)

Each component has a distinct responsibility and trust level.

---

## Network Architecture

### Internal Network

- **Network:** VMnet2 (Host-only)
- **Purpose:** Trusted internal enterprise network
- **Scope:** Identity services and domain-joined clients

Characteristics:
- No direct host or internet access
- DHCP disabled at the hypervisor layer
- All traffic destined for external networks must traverse the firewall

---

### External Network

- **Network:** VMnet8 (NAT)
- **Purpose:** Controlled internet egress
- **Scope:** Firewall WAN interface only

Characteristics:
- Provides outbound connectivity
- Prevents inbound exposure of internal systems
- Acts as the untrusted network boundary

---

## Network Boundary Enforcement

**Edge-FW01 (pfSense)** serves as the sole boundary device:

- Connected to both internal and external networks
- Performs routing and NAT
- Enforces firewall policy
- Acts as the default gateway for internal systems

Identity systems do not perform routing, NAT, or boundary enforcement.

---

## Identity Architecture

### Active Directory

- **Forest and Domain:** Single forest, single domain (`ad.enterprise.lab`)
- **Domain Controller:** DC01 (Windows Server 2022)

Responsibilities:
- Authentication and authorization
- Directory services
- AD-integrated DNS
- Centralized DHCP

Key design decisions:
- Domain Controller is never internet-facing
- DNS resolution for DC01 uses loopback (`127.0.0.1`)
- Identity services are isolated from network security functions

---

## Client Architecture

**Client1** represents a standard domain-joined workstation:

- Receives IP configuration via DHCP
- Uses DC01 as its DNS resolver
- Authenticates and authorizes through Active Directory
- Does not perform infrastructure or security functions

Clients consume identity services but do not provide them.

---

## Trust Boundaries

The architecture enforces multiple trust boundaries:

- External network → Firewall
- Firewall → Internal network
- Internal network → Identity services

Each boundary is explicit and enforced through configuration rather than assumption.

---

## Validation and Evidence

Architectural claims are validated through:
- System configuration evidence
- Command output artifacts
- Targeted screenshots where visual proof adds value

All evidence is stored separately in the [`/evidence`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/tree/main/Evidence) directory and referenced during validation.

---

## Scalability and Future State

This architecture supports future enhancements including:
- Additional Domain Controllers
- Administrative tiering enforcement
- Centralized logging and detection
- Network segmentation
- Hybrid identity integration

The architecture is designed to evolve without fundamental redesign.

---

## Summary

This architecture prioritizes:
- Identity security over convenience
- Clear trust boundaries over implicit access
- Enterprise-aligned design over lab shortcuts

The result is a clean, defensible foundation for identity and security experimentation.

