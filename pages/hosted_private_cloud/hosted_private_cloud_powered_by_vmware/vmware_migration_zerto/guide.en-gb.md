---
title: Move2Cloud - Migrate VMware workloads to OVHcloud Hosted Private Cloud with Zerto
excerpt: "Learn how to migrate your on-premises VMware workloads to an OVHcloud Hosted Private Cloud environment using Zerto Virtual Replication."
updated: 2025-07-02
---

## Objective

This guide explains how to migrate your on-premises VMware workloads to an **OVHcloud Hosted Private Cloud (HPC)** using **Zerto Virtual Replication**.

>[!warning]
> As of May 2025, **Zerto does not support replication of virtual machines with VMEncrypt enabled**.  
> vSAN’s encryption at rest is supported. You can also encrypt your VMs after migration is complete.

## Requirements

Before you begin, make sure you have:

- A complete inventory of your VMs, including FQDN, IP address, OS version, and application dependencies.
- A batch migration plan grouped by application stack.
- A full list of VLANs, subnets, and segments for your target network.
- An HPC environment properly sized (hosts, datastores, vSAN, NSX-T).
- A working IPsec VPN tunnel between your on-premises infrastructure and OVHcloud.
- Access to the Zerto console and vCenter interfaces on both sides.

## Practical steps

### Step 1: Inventory source VMs and network topology

- List all source VMs with OS version and IP/FQDN.
- Group VMs by application (web/app/db) for migration batches.
- Document all VLANs and IP subnets used in your infrastructure.

### Step 2: Size your target HPC environment

- Estimate your vCPU, RAM, and storage needs based on your consolidation ratio.
- Choose between NFS datastores and vSAN depending on IOPS requirements.
- If using NSX-T:
  - Plan segment creation and overlays.
  - Evaluate north/south traffic.
  - Select your virtual firewall (Stormshield, FortiVM, Palo Alto).
- For public-facing services, request public IPs or use the [BYOIP feature](/links/network/byoip).

### Step 3: Authorize access to OVHcloud vCenter

vCenter access is restricted by default. To enable it:

- Follow the guide “[Authorize IP addresses to access vCenter](https://help.ovhcloud.com/csm/en-gb-vmware-authorise-ip-addresses-vcenter?id=kb_article_view&sysparm_article=KB0045321)”.
- Whitelist the IP addresses of your on-premises infrastructure and Zerto components.

### Step 4: Set up user roles and permissions

- Use [OVHcloud IAM](https://help.ovhcloud.com/csm/en-gb-vmware-iam-presentation?id=kb_article_view&sysparm_article=KB0063154) to manage access.
- Alternatively, deploy your own AD or Okta instance, or configure ADFS for SSO:  
  [Configure SAML with ADFS](https://help.ovhcloud.com/csm/en-gb-connect-saml-sso-adfs?id=kb_article_view&sysparm_article=KB0043008)

### Step 5: Build the target network in your HPC

- Create a **flow matrix** that describes expected traffic between VMs (VLANs, ports, protocols).
- Use preconfigured VLANs or define new segments.
- NSX-T is pre-deployed (Tier-0/1 gateways, dFW). To get started:  
  [NSX First Steps](https://help.ovhcloud.com/csm/en-gb-vmware-nsx-first-steps?id=kb_article_view&sysparm_article=KB0056831)

### Step 6: Deploy core services in HPC

To reduce latency with your on-prem environment:

- **NTP**: use `ntp.ovh.net`
- **DNS**: deploy a domain controller if needed
- **Authentication**: either local AD or federated access

### Step 7: Install Zerto on your OVHcloud tenant

- Follow this deployment guide:  
  [Zerto Virtual Replication on OVHcloud HPC](https://help.ovhcloud.com/csm/en-gb-vmware-zerto-virtual-replication-customer-to-ovh?id=kb_article_view&sysparm_article=KB0046457)
- Zerto will automatically deploy a ZVM, ZVRAs, and a managed firewall gateway.
- Official documentation:  
  [Zerto Installation Guide](https://help.zerto.com/bundle/Install.VC.HTML/page/Performing_an_Express_Installation.htm){.external}

### Step 8: Install Zerto on your on-premises infrastructure

- Follow the same instructions as for the tenant side.
- Ensure network connectivity between ZVMs and ZVRAs:
  - TCP 9071 / 9081 (ZVM ↔ ZVM)
  - TCP 4007 / 4008 (ZVRA ↔ ZVRA)

### Step 9: Set up an IPsec tunnel

- A VPN without NAT is required for Zerto to function.
- Use OPNsense or any compatible device:  
  [IPsec tunnel configuration](https://help.ovhcloud.com/csm/en-gb-vmware-zerto-virtual-replication-customer-to-ovh?id=kb_article_view&sysparm_article=KB0046457)

### Step 10: Pair the ZVMs

- Pair your on-premises and OVHcloud ZVMs following step 5 of the previous guide.

### Step 11: Create Zerto VPGs

- Use **Virtual Protection Groups (VPGs)** to group the VMs to be replicated.
- Follow this guide:  
  [Create a VPG](https://help.zerto.com/bundle/Admin.ZSSP.HTML.10.0_U3/page/Creating_a_VPG.htm){.external}

### Step 12: Monitor replication jobs

- Use the Zerto interface to monitor VPG status:  
  [Monitor VPGs](https://help.zerto.com/bundle/Admin.ZSSP.HTML.10.0_U3/page/Monitoring_Virtual_Protection_Groups.htm){.external}

### Step 13: Run a test failover

- Run a **failover test** to validate your setup without interrupting production:  
  [Start test failover](https://help.zerto.com/bundle/Admin.VC.HTML.10.0_U3/page/StartingFailoverTest.htm){.external}  
  [Stop test failover](https://help.zerto.com/bundle/Admin.VC.HTML.10.0_U3/page/What_Happens_After_Starting_a_Test.htm){.external}

### Step 14: Perform the final migration

- Use the **Move** action in Zerto to start your production migration:  
  [Move process](https://help.zerto.com/bundle/Admin.ZSSP.HTML.10.0_U3/page/The_Move_Process.htm){.external}
- Choose your commit policy: automatic, manual, or rollback-enabled.

### Step 15: Validate your applications

- Ensure all migrated VMs are up and running.
- Test infrastructure services (AD, DNS, antivirus, database, public-facing apps).

### Step 16: Confirm or roll back the move

- If everything is operational, commit the migration in Zerto.
- If needed, roll back the operation as documented.

### Step 17: Move VMs to target storage

- Use **Storage vMotion** to optimize VM placement:  
  [VMware Storage vMotion](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vmware_storage_vmotion)

### Step 18: Back up your migrated VMs

Protect your workloads after the move:

- [Veeam as a Service (HPC)](/pages/storage_and_backup/backup_and_disaster_recovery_solutions/veeam/vmware_veeam_backup_as_a_service)
- [Veeam with Enterprise licenses (Public Cloud)](/pages/storage_and_backup/backup_and_disaster_recovery_solutions/veeam/public_cloud_storage_veeam_backup_replication)

## Go further

Need hands-on support or a project review? Reach out to your Technical Account Manager or contact our [Professional Services](/links/professional-services) team.

Join the Hosted Private Cloud discussion on [Discord](https://discord.gg/ovhcloud){.external} or ask your questions on our [community hub](/links/community).