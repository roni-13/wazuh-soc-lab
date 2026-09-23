# Active Response — Automatic IP Blocking

## Overview

This use case demonstrates Wazuh Active Response for automated containment of a source IP after repeated SSH authentication failures.

The goal is to automatically block a suspected brute-force source and reduce further unauthorized login attempts.

## Detection and Response Flow

```text id="r8k4p1"
SSH Failed Login
       ↓
Repeated Attempts
       ↓
Wazuh Rule 100510
       ↓
Active Response Triggered
       ↓
Source IP Blocked
       ↓
Temporary Containment
       ↓
Automatic Unblock
```

## Configuration

The lab uses custom Wazuh rule `100510` to detect repeated SSH authentication failures from the same source IP.

```xml
<rule id="100510" level="12" frequency="3" timeframe="60">
    <if_matched_sid>5760</if_matched_sid>
    <same_source_ip />
    <description>SSH Brute Force - Block Source IP for 60 Seconds</description>
    <group>authentication_failed,attack,</group>
</rule>
```

### Detection Threshold

| Setting            | Value              |
| ------------------ | ------------------ |
| Rule ID            | `100510`           |
| Failed attempts    | 3                  |
| Time window        | 60 seconds         |
| Source correlation | Same source IP     |
| Response           | Temporary IP block |
| Block duration     | 60 seconds         |

## Active Response

When the configured SSH brute-force threshold is reached, Wazuh triggers Active Response.

The source IP is automatically blocked for the configured period.

After the temporary block expires, the source IP is automatically unblocked.

## Validation

The response was validated by generating repeated incorrect SSH login attempts from the test source.

Expected behavior:

```text id="s7f2n4"
1st failed attempt → Authentication failure
2nd failed attempt → Authentication failure
3rd failed attempt → Brute-force detection
                         ↓
                    IP blocked
                         ↓
                    60 seconds
                         ↓
                    IP unblocked
```

## SOC Relevance

This demonstrates practical SOC capabilities including:

* Brute-force detection
* Detection threshold configuration
* Automated containment
* Source IP correlation
* Wazuh Active Response
* Temporary network blocking
* Automated recovery

## Evidence

Recommended evidence:

1. SSH failed-login events
2. Rule `100510` alert
3. Active Response execution
4. Source IP blocked
5. Source IP automatically unblocked after the configured duration

