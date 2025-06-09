---
title: Cold Storage product reversbility policy
updated: 2025-06-09
---

## Objective

This document outlines the reversibility policy for the product Cold Storage covering OVHcloud offer Cold Archive.

This policy aims at implementing the global reversibility principles and requirements of SWIPO IaaS Code of Conduct for Cloud Providers.

## Features map

Product Name  features are divided into three categories:

- The [core features](#core-features) for which we guarantee the ability to migrate
- The [OVHcloud implementation](#ovhcloud-implementation), whose migration will require adaptations to a new environment.
- [Specific functionalities](#specific-functionalities), whose migration as such is impossible to guarantee as they are tied to OVHcloud environment or specific developments.

### Core features 

|Feature|Description|Available formats|Migration model|Available documentation|
|---|---|---|---|---|
| **Standard S3 API Compatibility**| Access and management via S3-compatible API (RESTful, AWS CLI tools, SDK, etc.). | S3 (REST, JSON, objects) | **Incoming**: Direct upload into an Object Storage bucket via S3 API, CLI, or SDK. <br> **Outgoing**: Direct retrieval/export via S3 API, CLI, or SDK to any other S3-compatible provider. |  [Cold Archive offer presentation](https://www.ovhcloud.com/fr/public-cloud/cold-archive/) <br> [Cold Archive offer documentation](https://help.ovhcloud.com/csm/en-gb-documentation-storage-object-storage?id=kb_browse_cat&kb_id=38e74da5a884a950f07829d7d5c75217&kb_category=b29021c8e5a5edd0f078850a25104df8&spa=1) |
| **Massive Import/Export of objects**    | Batch data migration using S3 commands (`aws s3 cp/sync`, etc.). | S3 (objects, folders)| **Incoming**: Copy data from another S3 solution to OVHcloud Object Storage bucket. <br> **Outgoing**: Massive export via same tools to another S3 or compatible platform. | [Cold Archive offer documentation](https://help.ovhcloud.com/csm/en-gb-documentation-storage-object-storage?id=kb_browse_cat&kb_id=38e74da5a884a950f07829d7d5c75217&kb_category=b29021c8e5a5edd0f078850a25104df8&spa=1) |
| **Server-Side Encryption**| Native AES-256 bucket-level encryption, compatible with S3 SSE. | S3 (SSE-S3, SSE-C) | **Incoming**: Upload of encrypted or unencrypted data, transparently handled. <br> **Outgoing**: Export without adaptation; encryption maintained or reprocessed by the target. | [Cold Archive offer documentation](https://help.ovhcloud.com/csm/en-gb-documentation-storage-object-storage?id=kb_browse_cat&kb_id=38e74da5a884a950f07829d7d5c75217&kb_category=b29021c8e5a5edd0f078850a25104df8&spa=1) |
| **Long-Term data Retention** | Data stored on magnetic tapes, with a lifespan over 10 years. | S3 (objects) | **Incoming**: Import without adaptation. <br> **Outgoing**: Export of objects via S3 API; retrieval on any compatible storage. |[Cold Archive offer documentation](https://help.ovhcloud.com/csm/en-gb-documentation-storage-object-storage?id=kb_browse_cat&kb_id=38e74da5a884a950f07829d7d5c75217&kb_category=b29021c8e5a5edd0f078850a25104df8&spa=1) |

### OVHcloud implementation 

|Feature|Description|Available formats|Migration model|Available documentation|
|---|---|---|---|---|
| **Full Bucket Archiving**        | Archiving applies to the entire bucket (no object-level archiving). | S3 (bucket) | **Incoming**: Requires grouping of objects to archive into a dedicated bucket. <br> **Outgoing**: Export objects from the bucket, then import into the target (adaptation may be required if the target does not support bucket-level archiving). | [Cold Archive offer documentation](https://help.ovhcloud.com/csm/en-gb-documentation-storage-object-storage?id=kb_browse_cat&kb_id=38e74da5a884a950f07829d7d5c75217&kb_category=b29021c8e5a5edd0f078850a25104df8&spa=1) |
| **Delayed Restore (“unfreeze”)** | Data must be "unfrozen" before download (several hours of latency). | S3 (objects) | **Incoming**: Not applicable. <br> **Outgoing**: User must initiate a restore ("unfreeze") request, then download the objects within a 24-hour window; adaptation needed if the target lacks this mechanism. | [Cold Archive offer documentation](https://help.ovhcloud.com/csm/en-gb-documentation-storage-object-storage?id=kb_browse_cat&kb_id=38e74da5a884a950f07829d7d5c75217&kb_category=b29021c8e5a5edd0f078850a25104df8&spa=1)  |
| **Data Immutability** | Ability to make data immutable for a defined or indefinite period (WORM). | S3 (Object Lock) | **Incoming**: Source must support S3 data immutability. <br> **Outgoing**: Export possible, but target must support S3 locking or require manual adjustment of immutability policies. | [Cold Archive offer documentation](https://help.ovhcloud.com/csm/en-gb-documentation-storage-object-storage?id=kb_browse_cat&kb_id=38e74da5a884a950f07829d7d5c75217&kb_category=b29021c8e5a5edd0f078850a25104df8&spa=1)  |



### Specific functionalities 

|Feature|Description|Available formats|Migration model|Available documentation|
|---|---|---|---|---|
|**Anti-DDoS**|The anti-DDoS is a set of equipment and means put in place to absorb distributed denial of service attacks. It includes an analysis of traffic, the "aspiration" towards a specialized network, and mitigation, ensured by VAC technology developed by OVHcloud.|N/A|**Incoming**: The Anti-DDoS is a component of our infrastructure, enabled by default. No action is required.<br><br>**Outcoming**: Order and configure an anti-DDoS with the new provider.|[OVHcloud anti-DDoS protection](https://www.ovh.co.uk/anti-ddos/)<br><br>[Anti-DDoS Technology](https://www.ovh.co.uk/anti-ddos/anti-ddos-technology.xml)| 
| **OVHcloud 4-Datacenter Architecture** | Distribution across 4 datacenters in France using 8+4 erasure coding. | N/A    | **Incoming**: Not applicable. <br> **Outgoing**: Not transferable, depends on the target architecture. | [Cold Archive](https://www.ovhcloud.com/en/cold-archive/) |
| **Management via OVHcloud Manager/API** | Proprietary OVHcloud graphical interface and APIs for archive management. | N/A | **Incoming**: Not applicable. <br> **Outgoing**: Scripts/APIs need to be rewritten for the target; manual management may be required. | [Cold Archive offer documentation](https://help.ovhcloud.com/csm/en-gb-documentation-storage-object-storage?id=kb_browse_cat&kb_id=38e74da5a884a950f07829d7d5c75217&kb_category=b29021c8e5a5edd0f078850a25104df8&spa=1) |

### Architecture listing

OVHcloud's Cold Storage product is based on a geo-distributed architecture across four physically separated data centers (several kilometers apart), using IBM magnetic tape technology. Data is stored using 8+4 erasure coding, ensuring extreme resilience and tolerance to the loss of an entire site.

### Partner services

OVHcloud partners are listed under the keyword **"Cloud Migration"** in the dedicated partner directory.

OVHcloud also offers a dedicated service: [**OVHcloud Professional Services**](https://www.ovhcloud.com/fr/professional-services/).

### Cost and fees

No termination fees: There is no additional charge by default for data migration. Billing stops as soon as the service is terminated. However, a pricing change will occur when data is restored, based on the current pricing of the storage medium to which the data has been transferred.

### Retention of data after contract termination

OVHcloud does not retain any data after the service is terminated. Data are irreversibly deleted. A manual export must be performed beforehand to preserve the data.
To retrieve their data, the customer must unarchive it and then retrieve it from the bucket where it has been restored.
Note: the unarchiving process can take up to 48 hours.
