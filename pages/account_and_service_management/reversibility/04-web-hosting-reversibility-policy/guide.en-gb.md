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
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |
|Register and manage Domain names|Reservation and registration of domain names with domain name registrars.<br><br>DNS setting of domain names.|N/A|**Inbound migration**: Transfer request to original registrar and then manage via [OVHcloud Control Panel](/links/manager)<br><br>**Outbound migration**: Fully managed transfer request in [OVHcloud Control Panel](/links/manager).|**Inbound migration**: [Transferring a domain name to OVHcloud](/pages/web_cloud/domains/transfer_incoming_generic_domain)<br><br>[Transferring a .co.uk domain name to OVHcloud](/pages/web_cloud/domains/transfer_incoming_couk)<br><br>**Outbound migration**: [Transferring a domain name to another registrar](/pages/web_cloud/domains/transfer_outgoing_domain)<br><br>[Transferring a .co.uk domain name to another registrar](/pages/web_cloud/domains/transfer_outgoing_couk)|
|Web hosting - Providing HTTP Servers|Provision of a web front-end server and code execution environment|**PHP**: 7.3 / 7.2 / 7.1 / 7.0 / 5.6<br><br>**Node.js**: 8 / 10 / 11|**Inbound migration**: Order a new OVHcloud hosting.<br><br>**Outbound migration**: Order a new hosting from the new provider. Replicate the runtime environment configuration from the Control Panel or .ovhconfig file.|**Inbound migration**:<br>[Getting started with a web hosting - Define your project](/pages/web_cloud/web_hosting/hosting_first_steps_with_web_hosting#step-1-define-your-project)<br><br>[Getting started with Cloud Web - Define your project](/pages/web_cloud/web_hosting/getting_started_cloud_web#step-1-define-your-project)<br><br>[Configuring the .ovhconfig file of your web hosting plan](/pages/web_cloud/web_hosting/configure_your_web_hosting)<br><br>**Outbound migration**: [Configuring the .ovhconfig file of your web hosting plan](/pages/web_cloud/web_hosting/configure_your_web_hosting)<br><br>[Configuring PHP from your customer account](/pages/web_cloud/web_hosting/configure_your_web_hosting)<br><br>Note: these documents allow you to retrieve relevant information about the .ovhconfig file and the PHP version.|
|Web hosting - Providing file servers.|Provision of a file server to host the component files of the website (pages, scripts, resources...)|**Every format** - clients may upload any file on the server.|**Inbound migration**: FTP connection to the file server and import.<br><br>**Outbound migration**: FTP connection and file recovery.|**Inbound migration**: [Migrating your website to OVHcloud](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh)<br><br>**Outbound migration**: [Export a website - retrieve files from your FTP storage space](/pages/web_cloud/web_hosting/exporter-son-site-web#step-1-retrieve-files-from-your-ftp-storage-space)|
|Web hosting - providing databases|Provision of databases that can be connected to the website|**Shared SQL offers**:<br><br>**MySQL 5.6**<br><br>**Private SQL offers**:<br><br>**MySQL** 5.6 / 5.7<br><br>**MariaDB** 10.1<br><br>**PostgreSQL** 9.4 / 9.5 / 9.6 / 10|**Inbound migration**: Create a new database, then import the data by one of the available methods (backup restore, phpMyAdmin interface, script, SSH connection)<br><br>**Outbound migration**: Export data by one of the available methods (backup export, phpMyAdmin interface, script, SSH connection)|**Inbound migration**: [Importing a backup into a Web Hosting plan database](/pages/web_cloud/web_hosting/sql_importing_mysql_database)<br><br>[Private SQL - Importing a database](/pages/web_cloud/web_cloud_databases/starting_with_clouddb#importing-a-database-optional)<br><br>**Outbound migration**: [Retrieving the backup of a Web Hosting plan’s database](/pages/web_cloud/web_hosting/sql_database_export)|

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
