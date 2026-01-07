---
title: "Troubleshooting Guide"
excerpt: "Backup Agent Product Troubleshooting Guide"
updated: 2026-01-07
---

## Objective

Here is a list of potential issues you may encounter with the Backup Agent product.

## List of possible issues

* My agent is unable to connect to your server.
    * You must make sure you have your firewall that allows you to communicate with our server vspc-cgw1.prod01.eu-west-rbx.backup.ovhcloud.com (137.74.125.230) in Europe with TCP port and UDP 6180.
    * You must ensure that you do not have any services that could have a port conflict with your server.
    * You can find your agent logs in the folder: C:\ProgramData\Veeam\ or /var/logs.
* Your server cannot install the backup agent on my server.
    * The agent supports Windows distributions and Linux native kernels. If you have made changes to your kernel, you must ensure that you have the correct packages to install the agent. You can find the list of required parameters here: https://helpcenter.veeam.com/docs/agentforlinux/userguide/system_requirements.html?ver=13
* My agent cannot back up. I have the error: "Failed to perform backup. Neither blksnap nor veeamsnap module was found."
    * The agent supports Windows distributions and Linux native kernels. If you have made changes to your kernel, you must ensure that you have the correct packages to install the agent. You can find the list of required parameters here: https://helpcenter.veeam.com/docs/agentforlinux/userguide/system_requirements.html?ver=13
    * You will need the Linux kernel headers first, and you can then try to install or reconfigure your veeamsnap or veeamblksnap or blksnap package, depending on your operating system.
* My agent cannot back up. I get the error: "POSIX: Failed to create or open file [/.veeamsnapstorage/veeamsnapstore"
    * To back up, Veeam takes snapshots in addition to preserving the data that will be written to the backup. This snapshot is called "veeamsnapstorage".
    * To resolve the issue, you can increase the size of the snapshot via the /etc/veeam/veeam.ini file:
> [!primary]
>
> [blksnap]
>
> #The minimum allowable size of the difference storage in sectors
> diffStorageMinimum = 2097152
* Replace the value in bytes with the desired number of GB (GB divided by 512, for 3GB you must put 3221225472 / 512 = 6 291 456)
    * And finally restart the veeamservice service.
* I cannot start a manual backup.
    * Contact OVHcloud support to investigate by providing logs and screenshots.
* My storage usage did not refresh after an agent was removed.
    * We keep your data for 14 days following an agent deletion, storage usage will be updated following the 14 days and data deletion.
* I have uninstalled my Veeam Agent, how do I reinstall it?
    * Contact OVHcloud support to help you reinstall your agent.
* I have reinstalled my server. How do I reinstall the Backup Agent?
    * You must delete your agent in the Agents section of your vspc-tenant, and then download and install the agent on your new operating system.