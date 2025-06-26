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

For example, you can categorize your resources by site, service, or even security level. Such use of tags can notably facilitate searching, organizing your resources, managing associated costs, or applying strategies with the desired granularity.

## Requirements
- A [dedicated server](/links/bare-metal/bare-metal) in your OVHcloud account
- Access to the [OVHcloud Control Panel](/links/manager)

### Assigning a tag to a server in the OVHcloud Control Panel

To start using tags, log in to the [OVHcloud Control Panel](/links/manager){.external} and choose the `Bare Metal Cloud`{.action} section. Click on `Dedicated Servers`{.action} and select your server from the list.

![General information](images/general_information.png){.thumbnail}

In the tab `General information`{.action} (1), click on the `Add a tag`{.action} button (2) in the **Tags** box. Next, click `Assign a tag`{.action}  (2).

![Add a tag](images/add_a_tag.png){.thumbnail}

![Empty tag list](images/tag_list_empty.png){.thumbnail}

Open the dropdown menu under `Tag key`{.action} and select the tag you want to apply to the server. 
Then, similarly open the dropdown menu under `Tag value`{.action} and select the appropriate value. 
If you wish to use a tag or value that is not yet created, type it, then click `Add your-value`{.action}, where "your-value" is replaced by the text you entered.

![Assign a tag](images/assign_tag.png){.thumbnail}

![Assign a tag - populated](images/assign_tag_populated.png){.thumbnail}

Finally, click the `Add`{.action} button to create the tag, then the `Assign`{.action} button on the lower right part of the window. 
You will receive a green confirmation message, then see the list of tags applied to the chosen server.

![Tag added](images/tag_added.png){.thumbnail}

![Tag list with example](images/tag_list_with_example.png){.thumbnail}

### Removing a tag from a server

From the assigned tags list, click the `...`{.action} button, to the right of the tag you wish to remove.
Then, click `Remove`{.action}.

![Tag list remove](images/tag_list_remove.png){.thumbnail}

A window will appear, prompting you for confirmation. Click the `Confirm`{.action} button to remove the tag.

![Remove tag](images/remove_tag.png){.thumbnail}

## Go further

Join our [community of users](/links/community).