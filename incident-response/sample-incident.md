# Incident Response Case Study

## Incident Overview

On 15 September 2026, multiple failed VPN login attempts were detected from an external IP address targeting the corporate VPN gateway.

The activity triggered security monitoring alerts due to an abnormal number of authentication failures within a short period.

Severity: Medium

Status: Resolved

---

## Detection

Alert Source:

- FortiGate Firewall Log
- VPN Authentication Log

Observed Indicators:

- Multiple failed login attempts
- Repeated connections from a single public IP address
- Login attempts outside business hours

Source IP:

xxx.xx.xx.xx

Target Service:

SSL VPN Portal

---

## Initial Analysis

The security team reviewed firewall and authentication logs and identified:

- More than 100 failed login attempts within 15 minutes
- User accounts targeted included administrative and standard user accounts
- No successful authentication detected

Potential Risk:

- Brute Force Attack
- Credential Stuffing Attempt

---

## Containment

Immediate actions:

1. Blocked suspicious IP address on FortiGate Firewall
2. Increased monitoring of VPN authentication events
3. Notified IT Security Team
4. Verified MFA enforcement status

Firewall Action:

```text
Action: Deny
Source IP: xxx.xx.xx.xx
Service: SSL VPN
