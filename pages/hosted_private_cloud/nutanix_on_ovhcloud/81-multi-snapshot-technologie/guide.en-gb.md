---
title: Setting up Multicloud Snapshot Technology (MST)
excerpt: 'How to activate MST with an OVHcloud S3 container'
updated: 2025-09-18
---


## Objective

This guide describes how to deploy and configure **Multicloud Snapshot Technology (MST)** on a Nutanix on OVHcloud infrastructure with OVHcloud object storage.
With MST, you can **replicate snapshots** (UVM/Volume Groups) to **S3-compatible storage** to optimize TCO, improve data mobility, and simplify disaster recovery (DR.) using a **zero-compute** model.

---

## 1. Overview & advantages

**Main features:**
- Periodic replication of snapshots to S3 buckets (typical RPO: 1 hour via the Nutanix DR. infrastructure).
- Model **Zero-Compute**: no need to maintain compute standby nodes.
- Store recent snapshots on the main cluster; offload older snapshots to object storage.
- Restore anywhere **Nutanix Cloud Platform (NCP)**: cloud, edge, on-prem.
- Native integration with **Prism Central** and existing DR. workflows.

**Benefits:**
- Reduced TCO (reduced/no standby compute, less expensive object storage).
- Mobility: retrieve workloads on different NCP environments.
- Manageability via Prism.

---

## 2. Requirements

### Nutanix Cluster
- AOS 7.3 minimum
- Prism Central 7.3 minimum

### Network
- Create an **MST dedicated subnet** in Prism Element (internal network).
- **3 static IP addresses** reserved (outside the DHCP range of the subnet MST).
- **4 IP addresses** from the DHCP range of the MST subnet (consumed by the 4 MST VMs).

### VM resources (typical — Instance *Small*)
- 3 × **MSP Controller VMs**: 10 vCPU / 24 GiB RAM each.
- 1 × **MSP Load Balancer VM**: 2 vCPU / 4 GiB RAM.
- **Total**: 32 vCPU and 76 GiB RAM.

### Accounts/Access
- **admin** Prism Central account (only an admin can deploy an MST).
- API/credentials access for the S3 bucket with write/list/delete permissions.

### Functional limits (Instance Small)
- Up to **2000 protected entities**.
- **75 Recovery Points** per entity.
- **300 TB** of supported active data.

---

## 3. Deployment procedure (step by step)

### Prepare the environment
#### Create the Object Storage container (Bucket)

To create the container, you first need to create a project: [Create your first Public Cloud project - OVHcloud](https://help.ovhcloud.com/csm/en-public-cloud-compute-create-project?id=kb_article_view&sysparm_article=KB0050614)

In the Public Cloud universe

![01 Object Storage](images/mst1.png){.thumbnail}

create a user, for example *admin-mst-gra*

![02 Object Storage](images/mst2.png){.thumbnail}

Please note the following information:

![03 Object Storage Credentials](images/mst3.png){.thumbnail}

Then create a container (bucket): [Object Storage - Getting started with Object Storage - OVHcloud](https://help.ovhcloud.com/csm/fr-public-cloud-storage-s3-getting-started-object-storage?id=kb_article_view&sysparm_article=KB0047354)

In this example, I chose to create a container named: mst-dr-gra in Gravelines, since my cluster is Roubaix. This improves data resilience.

![04 Object Storage Container](images/mst4.png){.thumbnail}

>Once you have created the container and the user, you will need to have several pieces of information that are important to you:
>- name of your container: mst-dr-gra
>- url of the container endpoint: [https://s3.gra.io.cloud.ovh.net/](https://s3.gra.io.cloud.ovh.net/)
>- the**access key**
>- the **secret key**

#### Activate the Market Place

Log in to Prism Central, go to the admin center, then click Enable Mask Place

![05 Enable Market Place](images/mst5.png){.thumbnail}

#### Enable _Network Controller_

In _Infrastructure_ go to _Prism Central Settings_, then _Network Controller_

![06 Enable Network Controller](images/mst6.png){.thumbnail}

#### Create a Subnet dedicated to MST

We will create an IPAM subnet with a DHCP for using MST.

![07 IPAM Network](images/mst7.png){.thumbnail}

#### Reconfigure the Gateway

You will need to reconfigure the gateway with the new network.

Add a NIC to your VM:

![08 IPAM Network](images/mst8.png){.thumbnail}

Then reconfigure your gateway with the IP defined in the IPAM network creation.
On my alpine vm:

![09 gateway setup](images/mst9.png){.thumbnail}

I would add:

‘bash
auto eth3
iface eth3 inet static
address 10.8.0.254
netmask 255.255.255.0
“

Restarting network services:

![10 gateway setup2](images/mst10.png){.thumbnail}

### Deploy Multicloud Snapshot Technology

Log in to *Prism Central* as an**administrator**.
Go to **Admin Center → Marketplace**.
In *Nutanix Apps*, click **Get** for *Multicloud Snapshot Technology*.

![11 get mst](images/mst11.png){.thumbnail}

On the introduction page, click **Deploy**.

![12 Deploy mst](images/mst12.png){.thumbnail}

Then configure the MST instance:
- **MST Instance Size** : select `Small` (or other size if available).
- **Cluster Details**: choose the target Prism Element cluster.
- **Network Configuration**: select the MST subnet created.
- **Enter the 3 static IPs** reserved (expected fields).

![13 Deploy mst parameters](images/mst13.png){.thumbnail}

- **Object Store Provider**: select `Nutanix Object Store`
- **Object Store Endpoint**: enter your container's endpoint url, in our example [https://s3.gra.io.cloud.ovh.net/](https://s3.gra.io.cloud.ovh.net/)
- **Bucket Name**: enter the name of your container, in our example mst-dr-gra
- **Access Key**: enter your container’s ‘Access Key’
- **Secret Key**: enter the`Secret Key` of your container

![14 Deploy mst bucket parameters](images/mst14.png){.thumbnail}

Launch the deployment.

![15 End of mst deployment](images/mst15.png){.thumbnail}

## 4. Disaster Recovery: use and configuration
Once you have deployed an MST and connected to your Object Storage bucket, you can configure how your workloads are protected and restored.

### Entity protection
- **Steps:**
1. From **Prism Central**, go to **Protection Policies**, then create a protection policy.

![16 Create Protection policies](images/mst16.png){.thumbnail}

2. Define the policy name, the primary location: your cluster, in the Recovery Location keep Local AZ and select the container (Bucket) previously configured.

![17 Create Protection policies](images/mst17.png){.thumbnail}

3. Define an Add Schedule:
- frequency of snapshots (default every hour).
- The number of Recovery Points to keep locally.
- The number of Recovery Points to keep on the OVHcloud S3 container**.

![18 Define Schedule](images/mst18.png){.thumbnail}

4. Protect VMs
- Select the VMs you want to protect, then in action, data protection click _Protect_

![19 Protect VMs](images/mst19.png){.thumbnail}

- then select the _Protection policy_ you created earlier

![20 Protect VMs PP](images/mst20.png){.thumbnail}

### Restoration
- From **Prism Central, Data Protection, VM Recovery Points **, choose a **Recovery Point** available in the bucket.

![21 Select Restore Point](images/mst21.png){.thumbnail}

### Typical use cases
- **Disaster Recovery (DR.)**: total loss of the source cluster → deployment of VMs on another Nutanix cluster linked to the same OVHcloud bucket.
- **Workload migration**: move an application to another site (edge or cloud) by importing snapshots from the bucket.

---


## Go further <a name="gofurther"></a>

If you require training or technical support to implement our solutions, please contact your sales representative or click [this link](/links/professional-services) to get a quote and request a custom analysis of your project from our Professional Services team experts.

Join our [community of users](/links/community).

[Nutanix Reimagines Business Continuity for Hybrid Multicloud Users](https://www.nutanix.com/blog/nutanix-reimagines-business-continuity-for-hybrid-multicloud-users)
[Cloud Clusters (NC2) Hosted - Deploying Multicloud Snapshot Technology](https://portal.nutanix.com/page/documents/details?targetId=Nutanix-Clusters-AWS:aws-cluster-protect-deploying-mst-t.html)

