# Asset Inventory

## Purpose

This document maintains a complete inventory of all assets used throughout the Home Security Operations Center (SOC) Lab. It serves as the authoritative reference for systems, virtual machines, applications, and infrastructure deployed during the project.

---

## Asset Inventory

| Asset Name | Hostname | Operating System | IP Address | Network Role | Purpose | Installed Security Tools | Logging Status | Data Source | Criticality | Notes |
|------------|----------|------------------|------------|--------------|---------|--------------------------|----------------|-------------|-------------|-------|
| Windows Host | TBD | Windows 11 | TBD | Host System | Hosts the entire virtual lab environment | VirtualBox | N/A | N/A | High | Physical computer |
| Ubuntu SOC VM | UbuntuSOC | Ubuntu 26.04 LTS | TBD | SOC Workstation | Primary SOC analyst workstation | None | Not Configured | N/A | High | Oracle VirtualBox virtual machine |
| Windows 11 VM | Windows11SOC | Windows 11 Pro | TBD | Monitored Endpoint | Endpoint for monitoring, logging, and attack simulation | Planned | Not Configured | Windows Event Logs (Planned) | High | Not yet deployed |
| Kali Linux VM | KaliSOC | Kali Linux | TBD | Attack Simulation | Offensive security and attack simulation platform | Planned | N/A | N/A | High | Not yet deployed |
| Oracle VirtualBox | N/A | N/A | N/A | Hypervisor | Manages all virtual machines | N/A | N/A | N/A | High | Hosts all virtual machines |

---

## Asset Status Legend

| Status | Description |
|---------|-------------|
| Planned | Asset has not yet been deployed |
| Active | Asset is deployed and operational |
| Retired | Asset is no longer in use |

---

## Revision History

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-08-04 | Initial asset inventory created |