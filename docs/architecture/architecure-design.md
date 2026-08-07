# SOC Architecture Design

## Purpose

This document defines the planned architecture of the Home Security Operations Center (SOC) Lab and illustrates how its systems, security telemetry, attack traffic, and analyst workflows interact.

---

## Core Components

### Host Machine
- Windows 11
- Runs Oracle VirtualBox
- Provides the physical resources for the virtual lab

### Windows 11 VM
- Primary monitored endpoint
- Generates Windows Event Logs
- Generates PowerShell logs
- Runs Sysmon for enhanced telemetry
- Runs Splunk Universal Forwarder

### Kali Linux VM
- Used to generate authorized attack traffic
- Provides a controlled platform for attack simulation
- Targets only systems inside the isolated lab environment

### Ubuntu SOC VM
- Primary SOC analyst workstation
- Used to access and operate the SOC environment
- Supports investigation and analysis workflows

### Splunk Enterprise
- Central SIEM platform
- Receives and indexes security telemetry
- Supports searching, detection, dashboards, threat hunting, and investigations

---

## Log Flow

Security telemetry follows this general path:

`Windows Event Logs / Sysmon / PowerShell Logs → Splunk Universal Forwarder → Splunk Enterprise → Analyst`

---

## Attack Traffic Flow

Authorized attack simulations follow this path:

`Kali Linux VM → Windows 11 VM`

Attack activity generates telemetry on the Windows endpoint, which is forwarded to Splunk for detection and investigation.

---

## Analyst Investigation Flow

The analyst workflow follows this general path:

`Ubuntu SOC VM → Splunk Enterprise → Search / Detection / Investigation`

The analyst uses Splunk to review collected telemetry, investigate suspicious activity, validate detections, and document findings.

---

## Architecture Diagram

A visual architecture diagram will be created and maintained in the `diagrams/` directory.

The diagram will represent:

- Host machine
- Oracle VirtualBox
- Windows 11 VM
- Kali Linux VM
- Ubuntu SOC VM
- Splunk Enterprise
- Splunk Universal Forwarder
- Sysmon
- Windows Event Logs
- PowerShell logs
- Log flow
- Attack traffic flow
- Analyst investigation flow

---

## Revision History

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-08-06 | Initial SOC architecture design |