---
title: "Backup Agent Product Overview"
excerpt: "Overview of Backup Agent product features and benefits"
updated: 2026-01-07
---

## Objective

Are you interested in the Backup Agent product for your bare metal and would like more information.

This guide will help you understand how the Backup Agent works, and what it can do for you.

## In practice

The Backup Agent product allows you to back up your bare metal servers using an agent that will, according to a backup policy you have chosen, send your server data to an external storage point.

The Backup Agent product is based on two products from the Veeam software publisher:

* The Veeam Service Provider Console (VSPC).
* The Veeam Agent.

The VSPC allows you to downgrade the backup policies to the agents stored on them, and allows you to give each agent the storage and credentials information when starting the backup.

Once the agent obtains the information, it sends the data directly to the storage point without ever transitioning through the VSPC infrastructure.

The basic diagram is as follows:

![Backup Agent Functional Diagram](images/01-backup-agent-diagram.png){.thumbnail}

Please note that:

* The VSPC infrastructure is hosted in OVH datacentres and does not send data to Veeam servers.
*Storage points are OVHcloud Object Storage buckets that are hosted in OVHcloud datacentres.

There are several key advantages to this solution:

* First automatic backup policy with 14 days retention.
* Possibility to increase to 30 days of retention.
* 14 days of immutability on our buckets.
* The period for automatic backups is between 10pm and 6am.
* Encryption managed by OVHcloud of the storage hosting your backup data.
* Live sending of backup data to the bucket without placing a copy on our infrastructure.
* Storage point always distant from the location of your bare metal server (if you are in Roubaix, your storage point will be in Gravelines).

## Go further

Join our [community of users](/links/community).