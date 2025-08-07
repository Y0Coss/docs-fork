---
title: Reversibility Policy for Managed Dedicated Cloud product
updated: 2025-08-07
---

## Objective

This document describes the reversibility policy for the Managed Dedicated Cloud product covering the offer VMware on OVHcloud.

This policy aims to implement the general reversibility principles and our compliance with the SWIPO IAAS Code of Conduct for cloud providers.


## Features map

Features of the product line fall into three categories:

1. **Core features** for which we guarantee migration capacity.
2. **OVHcloud implementations** that require adaptation to a new migration environment.
3. **Specific features** that cannot be guaranteed for migration as they are related to the OVHcloud environment or involve custom developments.


## 1. Core features

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |




|Migration model|Available documentation|
|---|---|
|**Inbound migration**:<br>- Sign up for an Hosted Private Cloud project<br>-Order the appropriate number of hosts and datastores on the project to achieve capacity comparable to the original infrastructure.<br>-Migrate via a specialized tool (e.g. Veeam, Zerto...)<br><br>**Outbound migration**:<br>- Set up a vsphere hypervisor in the target environment<br>- Plan the capacities of the target environment in a manner comparable to the original environment<br>- Migrate via a specialized tool (e.g. Veeam, Zerto...)|[Standard vSphere documentation](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vm_admin.doc/GUID-CEFF6D89-8C19-4143-8C26-4B6D6734D2CB.html) applies.<br><br>[Deploying an OVF Linux, Windows Server and Windows SQL Server template](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/ovf_template)<br><br>[Deploying a virtual machine with vSphere](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/deploiement_d_une_machine_virtuelle)<br><br>[Create a cluster and enable EVC](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/create_cluster_enable_evc)(FR)|

## 2. OVHcloud Implementations

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |
|vRack|vRack, or Virtual rack, is a private VLAN technology that enables connection between OVHcloud services|N/A|**Inbound migration**: Hosted private Cloud is included by default into vRack.<br><br>**Outbound migration**: Record the network architecture and reproduce it with VLAN.|[Using Private Cloud with vRack](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/using_private_cloud_in_vrack)<br><br>[How to create a V(x)LAN](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/creation_vlan)|
|vROps|Standard VMware monitoring solution.|N/A|**Inbound migration**: ROps is included by default with every Hosted Private Cloud.<br><br>**Outbound migration**: Install & configure vROps in a vSphere environment.|[First connection on vROps](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vrops_introduction)|
|Managed Veeam backup|Backup-as-a-Service solution for your VMs|VBK, VIB, VBM|**Inbound migration**: Activate a Veeam backup option in the [OVHcloud Control Panel](/links/manager).<br><br>**Outbound migration**: Import backups manually, then restore backups|[Activating and using Veeam Managed Backup](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/veeam_backup_as_a_service)<br><br>[Importing backups](https://helpcenter.veeam.com/docs/backup/hyperv/importing_backups.html?ver=110)|
|Zerto|Business continuity and disaster recovery platform.|N/A|**Inbound migration**: Activate the zerto service either in the [OVHcloud Control Panel](/links/manager) or directly in the provided Zerto Replication Interface.<br><br>**Outbound migration**: Export zerto VPG settings and import those settings in the new environment.|[Setting up Zerto Virtual Replication for your DRP](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/zerto_virtual_replication_as_a_service)<br><br>[Exporting Zerto VPG settings](https://www.zerto.com/myzerto/knowledge-base/exporting-and-importing-vpg-settings-with-zerto-diagnostic-tool/)|

## 3. Specific features

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
|Anti-DDoS|The anti-DDoS is a set of equipment and means put in place to absorb distributed denial of service attacks. It includes an analysis of traffic, the "aspiration" towards a specialized network, and mitigation, ensured by VAC technology developed by OVHcloud.|N/A|**Inbound migration**: The Anti-DDoS is a component of our infrastructure, enabled by default. No action is required.<br><br>**Outbound migration**: Order and configure an anti-DDoS with the new provider.|[OVHcloud anti-DDoS protection](/links/security/antiddos)|
|SDDC Security advanced|Package of features improving security, such as Zero trust implementation, MFA, IDS for vSphere access ...|N/A|**Inbound migration**: Order the activation of security advanced in the [OVHcloud Control Panel](/links/manager).<br><br>**Outbound migration**: Order and configure appropriate security features with the new provider.|[SDDC Advanced Security Pack](https://www.ovhcloud.com/en-gb/enterprise/products/hosted-private-cloud/safety-compliance/sddc/)|

## List of architectures

xxxx


### Partner services

The OVHcloud partners concerned are listed in the [OVHcloud partners directory](/links/partner) under the "**Data center expansion and Migration**" keywords.

OVHcloud also has a dedicated service: [OVHcloud Professional Services](/links/professional-services).


### Cost and fees

No additional billing is planned from OVHcloud for the migration features listed here.

### Retention of data after contract termination

xxxx
