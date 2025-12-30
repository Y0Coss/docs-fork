---
title: "Zimbra Pro - Setting up your email account via ActiveSync on Outlook for Windows"
excerpt: "Find out how to configure your Zimbra Pro email address on Outlook for Windows using the ActiveSync protocol"
updated: 2025-12-17
---

<style>
details>summary {
    color:rgb(255,165,0) !important;
    cursor: pointer;
}
details>summary::before {
    content:'\25B6';
    padding-right:1ch;
}
details[open]>summary::before {
    content:'\25BC';
}
.w-600 {
  max-width:600px !important;
}
.h-500 {
  max-width:500px !important;
}
</style>

## Objective

> [!primary]
>
> This guide is aimed at customers with the email solution [Zimbra Pro](/links/web/emails-zimbra). This service will be available in beta version from July 2025.

Zimbra Pro accounts can be set up on Windows using the ActiveSync protocol, allowing you to configure all the collaborative features of your email address in one go. The Outlook application for Windows allows you to access your Zimbra Pro email account via the ActiveSync protocol.

**Find out how to configure your Zimbra Pro email address on Outlook for Windows using the ActiveSync protocol.**

## Requirements

- Have a [Zimbra Pro](/links/web/emails-zimbra) email address.
- Have the [Classic Outlook](https://support.microsoft.com/en-gb/office/install-or-reinstall-classic-outlook-on-a-windows-pc-5c94902b-31a5-4274-abb0-b07f4661edf5) application on Windows.
- Have the credentials for the email address you wish to set up.

/// details | Information regarding the management and configuration of OVHcloud services

OVHcloud provides services whose configuration, management, and responsibility lie with you. It is therefore your responsibility to ensure their proper functioning.

We provide this guide to assist you with common tasks. However, we recommend that you contact a [specialised partner](/links/transversal/marketplace-support-collaboration) and/or the service provider if you encounter difficulties. Indeed, we will not be able to provide assistance. More information is available in the « [Go further](go-further) » section of this guide.

///

## Instructions

> [!warning]
>
> Before starting your configuration, it is important to note that the Outlook application included free with Windows 11 is incompatible with the ActiveSync protocol, which is necessary for setting up a Zimbra Pro account. You will need to use the **Classic Outlook** version to benefit from ActiveSync protocol support.
>
> To install Classic Outlook on your Windows computer, download it from the Microsoft page « [Install or reinstall Classic Outlook on a Windows PC](https://support.microsoft.com/en-gb/office/install-or-reinstall-classic-outlook-on-a-windows-pc-5c94902b-31a5-4274-abb0-b07f4661edf5) », and install it.
>
> Once the installation is complete, to distinguish the two versions when both are installed, type « Outlook » in the Windows search bar. You will then be able to see the difference as shown below.
>
> ![outlook Windows](images/outlook-windows-identify01.png){.thumbnail .h-500}

### Add the account <a name="add-account"></a>

To add a Zimbra Pro account to Classic Outlook, follow the steps below by clicking on the tabs below in sequence:

> [!tabs]
> **Step 1**
>>
>> 1. Go to the **Control Panel** of Windows.
>> 2. Click on `User Accounts`{.action}.
>> 3. Click on `Mail`{.action}.
>> 4. Click on `Email Accounts...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step01.png){.thumbnail .h-500}
>>
> **Step 2**
>>
>> - From the **Account Settings** window, in the `Mail` tab, click on `New...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step02.png){.thumbnail .h-500}
>>
> **Step 3**
>>
>> - From the **Add Account** window, select `Manual setup or additional server types`{.action}.
>> - Click on `Next`{.action} to continue.
>>
>> ![outlook Windows](images/outlook-windows-add-step03.png){.thumbnail .h-500}
>>
> **Step 4**
>>
>> - Select `Exchange ActiveSync`{.action}.
>> - Click on `Next`{.action} to continue.
>>
>> ![outlook Windows](images/outlook-windows-add-step04.png){.thumbnail .h-500}
>>
> **Step 5**
>>
>> Enter the connection details for your account:
>>
>> - **Your name** : Set a display name.
>> - **Email address** : Enter your full email address.
>> - **Mail server** : Enter « zimbra1.mail.ovh.net ».
>> - **Username** : Enter your full email address.
>> - **Password** : Enter the password associated with your email address.
>>
>> Click on `Next`{.action} to finalise the account addition.
>>
>> ![outlook Windows](images/outlook-windows-add-step05.png){.thumbnail .h-500}
>>
> **Step 6**
>>
>> Your email address is now configured for Outlook. To benefit from full synchronisation of your Zimbra Pro account features, **download and install** the « [Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/) » module.
>> 
>> ![outlook Windows](images/outlook-windows-add-step06.png){.thumbnail .h-500}
>>
> **Step 7**
>>
>> Once the « [Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/) » module is installed, launch Classic Outlook.
>> The first time, the **Zimbra Server configuration Settings** window appears. Complete the following information:
>>
>> - **Server name** : Enter « zimbra1.mail.ovh.net ».
>> - **Email address** : Enter your full email address.
>> - **Password** : Enter the password associated with your email address.
>>
>> It is not necessary to modify the other settings. Click on `Apply`{.action} to validate the settings and ensure they are correct. Finally, click on `OK`{.action} to access Outlook and start using your email address.
>>
>> ![outlook Windows](images/outlook-windows-add-step-07.png){.thumbnail .h-500}

> [!warning]
>
> If you encounter any sending or receiving issues after following the configuration steps above, refer to the « [Modify existing settings](#modify-settings) » section of this guide.

### Using the email address

Once the email address is configured, you can start using it! You can now send and receive messages, as well as manage your calendars and tasks.

OVHcloud also offers a web application allowing you to access your email address from an Internet browser. You can connect to the [OVHcloud webmail](/links/web/email) using the credentials of your email address. For any questions regarding its use, refer to our guide « [Using Zimbra webmail](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_zimbra) ».

### How to modify existing settings? <a name="modify-settings"></a>

To modify the settings of an already configured email account, follow the instructions below:

1. Go to the **Control Panel** of Windows.
1. Click on `User Accounts`{.action}.
1. Click on `Mail`{.action}.
1. Click on `Email Accounts...`{.action}.
1. Select the concerned email account from the list and click on `Change...`{.action}.

![outlook ios](images/outlook-windows-modify-01.png){.thumbnail .h-500}

Find the settings at **Step 7** of the « [Add the account](#add-account) » chapter.

### How to delete an email account? <a name="delete-account"></a>

To delete your email account, follow the instructions below:

1. Go to the **Control Panel** of Windows.
1. Click on `User Accounts`{.action}.
1. Click on `Mail`{.action}.
1. Click on `Email Accounts...`{.action}.
1. Select the concerned email account from the list and click on `Delete`{.action}.

![outlook ios](images/outlook-windows-delete-01.png){.thumbnail .h-500}

> [!warning]
>
> To be able to delete your email account, it is necessary that it is not the default email account.

## Go further <a name="go-further"></a>

> [!primary]
>
> For more information on configuring an email address from the Outlook application on Windows, consult the [Microsoft help centre](https://support.microsoft.com/en-gb/office/add-an-email-account-to-outlook-for-windows-6e27792a-9267-4aa4-8bb6-c84ef146101b?ocmsassetID=HA102823161&CorrelationId=778d1d8d-9ac2-449b-9624-1268559fa794).

For specialised services (SEO, development, etc.), contact [OVHcloud partners](/links/partner).

If you wish to benefit from assistance with the use and configuration of your OVHcloud solutions, we offer you to consult our various [support offers](/links/support).

Join our [community of users](/links/community).