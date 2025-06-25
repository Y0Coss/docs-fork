---
title: Dedicated Servers 3-AZ Reversibility Policy
updated: 2025-06-24
---

## Objective

This document is the reversibility policy for the Dedicated Servers 3AZ product range.

This policy aims at implementing the global reversibility principles and requirements of SWIPO IaaS Code of Conduct for Cloud Providers.

## List of features

Dedicated Servers features are divided into three categories:

1. **Core features** for which we guarantee migration capacity.
1. **OVHcloud implementations** that require adaptation to a new migration environment.
1. **Specific features** that cannot be guaranteed for migration as they are related to the OVHcloud environment or involve custom developments.

### 1 - Core features 

| **Feature** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
|---|-----|---|-----|-----|
|Supplying dedicated servers|Supplying different ranges of high-performance dedicated servers|N/A|**Inbound migration**: Order a dedicated server in the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB), backup and migrate data, re-install software (or use automated installation).<br><br>**Outbound migration**: Order dedicated servers, backup and migrate data, re-install software|[Getting started with a dedicated server](/pages/bare_metal_cloud/dedicated_servers/getting-started-with-dedicated-server)|
|Backup storage|Backup storage delivered by default with every dedicated server|NFS/CIFS/FTP|**Inbound migration**: Migrate data on your dedicated servers and activate backup storage on those servers through the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB).<br><br>**Outbound migration**: enable access from outside your account through OVHcloud API, then migrate data using standard file transfer protocols, such as FTP.|[Using backup storage on a dedicated server](/pages/bare_metal_cloud/dedicated_servers/services_backup_storage)|
|Operating systems and software installed on dedicated server|Automatically install operating systems, databases, administration interfaces and virtualization software on a new dedicated server.<br>See [here](https://www.ovhcloud.com/en-gb/bare-metal/os/) the complete list.|For customized images used with "bring your own image": <br>- Boot type: **uefi** or **legacy**<br>- Partition type: **MBR** or **GPT**<br>- Image format: **qcow2** or **raw**|**Inbound migration**: Order dedicated servers and choose operating systems/software to install on the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB). Alternatively, use the"bring your own image" feature to install customized images.<br><br>**Outbound migration**: Export your image and install on another dedicated server.|[Installing or reinstalling your dedicated server](/pages/bare_metal_cloud/dedicated_servers/getting-started-with-dedicated-server#installing-or-reinstalling-your-dedicated-server)<br><br>[How to use the Bring Your Own Image feature](/pages/bare_metal_cloud/dedicated_servers/bring-your-own-image)|
| Bring Your Own IP | Allows the customer to import their own public IPv4 address ranges (from /24 to /19) into the OVHcloud infrastructure.| Public IP adresses registred in RIR | **Inbound migration**: Import using OVHcloud Control Panel after checking IPs ownership and reputation  <br> **Inbound migration**: IPs remain the property of the client and can be removed at any time, guaranteeing full reversibility | [How to use the Bring Your Own IP feature](/pages/network/bring_your_own_ip/bring-your-own-IP) |

### 2 - OVHcloud implementations

| **Feature** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
|---|-----|---|-----|-----|
|Floating IPs|Additional IP that can be switched from one service to another in the same datacenter.|IPv4, IPv6|**Inbound migration**: Plan the network architecture, configure the Floating IPs in the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB) or through OVHcloud API.<br><br>**Outbound migration**: Record the configured setup in the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.co.uk/&ovhSubsidiary=GB) and configure a similar setup at another provider.|[Moving an Additional IP](/pages/bare_metal_cloud/dedicated_servers/move-failover-ip)<br><br>[Assigning a virtual MAC to an Additional IP](/pages/bare_metal_cloud/dedicated_servers/network_virtual_mac)|
|vRack|vRack, or Virtual rack, is a private VLAN technology that enables connection between OVHcloud services.|N/A|**Inbound migration**: Plan the network architecture, Add your servers to the vRack, Configure network interfaces.<br><br>**Outbound migration**: Record the network architecture and reproduce it with VLAN.|[Configuring the vRack on your dedicated servers](/pages/bare_metal_cloud/dedicated_servers/vrack_configuring_on_dedicated_server)|
| ACL, firewall, advanced security | Management of security rules, ACL, firewall | Firewall rules, scripts |**Inbound migration**: <br> Configure rules manually or with scripts of rules **Outbound migration**: Export configurations and adapt security tools in the target environement | [Network and IP section](/pages/bare_metal_cloud/dedicated_servers) |


### 3 - Specific features

| **Feature** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
|---|-----|---|-----|-----|
|Anti-DDoS|The anti-DDoS is a set of equipment and means put in place to absorb distributed denial of service attacks. It includes an analysis of traffic, the "aspiration" towards a specialized network, and mitigation, ensured by VAC technology developed by OVHcloud.|N/A|**Inbound migration**: The anti-DDoS is a component of our infrastructure, enabled by default. No action is required.<br>>**Outbound migration**: Order and configure an anti-DDoS with the new provider.|**Inbound migration**: The anti-DDoS system is part of our infrastructure and is enabled by default. No action is required. <br><br>**Outbound migration**: Order and configure an anti-DDoS solution from the new provider| [OVHcloud anti-DDoS protection](https://www.ovh.co.uk/anti-ddos/) and [Anti-DDoS Technology](https://www.ovh.co.uk/anti-ddos/anti-ddos-technology.xml) |

### List of architectures

Dedicated servers are deployed in 3 datacentres across three physically independent availability zones, several kilometers apart, with a low-latency private network and redundant power, cooling, network and security for each datacentre.
### Partner services

The OVHcloud partners concerned are listed in the [OVHcloud partners directory](/links/partner) under the "**cloud migration**" keywords.

OVHcloud also has a dedicated service: [OVHcloud Professional Services](/links/professional-services).

### Cost and fees

No additional billing is planned from OVHcloud for the migration features listed here. Service cancellation will stop billing immediately. 

### Retention of data after contract termination

OVHcloud does not store any data. Automatic or manual backups are irreversibly deleted when the contract is terminated. A manual export is required to preserve data.
