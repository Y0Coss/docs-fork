---
title: "Reversibility Policy for the Managed Database System for Web Hosting product"
updated: 2025-08-21
---

##Objective

This document describes the reversibility policy for the Managed Database System for Web Hosting product covering the OVHcloud Web Hosting offer.

This policy aims to implement the general reversibility principles and our compliance with the SWIPO IAAS Code of Conduct for cloud providers.

## List of features

Features of the product line fall into three categories:

1. **Core features** for which we guarantee migration capacity.
2. **OVHcloud implementations** that require adaptation to a new migration environment.
3. **Specific features** that cannot be guaranteed for migration as they are related to the OVHcloud environment or involve custom developments.

## 1. Core features

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| Database package for a standard web hosting plan| Using standard open-source components | SQL, NoSQL | **Inbound**: copy of application files, import of databases via SQL dump, standard configuration <br>**Outbound**: export files/dumps, reusable on any compatible environment | [Creating a database on your web hosting plan](/pages/web_cloud/web_hosting/sql_create_database) |
| Export and import a database | Backup and restore databases via the API or the OVHcloud Control Panel | SQL, CSV | **Inbound**: Import an existing SQL dump <br>**Outbound**: Export an SQL dump, which can be imported on any MySQL/MariaDB/PostgreSQL server | [Importing a backup into a Web Hosting plan database](/pages/web_cloud/web_hosting/sql_importing_mysql_database) |
| Users and permissions | User and rights management system stored in the database | NA | **Inbound**: import users and permissions via database dump <br>**Outbound**: export users and permissions via database dump | [Changing the password for a Web Hosting plan’s database](/pages/web_cloud/web_hosting/sql_change_password) |



## 2. OVHcloud Implementations

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |


## 3. Specific features

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| Anti-DDoS protection| Anti-DDoS is a set of tools and mechanisms designed to absorb denial of service attacks. It includes traffic analysis, "clean-up" via a specialized network, and mitigation using VAC technology developed by OVHcloud. | N/A | **Inbound**: The anti-DDoS system is part of our infrastructure and is enabled by default. No action is required <br> **Outbound**: Order and configure an anti-DDoS solution from the new provider | [Anti-DDoS OVHcloud](/links/security/anti-ddos) |

## List of architectures
xxxx

The product is divided into two service offers:

* xxxx
* xxx

##Partner services

The OVHcloud partners concerned are listed in the [OVHcloud partners directory](/links/partner) under the "**Data center expansion and Migration**" keywords.

OVHcloud also has a dedicated service: [OVHcloud Professional Services](/links/professional-services).

##Cost and fees

##Data retention after contract termination 


