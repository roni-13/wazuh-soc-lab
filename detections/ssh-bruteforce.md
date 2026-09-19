# SSH Brute-Force Detection

## Overview

This detection scenario monitors repeated SSH authentication failures and identifies potential brute-force activity from the same source IP.

## Data Source

- Log Source: SSH authentication logs
- SIEM: Wazuh
- Detection Rule: `100510`
- Base Rule: `5760`

## Detection Logic

The custom Wazuh rule triggers when:

- SSH failed authentication is detected
- The same source IP generates repeated failures
- At least 3 failures occur within 60 seconds

## Custom Rule

```xml
<rule id="100510" level="12" frequency="3" timeframe="60">
    <if_matched_sid>5760</if_matched_sid>
    <same_source_ip />
    <description>SSH Brute Force - Block Source IP for 60 Seconds</description>
    <group>authentication_failed,attack,</group>
</rule>
