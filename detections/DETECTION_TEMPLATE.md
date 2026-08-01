# Detection Template

## Detection Information

| Field | Value |
|-------|-------|
| Detection Name | |
| Detection ID | DET-001 |
| Author | |
| Date Created | |
| Last Updated | |
| Status | Draft / Testing / Active / Deprecated |
| Severity | Low / Medium / High / Critical |

---

## Overview

Provide a brief summary of what this detection identifies, why it matters, and when it should trigger.

---

## Threat Description

Describe the attacker behavior or technique this detection is designed to identify.

---

## MITRE ATT&CK Mapping

| Tactic | Technique | Technique ID |
|---------|-----------|--------------|
| | | |

---

## Detection Coverage

Describe what this detection covers, what it does not cover, and any assumptions or dependencies.

---

## Data Sources

- Windows Event Logs
- Sysmon
- PowerShell Logs
- Splunk Indexes
- Other

---

## Detection Logic

Describe the logic used to identify suspicious activity.

---

## Splunk SPL Query

```spl
# Insert query here
```

---

## Expected Results

Describe what should be returned when the detection successfully triggers.

---

## Risk Assessment

| Category | Value |
|----------|-------|
| Impact | |
| Likelihood | |
| Priority | |

---

## False Positives

Describe situations where legitimate activity may trigger this detection.

---

## False Negatives

Describe situations where malicious activity could evade this detection.

---

## Validation

Describe how the detection was tested.

### Test Procedure

1.
2.
3.

### Validation Checklist

- [ ] Detection triggered successfully
- [ ] Expected logs collected
- [ ] No unexpected behavior
- [ ] Results verified

---

## Detection Tuning

Document improvements made to reduce false positives or improve detection accuracy.

---

## Incident Response Guidance

Describe the recommended analyst actions after this detection triggers.

Example:

- Validate the alert
- Identify the affected host
- Review related events
- Determine scope
- Escalate if necessary

---

## Evidence

### Screenshots

- Screenshot 1
- Screenshot 2

### Sample Logs

```text
Paste relevant log samples here.
```

---

## Security Impact

Describe the potential impact if this activity is malicious.

---

## Limitations

Describe any known weaknesses or assumptions of the detection.

---

## Lessons Learned

Document observations, improvements, and future enhancements.

---

## References

- MITRE ATT&CK
- Microsoft Documentation
- Splunk Documentation
- Additional references

---

## Revision History

| Version | Date | Description |
|---------|------|-------------|
| 0.1 | | Initial document |