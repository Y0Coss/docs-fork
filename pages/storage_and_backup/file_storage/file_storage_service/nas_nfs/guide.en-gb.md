---
title: File Storage Service - Getting started (Alpha)
excerpt: Learn how to set up and manage OVHcloud’s File Storage Service with your OpenStack project. This guide covers CLI setup, share creation, client access, and mounting on your VMs.
updated: 2025-13-08
---

## Objective 

OVHcloud provides a File Storage Service powered by OpenStack Manila. This service offers managed NFS shares on private networks, supporting ReadWriteMany (RWX) access across multiple instances or Kubernetes pods.

It can be accessed via OpenStack CLI, API, Manila CSI, and Terraform.

> [!warning]
>
> This service is currently in Alpha, available only in the **SBG5** region, and limited to registered Alpha customers. Features and availability may change.
>

## Requirements

- Your project is authorized for Manila Alpha (register [here](https://labs.ovhcloud.com/en/file-storage/){.external})
- You already have a [private network](/pages/public_cloud/public_cloud_network_services/getting-started-07-creating-vrack) available in your project.
- A [Public Cloud instance](/links/public-cloud/public-cloud) in your OVHcloud account
- An [OpenStack CLI ready environment](/pages/public_cloud/public_cloud_cross_functional/prepare_the_environment_for_using_the_openstack_api)

## Instructions

> [!primary]
>
> Currently, the File Storage Service can only be accessed and managed via the Manila CLI. Other interfaces will be supported in the future.
>

> [!tabs]
> via OpenStack CLI with the Manila plugin
>> 1. Install the Manila CLI Plugin
>>
>> If the Manila commands are not yet available, install the plugin:
>>
>> ```bash
>> sudo apt update && sudo apt install -y python3-manilaclient
>> ```
>>
>> Verify the installation:
>>
>> ```bash
>> openstack share --help
>> ```
>>
>> You should see commands such as:
>>
>> - share create
>> - share list
>> - share network create
>> - share access create
>>
>> 2. Check Available Share Types
>>
>> List the share types available in your region:
>>
>> ```bash
>> openstack share type list --os-region-name <REGION_NAME>
>> ```
>>
>> Expected output:
>>
>> ```bash
>> +----------+-----------+------------+------------+
>> | ID       | Name      | Visibility | Is Default |
>> +----------+-----------+------------+------------+
>> | acceb7b4 | generic_0 | public     | True       |
>> +----------+-----------+------------+------------+
>> ```
>>
>> > [!primary]
>> >
>> > Note: For the generic_0 type, you must always select a share network, otherwise the share cannot be created.
>> >
>>
>> 3. Create a Share Network
>>
>> Identify your private network and subnet:
>>
>> ```bash
>> openstack network list --os-region-name <REGION_NAME>
>> openstack subnet list --os-region-name <REGION_NAME>
>> ```
>>
>> Retrieve their IDs:
>>
>> ```bash
>> openstack network show --os-region-name <REGION_NAME> -c id -f value <PRIVATE_NETWORK_NAME>
>> openstack subnet show --os-region-name <REGION_NAME> -c id -f value <PRIVATE_SUBNET_NAME>
>> ```
>>
>> > [!primary]
>> >
>> > Both network and subnet IDs should look like: **abc12345-def6-4abc-8def-123456abcdef**
>> >
>>
>> Create a share network linked to your private network:
>>
>> ```bash
>> openstack share network create \
>>   --os-region-name <REGION_NAME> \
>>   --name <my-share-network-name> \
>>   --neutron-net-id <NETWORK_ID> \
>>   --neutron-subnet-id <SUBNET_ID>
>> ```
>>
>> > [!primary]
>> >
>> > Note: Replace <my-share-network-name> with your chosen name for the share network.
>> >
>>
>> Verify the share network:
>>
>> ```bash
>> openstack share network list --os-region-name <REGION_NAME>
>> ```
>>
>> 4. Create an NFS Share
>>
>> Create a 150 GB NFS share:
>>
>> ```bash
>> openstack share create \
>>   --os-region-name <REGION_NAME> \
>>   --share-type generic_0 \
>>   --share-network <my-share-network-name> \
>>   --name <my-first-share-name> \
>>   NFS 150
>> ```
>>
>> > [!primary]
>> >
>> > Note: Replace <my-first-share-name> with the name you want to assign to your share.
>> >
>>
>> Monitor the share status until it becomes available:
>>
>> ```bash
>> openstack share list --os-region-name <REGION_NAME>
>> ```
>>
>> 5. Authorize a Client VM
>>
>> Ensure your client VM is in the same private network as the share.
>>
>> Retrieve the VM’s private IP address:
>>
>> ```bash
>> openstack server show --os-region-name <REGION_NAME> <VM_NAME> -c addresses -f value
>> ```
>>
>> Example output:
>>
>> ```bash
>> {'my-private-net': ['10.1.0.123', '57.123.88.111']}
>> ```
>>
>> Grant access to the share using the VM’s private IP (e.g., 10.1.0.123):
>>
>> ```bash
>> openstack share access create \
>>   --os-region-name <REGION_NAME> \
>>   <my-first-share-name> \
>>   ip 10.1.0.123
>> ```
>>
>> Verify access:
>>
>> ```bash
>> openstack share access list --os-region-name <REGION_NAME> <my-first-share-name>
>> ```
>>
>> 6. Retrieve the Export Path
>>
>> Get the NFS export location:
>>
>> ```bash
>> openstack share export location list --os-region-name <REGION_NAME> <my-first-share-name>
>> ```
>>
>> Example output:
>>
>> ```bash
>> 10.1.0.12:/shares/share-abc12345-def6-4abc-8def-123456abcdef
>> ```
>>
>> > [!primary]
>> >
>> > Note: This export path is used to mount the share on your client VM.
>> >
>>
>> 7. Mount the Share on Your Client VM
>>
>> Connect to your VM and install NFS utilities:
>>
>> ```bash
>> sudo apt update && sudo apt install -y nfs-common
>> ```
>>
>> Create a mount point and mount the share:
>>
>> ```bash
>> sudo mkdir -p /mnt/share
>> sudo mount -t nfs4 10.1.0.12:/shares/share-abc12345-def6-4abc-8def-123456abcdef /mnt/share
>> ```
>>
>> Verify the mount:
>>
>> ```bash
>> df -h /mnt/share
>> ```
>>
>> > [!primary]
>> >
>> > Note: Replace the export path with the one retrieved for your share.
>> >
>>
>> 8. Check capacity and usage
>>
>> Display available space on the mounted share:
>>
>> ```bash
>> df -h /mnt/share
>> ```
>>
>> Example output:
>>
>> ```bash
>> Example:
>> Filesystem                          Size  Used  Avail Use% Mounted on
>> 10.1.0.12:/shares/share-abc1...     150G  100M   150G   1% /mnt/share
>> ```
>>
>> > [!primary]
>> >
>> > Note: This lets you monitor the storage capacity and usage of your NFS share.
>> >
>>
>> 9. Manage the share lifecycle
>>
>> Resize the share:
>>
>> > [!warning]
>> >
>> > Only extending a share is allowed for now; shrinking is not supported.
>> >
>>
>> ```bash
>> openstack share resize --os-region-name <REGION_NAME> <my-first-share-name> 200
>> ```
>>
>> Delete a share:
>>
>> ```bash
>> openstack share delete --os-region-name <REGION_NAME> <my-first-share-name>
>> ```
>>
>> Delete the share network:
>>
>> ```bash
>> openstack share network delete --os-region-name <REGION_NAME> <my-share-network-name>
>> ```
>>
>> > [!primary]
>> >
>> > Note: Ensure no active shares are using the network before deleting it.
>> >
>>
>> 10. Troubleshooting
>>
>> | Symptom	                  | Cause	                           | Solution                                                           |
>> | --------------------------- | ---------------------------------- | ------------------------------------------------------------------ |
>> | `Unknown command ['share']` |	Manila CLI not installed           | Install it with `sudo apt install python3-manilaclient`            |
>> | `Share network must be set` | Using a DHSS=True share type       | Provide `--share-network`                                          |
>> | Cannot mount NFS            | IP not authorized or wrong network | Ensure VM is in the same private subnet and access rule is created |
>> | `403 Forbidden`             | Project not whitelisted for Manila | Ensure you are registered to Alpha                                 |
>> | Share stuck in creating     | Invalid network ID or subnet       | Check `NETWORK_ID` and `SUBNET_ID`                                 |
>>

## Go further

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

Join our [community of users](/links/community).