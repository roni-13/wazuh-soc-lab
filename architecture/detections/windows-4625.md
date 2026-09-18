# Windows Failed Logon Detection

## Overview

Windows Event ID `4625` is generated when an account logon attempt fails.

This detection scenario monitors failed Windows authentication attempts through Wazuh.

## Data Source

- Operating System: Windows 10
- Event ID: `4625`
- Log Source: Windows Security Event Log
- SIEM: Wazuh

## Detection Objective

Identify repeated failed authentication attempts that may indicate:

- Brute-force activity
- Password guessing
- Unauthorized access attempts

## Investigation Points

When an alert is generated, the following information should be reviewed:

- Source IP address
- Target username
- Logon type
- Timestamp
- Workstation name
- Number of failed attempts
- Related authentication events

## SOC Investigation Workflow

```text
4625 Event
    ↓
Alert Generated
    ↓
Identify Source IP
    ↓
Review Username & Logon Type
    ↓
Check Repeated Attempts
    ↓
Determine True / False Positive
    ↓
Document Findings
