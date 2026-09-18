# PowerShell Process Detection

## Overview

PowerShell process execution was monitored using Sysmon and Wazuh.

This detection helps identify PowerShell activity that may require further SOC investigation.

## Data Source

- Operating System: Windows 10
- Sysmon Event ID: `1`
- Event Type: Process Creation
- Log Source: Sysmon
- SIEM: Wazuh

## Detection Logic

A custom Wazuh rule was created to detect:

- Sysmon Event ID `1`
- PowerShell process execution
- `powershell.exe` process image

## Custom Rule

```xml
<rule id="100020" level="10">
    <field name="win.system.eventID">^1$</field>
    <field name="win.eventdata.image">(?i)powershell\.exe</field>
    <description>Custom PowerShell Process Detection</description>
    <group>windows,sysmon,powershell,process_creation,custom_detection,</group>
</rule>
