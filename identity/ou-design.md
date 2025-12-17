# Organizational Unit (OU) Design

## Purpose

This document defines the **Organizational Unit (OU) design** for the Enterprise Active Directory Network Infrastructure Lab.

The purpose of the OU structure is to:
- Provide logical organization of directory objects
- Enable scoped Group Policy application
- Support delegated administration
- Reflect enterprise best practices without unnecessary complexity

OUs are used for management and policy boundaries, not security boundaries.

---

## Design Principles

The OU design follows these guiding principles:

- OUs represent **management scope**, not departments by default
- Group Policy is applied at the **lowest reasonable OU level**
- Delegation is enabled through OU structure, not domain sprawl
- The structure should scale without requiring redesign

This avoids tightly coupling identity structure to organizational charts.

---

## Top-Level OU Structure

The domain uses a small number of **top-level OUs**, each aligned to an object type or control function:

- **Servers**
- **Workstations**
- **Users**
- **Groups**
- **Service Accounts**
- **Admin**

Default containers (e.g., `Computers`, `Users`) are not used for ongoing management.

---

## Server OU Design

### `OU=Servers`

Purpose:
- Contain all server computer accounts
- Enable server-specific Group Policy

Sub-OUs may include:
- `Domain Controllers`
- `Member Servers`

Benefits:
- Clear separation between server and client policy
- Reduced risk of misapplied GPOs
- Foundation for tiered administration

---

## Workstation OU Design

### `OU=Workstations`

Purpose:
- Contain all domain-joined client systems
- Apply workstation security baselines

Potential sub-OUs:
- `Standard Workstations`
- `Privileged Workstations` (future state)

Benefits:
- Centralized client hardening
- Clear policy scope
- Easier troubleshooting of GPO application

---

## User OU Design

### `OU=Users`

Purpose:
- Contain standard user accounts
- Enable user-scoped policies

Design notes:
- Users are not mixed with computers
- Privileged users are excluded from this OU

This separation reduces privilege creep and policy overlap.

---

## Group OU Design

### `OU=Groups`

Purpose:
- Centralize security and distribution groups
- Support clean access-control design

Groups are managed independently of users and computers to support:
- Role-based access control (RBAC)
- Least privilege
- Clear audit trails

---

## Service Accounts OU Design

### `OU=Service Accounts`

Purpose:
- Isolate non-interactive identities
- Apply stricter security controls

Design considerations:
- Strong password and lifecycle controls
- Reduced interactive logon rights
- Clear ownership and purpose documentation

---

## Administrative OU Design

### `OU=Admin`

Purpose:
- Contain privileged accounts and systems
- Support administrative tiering models

This OU is reserved for:
- Domain administrators
- Privileged service accounts
- Administrative workstations (future state)

Separation of administrative objects is critical for identity security.

---

## Group Policy Alignment

OU structure is intentionally aligned with Group Policy strategy:

- Computer policies apply to computer OUs
- User policies apply to user OUs
- High-risk policies are scoped narrowly
- Inheritance is minimized and explicit

This reduces unintended policy impact.

---

## Delegation & Future State

This OU design supports future enhancements such as:
- Delegated administration by role
- Tiered administration models
- Additional security baselines
- Hybrid or cloud-integrated identity

The structure is intentionally simple but extensible.

---

## Summary

The OU design prioritizes:
- Manageability over mirroring org charts
- Security over convenience
- Scalability over short-term optimization

This approach reflects how enterprise Active Directory environments are structured and maintained.

