# Threat Hunt Template

## Hunt Information

| Field | Value |
|-------|-------|
| Hunt Name | |
| Hunt ID | HUNT-001 |
| Author | |
| Date Created | |
| Last Updated | |
| Status | Planned / In Progress / Complete |
| Priority | Low / Medium / High |

---

## Hunt Overview

Provide a brief description of the threat hunt, including its objective and why it is being conducted.

---

## Hunt Hypothesis

State the hypothesis being tested.

Example:

> If an attacker executed PowerShell with encoded commands, evidence should exist within PowerShell operational logs and Sysmon process creation events.

---

## Threat Intelligence

Document any threat intelligence, reports, IOCs, or attacker techniques that motivated this hunt.

---

## MITRE ATT&CK Mapping

| Tactic | Technique | Technique ID |
|---------|-----------|--------------|
| | | |

---

## Scope

Define what systems, users, endpoints, logs, or time periods are included in the hunt.

---

## Data Sources

- Windows Event Logs
- Sysmon
- PowerShell Logs
- Splunk
- Other

---

## Hunt Methodology

Describe the investigative approach used during the hunt.

---

## Splunk SPL Queries

```spl
# Query 1
```

```spl
# Query 2
```

(Add additional queries as needed.)

---

## Hunt Findings

Document all relevant findings.

- Finding 1
- Finding 2

---

## Indicators of Compromise (IOCs)

Document any discovered indicators.

- IP Address
- Domain
- Hash
- Process
- Registry Key
- File Path
- User Account

---

## Validation

Describe how findings were verified.

### Validation Checklist

- [ ] Hunt completed
- [ ] Queries validated
- [ ] Findings confirmed
- [ ] False positives reviewed

---

## Recommended Actions

Document recommended follow-up actions.

Example:

- Create a new detection
- Investigate affected endpoint
- Block malicious IP
- Reset compromised account
- Escalate incident

---

## Evidence

### Screenshots

- Screenshot 1
- Screenshot 2

### Relevant Logs

```text
Paste relevant logs here.
```

---

## Lessons Learned

Document improvements, observations, or ideas for future hunts.

---

## References

- MITRE ATT&CK
- Threat Intelligence Reports
- Microsoft Documentation
- Splunk Documentation
- Additional References

---

## Revision History

| Version | Date | Description |
|---------|------|-------------|
| 0.1 | | Initial document |