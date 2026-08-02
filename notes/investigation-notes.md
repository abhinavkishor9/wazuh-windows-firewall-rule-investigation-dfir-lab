# Investigation Notes

## Lab Summary

This investigation focused on analyzing Windows Firewall rule activity using native Windows logging and Wazuh Discover.

The investigation reconstructed firewall configuration changes by correlating Windows Firewall logs, Event Viewer, PowerShell, and Wazuh while validating endpoint logging.

---

## Analyst Methodology

1. Verify Wazuh agent connectivity.
2. Create a firewall rule.
3. Modify the firewall rule.
4. Delete the firewall rule.
5. Review Windows Firewall logs.
6. Validate events using PowerShell.
7. Investigate Wazuh Discover.
8. Correlate evidence.
9. Document findings.

---

## Investigation Scenario

A Windows firewall rule was created, modified, and removed.

The investigation aimed to determine:

- Whether firewall rule activity generated Windows events.
- Which logs recorded the activity.
- Whether Wazuh collected the events.
- Why expected events might not appear.

---

## Evidence Collected

### Evidence 1 – Firewall Rule

Collected:

- Test firewall rule

Finding:

Verified successful creation, modification, and deletion of the rule.

---

### Evidence 2 – Event Viewer

Collected:

- Windows Firewall Operational logs

Finding:

Reviewed native Windows logging for firewall activity.

---

### Evidence 3 – PowerShell Validation

Command Used

```powershell
Get-NetFirewallRule | Where-Object {$_.DisplayName -like "*DFIR*"}
```

Finding:

Validated firewall rule existence before deletion.

---

### Evidence 4 – Firewall Operational Log

Command Used

```powershell
Get-WinEvent -LogName "Microsoft-Windows-Windows Firewall With Advanced Security/Firewall" -MaxEvents 20
```

Finding:

Validated whether Windows generated firewall events.

---

### Evidence 5 – Wazuh Discover

Collected:

- Firewall-related searches

Finding:

Verified centralized collection of firewall activity.

---

## DFIR Analysis

The investigation demonstrated that firewall configuration changes can be investigated using native Windows logs and Wazuh Discover. Endpoint logging should always be validated before assuming SIEM collection failures.

---

## MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|----|
| Defense Evasion | Disable or Modify System Firewall | T1562.004 |
| Command and Control | Application Layer Protocol (Contextual) | T1071 |

---

## Analyst Observations

- Firewall rules are valuable forensic artifacts.
- Event Viewer remains the primary Windows evidence source.
- PowerShell rapidly validates firewall configuration.
- Wazuh only collects Windows-generated events.
- Firewall Operational logging varies across Windows configurations.

---

## Conclusion

This investigation demonstrated how Windows Firewall rule activity can be analyzed using native Windows logging and Wazuh Discover while emphasizing endpoint log validation before SIEM troubleshooting.
