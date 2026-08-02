# Investigation Timeline

| Time | Activity | Evidence |
|------|----------|----------|
| 09:00 | Verified Wazuh agent connectivity | agent_control |
| 09:05 | Opened Windows Firewall Console | wf.msc |
| 09:10 | Created test firewall rule | Firewall Console |
| 09:15 | Modified firewall rule | Firewall Console |
| 09:20 | Deleted firewall rule | Firewall Console |
| 09:25 | Reviewed Event Viewer | Firewall Operational Log |
| 09:30 | Validated using PowerShell | Get-NetFirewallRule |
| 09:35 | Investigated Wazuh Discover | Discover |
| 09:40 | Correlated findings | Documentation |

---

# Investigation Flow

Investigation Started

↓

Verified Agent Health

↓

Opened Firewall Console

↓

Created Firewall Rule

↓

Modified Firewall Rule

↓

Deleted Firewall Rule

↓

Reviewed Event Viewer

↓

Validated Using PowerShell

↓

Investigated Wazuh Discover

↓

Correlated Evidence

↓

Investigation Completed

---

# Summary

The investigation reconstructed Windows Firewall rule activity using native Windows Firewall logs and Wazuh Discover. Firewall rule creation, modification, and deletion were validated using Event Viewer and PowerShell while demonstrating the importance of verifying endpoint logging before relying on SIEM evidence.
