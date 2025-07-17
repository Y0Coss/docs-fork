---
title: IAM for Logs Data Platform - Presentation and FAQ 
excerpt: A presentation on how IAM works with Logs Data Platform
updated: 2025-07-21
---

> [!primary]
> IAM for Logs Data Platform will be available starting **17th September 2025**.
> The content of this documentation is valid starting this date.
>

## Objective 

This guide explains the integration of Logs Data Platform with OVHcloud IAM. 

## Requirements 

- An [OVHcloud account](/pages/account_and_service_management/account_information/ovhcloud-account-creation)
- Access to the [OVHcloud Control Panel](/links/manager)
- A Logs Data Platform service.

## Instructions 

### How is IAM useful for Logs Data Platform ? 

Enabling OVHcloud IAM on Logs Data Platform delegates authentication, access management, and permissions to OVHcloud IAM. There are several benefits to using IAM:

- [All OVHcloud identities](/pages/manage_and_operate/iam/identities-management) can connect using their credentials to all Web UIs (Graylog/OpenSearch Dashboards). The connected account will be the identity chosen for UI access. **You will no longer need the Logs Data Platform username**. IAM enables also the use of [two-factors authentication methods](/pages/account_and_service_management/account_information/secure-ovhcloud-account-with-2fa) and [Federation Services](/pages/account_and_service_management/account_information/ovhcloud-account-connect-saml-adfs).
- APIs token can be both [service account tokens](/pages/account_and_service_management/account_information/authenticate-api-with-service-account) and Personal Access Tokens handled directly with OVHCloud IAM APIs.
- [Resource groups](/pages/account_and_service_management/account_information/iam-policies-api) allow you to share Logs Data Platform sub resource in a more cohesive way.
- [IAM Policies](/pages/account_and_service_management/account_information/iam-policy-ui/) unlocks advanced use cases not possible with permission thanks to fine grained actions.


[!iam identities](images/iam_policies.png)


### How to enable OVHcloud IAM for my existing account in Logs Data Platform ? 

If you have an existing service, follow these steps:

- Replace all your **Roles** and permission with [appropriate policies](/pages/manage_and_operate/observability/logs_data_platform/iam_access_management/).
- Ensure you have no **Roles** declared in your service. 
- Ensure your service is not in any **Roles**.
- Ensure you don't have any [tokens](/pages/manage_and_operate/observability/logs_data_platform/security_tokens).
- Use the dedicated `Enable OVHcloud IAM`{.action} in the **Roles** sections of the Logs Data Platform Control Panel. 

[! Activate IAM](images/activate_iam_existing_service.png)


Once IAM is activated, A new **IAM Policies** section will replace the previous **Roles** section. 

[!Activated IAM](images/activated_iam.png)

### How to enable OVHcloud IAM on a new service ? 

When a new service is created, you can directly opt-in into using IAM directly and use [IAM policies](/pages/account_and_service_management/account_information/iam-policy-ui/) to handle access rights. 

[! Activate IAM on a new service](images/activate_iam_new_service.png). 

Once IAM has been activated, you can freely use any [OVHcloud identities](/pages/manage_and_operate/iam/identities-management) to interact with Logs Data Platform


### How to connect to Graylog with IAM ? 

When connecting to Graylog, you can choose between the legacy username/password system (for services without IAM activated) or any OVHcloud IAM providers (EU, CA, or US). Clicking the corresponding *Log in* button redirects you to the appropriate OVHcloud IAM provider to complete authentication.


> [!carousel]
>
> - ![Graylog provider IAM 1](images/graylog_iam_eu.png)
> - ![Graylog provider IAM 2](images/graylog_iam_ca.png)
> - ![Graylog legacy](images/graylog_legacy.png)
>

### How to connect to OpenSearch Dashboards with IAM ? 


When connecting to OpenSearch Dashboards, select the provider linked to your OVHcloud service. The *Log in with OVHcloud IAM* button redirects you to your provider to complete authentication.

![OSD login](images/osd_iam_eu.png)

Once completed, you will be redirected back to the OpenSearch Dasboard instance fully authenticated.


### How to connect to Grafana with IAM ? 

- If your Identity Provider is the OVHCloud IAM, you can select the option **Forward OAuth identity** to forward the identity connected to the Logs Data Platform. 
- If you use another authentication provider, you can forge an *Authorization* header with a IAM compatible token. See the next section to see how to generate that kind of token. The content of the header must be ```Bearer: <Your Token>```. Replace *<Your Token>* with the value of your token. 

![Grafana header](images/grafana_header.png)


### How to interact with Logs Data Platform backends API ?

With IAM enabled, [tokens](/pages/manage_and_operate/observability/logs_data_platform/security_tokens) are replaced by API keys (Bearer authentication scheme). These keys can be tokens from [service accounts](/pages/account_and_service_management/account_information/authenticate-api-with-service-account) or Personal Access Tokens. Use the OVHcloud API to generate these tokens.

> [!api]
>
> @api {v1} /me POST /me/identity/user/{user}/token
>


For example if you are on gra1 cluster, curl can use these tokens in the following way:

```bash 
ldp@laptop curl -k -v -H 'content-type: application/json' --oauth2-bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c  -XGET 'https://gra1.logs.ovh.com:9200/_cluster/health?pretty' 
```


### How to create indices or aliases on Logs Data Platform backend APIs ?

First, ensure the identity you want to use has permission to create indices and aliases for the service. If authorized, Personal Access Tokens or service account OAuth2 clients can perform creation/deletion operations.

> [!warning]
> The previous prefix for indices and aliases was the username. Now the prefix is the **service name**. You will find the service name on the Homepage of the Logs Data Platform Panel. It is also the suffix of A Logs Data Platform service URN. For example: 
>
> urn:v1:eu:resource:ldp:**ldp-ab-56945**
>


The service is tied to a unique Logs Data Platform so you will be allowed to create items only on this cluster. For example if ldp-ab-56945 is on gra1: 


```bash
ldp@laptop curl -k -v -H 'content-type: application/json' --oauth2-bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c  -XPOST 'https://gra1.logs.ovh.com:9200/ldp-ab-56945-i-my-new-index/_doc' -d '{ "user" : "ldp" }'
```

Similarly aliases created through OpenSearch APIs must be prefixed by one of your allowed services.

## Go further

- [Introduction to Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_introduction_to_LDP)
- [IAM for Logs Data Platform - Presentation and FAQ](/pages/manage_and_operate/observability/logs_data_platform/iam_presentation_faq)
- [Our documentation](/products/public-cloud-data-platforms-logs-data-platform)
- Community hub: [https://community.ovh.com](https://community.ovh.com/en/c/Platform/data-platforms){.external}
- Create an account: [Try it!](https://www.ovh.com/fr/order/express/#/express/review?products=~(~(planCode~'logs-account~productId~'logs))){.external}
