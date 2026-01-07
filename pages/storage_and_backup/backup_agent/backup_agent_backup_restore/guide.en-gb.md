---
title: "Manage your backups and restores"
excerpt: "Manage your backups and restores"
updated: 2026-01-07
---

## Objective

You have the Backup Agent product and you want to understand how to back up and restore your data on your Bare Metal servers.

## Requirements

* You must have the Backup Agent product.
* Have a Bare Metal server with the agent installed on it.

## In practice

### Create a backup for your server

This involves adding your server to your Backup Agent, downloading the agent and installing it on your server.

In order to add your server, you must:

* Go to the Backup Agent section of the Control Panel.
    * ![Backup Agent Menu](images/01-backup-agent-menu.png){.thumbnail}
* Click on your vspc-tenant, in the Services section.
    * ![Backup Agent Services](images/01-backup-agent-services.png){.thumbnail}
* Go to the "Agents" section
    * ![Backup Agent Tenant Infos](images/01-backup-agent-tenant-infos.png){.thumbnail}
* Click on the "Add a configuration" button.
    * ![Backup Agent](images/01-backup-agent-agent.png){.thumbnail}
* Select your server and operating system.
    * ![Backup Agent Add Server 01](images/01-backup-agent-add-server-01.png){.thumbnail}
    * ![Backup Agent Add Server 02](images/01-backup-agent-add-server-02.png){.thumbnail}

### Backup

You have two options for making backups:

* Automatic
* Manual

We will start with automatic backup.

#### Automatic

Automatic backup is included in the backup policy that we apply to your Backup Agent.

This backup will make a full backup of your server, which will be sent to your remote storage point.

> [!warning]
>
> This will trigger between 10pm and 6am, in the CET time zone for Europe, and in the EST time zone for Canada and APAC.

> [!primary]
>
> You cannot change or disable this automatic backup.

You can view the success of this backup via:

* The daily report received.
* The "Backup Jobs" dashboard of the Veeam Service Provider Console.
    * ![Backup Agent VSPC Backup Jobs](images/01-backup-agent-vspc-backup-jobs.png){.thumbnail}
    * ![Backup Agent VSPC Job](images/01-backup-agent-vspc-job.png){.thumbnail}

#### Manual

If necessary, you can trigger a manual backup.

It will also create a full backup of your server, always sent to your remote storage point.

Here's how:

* To open the "Veeam Agent" application on your Bare Metal server:
    * ![Backup Agent BKP Agent Search](images/01-backup-agent-bkpagent-search.png){.thumbnail}
* Press the "Backup Now" button to launch a backup:
    * ![Backup Agent BKP Agent](images/01-backup-agent-bkpagent.png){.thumbnail}

### Restoration

If you need to restore data, you have two options:

* Via the File Restore wizard.
* Via the Veeam Bare Metal Recovery ISO.

#### File Restore Wizard

In order to use the Restore Files wizard, you must follow the steps below:

* To open the "Veeam Agent" application on your Bare Metal server:
    * ![Backup Agent BKP Agent Search](images/01-backup-agent-bkpagent-search.png){.thumbnail}
* Go to the menu and select "Restore File":
    * ![Backup Agent Restore Menu](images/01-backup-agent-restore-menu.png){.thumbnail}
* Select the desired restore point in the wizard:
    * ![Backup Agent Restore Points](images/01-backup-agent-restore-points.png){.thumbnail}
* And confirm:
    * ![Backup Agent Restore Point Summary](images/01-backup-agent-restore-restore-points-summary.png){.thumbnail}
* Finally, search for your file and select an option:
    * ![Backup Agent Restore Wizard](images/01-backup-agent-restore-wizard.png){.thumbnail}
    * Restore - Overwrite : Allows you to restore the file while overwriting the one currently on the server.
    * Restore - Keep : Allows you to restore the file while keeping the one currently on the server.
    * Copy To: Allows you to copy the file to a location on your server.
    * Explore: Allows you to explore the backup.
    * Properties: Allows you to view the file properties.
    * Launching a restore will give you a final window that will show the transfer:
    * ![Backup Agent Restore Transfer](images/01-backup-agent-restore-transfer.png){.thumbnail}

### Veeam Baremetal Recovery ISO

Baremetal Recovery is a feature offered by Veeam in the form of an ISO that you must create in advance, and which allows you to boot it in order to restore a system backed up on another server.

You can follow this guide: https://help.ovhcloud.com/csm/en-veeam-agent-bare-metal-recovery?id=kb_article_view&sysparm_article=KB0067234
You will need to adapt the server and credentials to match the ones we have provided.

## Go further

Join our [community of users](/links/community).