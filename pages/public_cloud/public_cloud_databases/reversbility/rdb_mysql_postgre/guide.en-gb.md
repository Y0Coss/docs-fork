 ---
title: "Reversibility Policy for Managed Relational Database Product"
updated: 2025-06-06
---

## Objective

This document outlines the reversibility policy for the product line Managed Relational Database covering OVHcloud offers : Managed MySQL & Managed PostgreSQL .

This policy aims to implement general reversibility principles and our compliance with the SWIPO IaaS Code of Conduct for cloud providers.



## List of Features

Features of the Product are divided into three categories:

- **Core features** for which we guarantee migration capability.
- **OVHcloud implementations** that require adaptation to a new environment for migration.
- **Specific features** that cannot be guaranteed for migration as they are tied to the OVHcloud environment or involve custom developments.



## Core Features

| Feature                  | Description                                  | Formats       | Migration Model                                                                                                                                           | Documentation Available |
|--------------------------|----------------------------------------------|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|
| **Export/Import - PostgreSQL** | Use of `pg_dump`/`pg_restore` for native data transfer.                                                       | SQL, CSV, BINARY     | **Incoming**: Restore via CLI with rights adjustments. <br> **Outgoing**: Standard dump export.                     | [OVH - How to migrate](https://support.us.ovhcloud.com/hc/en-us/articles/21485451623059-PostgreSQL-Tutorial-How-to-Migrate-an-On-Premises-Database-to-Cloud-Databases)                      |
| **Export/Import - MySQL**      | Export and import using native MySQL tools (`mysqldump`, `mysql`, etc.).                                      | SQL, CSV             | **Incoming**: Export from source (SQL dump), then import into Managed MySQL via `mysql` or OVHcloud UI. <br> **Outgoing**: SQL dump via `mysqldump`, then import into target environment (cloud or on-premises). | [MySQL - Capabilities and Limitations](https://support.us.ovhcloud.com/hc/en-us/articles/20887483746067-MySQL-Capabilities-and-Limitations)                      |
| **Service Access - MySQL**     | Access to the database via standard MySQL protocol on a dynamic port made available in the OVHcloud Manager.   | N/A                  | **Incoming**: Connection from existing tools or applications. <br> **Outgoing**: Connect from any standard MySQL client for data extraction or migration. | [MySQL - Connect via Command Line (CLI)](https://support.us.ovhcloud.com/hc/en-us/articles/20805146473875-MySQL-Connect-with-CLI)<br>[MySQL - Connect with PHP](https://support.us.ovhcloud.com/hc/en-us/articles/20815696722963-MySQL-Connect-with-PHP)<br>[MySQL - Connect with Python](https://support.us.ovhcloud.com/hc/en-us/articles/20840434483219-MySQL-Connect-with-Python)<br>[MySQL - Connect with MySQL Workbench](https://support.us.ovhcloud.com/hc/en-us/articles/20845437747987-MySQL-Connect-with-MySQL-Workbench)|
| **Service Access - PostgreSQL**| Access via PostgreSQL protocol, compatible with standard clients and tools.                                    | N/A                  | **Incoming**: Direct connection from existing tools/applications. <br> **Outgoing**: Standard connection for extraction or migration. | [PostgreSQL - Connect via Command Line (CLI)](https://support.us.ovhcloud.com/hc/en-us/articles/21410499182995-PostgreSQL-Connect-with-CLI)<br>[PostgreSQL - Connect with PHP](https://support.us.ovhcloud.com/hc/en-us/articles/20898939497107-PostgreSQL-Connect-with-PHP)<br>[PostgreSQL - Connect with Python](https://support.us.ovhcloud.com/hc/en-us/articles/21408187602451-PostgreSQL-Connect-with-Python)<br>[PostgreSQL - Connect with pgAdmin](https://support.us.ovhcloud.com/hc/en-us/articles/21489279019155-PostgreSQL-Connect-with-pgAdmin)|
| **Manual Backup**              | Ability to generate a full on-demand database backup.                                                          | SQL, CSV, tar        | **Incoming**: Restore from existing SQL dump. <br> **Outgoing**: SQL dump generated from OVHcloud instance, usable on any compatible MySQL environment. | [MySQL dump](https://dev.mysql.com/doc/refman/8.4/en/mysqldump.html)                |


## OVHcloud Implementation

| Feature         | Description                                                                                                       | Available Formats | Migration Model                                                                                                                          | Documentation Available |
|------------------|-------------------------------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|
| **OVHcloud Automatic Backups**   | Backups managed by OVHcloud, not directly exportable outside the OVH ecosystem.                                          | Internal snapshots | **Incoming**: Not applicable for direct import. <br> **Outgoing**: Requires restoration on OVHcloud instance, then manual export (SQL dump) for migration. | [Databases & Analytics - Automated backups](https://support.us.ovhcloud.com/hc/en-us/articles/20735484294547-Databases-Analytics-Automated-backups)     |
| **Point in Time Recovery (PITR)**| Restore to a specific point in time using OVHcloud internal snapshots.                                                   | Internal snapshots | **Incoming**: Not applicable for direct import, prior restoration required. <br> **Outgoing**: Export restored snapshot as SQL dump, then manual import in target environment. | [Databases & Analytics - Automated backups](https://support.us.ovhcloud.com/hc/en-us/articles/20735484294547-Databases-Analytics-Automated-backups)     |
| **OVHcloud API**                 | Manage databases via OVHcloud REST API or graphical interface.                                                           | N/A                | **Incoming**: Automated creation and import of instances. <br> **Outgoing**: Data export via API or automated dump scripts. |[Premiers pas avec les API OVHcloud](https://help.ovhcloud.com/csm/fr-api-getting-started-ovhcloud-api?id=kb_article_view&sysparm_article=KB0042789)     |
| **OVHcloud Connection Pooling**  | Automatic PostgreSQL connection pooling, not directly portable.                                                          | N/A                | **Incoming**: May require adaptation depending on source setup. <br> **Outgoing**: Pooling must be reconfigured on target infrastructure. | [PostgreSQL - Create and Use Connection Pools](https://support.us.ovhcloud.com/hc/en-us/articles/21419624594323-PostgreSQL-Create-and-Use-Connection-Pools)                |
| **Observability**               | Metrics collection via OVHcloud-integrated Prometheus.                                                                   | Prometheus metrics | **Incoming**: Adapt dashboards and metrics to OVHcloud environment. <br> Outgoing: Metrics export possible, requires adaptation on new monitoring platform. | [MySQL - Capabilities and Limitations](https://support.us.ovhcloud.com/hc/en-us/articles/20887483746067-MySQL-Capabilities-and-Limitations)<br>[PostgresSQL â€“ Capabilities and Limitations](https://support.us.ovhcloud.com/hc/en-us/articles/21485451623059-PostgreSQL-Tutorial-How-to-Migrate-an-On-Premises-Database-to-Cloud-Databases)     |
| **vRack**                          | Virtual rack (vRack) is a private VLAN technology that connects OVHcloud services.                           | N/A                   | **Incoming** MySQL and PostgreSQL services are included in vRack by default. <br> **Outgoing:** Record the network architecture and replicate it using VLANs.               | [V(x)LAN creation](https://help.ovhcloud.com/csm/fr-vmware-vlan-creation?id=kb_article_view&sysparm_article=KB0045480)<br>[Public Cloud Databases](https://help.ovhcloud.com/csm/fr-public-cloud-databases-configure-vrack?id=kb_article_view&sysparm_article=KB0048824) |
| **Role and Permission Adaptation**| No superuser (e.g., `postgres`); roles must be adapted to `avnadmin` or equivalent.                                     | N/A                | **Incoming**: Modify dump to replace superuser roles with OVH-compatible roles. <br> **Outgoing**: Reverse adaptation based on target environment privileges. | [PostgresSQL â€“ Capabilities and Limitations](https://support.us.ovhcloud.com/hc/en-us/articles/21485451623059-PostgreSQL-Tutorial-How-to-Migrate-an-On-Premises-Database-to-Cloud-Databases)                |
| **OVHcloud ACL Management**      | Access rights managed through OVHcloud interface.                                                                       | N/A                | **Incoming**: Manually recreate rules in the OVHcloud interface. <br> **Outgoing**: Convert ACL rules to the new providerâ€™s format. | [MySQL - Capabilities and Limitations](https://support.us.ovhcloud.com/hc/en-us/articles/20887483746067-MySQL-Capabilities-and-Limitations)<br>[PostgresSQL â€“ Capabilities and Limitations](https://support.us.ovhcloud.com/hc/en-us/articles/21485451623059-PostgreSQL-Tutorial-How-to-Migrate-an-On-Premises-Database-to-Cloud-Databases)     |


## Specific Features

| Function               | Description                                                                           | Formats Available | Migration Model                                                                                   | Documentation Available |
|------------------------|---------------------------------------------------------------------------------------|--------------------|----------------------------------------------------------------------------------------------------|--------------------------|
| **OVHcloud Database Forking**    | Instant duplication of a database via OVHcloud's native "fork" feature.                                                  | OVHcloud internal   | **Incoming**: Feature not available for import. <br> **Outgoing**: Not portable â€” requires manual data export to replicate elsewhere. | [Databases & Analytics - Restore a backup](https://support.us.ovhcloud.com/hc/en-us/articles/20584170298515-Databases-Analytics-Restore-a-backup) |
| **Infrastructure as Code** | Automated deployment via OVHcloud-specific Terraform modules                           | N/A                | **Incoming:** Scripts need to be adapted for other providers.  <br> **Outcoming:** Configuration rewrite required for Terraform.                             | [Terraform](https://registry.terraform.io/providers/ovh/ovh/latest/docs)                      |
| **OVHcloud-Managed Updates**     | MySQL or PostgreSQL versioning and updates are managed by OVHcloud.                                                     | N/A                 | **Incoming**: Ensure compatibility. <br> **Outgoing**: Migration responsibility falls to the customer.                | [MySQL - Capabilities and Limitations](https://support.us.ovhcloud.com/hc/en-us/articles/20887483746067-MySQL-Capabilities-and-Limitations)<br>[PostgresSQL â€“ Capabilities and Limitations](https://support.us.ovhcloud.com/hc/en-us/articles/21485451623059-PostgreSQL-Tutorial-How-to-Migrate-an-On-Premises-Database-to-Cloud-Databases)     |
| **Anti-DDoS** | Anti-DDoS is a set of tools and mechanisms designed to absorb denial-of-service attacks. It includes traffic analysis, "scrubbing" through a specialized network, and mitigation handled by the VAC technology developed by OVHcloud.                                                  | N/A                | **Incoming:** The anti-DDoS system is part of our infrastructure and is enabled by default. No action is required.  <br> **Oucoming:** Order and configure an anti-DDoS service with the new provider.             | [Anti-DDoS Protection](https://www.ovh.com/fr/anti-ddos/)<br>[Anti-DDoS technologie](https://www.ovh.com/fr/anti-ddos/technologie-anti-ddos.xml)                        |



## List of Architectures

**Managed MySQL and Managed PostgreSQL** support different architectures depending on the selected service tier.  
The **Business** and **Enterprise** plans offer **high availability** with multiple nodes and **automatic asynchronous replication**.



## Partner Services

OVHcloud partners are listed under the keyword **"Cloud Migration"** in the dedicated partner directory.

OVHcloud also offers a dedicated service: [**OVHcloud Professional Services**](https://www.ovhcloud.com/fr/professional-services/).



## Cost and Fees

- **No termination fees**: There are no additional charges related to data migration by default.
- Billing stops as soon as the service is terminated.



## Data Retention After Contract Termination

OVHcloud **does not retain any data** after a Managed Data Visualization cluster is deleted.
Both **automatic and manual snapshots are permanently deleted**. 
A **manual export** must be performed in advance if data needs to be preserved.   
Primary instances are **deleted immediately**, and **backups are retained for a period ranging from 2 days to 1 month**
> **Important:** Clients cannot rely on these backups for data restoration.  
> OVH does not guarantee the usability or availability of backups for restoring customer data after the termination of the service.

