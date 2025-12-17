# Validation Tests

## Purpose

This document maps **acceptance criteria to concrete validation tests**.

Each test:
- States what is being validated
- Identifies how validation is performed
- References authoritative evidence

---

## Test 1: Client Network Configuration

**Objective:**  
Validate DHCP, DNS, and gateway configuration on Client1.

**Method:**  
Run `ipconfig /all` on Client1.

**Expected Result:**  
- IP address within internal scope  
- DNS server = DC01  
- Default gateway = Edge-FW01  

**Evidence:**  
[`/evidence/clients/ipconfig-all-client1.txt`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Evidence/Clients/ipconfig-all-client1.txt)

---

## Test 2: Domain Membership and Policy Application

**Objective:**  
Validate domain join and Group Policy application.

**Method:**  
Generate Resultant Set of Policy (RSoP).

**Expected Result:**  
- Domain policies applied
- No errors in policy processing

**Evidence:**  
[`/evidence/clients/gpresult-client1.html`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Evidence/Clients/gpresult-client1.html)

---

## Test 3: Identity Context Verification

**Objective:**  
Confirm authentication context is domain-based.

**Method:**  
Run `whoami` as logged-in user.

**Expected Result:**  
- Output reflects domain identity

**Evidence:**  
[`/evidence/clients/whoami-client1.txt`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Evidence/Clients/whoami-client1.txt)

---

## Test 4: Domain Membership Confirmation

**Objective:**  
Visually confirm system is domain-joined.

**Method:**  
Review system properties.

**Expected Result:**  
- Domain = `ad.enterprise.lab`

**Evidence:**  
[`/evidence/clients/system-domain-membership-client1.png`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Evidence/Clients/system-domain-membership-client1.png)

---

## Test 5: DHCP Scope and Options

**Objective:**  
Validate DHCP scope and delivery of options.

**Method:**  
Review DHCP Manager configuration.

**Expected Result:**  
- Correct scope range
- Correct router and DNS options

**Evidence:**  
- [`/evidence/dhcp/dhcp-scope-dc01.png`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Evidence/DHCP/dhcp-scope-dc01.png)
- [`/evidence/dhcp/dhcp-options-dc01.png`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Evidence/DHCP/dhcp-options-dc01.png)

---

## Test 6: Network Boundary Enforcement

**Objective:**  
Confirm firewall is enforcing internal/external boundary.

**Method:**  
Review firewall configuration.

**Expected Result:**  
- LAN/WAN correctly assigned
- Outbound NAT enabled
- No inbound exposure

**Evidence:**  
- [`/evidence/firewall/interfaces-edge-fw01.png`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Evidence/Firewall/interfaces-edge-fw01.png)
- [`/evidence/firewall/nat-outbound.png`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Evidence/Firewall/nat-outbound.png)
- [`/evidence/firewall/firewall-rules-lan.png`](https://github.com/williamolega/Enterprise-Active-Directory-Network-Infrastructure-Lab-Windows-Server-2022-VMware-/blob/main/Evidence/Firewall/firewall-rules-lan.png)

---

## Summary

These tests collectively validate that the environment meets all defined acceptance criteria and architectural intent.

