---
title: 'Migrate an MX Plan email address to an Email Pro, Exchange or Zimbra account'
excerpt: 'Discover how to migrate an MX Plan email address to an Email Pro, Exchange or Zimbra account'
updated: 2025-12-22
---

## Objective

OVHcloud offers several email solutions: MX Plan (sold separately or included in a web hosting offer), Email Pro, Exchange and Zimbra. These solutions have specific features and can be adapted to various uses. Have your needs changed? OVHcloud provides a migration tool to help you switch from one solution to another.

**Discover how to migrate an MX Plan email address to an Email Pro or Exchange account.**

<iframe class="video" width="560" height="315" src="https://www.youtube-nocookie.com/embed/0JLLoBBvsCc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> [!warning]
>
> [OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm) allows you to migrate your messages from one email server to another.<br>
> If your emails are only stored locally (POP configuration or local archiving), you can perform an [export from your email software](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration), then [import your PST file via OMM](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm#realiser-une-migration-par-fichier) or [import directly from your email software](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration).

## Requirements

- Have an MX Plan email address (via the MX Plan offer or included in an [OVHcloud web hosting](/links/web/hosting) offer).
- Have an [Exchange](/links/web/emails-hosted-exchange), [Email Pro](/links/web/email-pro) service with at least one unconfigured account (which will appear in the form of "@configureme.me") or [Zimbra](/links/web/zimbra).
- **Do not have any redirection set up on the MX Plan email address you want to migrate**.
- Be logged in to your [OVHcloud Control Panel](/links/manager).

## Instructions

### Step 1: define your project

Email Pro and Exchange solutions share a common set of features. However, there are differences depending on the use case. By choosing an Exchange address, you have access to all collaborative functions, such as calendar and contact synchronisation. The Email Pro solution, on the other hand, offers some of these functions but they are limited to use via a webmail only.

Before proceeding, it is therefore important to know which offer you want to migrate your MX Plan email addresses to. To help you make this choice, consult the page of [OVHcloud's professional email solutions](/links/web/emails) which provides a detailed comparison of the offers. You have the possibility to combine the solutions and thus use one or more Email Pro and Exchange accounts for the same domain name. Furthermore, if you need to migrate several accounts, we recommend that you set up a migration plan.

### Step 2: order your Email Pro or Exchange accounts

This step is optional if you already have an Exchange or Email Pro service to which you are making this migration.

Otherwise, log in to your [OVHcloud control panel](/links/manager), then order the Email Pro or Exchange service of your choice. Follow the various steps, then wait for the service to be installed. An email will be sent to you as soon as it is completed.

> [!primary]
>
> Once the account is ordered, leave it in the form « @configureme.me » for the time being. Indeed, it will be renamed during the migration.

### Step 3: Perform the migration

Before starting your migration, you will need to identify the version of the MX Plan from which you are migrating.

> [!primary]
>
> The email technology of your MX Plan offer may vary depending on the date of activation of your offer or if a migration has recently taken place. This technology is particularly distinguished by the interface of its webmail. To identify it from your control panel, follow these steps:
>
> 1. Log in to your [OVHcloud control panel](/links/manager).
> 1. Go to the `Web Cloud`{.action} section.
> 1. Click on `MX Plan`{.action}.
> 1. Select the concerned domain.
> 1. The `General Information`{.action} tab is selected by default.
> 1. Note the technology used under the mention **Webmail** in the `Subscription` box.
>
> ![MX plan](/pages/assets/schemas/emails/technology-email.png){.thumbnail .w-640}
>

#### 3.1 Manual migration of an MX Plan offer to Exchange, Email Pro or Zimbra  <a name="all-mxplan"></a>

> [!warning]
>
> This section concerns all MX Plan services using the Rouncube, Zimbra or OWA webmail technology.
>
> However, if you want to migrate an MX Plan service using the Roundcube webmail to an OVHcloud Email Pro or Exchange platform, follow the section « [Automatic migration of an MX Plan Roundcube offer to Exchange or Email Pro](#roundcube-mxplan) » of this guide.

> [!warning]
>
> If you have just ordered your new email offer, first add the domain name to your email platform before starting your migration. <br> - *For example, to migrate the account « myemail@mydomain.ovh », you must add the domain name « mydomain.ovh » to your platform.*
>
> Select the `Associated Domains`{.action} or `Domain`{.action} tab on your platform, then click on `Add a domain`{.action}. Once the domain name is added, make sure that the mention `OK` or `Active`{.action} is present in the `Status` column.
>
> ![exchange](images/account_migration_adddomain.png){.thumbnail}
>
> For more details on adding a domain name, follow the [Email Pro guide](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config#etape-2-ajouter-votre-nom-de-domaine), [the Exchange guide](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_adding_domain) or [the Zimbra guide](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra).

The migration of your MX Plan will take place in 3 main steps, **Rename**, **Create** and **Migrate**.

![exchange](images/mxplan-migration-configure-account.gif){.thumbnail}

1\. **Rename** the MX Plan account to be migrated with a temporary name (example: to migrate the MX plan account *john.smith@mydomain.ovh*, rename it to *john.smith01@mydomain.ovh*).

In the `Email Accounts`{.action} tab of your MX Plan platform, click on the `...`{.action} button then on `Edit`{.action}.

![exchange](images/mxplan-migration-configure-account01.png){.thumbnail}

> [!primary]
>
> The modification of the account is not immediate, please wait until the operation is completed before moving on to the next step.

2\. **Create** your email address on the new account of your Email Pro or Exchange platform (taking the previous example, you will therefore create *john.smith@mydomain.ovh* on your new platform).

In the `Email Accounts`{.action} tab of your Email Pro or Exchange platform, click on the `...`{.action} button then on `Edit`{.action}.

![exchange](images/mxplan-migration-configure-account02.png){.thumbnail}

3\. **Migrate** the MX Plan account to the account of your new platform using our [OMM](/links/web/omm) (OVHcloud Mail Migrator) tool.

For more information on OMM, consult our guide [Migrating email accounts via OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm).

![exchange](images/mxplan-migration-configure-account03.png){.thumbnail}

The migration time depends on the amount of content to be migrated to your new account. It can vary from a few minutes to several hours.

Check, after the migration, that you can find your items by logging in to the webmail at [Webmail](/links/web/email)

You can keep or delete the original account with the temporary name after this migration.

If you want to delete it, go to the `Email Accounts`{.action} tab of your MX Plan, click on the `...`{.action} button then on `Reset this account`{.action}.

#### 3.2 Automatic migration of an MX Plan Roundcube offer to Exchange or Email Pro <a name="roundcube-mxplan"></a>

> [!warning]
>
> This section concerns only MX Plan services using the Rouncube webmail technology.

> [!primary]
>
> Your OVHcloud account must be the administrator contact **and** the technical contact of the MX plan service to be migrated, **as well as** the Email Pro or Exchange service to which you are migrating.
>
> For more information on changing contacts, consult our guide for [managing the contacts of your services](/pages/account_and_service_management/account_information/managing_contacts).
>

The migration can be carried out from two interfaces:<br>

- **the Hosted Exchange configuration assistant interface**, only if you have just ordered a Hosted Exchange service and have not yet configured it;
- **the MX Plan interface**, as soon as you have an Email Pro or Exchange service (already configured or not) and an MX Plan address that you want to migrate.

> As a reminder, before starting the migration, make sure that no **redirection** or **autoresponder** is set up on your MX Plan.
>
> ![email](images/mxplan-legacy-redirect.png){.thumbnail}

Once you are ready, continue reading this documentation according to the selected interface. We remind you that the migration time depends on the amount of content to be migrated to your new account. It can vary from a few minutes to several hours.

> [!warning]
>
> Once the migration is confirmed, you will no longer be able to access your old MX Plan email address or cancel the migration process. We strongly advise you to carry out this operation at a suitable time.
>
> Even if you will no longer be able to access your current email address, the messages already received as well as those received will not be lost. All will be immediately accessible from your new account.
>

##### **Migration from the Exchange configuration assistant**

To access it, select the concerned service in the [OVHcloud control panel](/links/manager). The assistant should appear to help you configure your new Exchange service. During this process, you will be able to select the MX Plan email accounts to migrate.

If the configuration assistant does not appear, the general information of the Exchange service will appear instead. In this case, you will have to carry out the migration of your accounts via the MX Plan interface.

##### **Migration from the MX Plan interface**

To carry out the migration from this interface, go to the `Emails`{.action} section of your OVHcloud control panel. Then select the service bearing the domain name of your email addresses. Click on the cogwheel icon on the line of the concerned email account (also called the source account) then on `Migrate the account`{.action}.

![exchange](images/access_the_migration_tool.png){.thumbnail}

In the window that appears, select the destination service (the one to which you want to migrate the address) then click on `Next`{.action}. If it has at least one "free" account (i.e. not yet configured), the migration will take place to one of these accounts. Then, read the information that appears, validate them, then click on `Next`{.action} to continue the operation.

If you do not have a "free" account, a `Order accounts`{.action} button will appear. Follow the steps, then wait for the accounts to be installed to carry out the operation again.

Finally, confirm the password of the source email address (the one you want to migrate), then click on `Migrate`{.action}. This operation will have to be repeated as many times as necessary for the migration of other accounts.

![exchange](images/account_migration_steps.png){.thumbnail}

### Step 4: check or modify the configuration of your domain

At this stage, your email addresses should already be migrated and functional. For security reasons, we invite you to make sure that the configuration of your domain is correct by consulting your control panel.

To do this, select the concerned Email Pro, Exchange or Zimbra service, then go to the `Associated Domains`{.action} or `Domain`{.action} tab on your platform. Check the `Diagnostic`{.action} section or column.

![exchange](images/check_the_dns_records_associated_domains.png){.thumbnail}

> [!primary]
>
> If you have just completed the migration or modified a DNS record of your domain, it is possible that the display in the [OVHcloud control panel](/links/manager) will need a few hours to update.
>

To modify the configuration, click on the red badge and perform the requested operation. This operation requires a propagation time of 4 to 24 hours maximum before it is fully effective.

### Step 5: use your migrated email addresses

You just have to use your migrated email addresses. For this, OVHcloud provides a web application (_web app_) accessible at the address [Webmail](/links/web/email). You must enter the identifiers related to your email address.

If you have configured one of the migrated accounts on a mail client (such as Outlook), you must reconfigure it. The connection information to the OVHcloud server has changed following the migration. To help you with your operations, consult our documentation from the sections of the guides dedicated to [Email Pro](/products/web-cloud-email-collaborative-solutions-email-pro) and [Hosted Exchange](/products/web-cloud-email-collaborative-solutions-mx-plan). If you are not able to reconfigure the account immediately, access via the web application is still possible.

### Organisation of the content of your email addresses after a migration <a name="content-after-migration"></a>

When you log in for the first time on your new email account, the migrated content may be partially hidden. To display all items, from the webmail, click on the chevron next to the `Inbox` to reveal the sub-folders. The migrated content from your old email account should appear.

![exchange](images/owa_migrate_content.png){.thumbnail}

The default folders, such as "sent items" or "trash" appear in English ("Sent items" and "Trash"), except for the folders you have created.

After a migration, do not hesitate to explore all the folders and sub-folders of your account to check that all items are present.

### Manual Migration

You can also manually migrate your email addresses to your new OVHcloud email offer using only your email software. Refer to our guide [Manually Migrate Your Email Address](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration). We nevertheless recommend that you only use this method when the main methods are not possible.

## Go further

[Managing the contacts of your services](/pages/account_and_service_management/account_information/managing_contacts).

[Getting started with the Email Pro offer](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config).

[Getting started with the Exchange offer](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_hosted).

[Getting started with the Zimbra offer](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra)

Join our [community of users](/links/community).