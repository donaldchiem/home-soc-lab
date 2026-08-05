# Threat Model

## Purpose

This document defines the threat model for the Home Security Operations Center (SOC) Lab. It identifies the assets being protected, potential adversaries, attack vectors, security assumptions, logging requirements, and detection priorities that will guide the design and operation of the lab.

---

## Protected Assets

- Windows 11 virtual machine
- Ubuntu SOC workstation
- Splunk Enterprise
- Splunk Universal Forwarder
- Sysmon telemetry
- Windows Event Logs
- Detection rules
- Investigation documentation
- Configuration files
- GitHub repository

---

## Security Objectives

- Protect the integrity of collected security logs.
- Detect malicious activity as early as possible.
- Maintain an isolated lab environment.
- Produce reliable security telemetry for analysis.
- Document all configurations and investigations.

---

## Potential Threat Actors

- External attackers
- Malware operators
- Insider threats
- Script kiddies
- Ransomware operators

---

## Likely Attacker Goals

- Gain unauthorized access
- Execute malicious code
- Establish persistence
- Escalate privileges
- Disable logging
- Exfiltrate data
- Evade detection

---

## Entry Points

- Remote services
- Web downloads
- Email attachments
- PowerShell
- User execution
- Removable media

---

## Attack Surface

- Windows operating system
- PowerShell
- Network services
- Installed applications
- User accounts
- Virtual networking

---

## Trust Boundaries

- Host operating system
- Virtual machines
- Internal virtual network
- GitHub repository

---

## Security Assumptions

- The lab remains isolated from production systems.
- Only authorized software is installed.
- Logging remains enabled.
- Snapshots are available for recovery.
- Administrative access is controlled.

---

## Expected Attack Techniques

- Phishing
- PowerShell abuse
- Credential access
- Persistence
- Privilege escalation
- Defense evasion
- Command and scripting interpreter

---

## Logging Requirements

- Windows Event Logs
- Sysmon
- PowerShell Logging
- Splunk Universal Forwarder
- Splunk Enterprise

---

## Detection Priorities

- PowerShell execution
- Failed logon attempts
- Privilege escalation
- Persistence mechanisms
- Suspicious process creation
- Defense evasion activity

---

## Known Limitations

- Single-host lab environment
- Limited hardware resources
- Simulated attack scenarios only
- No production traffic
- Limited number of endpoints

---

## Revision History

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-08-05 | Initial threat model created |