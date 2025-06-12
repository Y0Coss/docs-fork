---
title: 'Reading and filtering NSX-T logs'
excerpt: 'Learn how to access, understand, and filter NSX-T firewall logs on your Hosted Private Cloud environment'
updated: 2025-06-12
---

## Objective

**This guide explains how to extract and analyze key information from NSX-T logs** to troubleshoot blocked traffic or monitor firewall activity on your Hosted Private Cloud.

## Requirements

- Access to the vSphere interface
- Access to NSX-T Manager or your Syslog/log aggregation system
- Basic understanding of NSX-T firewalling and network traffic

## Instructions

### Step 1: Identify useful log fields

When inspecting logs, focus on the following elements:

| Field                  | Description                                                      |
|------------------------|------------------------------------------------------------------|
| Timestamp              | Time when the event occurred                                     |
| Action                 | Whether traffic was allowed or dropped (e.g., ALLOW / DROP)      |
| Rule ID                | ID of the NSX-T rule that matched the traffic                    |
| Source IP              | Origin IP address                                                |
| Destination IP         | Target IP address                                                |
| Protocol               | Protocol used (TCP, UDP, ICMP, etc.)                             |
| Source/Destination Port| Ports involved in the connection                                 |

> **Tip:** These fields are sufficient for identifying most common connectivity issues.

### Step 2: Access the logs

#### Option 1: From NSX-T Manager

1. Log in to the **NSX Manager**
2. In the left-hand menu, navigate to the `Security`{.action} section
3. Under **Distributed Firewall**, click on the `Monitor`{.action} tab
4. Open the `Logs`{.action} view to explore real-time entries or download historical logs

#### Option 2: From a Syslog server

If NSX-T is configured to forward logs externally:

1. Connect to your Syslog or log aggregation platform
2. Filter entries using fields such as `DROP`, `ruleId`, `src`, `dst`, `proto`, or `dport`

Example log line:

DROP ruleId=101 src=192.168.1.10 dst=10.0.0.5 proto=TCP dport=443

### Step 3: Filter and analyze logs

Depending on your toolchain:

- Use `Log Insight`{.action} to create filters and dashboards
- In tools like Graylog, ELK, or Splunk, build queries to focus on dropped traffic or specific rule IDs
- From CLI exports, filter using:

```bash
grep "DROP" nsx-logs.log | awk '{print $2, $5, $7}'
```
## Go further

- [VMware NSX-T official documentation](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/index.html)
- [How to configure Syslog in NSX-T](https://kb.vmware.com/s/article/74656)

Join our [community of users](/links/community).