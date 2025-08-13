---
title: Reversibility policy for the product Managed Dedicated Cloud - SecNumCloud
updated: 2025-08-08
---

## Objective

This document is the reversibility policy of the Product Managed Dedicated Cloud - SecNumCloud covering the OVHcloud offer [VMware on OVHcloud under SecNumCloud qualification ](https://www.ovhcloud.com/en-gb/enterprise/products/secnumcloud/).

This policy aims to implement the general reversibility principles and our compliance with the SWIPO IAAS Code of Conduct for cloud providers.

## Features list

Features of the product line fall into three categories:

1. **Core features** for which we guarantee migration capacity.
2. **OVHcloud implementations** that require adaptation to a new migration environment.
3. **Specific features** that cannot be guaranteed for migration as they are related to the OVHcloud environment or involve custom developments.


## 1. Core features

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |


the tab to be transformed 

|Migration model|Documentation available|
|---|---|
|**Inbound migration**:<br>- Subscribe to a Hosted Private Cloud SecNumCloud
 project.<br>- Order the appropriate number of hosts and datastores on the project to get a capacity comparable to that of the original infrastructure.<br>-Migrate using a specialized tool (Veeam, API, ...) or migrate manually.<br>-Use the SecNumCloud zone's VPN Gateway or a custom VPN solution (e.g. NSX or virtual machine third party solution) to ensure data encryption when migrating from an external network.<br>-Then enable VM encryption and vSAN Cluster datastores using the vNKP software brick or your own KMS (compatible with the KMIP protocol). <br> -Use the SPN (Secure Private Network) to connect SecNumCloud services inside a hosting site. <br>-Use the inter DC SPN solution to connect your qualified infrastructure hosted in other hosting sites covered by the SecNumCloud qualification at OVHcloud <br><br>**Outbound migration**: <br> - -Plan the target environment capabilities compared to the original environment. <br>**- Encrypted data migration scenario with vNKP :** Set up an encrypted link between the OVHcloud hosting site and destination site. Export the vNKP key of the OVHcloud hosting environment. Import the vNKP key into the remote site’s vSphere environment. Cold-migrate your data via a manual copy between the two sites, or hot-migrate your data (via a failover mechanism) using a compatible third-party tool supported by the two providers. <br>**-Customer-specific KMS encrypted data scenario:** Set up an encrypted link between the OVHcloud hosting site and destination site. Configure your KMS on the remote site’s vSphere environment. Cold-migrate your data via a manual copy between the two sites, or hot-migrate your data (via a failover mechanism) using a compatible third-party tool supported by the two providers. <br>- Migrate via a specialized tool (e.g. Veeam, ...)  |The documentation [vSphere SecNumCloud](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/snc_getting_started) applies as soon as the service is delivered, to secure the connection and an end-to-end data encryption. Following this, the [documentation vSphere standard](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vm_admin.doc/GUID-CEFF6D89-8C19-4143-8C26-4B6D6734D2CB.html) applies.<br><br>[Deploy an OVF Linux, Windows Server et Windows SQL Server](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/ovf_template)<br><br>[Deploy a virtual machine with vSphere](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/deploiement_d_une_machine_virtuelle)<br><br>[Create a cluster and activate EVC](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/create_cluster_enable_evc)<br><br>[Virtual machine encryption interoperability](https://docs.vmware.com/fr/VMware-vSphere/8.0/vsphere-security/GUID-C0AF1F3A-67B4-41A6-A933-7E52A3603D9D.html)<br><br>[Back up a vSphere Native Key Provider](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.security.doc/GUID-E0EB371A-F6E4-463B-A1E9-9D4DDCAA039D.html)|

## 2. OVHcloud Implementations

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |
|VPN Gateway|An IPsec VPN gateway that connects external networks to the SecNumCloud infrastructure through an encrypted funnel |N/A|**Inbound**: Subscribe to and use the VPN Gateway service included in the qualified scope. <br><br>**Outbound**: Use the vRack service included with other OVHcloud services, or take note of the network architecture and replicate it with VLANs and another encrypted funnel.|[Introduction to SecNumCloud Connectivity](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/snc-connectivity-concepts-overview)<br><br>[VPN-SPN concept overview](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/snc-connectivity-concepts-vpn-spn)<br><br>[Personalized VPN via NSX](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/nsx_configurer_un_vpn_via_une_gateway_edge)|
|SPN|A private network that connects the resources and services available in the SecNumCloud infrastructure to one or more sites in the SecNumCloud zone. You can also use it to connect other OVHcloud services, or services hosted with a third party via the VPN Gateway.|N/A|**Inbound**: Subscribe to and use the SPN service included in the qualified scope.<br><br>**Outbound**: Take note of the network architecture and replicate it with the concepts of subnets and routing.|[SPN introduction and concepts](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/snc-connectivity-concepts-spn)<br><br>[SPN connector](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/snc-connectivity-concepts-spn-connector)|
|SPN Inter-DC|An encrypted link between two sites hosting the SecNumcloud infrastructure, enabling SPNs to be connected.|N/A|**Incoming**: Subscribe to and use the Inter-DC SPN service included in the qualified scope.<br><br>**Outbound**: Configure your IP routing between two sites hosting the SecNumcloud infrastructure outside of OVHcloud.|[SPN InterDC option](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/snc-connectivity-concepts-spn)|
|vROps TBC ....|A standard VMware monitoring solution.|N/A|**Inbound**: vROps is included by default with each Hosted Private Cloud SecNumCloud <br><br>**Outbound**: Install and configure vROps in a vSphere environment.|[First connection on vROps](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vrops_introduction)|
|Monitoring and supervision|VMware standard monitoring solution via vROps|Many formats supported by the platform(e.g JSON, Syslog, etc) |**Inbound**: vROps is included by default with every Hosted Private Server. Adaptation of Cloud dashboards and monitoring agents.<br><br>**Outbound**: Install and configure vROps in a vSphere environment.|[First connection on vROps](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vrops_introduction)|
|Managed Veeam backup|Backup as a service solution for your VMs|VBK, VIB, VBM|**Inbound**: Enable a Veeam backup option in the [OVHcloud Control Panel](/links/manager). Please note that it will not be possible to import the data. <br><br>**Outbound**: This feature is not currently supported. Customers can export their primary data (excluding backed-up data) and configure a backup solution of their choice at the destination site.|[Enable and use Veeam Managed Backup](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/veeam_backup_as_a_service)<br><br>[Move2Cloud - Migrating VMware Workloads to OVHcloud SecNumCloud with Veeam Replicationn](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vmware_migration_veeam_secnumcloud)|
|Zerto|Business continuity and disaster recovery platform.|N/A|**Inbound**: activation of the option in the [OVHcloud Control Panel](/links/manager) or directly in the provided Zerto Replication Interface.<br><br>**Outbound**: export zerto VPG settings and import those settings in the new environment.|[Setting up Zerto Virtual Replication for your DRP](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/zerto_virtual_replication_as_a_service)<br><br>[Migrate VMware workloads to OVHcloud SecNumCloud Hosted Private Cloud with Zerto](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vmware_migration_zerto_secnumcloud)<br><br>[Exporting Zerto VPG settings](https://www.zerto.com/myzerto/knowledge-base/exporting-and-importing-vpg-settings-with-zerto-diagnostic-tool/)|

## 3. Specific features

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
|---|---|---|---|---|
|Anti-DDoS|Anti-DDoS is a set of equipment and means put in place to absorb denial-of-service attacks. It includes traffic analysis, “vacuuming” to a specialized network, and mitigation, powered by VAC technology developed by OVHcloud.|N/A|**Inbound**: The anti-DDoS system is a component of our infrastructure, enabled by default. No action is required. It is only enabled on public IPs and does not cover links to the OVHcloud Connect service.<br><br>**Outbound**: Order and configure an anti-DDoS protection with the new hosting provider. |[OVHcloud anti-DDoS Protection](/links/security/antiddos)|
|OVHcloud Connect|A connectivity service, via points of presence (POPs), that connects a company network hosted outside (Tier site) to an infrastructure service provided by OVHcloud, through a private network and without passing through internet access. |N/A|**Inbound**: Once the service has been delivered, and after you have received the service key, configure it via the interface available in the OVHcloud Control Panel.<br><br>**Outbound**: Use the network connection ports provided and OVHcloud POP or POP Provider to reproduce a new network architecture |[OVHcloud Connect direct commissioning ](/pages/network/ovhcloud_connect/occ-direct-control-panel)<br><br>[OVHcloud Connect Provider implementation ](/pages/network/ovhcloud_connect/occ-provider-control-panel)|
|Advanced security for SDDC|Set of features enhancing security, such as the implementation of Zero Trust Security, MFA, IDS for vSphere access...|N/A|**Inbound**: These features are available by default on SecNumCloud-qualified infrastructure.<br><br>**Outbound**: Order and configure the appropriate security features with the new provider.|[SDDC Advanced Security Pack](https://www.ovhcloud.com/en-gb/enterprise/products/hosted-private-cloud/safety-compliance/sddc/)|

### List of architectures

The product is based on a dedicated SecNumCloud-qualified VMware Software-Defined Data Center (SDDC) architecture, including vSphere, vCenter, NSX (SDN), vSAN (distributed storage), vROps (monitoring), and advanced security options (encryption, MFA, zero trust). Resources (compute, storage, network) are physically and logically isolated, with fine-grained rights management (IAM), multi-site support (SPN Inter-DC), and integration of private network services (SPN, VPN Gateway). The architecture is carried out in Datacentres based in France.

### Partner Services

The OVHcloud partners concerned are listed in the [OVHcloud partners directory](/links/partner) under the "**Data center expansion and Migration**" keywords.

OVHcloud also has a dedicated service: [OVHcloud Professional Services](/links/professional-services).

### Cost and fees

No additional billing is planned from OVHcloud for the migration features listed here.

### Data retention after contract termination

The data is stored until the end of the month following the termination of the service, then permanently deleted in accordance with the commitments of the SecNumCloud Terms of Service.

