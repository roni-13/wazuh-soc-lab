# Wazuh Architecture

## Overview

This lab uses Wazuh as a centralized security monitoring and detection platform.

The environment consists of a Windows endpoint, Wazuh Server/Manager, Wazuh Indexer, and Wazuh Dashboard.

## Architecture

```text
Windows Endpoint
      |
      | Security Events / Sysmon / Logs
      v
Wazuh Agent
      |
      v
Wazuh Manager
      |
      +---- Decoders
      |
      +---- Detection Rules
      |
      +---- Active Response
      |
      v
Wazuh Indexer
      |
      v
Wazuh Dashboard
```

## Components

### Wazuh Agent

The Wazuh Agent is installed on the monitored Windows endpoint.

It collects security-relevant telemetry such as:

* Windows Event Logs
* Sysmon events
* Authentication events
* Process creation events
* File integrity events

The collected data is securely forwarded to the Wazuh Manager.

### Wazuh Manager

The Wazuh Manager is responsible for processing and analyzing events received from agents.

Key functions used in this lab include:

* Log analysis
* Decoding
* Detection rules
* Alert generation
* Custom rule creation
* Active Response

### Wazuh Indexer

The Wazuh Indexer stores security events and alerts so they can be searched and investigated.

### Wazuh Dashboard

The Wazuh Dashboard provides the interface used for:

* Alert monitoring
* Event investigation
* Agent monitoring
* Security analysis
* Detection validation

## Lab Environment

| Component       | Role                                  |
| --------------- | ------------------------------------- |
| Windows 10      | Monitored endpoint                    |
| Wazuh Agent     | Endpoint telemetry collection         |
| Wazuh Manager   | Detection and alert processing        |
| Wazuh Indexer   | Event and alert storage               |
| Wazuh Dashboard | Security monitoring and investigation |
| Sysmon          | Detailed Windows process telemetry    |

## Detection Flow

A typical detection in this lab follows this workflow:

```text
Windows Event / Sysmon Event
            |
            v
       Wazuh Agent
            |
            v
      Wazuh Manager
            |
            v
     Decoder / Rule
            |
            v
          Alert
            |
            v
 Investigation / Response
```

For selected detections, Active Response can automatically take action after the configured detection threshold is reached.

## Detection Use Cases

This portfolio demonstrates the following SOC-relevant detections:

* Windows failed logon detection — Event ID 4625
* Windows failed-login brute-force detection
* SSH brute-force detection
* Automated source IP blocking using Active Response
* PowerShell process detection using Sysmon
* MITRE ATT&CK mapping for PowerShell activity

## SOC Workflow

The lab follows a practical SOC investigation workflow:

```text
Detection
   ↓
Triage
   ↓
Investigation
   ↓
Containment
   ↓
Response
   ↓
Documentation
```

The purpose of this architecture is to demonstrate how endpoint telemetry can be centrally collected, analyzed, detected, investigated, and responded to using Wazuh.
