---
title: 'Assigning a tag to a Bare Metal server'
excerpt: 'Create and modify tags for individual servers in the OVHcloud Control Panel'
updated: 2025-02-05
---

## Objective

Create tags to assign to your services, in order to organize them, and apply policies to them with the desired granularity.

**This guide details how to assign and remove tags for individual servers, from the OVHcloud Control Panel.**

## Introduction

Tags are labels that you can assign to your resources, which allow you to organize and manage them more efficiently. Each tag consists of two parts: the key, which represents an attribute or category, and the value, which is the information associated with that key.

For example, you can categorize your resources by site, service, or even security level. Such use of tags can facilitate searching, organizing your resources, managing associated costs, or applying strategies with the desired granularity, notably.

## Requirements
- A [dedicated server](/links/bare-metal/bare-metal) in your OVHcloud account
- Access to the [OVHcloud Control Panel](/links/manager)

### Assigning a tag to a server in the OVHcloud Control Panel

To start using tags, log in to the [OVHcloud Control Panel](/links/manager){.external} and choose the `Bare Metal Cloud`{.action} section. Click on `Dedicated Servers`{.action} and select your server from the list.

![General information](images/general_information2025.png){.thumbnail}

[//]: # (The image links in this guide have to be populated with the appropriate screenshots from the FIGMA prototype, or directly from the OVHcloud Control Panel when available)

In the tab `General information`{.action} (1), click on the `Add tags`{.action} button (2) in the **Tags** box. Next, click `Assign tag`{.action}  (2).

![Tag list empty](images/Tag_list_empty2025.png){.thumbnail}

Open the dropdown menu under `Tag key`{.action} and select the tag you want to apply to the server. 
Then, similarly open the dropdown menu under `Tag value`{.action} and select the appropriate value. 
If you wish to use a tag or value that is not yet created, type it, then click `Add your-value`{.action}, where "your-value" is replaced by the text you entered.

![Assign tag](images/assign_tag2025.png){.thumbnail}
![Assign tag populated](images/assign_tag_populated2025.png){.thumbnail}

Finally, click the `Assign`{.action} button on the lower right part of the window.
You can then see the list of tags applied to the chosen server.

![Tag list with example](images/tag_list_with_example2025.png){.thumbnail}

### Removing a tag from a server

From the assigned tags list, click the `...`{.action} button, to the right of the tag you wish to remove.
Then, click `Unassign`{.action}.

![Tag list unassign](images/tag_list_unassign2025.png){.thumbnail}

A window will appear, prompting you for confirmation. Click the `Confirm`{.action} button do unassign the tag.

![Unassign tag](images/unassign_tag2025){.thumbnail}

## Go further

[How to use the Resource Tag Manager](/pages/bare_metal_cloud/dedicated_servers/resource-tag-manager)

Join our [community of users](/links/community).