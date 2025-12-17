# Group Strategy

## Purpose

This document defines the **group strategy** for the Enterprise Active Directory Network Infrastructure Lab.

Groups are the primary mechanism for:
- Authorization
- Access control
- Policy scoping
- Enforcing least privilege

This strategy ensures access decisions are scalable, auditable, and separate from individual user accounts.

---

## Design Principles

The group strategy follows these core principles:

- **Users are never assigned permissions directly**
- Access is always granted via **groups**
- Groups represent **roles or access needs**, not individuals
- Group design must support **least privilege and auditability**

This mirrors real-world enterprise identity governance practices.

---

## Group Types Used

### Security Groups
Security groups are used for:
- Access control to resources
- Group Policy filtering
- Authorization decisions

They are the default and preferred group type.

---

### Distribution Groups
Distribution groups are not used for access control in this lab.

Rationale:
- They do not provide security enforcement
- Mixing distribution and security intent increases confusion

---

## Group Naming Convention

Groups follow a clear, descriptive naming standard:

`Scope-Role-Resource`


Examples:
- `DL-FS-Finance-Read`
- `GG-IT-Admins`
- `GG-Users-Standard`

Naming conventions provide:
- Immediate context
- Easier auditing
- Reduced administrative error

---

## Role-Based Access Control (RBAC)

This lab uses **Role-Based Access Control (RBAC)** principles.

- Users are assigned to groups based on **role**
- Roles determine access, not individual users
- Changes in responsibility require **group membership changes only**

RBAC reduces operational risk and simplifies access reviews.

---

## Group Nesting Strategy (AGDLP)

The following model is used where applicable:

**AGDLP**
- **A**ccounts (users)
- **G**lobal groups (roles)
- **D**omain Local groups (resources)
- **P**ermissions assigned to domain local groups

Example flow:

User → Global Group → Domain Local Group → Resource Permission


This approach:
- Separates identity from resource access
- Scales cleanly as the environment grows
- Simplifies permission auditing

---

## Global Groups

Global groups represent **roles or identity types**, such as:
- Standard users
- IT administrators
- Service operators

Characteristics:
- Contain user or computer accounts
- Do not directly hold permissions
- Can be nested into domain local groups

---

## Domain Local Groups

Domain local groups represent **resource access**, such as:
- File shares
- Application permissions
- Administrative rights

Characteristics:
- Hold permissions directly
- Contain global groups
- Are scoped to specific resources

---

## Service Account Grouping

Service accounts are:
- Isolated from standard user groups
- Assigned only the permissions required for operation
- Grouped separately to support tighter controls and auditing

Service accounts are never placed in broad or user-facing groups.

---

## Administrative Groups

Privileged access is tightly controlled:

- Administrative groups are separate from standard user groups
- Membership is limited and explicitly managed
- Supports future **tiered administration** models

This reduces privilege creep and lateral movement risk.

---

## Group Policy Integration

Groups are used to:
- Filter GPO application
- Scope administrative policies
- Target high-risk configurations

This allows policy enforcement without restructuring OUs.

---

## Security Considerations

This group strategy:
- Enforces least privilege
- Reduces identity-based attack surface
- Improves access review and auditability
- Supports Zero Trust-aligned identity practices

Permissions are always granted to **groups**, never directly to users.

---

## Scalability and Future State

This strategy supports:
- Additional applications and resources
- Centralized access reviews
- Privileged access management (PAM)
- Hybrid or cloud-integrated identity models

The structure is intentionally simple but extensible.

---

## Summary

The group strategy in this lab prioritizes:
- Role-based access over individual assignment
- Clear separation of identity and permissions
- Auditability and long-term maintainability

This approach reflects how enterprise authorization models are designed and operated.


