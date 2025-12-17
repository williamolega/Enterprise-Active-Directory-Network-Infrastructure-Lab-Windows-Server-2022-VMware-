# Logging and Audit Strategy

## Purpose

This document defines the **logging and audit strategy** for the Enterprise Active Directory Network Infrastructure Lab.

The goal is to:
- Provide visibility into identity-related activity
- Support incident investigation and access review
- Establish an auditable security baseline
- Reflect enterprise detection and governance practices

Logging is treated as a **security control**, not an afterthought.

---

## Logging Philosophy

The logging strategy follows these principles:

- **Identity events are security events**
- Logs must be centralized and consistent
- Signal is prioritized over volume
- Logging should support both **detection and review**

Logs exist to answer:
- Who authenticated?
- What changed?
- When did it happen?
- Was it authorized?

---

## Scope of Logging

Logging focuses on **identity-centric activity**, including:
- Authentication and authorization
- Account lifecycle events
- Privilege and group membership changes
- Policy and configuration changes

This aligns logging with the highest-risk control plane.

---

## Domain Controller Logging

### Objectives
- Detect unauthorized access attempts
- Monitor changes to identity objects
- Provide forensic visibility into authentication behavior

### Key Event Categories
- Logon and logoff events
- Kerberos authentication events
- User and computer account management
- Group membership changes
- Policy changes

These events are generated primarily on **Domain Controllers**.

---

## Audit Policy Configuration

Audit policies are:
- Centrally defined via Group Policy
- Applied consistently across systems
- Enabled with both **success and failure** where appropriate

Key audit areas include:
- Account logon
- Account management
- Privilege use
- Policy change
- Directory service access

Audit configuration avoids local overrides.

---

## Client and Member Server Logging

### Objectives
- Detect endpoint-level identity misuse
- Correlate authentication behavior with user activity

Key events include:
- Interactive logons
- Failed authentication attempts
- Privilege escalation activity

Clients provide context; Domain Controllers provide authority.

---

## Evidence and Validation

Logging configuration and effectiveness are validated using:
- Event Viewer (Directory Service, Security logs)
- `gpresult` audit policy confirmation
- Sample security event exports

Evidence artifacts are stored in the [`/evidence`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/tree/main/Evidence) directory and referenced during validation.

---

## Incident and Review Use Cases

This logging strategy supports:
- Access reviews
- Identity misuse investigations
- Policy compliance verification
- Baseline drift detection

Logs are structured to support both **reactive investigation** and **proactive review**.

---

## Scalability and Future State

This design supports future enhancements such as:
- Centralized log aggregation (SIEM)
- Detection engineering and alerting
- Correlation with firewall and endpoint telemetry
- Cloud or hybrid identity logging integration

The logging strategy is intentionally extensible.

---

## Summary

The logging and audit strategy in this lab prioritizes:
- Visibility over silence
- Identity signal over noise
- Auditability over convenience

This reflects how enterprise identity logging is designed to support security operations and governance.

