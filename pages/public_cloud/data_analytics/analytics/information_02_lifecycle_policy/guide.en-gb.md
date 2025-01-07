---
title: Data Analytics - Lifecycle policy
excerpt: Lifecycle policy for Data Analytics engines
updated: 2025-01-07
---

## Objective

OVHcloud Data Analytics allow you to focus on building and deploying cloud applications while OVHcloud takes care of the database infrastructure and maintenance.
Each service is powered by third-party databases management systems (DBMS), maintained by third-party companies or communities such as Apache Kafka, M3DB.

**This guide explains the OVHcloud policy for major DBMS versions provided in Data Analytics.**

## Lifecycle policy

This policy is being provided to help customers understand the lifecycle of OVHcloud Data Analytics, in order to anticipate and prepare transitions to newer versions.

**End Of Life (EOL)** refers to the deadline after which affected Data Analytics services are deprecated and will no longer be supported nor maintained.

OVHcloud aims to follow the EOL schedule set by the original authors and maintainers of the DBMS software, aka upstream projects. Once the upstream project retires a specific version, they no longer receive security updates or critical bug fixes.

Continued use of outdated services means that they no longer offer our customers the level of protection their business needs. Therefore, by following upstream project's EOL schedule, we ensure that OVHcloud services are always running on supported versions of the DBMS software.

### Service coverage

This lifecycle policy is applicable to :

- All Data Analytics services except Data Processing;
- Including all the service plans (Essential, Business, Enterprise, Production, Advanced);
- And all proposed DBMS, such as Kafka, M3 ...
- Whatever state; if they are **up and running** or in a **sleeping state** (powered off, waiting for payment).

### Providing new major versions

Once a new DBMS major version is considered stable to use, OVHcloud will do its best to provide it to our customers as soon as we can.
Since many factors can come into play, we cannot provide an exact timeline or engagement.

### Prior EOL

When OVHcloud defines the EOL date for a service major version :

- Customers will receive an EOL email announcement via their main contact point (NIC-admin);
- The OVHcloud Control Panel will also show an EOL notification for affected services;
- Email reminders may also be sent to customers.

### Upon EOL

Once the EOL date is reached :

- Affected **running services** will be **automatically upgraded to the latest available version**. For example, if the latest version is Kafka 3, then upon Kafka 1.6 EOL, it will be upgraded to the latest Kafka 3 instead of Kafka 2.
- Affected **sleeping state** (powered-off, ...) services **will no longer be accessible and their backups will be deleted**.

### Potential impacts

New DBMS versions can introduce minor changes but also breaking changes, leading to malfunctions in your code thus applications. One feature might not work properly, or your whole website or application can become broken and unavailable. **Impacts cannot be known by OVHcloud** and customers are responsible for their own code.
We recommend to browse official DBMS documentation to check the newly introduced features and/or deprecated ones.

## Recommendations for upgrades

We highly recommend to perform the version upgrade well before EOL so that you can test compatibility for any breaking changes, plan for unforeseen issues, and migrate to the newer version at your own schedule.

Data Analytics offer database forking (a copy) as an efficient tool to verify the version upgrade so that you can safely test compatibility without committing your production services to a one-way upgrade.

To perform a fork, navigate to the "Overview" page of your service, and scroll down until you see a "New database fork" button. This will allow you to make a separate new database service that is cloned from the current one's backups.

## EOL Announcements for major versions

### Kafka

Data Analytics for Kafka *major.minor* version will reach EOL approximately one year after it's made available on Data Analytics.

| **Kafka Version** | **OVHcloud EOL** | **Availability on Data Analytics** |
|-------------------|------------------|-------------------------------------------|
| 3.4.x             | 2024-05-13       | 2023-05-09                                |
| 3.5.x             | 2024-07-31       | 2023-07-31                                |
| 3.6.x             | 2024-10-18       | 2023-10-18                                |
| 3.7.x             | 2025-04-17       | 2024-04-17                                |

## Go further

Visit our dedicated Discord channel: <https://discord.gg/ovhcloud>. Ask questions, provide feedback and interact directly with the team that builds our databases services.

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/en-gb/professional-services/) to get a quote and ask our Professional Services experts for a custom analysis of your project.

Join our community of users on <https://community.ovh.com/en/>.
