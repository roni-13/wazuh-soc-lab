# Wazuh SOC Lab Architecture

This lab demonstrates a small SOC environment using Wazuh for centralized security monitoring, detection, alert investigation, and automated response.

## Components

- Wazuh Server
- Wazuh Dashboard
- Wazuh Indexer
- Windows 10 endpoint
- Sysmon
- Kali Linux

## Monitoring Flow

```text
Windows 10 + Sysmon
        ↓
   Wazuh Agent
        ↓
   Wazuh Server
        ↓
  Wazuh Indexer
        ↓
 Wazuh Dashboard
        ↓
Alert Investigation
        ↓
Active Response
