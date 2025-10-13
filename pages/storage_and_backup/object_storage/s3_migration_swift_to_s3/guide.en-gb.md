---
title: Object Storage - How to migrate from OVHcloud Swift Object Storage to OVHcloud S3-compatible Object Storage
excerpt: This guide provides details on how to migrate from OVHcloud Swift Object Storage to OVHcloud S3-compatible Object Storage using Rclone
updated: 2025-10-13
---

## Objective

OVHcloud offers two types of object storage: one based on OpenStack Swifr and the other based on native S3 APIs (if you want to know more about available object storage offerings and classes, read this [guide](/pages/storage_and_backup/object_storage/s3_choosing_the_right_storage_class_for_your_needs)). This guide provides detailed steps to help you migrate from OVHcloud Swift Object Storage to OVHcloud S3-compatible Object Storage using [Rclone](https://rclone.org/) tool, a command-line tool that can be used to manage cloud storage resources.

> [!warning]
>
> OVHcloud provides services which you are responsible for with regard to their configuration and management. You are therefore responsible for ensuring they function correctly.
>
> This guide is designed to assist you in common tasks as much as possible. If you encounter any difficulties performing these actions, please contact a [specialist service provider](/links/partner) and/or discuss the issue with our [community of users](/links/community). OVHcloud cannot provide you with technical support in this regard.
>

## Requirements

- An **OVHcloud account** with access to both Swift Object Storage containers and S3-compatible buckets.
- An **OVHcloud Swift Object Storage source container** in your current object storage with:
    - Your bucket name
    - Your associated user and password
    - The associated region ID
- An **OVHcloud S3-compatible Object Storage destination bucket** with:
    - Your bucket name
    - Your associated access and secret keys
    - The associated region ID
- An **OVHcloud virtual machine** with Rclone installed working as the management workstation in our scenario. To get the best results, within your budget, we suggest at least the following specifications:
    - b3-16: 4 v-cores and 16 GB of RAM
    - c3-16: 8 v-cores and 16 GB of RAM
 
## Step 1 - Installing Rclone

If you haven’t done it already, install **Rclone** by following the instructions from its [documentation](https://rclone.org/install/), based on your OS configuration.

## Step 2 - Configuring Rclone

After installing **Rclone** on your virtual machine, configure its connection to both the source container and destination buckets. To do so, you can either follow Rclone step by step configuration or you can also create/modify the configuration file yourself.

### Step 2.1 - Using Rclone config command

```bash
$ rclone config
```

This command will open the configuration menu and will guide you step by step with the configuration. Then:
- For your source container: we recommand using your OpenStack user and associated rclone config file from the [OVHcloud Control Panel](/links/manager). Follow the steps [here](/pages/storage_and_backup/object_storage/pcs_sync_rclone_object_storage) to access the config file associated to your OpenStack user.
- For your destination bucket: the official OVHcloud provider configuration is available and will guide you step by step. Follow the steps available [here](https://rclone.org/s3/#ovhcloud).


### Step 2.2 - Using Rclone config file

As said, you can also create/modify the configuration file yourself with the following command:

```bash
$ rclone config file
```

If the configuration file doesn’t exist, you’ll be prompted to add the following configuration using your preferred editor. For example, on Linux you can use `nano` :

```bash
$ nano /home/<your linux user>/.config/rclone/rclone.conf
```
In both cases your configuration blocks should look like:

```bash
[ovhcloud-swift]
type = swift
env_auth = false
auth_version = 3
auth = https://auth.cloud.ovh.net/v3
endpoint_type = public
tenant_domain = default
tenant = <tenant number>
domain = default
user = <your user>
key = <your key>
region = <region>

[ovhcloud-s3]
type = s3
provider = OVHcloud
env_auth = false
access_key_id = OVH-ACCESS-KEY
secret_access_key = OVH-SECRET-KEY
endpoint = s3.<region>.io.cloud.ovh.net
region = <region>
```

> [!primary]
>
> To get the list of OVHcloud region endpoints, see [Object Storage - Endpoints and Object Storage geoavailability](/pages/storage_and_backup/object_storage/s3_location).
>

You can then test your two connections using the `rclone config` command by as below:

```bash
$ rclone config
```

## Step 3.3 - Running Rclone

Depending on your strategy you can use two different commands to start the migration. Either you use the `rclone sync` command to start the migration of one or all buckets. As detailed in the documentation, the `rclone sync`command will make source and destination identical. Be careful then when using it.

You can also use the `rclone copy` command that will copy files from your source to your destination.
In both cases, remember to change `source-container-name` and `destination-bucket-name` to your OVHcloud Swift source container and your OVHcloud S3-compatible desintation bucket names, respectively:

```bash
$ rclone sync ovhcloud-swift:source-container-name/ ovhcloud-s3:destination-bucket-name/ --progress
```

or:

```bash
$ rclone copy ovhcloud-swift:source-container-name/ ovhcloud-s3:destination-bucket-name/ --progress
```

`--progress` shows progress during transfer.

#### Migration status

We recommend comparing the source and destination buckets after migration. Your source and OVHcloud destination buckets can be compared via command line or directly from the [OVHcloud Control Panel](/links/manager)

You can check the size of both buckets and number of objects using this command line:

```bash
rclone size <your source provider name>:source-bucket-name/
rclone size ovhcloud:ovh-bucket-name/
```

## Go further

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

Join our [community of users](/links/community).

