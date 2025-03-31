---
title: Bare Metal recovery with Veeam Backup Agent  
excerpt: Learn how to restore your entire system using a recovery ISO and your Veeam Cloud backups.  
updated: 2025-03-31  
---

## Objective

**This guide explains how to recover your entire Windows system using Veeam's Bare Metal Recovery, with your backups stored on OVHcloud’s Cloud Connect service.**

You’ll learn how to:
- Create a recovery ISO (a file that helps you start your PC when Windows doesn’t work)
- Use it to boot your computer and restore everything from your latest backup

## Requirements

Before you begin, make sure you have:

- A tenant delivered with the Alpha Backup Agent
- A machine where the Veeam Backup Agent is running and has already pushed at least one backup


## Instructions

### Step 1: Create your recovery media ISO

If your computer ever stops working, you’ll need a recovery ISO to boot it up. Let’s create it now.

1. Open the **Create Recovery Media** tool on your computer (it comes with the Veeam Backup Agent).

    ![Launch the Create Recovery Media tool](images/baremetal_recovery_01.png){.thumbnail}

2. Veeam will ask if you want to include extra drivers.

    > **Tip:** If you’re using special hardware (like a RAID controller or a Wi-Fi dongle), select the drivers you need. Otherwise, the default is usually fine.

    ![Select drivers for boot image](images/baremetal_recovery_02.png){.thumbnail}

3. Choose where to save the recovery ISO and give it a name.

    ![Set ISO location and name](images/baremetal_recovery_03.png){.thumbnail}

4. Let the tool finish. Your ISO file will be created.

    ![Recovery ISO creation complete](images/baremetal_recovery_04.png){.thumbnail}

You can now use this ISO to create a bootable USB stick using a tool like Rufus or your favorite ISO-to-USB tool.

### Step 2: Boot your computer from the recovery ISO

If your system isn’t working and you need to restore it:

1. Plug in the USB stick or insert the ISO and **boot your computer from it**.

    > **Not sure how to boot from USB?** Restart your PC and press the key shown (usually F2, F12, ESC, or DEL) to access the boot menu.

2. Once the system starts, the Veeam Recovery Wizard will open. Click **Bare Metal Recovery**.

    ![Launch Bare Metal Recovery](images/step2_01.png){.thumbnail}

3. Choose **Network Storage** to access your online backups.

    > **Important:** If your internet doesn’t work at this stage, you may need to manually configure the network. The recovery system may not recognize your network card automatically.

    ![Select Network Storage](images/step2_02.png){.thumbnail}

4. Select **Veeam Cloud Connect repository**.

    ![Choose Cloud Connect Repository](images/step2_03.png){.thumbnail}

5. Enter the following address when prompted for the service provider:

backup.private.ovhcloud.dev

    ![Enter DNS](images/step2_04.png){.thumbnail}

6. Enter your username and password to log in.

    ![Enter credentials](images/step2_05.png){.thumbnail}

7. Select the server you want to restore.

    ![Select server](images/step2_06.png){.thumbnail}

8. Choose the restore point (date/time) you want to go back to.

    > **Tip:** We recommend using the most recent successful backup unless you have a specific reason to go back further.

    ![Choose restore point](images/step2_07.png){.thumbnail}

9. Choose the recovery mode that fits your situation—usually “Entire computer.” 

    ![Recovery mode](images/step2_08.png){.thumbnail}

Then start the restore process.

![Launch restore](images/step2_09.png){.thumbnail}

![Launch restore](images/step2_10.png){.thumbnail}

> **Note:** The recovery can take some time, depending on your backup size and internet connection. Once complete, your system will reboot with everything restored as it was at the time of the selected backup.

## Go Further

If you need training or technical assistance to implement our solutions, please contact your Technical Account Manager or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for a custom analysis of your project.

Ask questions, give your feedback and interact directly with the team building our Hosted Private Cloud services on the dedicated [Discord](https://discord.gg/ovhcloud) channel.

Join our [community of users](/links/community).