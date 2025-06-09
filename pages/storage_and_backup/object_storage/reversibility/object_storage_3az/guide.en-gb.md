---
title: Object Storage 3AZ product reversbility policy
updated: 2025-06-09
---

**Objective**

This document outlines the reversibility policy for the product Object Storage 3AZ. 

This policy aims to implement the general principles of reversibility and our compliance with the SWIPO IaaS Code of Conduct for cloud providers.

**List of features**

The functionalities of the Product are divided into three categories:

* The main [features for which we guarantee you the possibility to migrate.](https://help.ovhcloud.com/csm)
* OVHcloud is currently in operation, and [the migration will require adaptations to a new environment.](https://help.ovhcloud.com/csm)
* Specified functionalities whose migration as such is impossible to guarantee because they are linked to the OVHcloud environment or specific developments.

**Main features**

| **Functionality** | **Description** | **Formats**  **Available** | **Migration model** | **Documentation available** |
| --- | --- | --- | --- | --- |
| S3 API Compatibility | S3 compatible interface (standard RESTful API, AWS CLI tools, SDK, etc.) | S3 (REST, JSON, multipart upload) | **Incoming** : Direct upload via  **compatible S3** API, CLI tools, SDK or migration from any other S3-compatible storage. Outbound: Direct upload/export via S3 API, CLI or SDK to any other S3-compatible provider. | [S3 API](https://help.ovhcloud.com/csm/fr-public-cloud-storage-pcs-s3-swift-rest-api-compatibility?id=kb_article_view&sysparm_article=KB0047191) |
| Massive export/import of objects | Batch data import/export via S3 tools (sync, cp, etc.) | S3 (objects, folders) | **Inbound** : Use rclone or equivalent tools to migrate data from another solution  **Outgoing** : Massive export via the same tools to another S3 platform or compatible. | [Manage buckets](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-getting-started-object-storage?id=kb_article_view&sysparm_article=KB0047348) |
| Object versioning | Native management of object versions (storage of each version when editing/deleting) | S3 (versioning) | **Inbound** : Import  **versioned** objects from another S3. Outbound: Export versions via API/CLI, compatible with other S3. | [Getting started with versionning](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-versioning?id=kb_article_view&sysparm_article=KB0063856) |
| Server-side encryption (SSE-S3/SSE-C) | Native encryption of objects at rest, compatible with S3 standards | S3 (HSSE-S3, HSSE-C) | **Incoming** : Upload of encrypted or unencrypted data, transparent management.  **Output** : Export without adaptation, encryption maintained or reprocessed by the target. | [Object Storage Encryption](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-encrypt-objects-sse-c?id=kb_article_view&sysparm_article=KB0047314) |
| Interoperability with third-party solutions | Native support for Veeam, HYCU, Nextcloud, Kubernetes, etc. | S3 (API, JSON, objets) | **Incoming** : Direct integration via plugins or connectors.  **Output** : Export data via native tools or S3 API to the target. | [Object storage with Veeam](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-veeam?id=kb_article_view&sysparm_article=KB0047693) |

**OVHcloud Implementation**

| **Functionality** | **Description** | **Available formats** | **Migration model** | **Documentation available** |
| --- | --- | --- | --- | --- |
| Offsite Replication OVHcloud | Automatic replication of data to a separate OVHcloud 1-AZ region | S3 (replicated objects) | **Incoming** : Not applicable to direct import, requires OVHcloud configuration.  **Output** : Manual restore from the replicated region, then export to external target (requires adaptation if the target does not have an equivalent mechanism). | [Cross region replication](https://help.ovhcloud.com/csm/fr-public-cloud-storage-s3-asynchronous-replication-buckets?id=kb_article_view&sysparm_article=KB0062418) |
| Object Lock | Object immutability (WORM), prevents deletion/modification for a defined period | S3 (Object Lock) | **Inbound** : Requires the source to support S3 Object Lock.</b>  **Output: Export possible, but the target must support S3 locking or manual adjustment of immutability policies.** | [Object storage ObjectLock](https://help.ovhcloud.com/csm/fr-public-cloud-storage-s3-managing-object-lock?id=kb_article_view&sysparm_article=KB0047404) |
| ACL and advanced permissions management | Rights management via ACL S3, or specific policies | S3 (ACL, policies) | **Incoming** : Adaptation of permissions according to the target structure.  **Outgoing** : Export of objects, but reconfiguration of ACL/policies required on the destination platform | [Access management](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-bucket-acl?id=kb_article_view&sysparm_article=KB0057089) |

**Specific features**

| **Function** | **Description** | **Available formats** | **Migration model** | **Documentation available** |
| --- | --- | --- | --- | --- |
| Management via OVHcloud Manager/OVH API | OVHcloud proprietary GUI and API for storage management | N/A | **Incoming** : Not applicable.  **Output** : Scripts/API to be rewritten for the target environment. | [Manage-buckets](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-getting-started-object-storage?id=kb_article_view&sysparm_article=KB0047348) |

**List of architectures**

Object Storage 3-AZ by OVHcloud is based on a multi-AZ architecture, with automatic distribution of data to three physically separated availability zones (data centers several kilometers apart). This architecture uses erasure coding to ensure local redundancy and tolerance for loss of a complete zone, thus ensuring high availability (SLA 99.99%) and continuity of service even in the event of major outages. Asynchronous inter-region replication is available as an option (Offsite Replication), allowing automatic data backup to another 1-AZ OVHcloud region

**Partner services**

OVHcloud partners are listed with the keyword â€œCloud Migrationâ€ in the [dedicated directory](https://partner.ovhcloud.com/fr/directory/).

**Cost and costs**

**No termination fees:** No on-demand billing. The service is stopped immediately after the service is removed.

**Data retention after termination of the contract**

The data is deleted by the customer himself. OVHcloud does not store any data. Prior manual export is required to preserve data.

A point of attention regarding the ObjectLock feature. More information to find on the product doc here:  [ObjectLock](https://docs.ovh.com/gb/en/storage/s3/object-lock/)

Once the service is terminated by the client, OVHCloud releases the resources that were allocated.
