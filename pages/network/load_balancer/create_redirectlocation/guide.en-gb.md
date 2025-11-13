---
title: 'Working with redirections'
universe: cloud
excerpt: 'Integrate your web services behind a Load Balancer with redirections'
updated: 2021-02-05
---

## Objective

The **OVHcloud Load Balancer** operates by default as a proxy. It can also be configured to redirect client traffic to a third-party website. This functionality is essential for scenarios such as **domain name migration** or enforcing the **HTTPS version** of a website. This is known as **HTTP redirection**.

**This guide outlines the process for integrating your web services behind an OVHcloud Load Balancer utilizing HTTP redirections.**

## Requirements

- An [OVHcloud Load Balancer](/links/network/load-balancer)
- Access to the [OVHcloud Control Panel](/links/manager)
- Access to the [OVHcloud API](/links/api)

## Instructions

### Presentation

An HTTP redirection is presented as follows:

```bash
HTTP/1.1 301 Moved Permanently
Location: http://www.example.org/
Content-Type: text/html
Content-Length: 174
```

Custom redirections must use the following format: `<scheme>://<net_loc>/<path>;<params>?<query>#<fragment>`. Only **one redirection** can be specified per front-end.

Custom redirections can be configured via the OVHcloud Control Panel and the API, both on new and existing `front-ends`{.action}.

### Add a custom redirection via the OVH Control Panel.

You can configure custom redirections from the [OVHcloud Control Panel](/links/manager) by navigating to the `Cloud`{.action} section, then selecting `Load Balancer`{.action}.

This configuration can be performed either during the creation of a new front-end or by modifying an existing one.

- **Add a new front-end.**

In the `Front-ends`{.action} section of the OVHcloud Control Panel, click `Add a front-end`{.action} to create a new one.

On the front-end editing page, select either the `HTTP`{.action} or `HTTPS`{.action} protocol. Provide the required information. However, be aware that setting a `Default farm`{.action} is unnecessary, as it will not be utilized for a redirection front-end.

Under advanced settings, input the target `HTTP redirection`{.action} URL.

- **Edit an existing front-end.**

In the `Front-ends`{.action} section of the OVHcloud Control Panel, select the front-end you would like to edit. To do this, click the `...`{.action} button, then select `Edit`{.action} from the menu. Please ensure that the selected front-end uses either the `HTTP` or `HTTPS` protocol.

On the front-end editing page, complete the configuration as needed. However, please note that defining a `Default farm`{.action} is not required, as it will not be used.

In the advanced settings, enter the `HTTP redirection`{.action} URL.

![Configure a front-end redirection](images/add_redirectlocation.png){.thumbnail}

Once the front-end has been configured, click `Add`{.action} or `Edit`{.action}, depending on whether you are configuring a new or existing front-end. Please remember to deploy the configuration. This can be achieved in two ways:

- via the `Status`{.action} section of the OVHcloud Control Panel, by clicking on your Load Balancer’s `...`{.action} button, then selecting `Apply configuration`{.action}

- via the reminder banner in the OVHcloud Control Panel, which notifies you that the configuration has not been applied, by clicking `Apply configuration`{.action}

![Apply a Load Balancer configuration](images/apply_configuration.png){.thumbnail}

### Add a custom redirection via the API.

Within the [OVHcloud API](/links/api), redirections are specified using the `redirectLocation` character string parameter.

- **If you are creating a new front-end:**

> [!api]
>
> @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/http/frontend
> 

|Setting|Meaning|
|---|---|
|serviceName|Your Load Balancer service ID|
|port|Front-end listening ports|
|zone|Front-end deployment zones|
|redirectLocation|HTTP redirection URL|

- **If you are updating an existing front-end:**

> [!api]
>
> @api {v1} /ipLoadbalancing PUT /ipLoadbalancing/{serviceName}/http/frontend/{frontendId}
> 

|Setting|Meaning|
|---|---|
|serviceName|Your Load Balancer service ID|
|frontendId|ID of the front-end to be updated|
|redirectLocation|HTTP redirection URL|

Then, you must apply the modifications:

> [!api]
>
> @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/refresh
>

|Setting|Meaning|
|---|---|
|serviceName|Your Load Balancer service ID|
|zone|Front-end deployment zones|

## Go further

Join our community of users on <https://community.ovhcloud.com/en/>.