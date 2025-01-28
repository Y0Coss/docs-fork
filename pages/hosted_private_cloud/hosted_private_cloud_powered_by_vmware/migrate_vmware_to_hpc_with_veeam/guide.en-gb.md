# Move2Cloud: Migrating VMware Workloads to OVHcloud Hosted Private Cloud with Veeam Replication
---
title: "Move2Cloud: Migrating VMware Workloads to OVHcloud HPC with Veeam Replication"
excerpt: "Learn how to migrate your on-prem VMware workloads to an OVHcloud Hosted Private Cloud environment using Veeam Replication."
updated: 2025-01-28
---
## Objective

This guide outlines the steps to migrate your on-premises VMware workloads to an OVHcloud Hosted Private Cloud (HPC) using Veeam Replication. It walks you through migrating your workloads smoothly with as little downtime as possible.

## Requirements

Before getting started, make sure you have the following:

1. **Prepare your source environment:**
   - A complete list of VMs with FQDNs and IP addresses.
   - Updated operating systems and mapped dependencies.
   - Subnets and VLAN IDs for planning your network.

2. **Prepare the target environment:**
   - Correctly sized resources (hosts, datastores, vSAN clusters).
   - A Hosted Private Cloud with NSX-T and VLANs, if needed.
   - A valid Veeam Backup & Replication (B&R) license.

3. **Network setup:**
   - A VPN tunnel or OVHcloud Connect (optional) for secure communication.

4. **Core services and tools:**
   - Access to vCenter.
   - Pre-configured DNS, NTP, and authentication services in HPC.

5. **Access to documentation:**
   - Relevant OVHcloud and Veeam guides for configuration details.

## Instructions

### 1. Inventory Source VMs and Network Configuration
- List all VMs with their FQDNs, IP addresses, operating systems, and dependencies.
- Group VMs by application to reduce service interruptions during migration.
- Document subnets and VLAN IDs for replication planning.

### 2. Size Target Resources
- Calculate your needs for cores, RAM, and storage.
- Decide on storage types (NFS or vSAN) based on performance requirements.
- Plan VLAN routing and network segregation with NSX-T if needed.

### 3. Whitelist IPs for vCenter Access
- Allow required IPs to access the vCenter through the OVHcloud Secure SSL Gateway.
- Follow the [guide to whitelist IPs](https://help.ovhcloud.com/csm/en-gb-vmware-authorise-ip-addresses-vcenter?id=kb_article_view&sysparm_article=KB0045321).

### 4. Set Up Roles and Permissions
- Mirror roles and permissions from your current environment in HPC.
- Use OVHcloud IAM or integrate your existing IAM (e.g., Active Directory, Okta).
- Enable SSO via ADFS using [this guide](https://help.ovhcloud.com/csm/en-gb-connect-saml-sso-adfs?id=kb_article_view&sysparm_article=KB0043008).

### 5. Build Your Target Network
- Set up VLANs, routing, and traffic flow matrices in NSX-T.
- Configure dVS and NSX-T gateways for network segregation and filtering.
- Check the [NSX first steps guide](https://help.ovhcloud.com/csm/en-gb-vmware-nsx-first-steps?id=kb_article_view&sysparm_article=KB0056831).

### 6. Deploy Core Services in HPC
- Deploy services like NTP, DNS, and authentication to reduce cross-traffic.
- Use `ntp.ovh.net` for time synchronization.
- Set up DNS services, such as an AD Domain Controller.

### 7. Install Veeam B&R Server
- Install Veeam Backup & Replication on your OVHcloud HPC.
- Activate the license using [this guide](https://help.ovhcloud.com/csm/en-gb-public-cloud-storage-veeam-backup-replication?id=kb_article_view&sysparm_article=KB0046503).

### 8. Configure a VPN Tunnel
- Create an IPsec tunnel between your on-prem infrastructure and OVHcloud.
- Use NSX, Stormshield, or OpnSense for the configuration:
  - [NSX VPN setup](https://help.ovhcloud.com/csm/en-gb-vmware-nsx-configure-ipsec?id=kb_article_view&sysparm_article=KB0058696)
  - [Stormshield VPN setup](https://documentation.stormshield.eu/SNS/v4/en/Content/User_Configuration_Manual_SNS_v4/IPSec_VPN/IPSEC_VPN.htm)
  - [OpnSense VPN setup](https://docs.opnsense.org/manual/how-tos/ipsec-s2s.html)
- Or use [OVHcloud Connect](https://www.ovhcloud.com/fr/network/ovhcloud-connect/) for low-latency and high bandwidth.

### 9. Deploy Veeam Proxy Server
- Set up a Veeam proxy on your on-prem infrastructure.
- Verify connectivity with the Veeam B&R server in the HPC.
- Follow the [proxy setup guide](https://helpcenter.veeam.com/docs/backup/vsphere/add_vmware_proxy.html?ver=120).

### 10. Create Replication Jobs
- Use the Veeam B&R server to define replication jobs.
- Follow the [replication job setup guide](https://helpcenter.veeam.com/docs/backup/vsphere/replica_job.html?ver=120).

### 11. Start and Test Replication Jobs
- Start replication jobs and monitor their progress.
- Run a pre-test with Veeam’s failover function to check replication without affecting source VMs:
  - [Failover process](https://helpcenter.veeam.com/docs/backup/vsphere/failover.html?ver=120)
  - [Undo failover process](https://helpcenter.veeam.com/docs/backup/vsphere/undo_failover.html?ver=120)

### 12. Migrate Workloads
- Perform a planned failover to turn off on-prem VMs, replicate any final changes, and power on the VMs in HPC.
- Check the [planned failover guide](https://helpcenter.veeam.com/docs/backup/vsphere/planned_failover.html?ver=120).

### 13. Validate Applications and Services
- Confirm VMs boot without issues.
- Test connectivity to services like AD, DNS, and internet-facing apps.
- Verify that all applications are working correctly.

### 14. Confirm Permanent Failover
- Finalize the migration by using the permanent failover action:
  - [Permanent failover guide](https://helpcenter.veeam.com/docs/backup/vsphere/permanent_failover.html?ver=120).

### 15. Optimize and Secure Your Environment
- Move VMs to the desired storage (e.g., vSAN or NFS datastores) using [Storage vMotion](https://help.ovhcloud.com/csm/fr-vmware-storage-vmotion?id=kb_article_view&sysparm_article=KB0046287).
- Create backups for your workloads with OVHcloud S3 storage as described [here](https://help.ovhcloud.com/csm/fr-public-cloud-storage-s3-veeam?id=kb_article_view&sysparm_article=KB0047499).

## Go Further

For more details and advanced options:
- Check [OVHcloud Hosted Private Cloud documentation](https://www.ovhcloud.com/en/private-cloud/).
- Review [Veeam documentation](https://helpcenter.veeam.com/docs/backup/vsphere/index.html?ver=120).
- Contact OVHcloud support if you need additional help.
