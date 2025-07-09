---
title: "Reversibility Policy for the Managed Search Engine Software Platform product"
updated: 2025-06-27
---

##Objective

This document describes the reversibility policy for the Managed Search Engine Software Platform product covering the OVHcloud Managed OpenSearch offer.

This policy aims to implement the general reversibility principles and our compliance with the SWIPO IAAS Code of Conduct for cloud providers.

##List of features

Features of the product line fall into three categories:

1. **Core features** for which we guarantee migration capacity.
2. **OVHcloud implementations** that require adaptation to a new migration environment.
3. **Specific features** that cannot be guaranteed for migration as they are related to the OVHcloud environment or involve custom developments.

## 1-Core features

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| Platform as a Service | NoSQL indexing, content search and data analysis engine fully managed by OVHcloud | JSON (S3 snapshots) | **Inbound** : source snapshot creation, migration via RFS to the platform <br>**Outbound** : export OVHcloud snapshots to any compatible OpenSearch cluster via RFS or native tools | [OpenSearch-Getting started](/pages/public_cloud/public_cloud_databases/opensearch_02_getting_Started) |
| Standard REST API access | Access via OpenSearch REST API (port 9200) | JSON | **Inbound**: direct connection from existing tools and applications <br>**Outbound**: data extraction via API for migration to another cluster. | [OVH-OpenSearch API](https://eu.api.ovh.com/console/?section=%2Fcloud&branch=v1#get-/cloud/project/-serviceName-/database/opensearch) |
| Manual snapshots | Create snapshots manually via API or Dashboard | JSON (S3, external storage) | **Inbound**: restoring an external snapshot. <br>**Outbound**: snapshot exportable to any OpenSearch environment. | [OVH-OpenSearch API](https://eu.api.ovh.com/console/?section=%2Fcloud&branch=v1#get-/cloud/project/-serviceName-/database/opensearch) |
| Standard plugins | List of open-source plugins (ICU Analysis, Phonetic Analysis, etc.) that can be activated, deactivated and compatible with the technology   | Official OpenSearch plugins | **Inbound**: Enable plugins compatible with the target version <br>**Outbound**: reuse plugins if it's are supported by the new environment | [OpenSearch - Capabilities and Limitations](/pages/public_cloud/public_cloud_databases/opensearch_01_capabilities) |


## 2-OVHcloud Implementations

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |


## 3-Specific features

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| Anti-DDoS protection| Anti-DDoS is a set of tools and mechanisms designed to absorb denial of service attacks. It includes traffic analysis, "clean-up" via a specialized network, and mitigation using VAC technology developed by OVHcloud. | N/A | **Inbound**: The anti-DDoS system is part of our infrastructure and is enabled by default. No action is required <br> **Outbound**: Order and configure an anti-DDoS solution from the new provider | [Anti-DDoS OVHcloud](https://www.ovhcloud.com/en/security/anti-ddos/) |

##List of architectures
xxxx

The product is divided into two service offers:

* xxxx
* xxx

##Partner services

The OVHcloud partners concerned are listed in the [OVHcloud partners directory](/links/partner) under the "**Data center expansion and Migration**" keywords.

OVHcloud also has a dedicated service: [OVHcloud Professional Services](/links/professional-services).

##Cost and fees

##Data retention after contract termination 


