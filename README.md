# Wazuh SOC Lab

A hands-on Security Operations Center (SOC) lab built using Wazuh to practice security monitoring, detection engineering, alert investigation, and active response.

## Lab Objectives

* Monitor Windows security events
* Detect failed Windows logon attempts
* Monitor Sysmon process creation events
* Detect PowerShell activity
* Create and test custom Wazuh detection rules
* Detect SSH brute-force attempts
* Implement Active Response for automated IP blocking
* Practice alert triage and investigation
* Understand MITRE ATT&CK mapping and incident response workflows

## Architecture

The lab uses a centralized Wazuh architecture consisting of:

* Windows endpoint with Wazuh Agent
* Wazuh Manager
* Wazuh Indexer
* Wazuh Dashboard
* Sysmon for Windows process telemetry

See the detailed architecture documentation:

➡️ [Architecture](./architecture/README.md)

## Technologies Used

* Wazuh
* Windows 10
* Linux
* Sysmon
* PowerShell
* SSH
* GitHub

## Detection Scenarios

### 1. Windows Failed Logon Detection

Monitored Windows Event ID `4625` to identify failed authentication attempts.

[View Detection Details](./detections/windows-4625.md)

### 2. PowerShell Process Detection

Monitored Sysmon Event ID `1` and created a custom Wazuh rule to detect PowerShell process execution.

**MITRE ATT&CK:** `T1059.001 - PowerShell`

[View Detection Details](./detections/powershell.md)

### 3. SSH Brute-Force Detection

Configured Wazuh to detect repeated SSH authentication failures from the same source IP.

[View Detection Details](./detections/ssh-bruteforce.md)

### 4. Active Response

Implemented automated Active Response to temporarily block a source IP after repeated SSH failed login attempts.

## Custom Detection Rules

| Rule ID  | Detection            | Purpose                                     |
| -------- | -------------------- | ------------------------------------------- |
| `100016` | Windows Failed Logon | Detect Event ID 4625                        |
| `100017` | Windows Brute Force  | Correlate repeated failed logons            |
| `100020` | PowerShell Process   | Detect PowerShell process creation          |
| `100510` | SSH Brute Force      | Detect repeated SSH authentication failures |

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
```

## Skills Demonstrated

* SIEM monitoring with Wazuh
* Windows security event analysis
* Sysmon telemetry analysis
* Detection rule development
* Authentication failure investigation
* Brute-force detection
* Active Response
* PowerShell monitoring
* MITRE ATT&CK mapping
* SOC alert triage
* Incident response workflow

## Project Structure

```text
wazuh-soc-lab/
├── architecture/
│   ├── svg/
│   └── README.md
│
├── detections/
│   ├── powershell.md
│   ├── ssh-bruteforce.md
│   ├── windows-4625.md
│   └── svg/
│
└── README.md
```

## Evidence

The repository contains supporting lab evidence and architecture documentation for the demonstrated detection scenarios.

Evidence includes:

* Wazuh alerts
* Windows security events
* Sysmon process creation events
* Detection rule results
* Active Response results
* Architecture documentation

## Project Status

**Status: Completed**

This project demonstrates a practical Wazuh-based SOC monitoring and detection lab focused on Windows security monitoring, custom detection engineering, alert investigation, and automated response.
