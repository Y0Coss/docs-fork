---
title: "Email Pro - Configure your Email Pro account on the new Outlook for Windows"
excerpt: "Find out how to configure your Email Pro address on the New Outlook for Windows"
updated: 2025-09-02
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
</style>

## Objective

The email addresses from the [Email Pro](/links/web/email-pro) offer can be configured on a compatible email client. This allows you to send and receive messages from the application of your choice.

The **New Outlook** has replaced the **Mail** application on Windows since January 1, 2025. For more information on this topic, please refer to Microsoft's official page: "[Outlook for Windows: The future of mail, calendar, and People on Windows 11](https://support.microsoft.com/office/outlook-pour-windows-l-avenir-du-courrier-du-calendrier-et-des-personnes-sur-windows-11-715fc27c-e0f4-4652-9174-47faa751b199)".

**Learn how to configure your Email Pro account on the New Outlook for Windows.**

## Requirements

- An [Email Pro](/links/web/email-pro) address.
- The [New Outlook](https://support.microsoft.com/office/getting-started-with-the-new-outlook-for-windows-656bb8d9-5a60-49b2-a98b-ba7822bc7627) for Windows.
- Possess the credentials for the email address you wish to configure.

> [!warning]
>
> This documentation applies only to the **New Outlook** and not to the "[Outlook Classic](https://support.microsoft.com/office/installer-ou-r%C3%A9installer-outlook-classique-sur-un-pc-windows-5c94902b-31a5-4274-abb0-b07f4661edf5)" available in the Microsoft 365 suite or previously installed on your computer.

/// details | Information related to the management and configuration of OVHcloud services

OVHcloud provides you with services whose configuration, management, and responsibility fall under your control. Consequently, it is your responsibility to ensure their proper functioning.

We provide this guide to assist you with common tasks. However, we recommend contacting a [specialized partner](https://marketplace.ovhcloud.com/c/support-collaboration) and/or the service publisher if you encounter difficulties. Please note that we cannot provide assistance. For more information, refer to the "Go further" section of this guide.

///

## Instructions

### Add the account <a name="add-account"></a>

> [!warning]
>
> In our example, we use the server name: pro?.mail.ovh.net. You must replace the "?" with the number corresponding to your Email Pro service server.
> 
> Find this number in your [OVHcloud Control Panel](/links/manager), under the `Web Cloud`{.action} section, then `Email Pro`{.action}. The server name is visible in the **Connection** section of the `General Information`{.action} tab.

> [!tabs]
> **Step 1**
>> - Open Outlook. In the left column, click on `Add an account`{.action} to start the configuration.
>>
>> ![outlook](images/configuration-newoutlook-windows-01.png){.thumbnail .w-400}
>>
> **Step 2**
>> - Enter your email address, then click `Continue`{.action}.
>> - Enter your password and click the `Show more`{.action} button.
>>
>> ![outlook](images/configuration-newoutlook-windows-02.png){.thumbnail .w-400}
>>
> **Step 3**
>> - Enter the following parameters:
>>    - **IMAP incoming server**: pro?.mail.ovh.net
>>    - **Port**: 993
>>    - **Secure connection type**: SSL/TLS
>>    - **SMTP username**: The email address you are adding.
>>    - **SMTP outgoing server**: pro?.mail.ovh.net
>>    - **Port**: 587
>>    - **Secure connection type**: STARTTLS
>>    - **Password**: Do not enter anything; the password entered earlier will be used.
>> - Click `Continue`{.action} to finalize the configuration.
>>
>> ![outlook](images/configuration-newoutlook-windows-emp-03.png){.thumbnail .w-400}

### Using the email address <a name="use-account"></a>

Once the email address is configured, you can start using it! You can now send and receive messages.

OVHcloud also provides a web application that allows you to access your email address from your web browser at [Webmail](/links/web/email). You can log in using the credentials for your email address.

### Modifying existing settings <a name="modify-settings"></a>

The Outlook application does not allow you to modify the server settings for your email account.

If your email account is already configured and you wish to reconfigure it, you will need to delete it and recreate it:

- Click on the settings icon "⋮" at the bottom of the left column.
- In the "Your accounts" section, click on `Manage`{.action} to the right of the relevant email address.

![outlook](images/configuration-newoutlook-windows-04.png){.thumbnail .w-400}

- Scroll to the bottom of the page.
- Click on `Delete`{.action} to start the deletion process.
- Determine whether you want to delete it only from this device or from all devices using Outlook.

![outlook](images/configuration-newoutlook-windows-emp-05.png){.thumbnail .w-400}

> [!success]
>
> Once your email account is deleted, follow the instructions in the "[Add the account](#add-account)" section of this documentation.

### General sending and receiving settings <a name="settings-account"></a>

#### IMAP and POP receiving settings <a name="imap-pop"></a>

For receiving emails, we recommend using **IMAP** when choosing the account type. However, you can also select **POP**.

Select the tab corresponding to your configuration type:

> [!tabs]
> **IMAP Configuration**
>>
>> - **Username**: Enter the **complete** email address.
>> - **Password**: Enter the email address password.
>> - **Incoming server**: pro?.mail.ovh.net (replace "?" with your server number).
>> - **Port**: 993.
>> - **Security type**: SSL/TLS.
>>
> **POP Configuration**
>>
>> - **Username**: Enter the **complete** email address.
>> - **Password**: Enter the email address password.
>> - **Incoming server**: pro?.mail.ovh.net (replace "?" with your server number).
>> - **Port**: 995.
>> - **Security type**: SSL/TLS.

#### SMTP sending settings <a name="smtp"></a>

For sending emails, find the **SMTP** settings to use below:

**SMTP Configuration**

- **Username**: Enter the **complete** email address.
- **Password**: Enter the email address password.
- **Outgoing server**: pro?.mail.ovh.net (replace "?" with your server number).
- **Port**: 587.
- **Security type**: STARTTLS.

## Go further <a name="go-further"></a>

> [!primary]
>
> For more information on configuring an email address from the New Outlook messaging client on Windows, please refer to [Microsoft's help center](https://support.microsoft.com/office/start-using-new-outlook-for-windows-4395454d-cb2f-4c16-bb24-fa4bb36650ae).

[First steps with the Email Pro solution](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config)

For specialized services (SEO, development, etc.), contact [OVHcloud partners](/links/partner).

If you would like assistance using and configuring your OVHcloud solutions, we recommend consulting our various [support offers](/links/support).

Join our [community of users](/links/community).