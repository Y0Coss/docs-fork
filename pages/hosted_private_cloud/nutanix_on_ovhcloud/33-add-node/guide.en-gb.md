---
title: "Add or Remove Nodes in a Nutanix Cluster (Scale In/Out)"
excerpt: 'Scale your Nutanix cluster on OVHcloud by adding or removing nodes via the Control Panel'
hidden: true
updated: 2025-05-22
---

<style>
 pre {
     font-size: 14px !important;
 }
 pre.bgwhite {
   background-color: #fff !important;
   color: #000 !important;
   font-family: monospace !important;
   padding: 5px !important;
   margin-bottom: 5px !important;
 }
 pre.bgwhite code {
   background-color: #fff !important;
   border: solid 0px transparent !important;
   font-family: monospace !important;
   font-size: 0.90em !important;
   color: #000 !important;
 }
 .small {
     font-size: 0.90em !important;
 }
</style>

## Objective

Nutanix clusters on OVHcloud are scalable. You can now **add (scale out)** or **remove (scale in)** nodes directly from the OVHcloud Control Panel.

> [!warning]
> OVHcloud provides services for which you are responsible, with regard to their configuration and management. You are therefore responsible for ensuring they function correctly.
>
> This guide is designed to assist you in common tasks as much as possible. Nevertheless, we recommend that you contact the [OVHcloud Professional Services team](https://www.ovhcloud.com/en-gb/professional-services/) or a [specialist service provider](https://partner.ovhcloud.com/en-gb/directory/) if you have difficulties or doubts concerning the administration, usage or implementation of services on a server.

## Requirements

- A Nutanix cluster hosted in your OVHcloud account
- Access to the [OVHcloud Control Panel](/links/manager)
- Access to the Prism Central administration interface
- Access to the [OVHcloud API](https://api.ovh.com/).

## Technical Information

- Your cluster must have between **3 and 15 nodes**
- All new nodes must run the **same AOS version** as the existing cluster

## Instructions

### Scale Out (add a node)

#### Add a node

1. From the [OVHcloud Control Panel](/links/manager), navigate to your Nutanix cluster via the `Hosted Private Cloud`{.action} and `Nutanix`{.action} menus.

![Nutanix cluster overview](images/control-panel.png){.thumbnail}

2. In the **General information** tab, you can see the **Number of nodes**. Click `Manage my nodes`{.action}.

![Number of nodes](images/manage-nodes.png){.thumbnail}

3. In the **Nodes** tab, select `Add nodes`{.action}.

![Add nodes tab](images/adding-nodes-03.png){.thumbnail}

5. Review the configuration and pricing in the pop-up window, then click `Order`{.action} to add the node(s).

![Order popup](images/adding-nodes-04.png){.thumbnail}

Once the node is delivered, you can see the status in the **General information** tab.

The **Number of nodes** area will show a new node to install.

![New node to install](images/adding-nodes-05.png){.thumbnail}

#### Install an OS

> [!tabs]
> OVHcloud Control Panel
>> 1. If you click `Manage my nodes`{.action} again, you will see a list of your nodes. For any node with an **OS not installed** status, click the *more options* `...`{.action} button and select `Install`{.action}.
>>
>> [Node status](images/install-os-01.png){.thumbnail}
>>
>> 2. Enter the configuration details for your node. Be sure to install the same AOS version as your cluster.
>>
>> Click  `Install`{.action}.
>>
>> ![Install option](images/install-os-02.png){.thumbnail}
>>
>> 3. A confirmation banner will appear.
>>
>> ![Confirmation message](images/install-os-03.png){.thumbnail}
>>
> OVHcloud API
>> To install your node via the [OVHcloud API](https://api.ovh.com/){.external}, use this call:
>>
>> > [!api]
>> > @api {v1} PUT /nutanix/{serviceName}/nodes/{server}/deploy

Once the node has been installed, you can connect to Prism Central/Element and expand your cluster. 

Please refer to the documentation below: 

- [Expanding a Cluster through Prism Central](https://portal.nutanix.com/page/documents/details?targetId=Prism-Central-Guide-vpc_2024_3_1:mul-node-add-pc-t.html)

- [Expanding a Cluster](https://portal.nutanix.com/page/documents/details?targetId=Web-Console-Guide-Prism-v7_0:wc-cluster-expand-wc-t.html)

### Scale In (remove a node)

#### Power down a node

1. From the [OVHcloud Control Panel](/links/manager), navigate to your Nutanix cluster via the `Hosted Private Cloud`{.action} and `Nutanix`{.action} menus.

![Nutanix cluster overview](images/control-panel.png){.thumbnail}

2. In the **General information** tab, you can see the Number of nodes. Click `Manage my nodes`{.action}.

![Manage my nodes](images/manage-nodes.png){.thumbnail}

3. Here, you have 2 options:

> [!tabs]
> OVHcloud Control Panel
>> For the node you wish to remove, click the *more options* `...`{.action} button and select `Power down`{.action}.
>> ![Power down](images/powerdown-nodes-01.png){.thumbnail}
>>
>> A warning pop-up will appear. Type the required term and click `Power down`{.action}.
>>
>> > [!info]
>> > **NOTE:** Powering down a Nutanix node may impact your cluster. Please check the [requirements on the Nutanix portal](https://portal.nutanix.com/page/documents/list?type=software) to complete this action.
>>
>> ![Power down warning](images/powerdown-nodes-02.png){.thumbnail}
>>
>> A confirmation banner will appear.
>> ![Power down confirmation](images/powerdown-nodes-03.png){.thumbnail}
>>
> OVHcloud API
>> You can also power down your node via the [OVHcloud API](https://api.ovh.com/){.external}.
>> Get the Boot ID: 
>> Enter *power* as the **bootType**.
>>
>> > [!api]
>> > @api {v1} GET /dedicated/server/{serviceName}/boot
>>
>> Set the Boot ID: 
>> > [!api]
>> > @api {v1} PUT /dedicated/server/{serviceName}
>>
>> Power down the node:
>> > [!api]
>> > @api {v1} POST /dedicated/server/{serviceName}/reboot

#### Uninstall the node

> [!tabs]
> OVHcloud Control Panel
>> Once the node is powered down, click the *more options* `...`{.action} button and select `Uninstall`{.action}.
>> ![Uninstall button](images/remove-nodes-01.png){.thumbnail}
>>
>> A warning pop-up will appear. Type the required term and click `Uninstall`{.action}.
>>
>> > [!info]
>> > **NOTE:** Uninstalling a Nutanix node may impact your cluster. Please check the [requirements on the Nutanix portal](https://portal.nutanix.com/page/documents/list?type=software) to complete this action.
>>
>> ![Uninstall warning](images/remove-nodes-02.png){.thumbnail}
>>
>> A confirmation banner will appear.
>>
>> ![Uninstall confirmation](images/remove-nodes-03.png){.thumbnail}
>>
> OVHcloud API
>> To uninstall your node via the [OVHcloud API](https://api.ovh.com/){.external}, use this call:
>> > [!api]
>> > @api {v1} POST /nutanix/{serviceName}/node/{server}/terminate

#### Remove the node

Once the node is uninstalled, click the *more options* `...`{.action} button and select `Terminate`{.action}.

![Remove the node](images/remove-nodes-04.png){.thumbnail}

A warning pop-up will appear. Type the required term and click `Confirm`{.action}.

> [!info]
> **NOTE:** Your suspended service will appear in your nodes list for approximately one week before being permanently deleted. This allows you to reactivate the service if you need to reverse the deletion.

## Go further

You can go even further by reading these guides:

[Nutanix Hyperconvergence](/pages/hosted_private_cloud/nutanix_on_ovhcloud/03-nutanix-hci)

[Nutanix Node Addition Guide](https://portal.nutanix.com/page/documents/details?targetId=Web-Console-Guide-Prism-v7_0:wc-cluster-expand-wc-t.html)

If you need training or technical assistance to implement our solutions, please contact your Technical Account Manager or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for a custom analysis of your project.

Ask questions, give your feedback and interact directly with the team building our Hosted Private Cloud services on the dedicated [Discord](https://discord.gg/ovhcloud) channel.

Join our [community of users](/links/community).