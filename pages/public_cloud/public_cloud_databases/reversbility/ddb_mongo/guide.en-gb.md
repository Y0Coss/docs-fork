---
title: "Reversibility Policy for Managed Document Database Product"
updated: 2025-06-06
---

**Objective**

This document outlines the reversibility policy for the product line Managed Document Database covering OVHcloud offer MongoDB.

This policy aims to implement the general principles of reversibility and our compliance with the SWIPO IaaS Code of Conduct for cloud providers.

**List of features**

The functionalities of the Product are divided into three categories:

* The main features for which we guarantee you the possibility to migrate.
* OVHcloud is currently in operation, and the migration will require adaptations to a new environment.
* Specified functionalities whose migration as such is impossible to guarantee because they are linked to the OVHcloud environment or specific developments.

**Main features**

| **Function** | **Description** | **Formats**  **Available** | **Migration model** | **Documentation available** |
| --- | --- | --- | --- | --- |
| Document oriented database | Flexible JSON/BSON data storage for high scalability | BSON, JSON, CSV | **Incoming** : import via mongorestore/mongoimport <br><br>  **Outgoing** : export via mongodump/mongoexport | [MongoDB documentation](https://docs.mongodb.com/) |
| Open-source MongoDB compatibility | Standard version of MongoDB without modification, facilitating portability | Standard MongoDB (CLI, API, tools) | **Incoming** : direct integration <br><br>  **Outgoing** : full export without adaptation | [MongoDB](https://help.ovhcloud.com/csm/en-gb-documentation-public-cloud-databases-mongodb?id=kb_browse_cat&kb_id=574a8325551974502d4c6e78b7421938&kb_category=7165a1f6259c6110f0782e7048ecedec&spa=1) |
| High availability | Replica sets ensuring redundancy and auto recovery | N/A | **Incoming** : configuration of replicas at import <br><br>  **Outgoing** : export and deployment on another cluster | [Replication](https://docs.mongodb.com/manual/replication/) |
| Automatic backups | Daily backups with possibility of restoration | Snapshots MongoDB | **Incoming** : restoration possible <br><br>  **Outgoing:** manual download/export required | [MongoDB Backups](docs/pages/public_cloud/public_cloud_databases/mongodb_06_howto_backup_restore) |

**OVHcloud Implementation**

| **Function** | **Description** | **Available formats** | **Migration model** | **Documentation available** |
| --- | --- | --- | --- | --- |
| OVHcloud Dashboard | MongoDB cluster management and monitoring interface | N/A | **Incoming** : initial configuration via the interface <br><br>  **Outgoing** : administration interrupted after termination | [MongoDB](https://help.ovhcloud.com/csm/en-gb-documentation-public-cloud-databases-mongodb?id=kb_browse_cat&kb_id=574a8325551974502d4c6e78b7421938&kb_category=7165a1f6259c6110f0782e7048ecedec&spa=1) |
| Integrated monitoring | Performance tracking via metrics in the interface | N/A | **Incoming** : alert configuration <br><br>  **Outgoing** : to be reconfigured in another environment | [MongoDB](https://help.ovhcloud.com/csm/en-gb-documentation-public-cloud-databases-mongodb?id=kb_browse_cat&kb_id=574a8325551974502d4c6e78b7421938&kb_category=7165a1f6259c6110f0782e7048ecedec&spa=1) |
| Network security (ACL) | IP filtering, TLS/SSL, and access restricted by vRack | IP, TLS/SSL | **Incoming** : definition of security rules <br><br>  **Outgoing** : export configuration | [MongoDB](https://help.ovhcloud.com/csm/en-gb-documentation-public-cloud-databases-mongodb?id=kb_browse_cat&kb_id=574a8325551974502d4c6e78b7421938&kb_category=7165a1f6259c6110f0782e7048ecedec&spa=1) |

**Specific features**

| **Function** | **Description** | **Available formats** | **Migration model** | **Documentation available** |
| --- | --- | --- | --- | --- |
| Private network OVHcloud (vRack) | Connection with other OVHcloud services in private network | N/A | **Incoming** : config vRack <br><br>  **Outgoing** : non-transferable functionality | [vRack](docs/pages/public_cloud/public_cloud_databases/databases_08_vrack) |
| Updates managed by OVHcloud | MongoDB versioning by OVHcloud | N/A | **Incoming** : check compatibility <br><br>  **Outgoing** : migration under client responsibility | [MongoDB](https://help.ovhcloud.com/csm/en-gb-documentation-public-cloud-databases-mongodb?id=kb_browse_cat&kb_id=574a8325551974502d4c6e78b7421938&kb_category=7165a1f6259c6110f0782e7048ecedec&spa=1) |
| Anti-DDoS | Anti-DDoS is a set of equipment and means put in place to absorb denial-of-service attacks. It includes traffic analysis, â€œaspirationâ€ to a dedicated network and mitigation, provided by VAC technology developed by OVHcloud. | N/A | **Incoming migration** : The anti-DDoS system is a component of our infrastructure, enabled by default. No action required. <br><br>   **Outbound migration** : Order and configure an anti-DDoS with the new provider. | [OVHcloudDDoS Protection](https://www.ovh.com/fr/anti-ddos/) |

**List of architectures**

Managed MongoDB relies on a distributed architecture with Replica Sets to ensure high availability. Data is distributed across multiple nodes with regular backups, continuous monitoring and integrated security tools.

**Partner services**

OVHcloud partners are listed with the keyword **Cloud Migration** in the [dedicated directory](https://partner.ovhcloud.com/fr/directory/).

OVHcloud also has a dedicated service: [OVHcloud Professional Services](https://www.ovhcloud.com/fr/professional-services/)

**Cost and costs**

Features described in tables are free of charge unless otherwise stated, and are freely usable by the customer

Billing is based on cluster size, storage capacity, and backups. There is no exit fee, but the data must be exported before termination as it will be deleted.

**Data retention after termination of the contract**

After termination, all data from the instance is permanently deleted including backups made by OVHcloud. It is the responsibility of the customer to complete the export before the end of the service, with OVHcloud not retaining any copies.

OVHcloud does not guarantee the use and availability of backups to restore customer data after termination of the service*.*

Primary instances are deleted immediately and backups are kept between 2 days and one month depending on the options specified in the contract.
