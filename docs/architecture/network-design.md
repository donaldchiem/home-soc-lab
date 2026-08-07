# SOC Network Design

## Purpose

This document defines the planned network architecture for the Home Security Operations Center (SOC) Lab. The network is designed to allow controlled communication between authorized lab systems while isolating simulated attack traffic from production systems and external networks.

---

## Network Design

The lab will use a dedicated **VirtualBox Host-Only Network** as its primary internal network.

This network allows:

- Communication between the host computer and lab virtual machines
- Communication between lab virtual machines
- Controlled Windows-to-Splunk log forwarding
- Controlled Kali-to-Windows attack simulation
- Isolation from the public Internet by default

A secondary **NAT adapter** may be enabled temporarily when a virtual machine requires Internet access for operating system updates, package installation, or trusted software downloads.

The NAT adapter should be disabled during attack simulations whenever Internet connectivity is not required.

---

## Planned Network Configuration

| System | Interface / Adapter | Network Type | Planned IP Address | Subnet | Default Gateway | Purpose |
|--------|---------------------|--------------|--------------------|--------|-----------------|---------|
| Windows Host | VirtualBox Host-Only Interface | Host-Only | 192.168.56.1 | 192.168.56.0/24 | N/A | Host management and VM communication |
| Windows 11 VM | Adapter 1 | Host-Only | 192.168.56.10 | 192.168.56.0/24 | None | Monitored endpoint and log source |
| Kali Linux VM | Adapter 1 | Host-Only | 192.168.56.20 | 192.168.56.0/24 | None | Authorized attack simulation |
| Ubuntu SOC VM | Adapter 1 | Host-Only | 192.168.56.30 | 192.168.56.0/24 | None | SOC workstation and Splunk access |
| Lab VMs when updates are required | Adapter 2 | NAT | DHCP | VirtualBox NAT | VirtualBox NAT Gateway | Temporary Internet access |

> IP addresses are planned values and will be validated during the infrastructure milestones before being treated as deployed configuration.

---

## Network Components

### Windows 11 VM

- Primary monitored endpoint
- Receives authorized attack traffic from the Kali Linux VM
- Generates Windows Event Logs, Sysmon telemetry, and PowerShell logs
- Runs the Splunk Universal Forwarder
- Sends security telemetry to Splunk Enterprise
- Uses the Host-Only network for lab communication

### Kali Linux VM

- Generates authorized attack traffic
- Communicates with the Windows 11 VM during controlled simulations
- Operates only against systems explicitly included in the isolated lab
- Uses the Host-Only network during attack simulations

### Ubuntu SOC VM

- Primary SOC analyst workstation
- Provides analyst access to Splunk Enterprise
- Supports searches, detections, threat hunts, and investigations
- Uses the Host-Only network for SOC communication

### Splunk Enterprise

- Central SIEM platform
- Receives telemetry forwarded from the Windows 11 VM
- Provides centralized searching, detection, dashboards, and investigation capabilities
- Is accessible from the Ubuntu SOC workstation through the isolated lab network

### Windows Host

- Runs Oracle VirtualBox
- Provides the Host-Only network interface
- Can communicate with lab systems for administration and troubleshooting
- Does not intentionally route simulated attack traffic to external networks

---

## Communication Paths

### Kali-to-Windows Traffic

```text
Kali Linux VM
      |
      | Authorized Attack Traffic
      v
Windows 11 VM
```

This path generates controlled malicious or suspicious behavior exclusively within the lab.

### Windows-to-Splunk Log Flow

```text
Windows Event Logs
Sysmon
PowerShell Logs
      |
      v
Splunk Universal Forwarder
      |
      | Log Forwarding
      v
Splunk Enterprise
```

This path transports endpoint telemetry to the SIEM for searching, detection, and investigation.

### Analyst Investigation Flow

```text
Ubuntu SOC VM
      |
      | Analyst Access
      v
Splunk Enterprise
```

The analyst uses Splunk Enterprise to review telemetry, validate detections, perform threat hunts, and investigate simulated incidents.

### Host-to-VM Communication

```text
Windows Host
      |
      | Host-Only Network
      v
Lab Virtual Machines
```

Host-to-VM communication is available for administration and troubleshooting without exposing the lab directly to the external network.

---

## Isolation Boundaries

The **Host-Only network** is the primary security boundary for the lab.

```text
                Internet
                   ^
                   |
            Temporary NAT
             when required
                   |
+------------------------------------------+
|          Isolated Lab Boundary           |
|                                          |
|  Kali VM <------> Windows 11 VM          |
|                       |                  |
|                       v                  |
|               Splunk Enterprise          |
|                       ^                  |
|                       |                  |
|                 Ubuntu SOC VM            |
|                                          |
+------------------------------------------+
                   ^
                   |
             Windows Host
```

During attack simulations, systems should communicate through the Host-Only network and unnecessary NAT connectivity should be disabled.

---

## Internet Access Decision

Internet access is **not required for normal attack simulation or SOC monitoring activities**.

NAT connectivity may be temporarily enabled for:

- Operating system updates
- Trusted package installation
- Security tool installation
- Vendor documentation access
- Required software downloads

After required Internet-dependent tasks are completed, NAT connectivity should be disabled when practical before conducting attack simulations.

---

## Security Considerations

- All attack simulations must remain inside the authorized lab environment.
- Kali Linux must never be used to attack public, school, workplace, or unauthorized systems.
- Host-Only networking is preferred for attack simulations because it prevents direct Internet access by default.
- NAT should only be enabled when Internet connectivity is required.
- Lab services should not be exposed through unnecessary port forwarding.
- Bridged networking should not be used for attack simulations because it would place the VMs directly onto the physical network.
- VM snapshots should be created before significant attack simulations or major configuration changes.
- Network configuration must be validated before offensive simulations begin.

---

## Why This Design Is Suitable

This design provides the communication required for a functioning SOC while maintaining clear isolation boundaries.

The Host-Only network allows the Windows endpoint, Kali attack system, Ubuntu SOC workstation, Splunk Enterprise, and the physical host to communicate without placing simulated attack traffic directly onto the home or public network.

Temporary NAT connectivity provides a controlled method for downloading updates and trusted software without making Internet access a permanent dependency of the lab.

This approach balances:

- Lab isolation
- Required system communication
- Administrative accessibility
- Safe attack simulation
- Log forwarding
- Analyst investigation
- Ease of recovery and troubleshooting

---

## Validation Plan

The planned network will be validated during the infrastructure phase by verifying:

- Host-to-VM connectivity
- Windows VM connectivity
- Kali Linux VM connectivity
- Ubuntu SOC VM connectivity
- Windows-to-Splunk communication
- Kali-to-Windows test traffic
- Correct IP addressing
- Name resolution when applicable
- Isolation from unintended systems
- Temporary Internet access when NAT is enabled
- Recovery using VirtualBox snapshots

Actual addresses and configuration results will be updated after deployment and validation.

---

## Revision History

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-08-07 | Initial SOC network design |  