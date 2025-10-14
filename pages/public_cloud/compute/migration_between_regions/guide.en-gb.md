---
title: 'Migration of instances between different regions'
excerpt: 'This guide describes how to migrate an OVHcloud Public Cloud instance between two regions, in 1AZ or 3AZ. It covers the backup, transfer and recreation steps, with instructions via the Manager, Horizon or the OpenStack CLI.'
updated: 2025-07-20
---

## Objectives

This guide explains how to migrate a Public Cloud instance from one region to another, from 1AZ to 3AZ or vice versa. It centralizes the key steps - backup, transfer and recreation - and redirects to the detailed guides for each element.

## Requirements

- An [OVHcloud Public Cloud instance](/pages/public_cloud/compute/public-cloud-first-steps) 
- Access to the [OVHcloud Control Panel](/links/manager)

## Instructions

> [!primary]
>
> Before migrating an instance, it's important to understand the differences between the deployment types offered in the OVHcloud Public Cloud. Each mode - 1AZ, 3AZ or Local Zones - has a direct impact on the resilience, availability and design of your infrastructure.
>
> To find out more, consult the documentation: [Comparison and resilience of Deployment Modes - Understanding 3-AZ / 1-AZ / Local Zones](/pages/public_cloud/public_cloud_cross_functional/deployment_modes_comparison_resilience_details)
>

### Étape 1. Backup your instance

Start by creating a backup of your instance to be migrated, or use an existing one if it's still valid.

OVHcloud offers two types of backup, with different behaviors depending on the type of migration desired:

- Local backup: requires manual transfer if you're migrating to another region or AZ.
- Remote backup - recommended: automatically managed by OVHcloud, the local backup is replicated in the selected region. No manual transfer required.

> [!primary]
>
> If your local backup was performed in a 3AZ region and you wish to recreate the instance in another AZ in the same region, no transfer is required.
>
> Local backups are accessible from all availability zones within a 3AZ region. You can proceed directly to the instance recreation stage.
>
> Currently, creating a distant backup is not available through the OVHcloud Control Panel. You can only perform this action via the OVHcloud API or OpenStack.
>

> [!tabs]
> Via the OVHcloud Control Panel
>> To create an instance backup from the OVHcloud client space, follow [this section](/pages/public_cloud/compute/save_an_instance#createinstanceviamanager) of our guide to creating an instance backup.
>>
> Via the OVHcloud API
>> To create an instance backup from the OVHcloud API, follow [this section](/pages/public_cloud/compute/save_an_instance#createinstanceviaapi) of our guide to creating an instance backup.
>>
> Via the Openstack CLI
>> To create an instance backup from the OpenStack CLI, follow [this section](/pages/public_cloud/compute/save_an_instance#createinstanceviaopenstack) of our guide to creating an instance backup.
>>
> via Horizon
>> To create an instance backup from the Horizon, follow [this section](/pages/public_cloud/compute/save_an_instance#createinstanceviahorizon) of our guide to creating an instance backup.
>>

### Étape 2. Migrating your backup to another region

> [!primary]
>
> If you used a remote backup, you can go straight to [step 3. restore instance in new region](#step3recreateinstance).
>

> [!tabs]
> Via the Openstack CLI
>> To transfer your backup from one AZ to another via the Openstack CLI, please follow our guide: [Downloading and transferring an instance backup from one OpenStack region to another](/pages/public_cloud/compute/transfer_instance_backup_from_one_datacentre_to_another)
>>

### Étape 3. restore instance in new region <a name="step3recreateinstance"></a>

> [!tabs]
> Via the OVHcloud Control Panel
>> To create an instance from an existing backup, please follow [this section](/pages/public_cloud/compute/create_restore_a_virtual_server_with_a_backup#createinstanceviamanager) from our guide : Using instance backups to create or restore an instance.
>>
> Via the OVHcloud API
>>  To create an instance from an existing backup, please follow [this section](/pages/public_cloud/compute/create_restore_a_virtual_server_with_a_backup#createinstanceviaapi) from our guide : Using instance backups to create or restore an instance.
>>
> Via the Openstack CLI
>> To create an instance from an existing backup via the Openstack CLI, follow [this section](/pages/public_cloud/compute/create_restore_a_virtual_server_with_a_backup#createinstanceviaopenstack) from our guide: Using instance backups to create or restore an instance.
>>
> Via Horizon
>> To create an instance from an existing backup via Horizon, follow [this section](/pages/public_cloud/compute/create_restore_a_virtual_server_with_a_backup#createinstanceviahorizon) from our guide : Using instance backups to create or restore an instance.
>>

## Go further

Join our [community of users](/links/community).