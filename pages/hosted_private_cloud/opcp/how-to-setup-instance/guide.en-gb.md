---
title: "OPCP - How to install an instance from the Horizon interface"
excerpt: "Learn how to install an OPCP instance via Horizon by configuring networks, subnets, instances, and SSH keys."
updated: 2025-11-06
---

## Objective

Before deploying services on your **OPCP** arrays, you must have an installed and active instance.  
This guide details the steps to install an OPCP instance from the **Horizon** interface.

---

## Prerequisites

- Have an active [OPCP](https://www.ovhcloud.com/en/hosted-private-cloud/onprem-cloud-platform/) service.
- Have a **user account** with sufficient permissions to access Horizon for the OPCP offer.

---

## In practice

### 1. Log in to Horizon

Log in to the **Horizon** interface of your OPCP environment.  
![horizon-interface](images/01-log-to-horizon-step01.png){.thumbnail}

Once connected, select the **project** where you want to install your instance.  
![horizon-select-project](images/01-log-to-horizon-step02.png){.thumbnail}

### 2. Creating a private network

Before deploying your instance, it’s generally necessary to create a **private network** so that it can be accessed within your local infrastructure.

1. In the left-hand menu, click **Network > Networks**.  
![horizon-network-networks](images/02-create-network-step01.png){.thumbnail}  
2. Click **Create Network**.  
![horizon-network-networks](images/02-create-network-step02.png){.thumbnail}  

#### Step 1: Network

![horizon-network-setup-network](images/02-create-network-setup-network.png){.thumbnail}  

| Field | Description |
|--------|--------------|
| **Network Name** | Enter a name for your network. |
| **Enable Admin State** | Leave this option checked to activate the network. |
| **Shared** | Check this box if you want to make the network available to multiple projects. |
| **Create Subnet** | Leave this option checked to create a subnet. |
| **Availability Zone Hints** | Leave the default value. |

#### Step 2: Subnet

![horizon-network-setup-subnet](images/02-create-network-setup-subnet.png){.thumbnail}  

> Although it is possible to create a network without a subnet, it cannot be attached to an instance unless it has one.

| Field | Description |
|--------|--------------|
| **Subnet Name** | Enter a name for your subnet. |
| **Network Address** | Define a private IP range, for example `192.168.100.0/24`. |
| **IP Version** | Leave the default value **IPv4**. |
| **Gateway IP** | Optional. If not specified, an address will be automatically selected. |
| **Disable Gateway** | Check this box to not assign a gateway address. |

#### Step 3: Subnet Details

![horizon-network-setup-subnet](images/02-create-network-setup-subnet-details.png){.thumbnail}  

| Field | Description |
|--------|--------------|
| **Enable DHCP** | Keep enabled if you want IP addresses to be automatically assigned. |
| **Allocation Pools** | Optional. Allows you to define a specific IP address range. |
| **DNS Name Servers** | Optional. Lets you specify one or more DNS servers. |
| **Host Routes** | Optional. Allows you to add static routes. |

---

### 3. Creating an instance

1. In the left-hand menu, click **Compute > Instances**.  
![horizon-compute-instances](images/03-create-instance-horizon-step01.png){.thumbnail}  
2. Click **Launch Instance** to create a new instance.  
![horizon-compute-instances-launch-instance](images/03-create-instance-horizon-step02.png){.thumbnail}  

#### Tab: Details

![horizon-compute-instances-launch-instance-details](images/03-create-instance-horizon-details.png){.thumbnail}  

| Field | Description |
|--------|--------------|
| **Instance Name** | Enter the name of the instance to create. |
| **Description** | Optional. Add a description if needed. |
| **Availability Zone** | Leave the default value **nova**. |
| **Count** | Specify the number of instances to deploy. |

#### Tab: Source

![horizon-compute-instances-launch-instance-source](images/03-create-instance-horizon-source.png){.thumbnail}  

| Field | Description |
|--------|--------------|
| **Boot Source** | Select the boot source: *Image* or *Instance Snapshot*. |
| **Image Name** | Choose the image to use (e.g. *Debian 12 BMPOD*). |

#### Tab: Flavor

![horizon-compute-instances-launch-instance-flavor](images/03-create-instance-horizon-flavor.png){.thumbnail}  

Select the appropriate **hardware configuration** (vCPU, memory, storage).

#### Tab: Networks

![horizon-compute-instances-launch-instance-network](images/03-create-instance-horizon-networks.png){.thumbnail}  

Select the **private network** previously created.  
You can also attach an existing **network port** from the *Network Ports* tab.

---

### 4. Managing SSH key pairs

> Although selecting an SSH key in Horizon is not mandatory, it is **essential for connecting to the instance** once it has been created.  

![horizon-compute-instances-launch-instance-key-pairs](images/03-create-instance-horizon-key-pairs.png){.thumbnail}  

#### Create a new key pair

1. Click **+ Create Key Pair**.  
2. Fill in the following fields:

| Field | Description |
|--------|--------------|
| **Key Pair Name** | Enter a name for the key. |
| **Key Type** | Select **SSH Key**. |

3. Click **Create Keypair**.  
4. Copy the private key with **Copy Private Key to Clipboard**, then click **Done**.  
![horizon-compute-instances-launch-instance-key-pairs-create-step01](images/03-create-instance-horizon-key-pairs-create-step01.png){.thumbnail}  

5. The key is now selected by default. Click **Launch Instance** to start creating the instance.  
![horizon-compute-instances-launch-instance-key-pairs-create-step02](images/03-create-instance-horizon-key-pairs-create-step02.png){.thumbnail}  

#### Import an existing key

1. Click **Import Key Pair**.  
2. Fill in the following fields:

| Field | Description |
|--------|--------------|
| **Key Pair Name** | Name of the key. |
| **Key Type** | Select **SSH Key**. |
| **Public Key** | Paste your public key or upload the corresponding file. |

3. Click **Import Key Pair**.  
![horizon-compute-instances-launch-instance-key-pairs-import-step01](images/03-create-instance-horizon-key-pairs-import-step01.png){.thumbnail}  

4. The key is now selected by default. Click **Launch Instance** to start creating the instance.  
![horizon-compute-instances-launch-instance-key-pairs-import-step02](images/03-create-instance-horizon-key-pairs-import-step02.png){.thumbnail}  

---

### 5. Other options

The other configuration tabs (Security Groups, Configuration, Metadata, etc.) are not required for a standard installation.  
To learn more, refer to the [official OpenStack documentation](https://docs.openstack.org/).

### 6. References

- [OpenStack Official Documentation – Horizon](https://docs.openstack.org/horizon/latest/)  
- [OpenStack Networking Guide (Neutron)](https://docs.openstack.org/neutron/latest/)  
- [OpenStack Compute Guide (Nova)](https://docs.openstack.org/nova/latest/)  
- [OpenStack Key Pairs](https://docs.openstack.org/nova/latest/user/ssh-keys.html)  
- [Debian 12 Official Site](https://www.debian.org/releases/book/)
