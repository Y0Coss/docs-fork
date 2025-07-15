---
title: 'Configure access control using OVHcloud IAM on an OVHcloud Managed Private Registry'
excerpt: 'Learn how to enable and manage OVHcloud IAM authentication to control access to your Managed Private Registry (MPR) using centralized identities and roles.'
updated: 2025-07-21
---

## Objective

OVHcloud Managed Private Registry (MPR) supports authentication through OVHcloud IAM, allowing you to manage access using centralized user identities and roles. This guide explains how to enable IAM authentication and control user access to your registry using OVHcloud IAM users and roles.

## Requirements

- An OVHcloud Managed Private Registry (see the [creating a private registry](/pages/public_cloud/containers_orchestration/managed_private_registry/creating-a-private-registry) guide for more information)
- An access to the Harbor UI to operate the private registry (see the [connecting to the UI](/pages/public_cloud/containers_orchestration/managed_private_registry/connecting-to-the-ui) guide for more information)

## Instructions

### Introduction to OVHcloud IAM

OVHcloud IAM (Identity and Access Management) is a centralized system that lets you manage who can access your OVHcloud services and what they are allowed to do. It provides fine-grained access control through users, groups, and roles.

When used with Managed Private Registry (MPR), OVHcloud IAM replaces Harbor’s local user database. This enables you to:

- Use SSO (Single Sign-On) with your OVHcloud credentials to access Harbor.
- Assign predefined IAM roles (admin, standard) to control access levels.
- Manage permissions at scale using IAM groups and projects.

By integrating IAM with your registry, you ensure consistent access control across your OVHcloud services — reducing manual management and improving security.

### Activate/Disable authentication via OVHcloud IAM

> [!warning]
>
> When you enable OVHcloud IAM authentication on your Managed Private Registry:
> 
> - All existing Harbor users and robot accounts will be removed.
> - Existing robot accounts will continue to function, but you will no longer be able to create or manage them directly in Harbor.
> - From this point on, access is fully managed via OVHcloud IAM users and roles.
>

Log in to the [OVHcloud Control Panel](/links/manager), navigate to the `Public Cloud`{.action} section, and select the relevant project. Then, in the left-hand menu under **Containers & Orchestration**, click on `Managed Private Registry`{.action}.

In the list of registries, click the `...`{.action} button on the relevant line, then choose:

- `Activate authentication via OVHcloud IAM`{.action} to enable it.
- `Disable authentication via OVHcloud IAM`{.action} to disable it.

### Authentication using SSO with OVHcloud IAM users

Once IAM authentication is enabled, access to the Harbor UI is handled via OVHcloud Single Sign-On (SSO). Users no longer log in with Harbor-local credentials but authenticate directly using their OVHcloud IAM identity.

To log in via SSO:

- Open the `Harbor user interface`{.action} from the Control Panel.

![harbor user interface](images/)

- You will be redirected to the OVHcloud authentication page, log in using your OVHcloud IAM credentials.

![login with SSO](images/)

- Access to Harbor is granted based on the IAM role associated with your user account.

> [!primary]
>
> Only users with the appropriate IAM role (admin or standard) can access the registry after IAM authentication is enabled.
>

### Managing access rights with OVHcloud IAM

OVHcloud IAM provides two predefined roles for managing access to your Managed Private Registry (MPR):

- Standard
- Admin

> [!primary]
>
> **Admin** role: Regardless of the user group defined in the Identities section, assigning the Admin role will grant full administrative privileges on the selected registry.
> 
> **Standard** role: Make sure users assigned to the Standard role do not belong to the Default group in the `Identities` section. This group has elevated rights by default (including admin-level access with limited capabilities, such as no user creation). To ensure clean separation of roles, we recommend:
> 
> - Organizing users into clearly defined groups.
> - After changing a user’s group and assigning the Standard role, fine-tune their permissions directly in Harbor for better control and consistency. See the different roles in Harbor [here.](https://goharbor.io/docs/1.10/administration/managing-users/user-permissions-by-role/){.external}
>

These roles are assigned through IAM policies. To create and configure a policy: pour configurer une policy, navigate to the `Identity, Security & Operations`{.action} sectiont. Then, in the left-hand menu under **Identity and Access management**, click on `Policies`{.action} and click on `Create a policy`{.action} button.

In the OVHcloud Control Panel, go to the `Identity, Security & Operations`{.action} section. In the left-hand menu, under `Identity and Access Management`, click on `Policies`{.action} and `Create a policy`{.action}.

![Create policy](images/)

Define users and groups, name your policy, add the users you want to include and optionally, add user groups if they have already been created.

![Create policy users](images/)

Set permissions for MPR, in the `Product types` section, select `Public Cloud Project/Managed Registry`. In `Resources`, choose the specific MPR instance to which the policy will apply.

![Create policy product types](images/)

Expand `Public Cloud Project/Managed Registry` and select the desired role for the users defined in the policy.

![Create policy roles](images/)

### Go further

To go further you can look at our guides on:

- [Managing users and projects](/pages/public_cloud/containers_orchestration/managed_private_registry/managing-users-and-projects).
- [Creating and using a private image](/pages/public_cloud/containers_orchestration/managed_private_registry/creating-and-using-a-private-image).