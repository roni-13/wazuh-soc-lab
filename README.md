# Wazuh SOC Lab

A hands-on Security Operations Center (SOC) lab built using Wazuh to practice security monitoring, detection engineering, alert investigation, and active response.

## Lab Objectives

- Monitor Windows security events
- Detect failed Windows logon attempts
- Monitor Sysmon process creation events
- Detect PowerShell activity
- Create and test custom Wazuh detection rules
- Detect SSH brute-force attempts
- Implement Active Response for automated IP blocking
- Practice alert triage and investigation
- Understand MITRE ATT&CK mapping and incident response workflows

## Technologies Used

- Wazuh
- Windows 10
- Linux
- Sysmon
- PowerShell
- SSH
- GitHub

## Detection Scenarios

### 1. Windows Failed Logon Detection

Monitored Windows Event ID `4625` to identify failed authentication attempts.

### 2. PowerShell Process Detection

Monitored Sysmon Event ID `1` and created a custom Wazuh rule to detect PowerShell process execution.

**MITRE ATT&CK:** `T1059.001 - PowerShell`

### 3. SSH Brute-Force Detection

Configured Wazuh to detect repeated SSH authentication failures from the same source IP.

### 4. Active Response

Implemented automated Active Response to temporarily block a source IP after repeated SSH failed login attempts.

## SOC Investigation Workflow

```text
Alert
  ↓
Triage
  ↓
Investigation
  ↓
Validation
  ↓
Containment
  ↓
Recovery
  ↓
Documentation
