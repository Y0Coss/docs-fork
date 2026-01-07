---
title: "Migrate your email addresses from one OVHcloud email platform to another"
excerpt: "Learn how to migrate email addresses from an Exchange or E-mail Pro platform to another Exchange, E-mail Pro, MX Plan or Zimbra platform"
updated: 2025-12-22
---

## Objective

You want to migrate your email addresses from an Exchange or E-mail Pro platform to another Exchange, E-mail Pro or MX Plan platform. This guide provides a two-phase migration process:

1. **Configure the destination platform**.
2. **Migrate the email accounts** from your current platform to the new one.

![email-migration](images/migration_platform01.gif){.thumbnail}

> [!primary]
>
> To migrate an MX Plan solution to an Exchange or E-mail Pro platform, we invite you to follow our guide [Migrate an MX Plan email address to an E-mail Pro or Exchange account](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_control_panel).
>

**Discover how to migrate email addresses from an Exchange or E-mail Pro platform to another Exchange or E-mail Pro platform.**

## Requirements

- Have a **"source"** platform with configured [Exchange](/links/web/emails-hosted-exchange) or [E-mail Pro](/links/web/email-pro) accounts or [Zimbra](/links/web/zimbra).
- Have a **"destination"** platform with [Exchange](/links/web/emails-hosted-exchange), [E-mail Pro](/links/web/email-pro) or MX Plan (via the MX Plan offer or included in an [OVHcloud web hosting](/links/web/hosting) offer) accounts. This platform must have unconfigured or available accounts to accommodate the email addresses to be migrated.
- Be logged in to your [OVHcloud Control Panel](/links/manager).

## Instructions

### Configure the destination platform

> [!warning]
>
> Before starting your migration, if you have just ordered your new email offer, first add the domain name to your email platform. If you are migrating to an MX Plan platform, the attached domain name being "fixed", you can directly proceed to the [next step](#accountsmigration).
>
> Select the `Associated Domains`{.action} or `Domain`{.action} tab on your platform, then click on `Add a domain`{.action}. Once the domain name is added, make sure the `OK` or `Active`{.action} mention is present in the `Status` column.
>
> ![exchange](images/account_migration_adddomain.png){.thumbnail}
>
> For more details on adding a domain name, follow the [E-mail Pro guide](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config#etape-2-ajouter-votre-nom-de-domaine), [the Exchange guide](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_adding_domain) or [the Zimbra guide](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra).

### Migrate the email accounts <a name="accountsmigration"></a>

The migration of your email accounts will take place in 3 main steps: **Rename** the original email account, **create** the new email account and **migrate** from the original platform to the new one.

![email-migration](images/migration_platform03.gif){.thumbnail}

> [!warning]
>
> Special case:
>
> - If you need to migrate an **Exchange or Zimbra PRO** account to an **E-mail Pro** or **Zimbra STARTER** account, you must ensure that your email accounts do not exceed 10 GB (E-mail Pro) or 15 GB (Zimbra STARTER). Collaborative features, calendar and contact synchronization are not available on E-mail Pro or Zimbra STARTER and cannot be migrated.
> - If you need to migrate an **Exchange, E-mail Pro or Zimbra** account to an **MX Plan** account, you must ensure that your email account does not exceed 5 GB. Collaborative features, calendar and contact synchronization are not available on MX Plan and cannot be migrated.

#### Rename

Rename the email account to be migrated with a temporary name (example: to migrate the email account *john.smith@mydomain.ovh*, rename it to *john.smith01@mydomain.ovh*).

In the `Email Accounts`{.action} tab of your email platform, click on the `...`{.action} button then on `Edit`{.action}.

![email-migration](images/migration_platform04.png){.thumbnail}

#### Create

Create your email address on the new account of your E-mail Pro, Exchange or MX Plan platform (using the previous example, you will therefore create *john.smith@mydomain.ovh* on your new platform).

In the `Email Accounts`{.action} tab of your platform, click on the `...`{.action} button, to the right of the destination email account, then on `Edit`{.action}.

![email-migration](images/migration_platform05.png){.thumbnail}

#### Migrate

> [!warning]
> 
> Only the data from your email accounts will be migrated (emails, contacts, calendars, inbox rules, etc.). Features related to your platform will need to be recreated on the new platform :
>
> - [Aliases](/pages/web_cloud/email_and_collaborative_solutions/common_email_features/feature_redirections) 
> - [Rights Delegation](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_delegation) 
> - [Groups](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_groups)
> - External contacts
> - [Footers](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_footers)

Migrate the "source" email account to your new platform account using our [OMM](/links/web/omm) (OVHcloud Mail Migrator) tool.

For more information on OMM, see our guide [Migrate email accounts via OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm).

![email-migration](images/migration_platform06.png){.thumbnail}

The migration time depends on the amount of data to be migrated to your new account. It can vary from a few minutes to several hours.

After the migration, check that you can find all your items by logging in to the webmail at [Webmail](/links/web/email).

Once the migration is complete, you can keep or delete the original account with the temporary name.

If you want to delete it, go to the `Email Accounts`{.action} tab of your original email platform, click on the `...`{.action} button then on `Reset this account`{.action}.

### Check or modify your domain configuration

At this stage, your email addresses should already be migrated and functional. For security reasons, we recommend that you check that your domain configuration is correct by consulting your customer area.

To do this, select the relevant E-mail Pro, Exchange or Zimbra service, then go to the `Associated Domains`{.action} or `Domain`{.action} tab on your platform. Check the `Diagnostics`{.action} section or column.

![exchange](images/check_the_dns_records_associated_domains.png){.thumbnail}

> [!primary]
>
> If you have just completed the migration or modified a DNS record of your domain, it is possible that the display in the [OVHcloud Control Panel](/links/manager) will need a few hours to update.
>

To modify the configuration, click on the red badge and perform the requested action. This will require a propagation time of up to 4 to 24 hours before it is fully effective.

![email-migration](images/check_the_dns_records_associated_domains.png){.thumbnail}

### Use your migrated email addresses

All that remains is to use your migrated email addresses. For this, OVHcloud provides an online application (_web app_) accessible at [Webmail](/links/web/email). You must enter the credentials related to your email address there.

If you have configured one of the migrated accounts on an email client (example: Outlook, Thunderbird), you must reconfigure it. The connection information to the OVHcloud server has changed following the migration.

> [!primary]
>
> You can also manually migrate email addresses to OVHcloud using our [OVHcloud Mail Migrator (OMM)](/links/web/omm) tool. For this, you must have the information (user, password, servers) of the source and destination emails.
>

## Go further

[Managing contacts for your services](/pages/account_and_service_management/account_information/managing_contacts).

[Getting started with the E-mail Pro offer](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config).

[Getting started with the Exchange offer](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_hosted).

[Getting started with the Zimbra offer](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra)

Join our [community of users](/links/community).