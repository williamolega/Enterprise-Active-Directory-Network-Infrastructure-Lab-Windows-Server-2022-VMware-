# Role-Based Access Control (RBAC) Model

## Purpose

This document defines the **Role-Based Access Control (RBAC) model** for the Enterprise Active Directory Network Infrastructure Lab.

The purpose of RBAC is to:
- Ensure access is granted based on **job function**, not individual identity
- Enforce **least privilege**
- Simplify access reviews and audits
- Reduce operational risk from ad hoc permissions

RBAC serves as the **governance layer** between identity and permissions.

---

## RBAC Design Philosophy

The RBAC model follows these principles:

- Roles are **intentional and documented**
- Users inherit access through **role membership**
- Permissions are never assigned directly to users
- Access decisions are **reviewable and reversible**

RBAC answers the question:
 “What should someone in this role be able to do?”

---

## RBAC Components

The RBAC model is composed of four elements:

### 1. Users
- Individual identities (human or service)
- Do not hold permissions directly
- Are assigned to roles via group membership

---

### 2. Roles
- Represent job functions or operational responsibilities
- Implemented as **Global Security Groups**
- Examples:
  - `GG-IT-Admins`
  - `GG-Helpdesk`
  - `GG-Standard-Users`

Roles describe **what someone is responsible for**, not what they can access.

---

### 3. Resources
- Systems, applications, data, or services
- Protected objects that require controlled access
- Examples:
  - File shares
  - Servers
  - Administrative interfaces

Resources do not know users — they know **permissions**.

---

### 4. Permissions
- Actions that can be performed on resources
- Assigned only to **Domain Local Groups**
- Examples:
  - Read
  - Modify
  - Administer

Permissions are granted indirectly through role membership.

---

## RBAC Implementation Model

This lab implements RBAC using **AGDLP**:

User  
↓  
Global Group (Role)  
↓  
Domain Local Group (Resource Access)  
↓  
Permission

This separation ensures:
- Roles remain stable
- Resources can change without reassigning users
- Access reviews are straightforward

---

## Example RBAC Flow

**Scenario:**  
A user requires read access to a finance file share.

**Implementation:**
- User is added to: `GG-Finance-Users`
- `GG-Finance-Users` is nested into: `DL-FS-Finance-Read`
- NTFS permissions are assigned to: `DL-FS-Finance-Read`

No permissions are ever assigned directly to the user.

---

## Exception Handling

RBAC exceptions:
- Are handled via **explicit role groups**
- Are documented and reviewed
- Do not bypass the group-based model

Example:
- `GG-App-SpecialAccess`

Exceptions remain auditable and removable.

---

## RBAC and Administrative Access

Administrative roles are:
- Segmented by tier (Tier 0, Tier 1, Tier 2)
- Assigned via dedicated admin groups
- Isolated from standard user roles

RBAC supports administrative tiering without overlap.

---

## Access Reviews

RBAC enables effective access reviews by focusing on:
- Group membership, not individual permissions
- Role relevance, not historical access

Review question:
 “Should this user still be in this role?”

This aligns with both on-prem AD reviews and cloud IAM access reviews.

---

## Scalability and Future State

This RBAC model supports:
- Additional roles and resources
- Centralized access reviews
- Privileged Access Management (PAM)
- Hybrid and cloud-based RBAC extensions

The model is intentionally simple but extensible.

---

## Summary

The RBAC model in this lab ensures:
- Access is role-driven, not user-driven
- Permissions are centralized and auditable
- Identity governance scales with the environment

This reflects how enterprise authorization models are designed, enforced, and reviewed.
