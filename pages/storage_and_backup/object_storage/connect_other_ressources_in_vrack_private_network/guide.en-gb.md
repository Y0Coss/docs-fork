---
title: Object Storage - How to connect my Object Storage buckets with other resource in a vRack Private Network?
excerpt: This guide explains how to use Object Storage together with resources in a Private Network. 
updated: 2025-03-25
---

## Objective

This guide explains how to use Object Storage together with resources in a Private Network. 

## Requirements

-	An [Object Storage bucket.](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage)
-	A [vRack Private Network service.](/pages/public_cloud/public_cloud_network_services/getting-started-07-creating-vrack)
-	A [Public Cloud Gateway.](/pages/public_cloud/public_cloud_network_services/getting-started-02-create-private-network-gateway)
-	Other resources (Public Cloud instances, Managed Kubernetes, Bare Metal servers…)

## Instructions

### Context

Your use case may require a secure connection between a private network and your Object Storage bucket. Our vRack Private Network & Public Cloud Gateway services will help meeting your specific requirements both in terms of security and performance. 

This also allows you to interconnect both Object Storage buckets with your resources gathered in a vRack Private Network (see architecture diagram below).

![vrack private network with buckets - diagram](images/object_storage_buckets_vrack_private.png){.thumbnail}

### Creating a vRack Private Network and Public Cloud Gateway

In order to create and configure both a Public Cloud Gateway and a vRack Private Network, please follow the instructions in the [Creating a private network with Gateway documentation](/pages/public_cloud/public_cloud_network_services/getting-started-02-create-private-network-gateway). The documentation will explain how to:

-	Select and create the appropriate Gateway both in term of performance and geo-availability.
-	Attach to an existing or newly created vRack Private Network.

### Gateway IPs whitelisting

Once the Gateway has been created and associated to a vRack Private Network, the next step is to whitelist a set of IPs from your Object Storage. To do so, there are multiple ways:

-	using Object Storage Bucket Policies: the feature is not yet implemented but will be soon available.
-	we built an internal process helping you whitelisting a set of IPs based on your Gateway and vRack Private Network configuration.

To do so, please contact our technical support team with the specific request header “Object Storage – IP whitelisting process” with the list of IP ranges you would need to whitelist, and our team will automate the configuration for you. The workflow generally takes up to 1 day.

After this last step, you’re ready to use your Object Storage together with resources gathered in a vRack Private Network.

## Go further

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

Join our [community of users](/links/community).
