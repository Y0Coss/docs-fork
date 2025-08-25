---
title: 'Reading and filtering NSX-T logs'
excerpt: 'Learn how to access and filter NSX-T firewall logs to troubleshoot blocked traffic on your Hosted Private Cloud.'
updated: 2025-08-25
---

## Objective

This guide explains how to extract and analyze key information from NSX-T logs to troubleshoot blocked traffic or monitor firewall activity on your Hosted Private Cloud.

## Requirements

- Access to the vSphere interface
- Access to the [OVHcloud Control Panel](/links/manager) with NSX-T enabled, or to your Syslog/log aggregation system
- Basic understanding of NSX-T firewalling and network traffic

## Instructions

### Step 1: Identify useful log fields

When inspecting logs, focus on the following elements:

| Field          | Description                                            |
|----------------|--------------------------------------------------------|
| Timestamp      | Time when the event occurred                           |
| Action         | Whether traffic was allowed or dropped (ALLOW or DROP) |
| Rule ID        | ID of the NSX-T rule that matched the traffic          |
| Source IP      | Origin IP address                                      |
| Destination IP | Target IP address                                      |
| Protocol       | Protocol used such as TCP, UDP, or ICMP                |

> [!primary]
> The following fields are usually sufficient to identify the most common connectivity issues.

*Optional: Source and destination ports can help identify application specific issues.*

### Step 2: Access the logs

You can access NSX-T logs either directly in the OVHcloud Control Panel or through an external Syslog server if log forwarding is enabled.

#### Option 1: From the OVHcloud Control Panel

1. Log in to the [OVHcloud Control Panel](/links/manager), then access NSX-T.
2. In the left-hand menu, navigate to the `Security`{.action} section.
3. Under **Distributed Firewall**, click on the `Monitor`{.action} tab.
4. Open the `Logs`{.action} tab to explore real-time entries or download historical logs.

#### Option 2: From a Syslog server

If NSX-T is configured to forward logs externally:

1. Connect to your Syslog or log aggregation platform
2. Filter entries using fields such as `DROP`, `ruleId`, `src`, `dst`, `proto`, or `dport`

Example log lines:

```bash
ALLOW ruleId=202 src=10.0.0.15 dst=192.168.2.20 proto=UDP dport=53

DROP   ruleId=101 src=192.168.1.10 dst=10.0.0.5   proto=TCP dport=44
```

### Step 3: Filter and analyze logs

Depending on your toolchain:

- Use `Log Insight`{.action} to create filters and dashboards
- In tools like Graylog, ELK, or Splunk, build queries to focus on dropped traffic or specific rule IDs
- From CLI exports, filter using:

```bash
grep "DROP" nsx-logs.log | awk '{print $1, $3, $5, $7}'
```
## Go further

- [VMware NSX-T official documentation](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/index.html)
- [How to configure Syslog in NSX-T](https://kb.vmware.com/s/article/74656)

If you require training or technical assistance in implementing our solutions, contact your sales representative or [click here](/links/professional-services) for a quote and request a custom analysis of your project from our Professional Services team experts.

Ask questions, give your feedback and interact directly with the team building our Hosted Private Cloud services on the dedicated [Discord channel](https://discord.gg/ovhcloud).

Join our [community of users](/links/community).