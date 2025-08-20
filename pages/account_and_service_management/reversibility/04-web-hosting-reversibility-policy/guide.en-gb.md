---
title: Reversibility Policy for the Managed Web Hosting product
updated: 2025-08-20
---

## Objective

This document describes the reversibility policy for the Managed Web Hosting product covering the OVHcloud Web Hosting offer.

This policy aims to implement the general reversibility principles and our compliance with the SWIPO IAAS Code of Conduct for cloud providers.


## List of features

Features of the product line fall into three categories:

1. **Core features** for which we guarantee migration capacity.
2. **OVHcloud implementations** that require adaptation to a new migration environment.
3. **Specific features** that cannot be guaranteed for migration as they are related to the OVHcloud environment or involve custom developments.


## 1. Core features

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| Standard web hosting package | Use standard open-source components: Linux, Apache, MySQL/MariaDB, PHP | SQL, PHP, HTML, JSON, CSV | **Inbound**: copy of application files, import databases via SQL dump <br>**Outbound**: export data files/database dumps, reusable on any compatible environment | [How to create a Debian or Ubuntu web server](/pages/bare_metal_cloud/dedicated_servers/installing_lamp_debian9_ubuntu18) |
| Import and export application files | Transfer web files (PHP, HTML, assets) via FTP/SFTP and rsync for professional and performance offers | All file formats | **Inbound**: Direct file upload <br>**Outbound**: Direct file export for migration to any other hosting provider | [Export your website](/pages/web_cloud/web_hosting/export-your-website) |
| SSH/SFTP access to the client environment | Easy user access to your environment for file transfer and automation | Files, scripts, dumps | **Inbound**: application file transfer, SQL dumps, scripts via FTP/SFTP and rsync/scp/SSH for Professional and Performance plans <br>**Outbound**: export files, dumps, scripts via FTP/SFTP and rsync/scp/SSH for Professional and Performance plans to any other hosting provider| [Export your website](/pages/web_cloud/web_hosting/export-your-website) |

## 2. OVHcloud Implementations

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |
|1-click modules|Automated installation of CMS (WordPress, PrestaShop, Joomla!, Drupal)|N/A|**Inbound migration**: Not applicable<br><br>**Outbound migration**: Once the module is installed, follow the standard website migration procedure (including database migration)|**Outbound migration**: See "Web Hosting" above.|
|Automatic Backups|Automated website and database backups|N/A, restore a backup to export its content|**Inbound migration**: Backups are automatically enabled.<br><br>**Outbound migration**: Enable a backup plan with the new provider after the site is migrated.<br><br>It is not possible to export a backup as such: backups are internal and are not presented as a file or archive. To import the contents of a file server and database, **restore the backup and then export the website** as shown above.|**Inbound migration**: See "Web Hosting" above.<br><br>**Outbound migration**: See "Web Hosting" above.|
|Logging|Retention and browsing of the website logs. Analysis and graphic representation of these logs with the Urchin WebAnalytics application.|Plain text with standard apache log format|**Inbound migration**: Not applicable - logs from previous infrastructure are unlikely to be relevant to another.<br><br>**Outbound migration**: Download log files from the [OVHcloud Control Panel](/links/manager)|**Inbound migration**: N/A<br><br>**Outbound migration**: [Exporting a website - retrieving the logs](/pages/web_cloud/web_hosting/exporter-son-site-web#step-3-retrieve-the-logs-for-your-ovhcloud-web-hosting-plan)|
|Job scheduling|Performing periodic automated tasks (cron)|N/A|**Inbound migration**: Scripts are not imported as is. Retrieve old scripts, or their business logic, and reimplement them on OVHcloud hosting through the [OVHcloud Control Panel](/links/manager).<br><br>**Outbound migration**: Scripts are not exported as is. Retrieve the business logic of the scripts in the [OVHcloud Control Panel](/links/manager) and reimplement them in the target environment.|**Inbound and outbound migration**: [Using automated tasks on a Web Hosting plan](/pages/web_cloud/web_hosting/cron_tasks)|

## 3. Specific features

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
|Web application Firewall|HTTP Server Module for Filtering Inbound and Outbound Web Content|N/A|**Inbound migration**: Enabling the firewall from the [OVHcloud Control Panel](/links/manager).<br><br>**Outbound migration**: Order and configure a firewall with the new provider|**Inbound migration**: [Activating the application firewall](/pages/web_cloud/web_hosting/multisites_activating_application_firewall)<br><br>**Outbound migration**: N/A|
| Anti-DDoS protection| Anti-DDoS is a set of tools and mechanisms designed to absorb denial of service attacks. It includes traffic analysis, "clean-up" via a specialized network, and mitigation using VAC technology developed by OVHcloud. | N/A | **Inbound**: The anti-DDoS system is part of our infrastructure and is enabled by default. No action is required <br> **Outbound**: Order and configure an anti-DDoS solution from the new provider | [Anti-DDoS OVHcloud](/links/security/anti-ddos) |

### List of architectures

All components of an OVHcloud Web product are accessible through the [OVHcloud Control Panel](/links/manager). This allows to visualize and manage the front-end web servers, file servers, databases, domain names, email, ... as well as the features that are attached to these components.

### Partner services

The OVHcloud partners concerned are listed in the [OVHcloud partners directory](/links/partner) under the "**Data center expansion and Migration**" keywords.

OVHcloud also has a dedicated service: [OVHcloud Professional Services](/links/professional-services).

### Cost and fees

No additional billing is planned from OVHcloud for the migration features listed here.

### Retention of data after contract termination

The data is retained 45 days after the termination of the service and then deleted permanently.
