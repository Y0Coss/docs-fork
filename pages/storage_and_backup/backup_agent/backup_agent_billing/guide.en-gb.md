---
title: "Billing"
excerpt: "Backup Agent product billing"
updated: 2026-01-07
---

## Objective

You have the Backup Agent product, and you would like to know how you are billed for it.

## In practice

The product uses two elements to offer its service:

* The Veeam Agent installed on your Bare Metal servers.
* OVHcloud Object Storage.

We do not charge for the agent on your servers, i.e. you can deploy it on one or more bare metal servers, it will not cost you anything.

However, you will be billed per GB per month for using OVHcloud Object Storage. You will be billed at the beginning of each month for your usage during the previous month.

You will find the price per GB per month on our website.

You have a "Billing" dashboard in your Manager to view your current usage, and thus predict the final bill at the end of the month.

Example 1: You have deployed the agent on 3 bare metal servers, and they send their data to their respective Vault. The total capacity used by your backup data on the Vault servers is 600GB. You will be billed at the end of the month for 600GB.

Example 2: You have deployed the agent to 10 bare metal servers, and they send their data to their respective Vault. The total capacity used by your backup data on the Vault servers is 600GB. After a few backups, you remove the agent from 4 servers, deleting the data after 14 days. Total Vault usage drops to 400GB. You will be billed at the end of the month for 600GB.