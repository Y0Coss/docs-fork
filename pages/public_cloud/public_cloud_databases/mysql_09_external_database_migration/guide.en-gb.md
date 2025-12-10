---
title: MySQL - External database migration
excerpt: This guide explain how to migrate an external Mysql database to a managed Mysql database
updated: 2025-12-09
---

## Objective

This guide explain how to migrate an external Mysql database to a Mysql Public Cloud Databases.

## Requirements

- A [Public Cloud project](/links/public-cloud/public-cloud) in your OVHcloud account.
- A database running on your OVHcloud Public Cloud Databases ([this guide](/pages/public_cloud/public_cloud_databases/databases_01_order_control_panel) can help you to meet this requirement).
- Access to your [OVHcloud Control Panel](/links/manager) or to the [OVHcloud API](/links/api).

## Instructions

### Prerequise

- The source database should be in >= 5.7 and <= 8.0
- gtid_mode is ON on both the source and the target
- User with read and replication data permission can be create on the source database

### Set up

- Create a managed Mysql in your public cloud project
- Create a user on the source database with replication and read data permissions

### Using API

>> > [!api]
>> >
>> > @api {v1} /cloud POST /cloud/project/{serviceName}/database/mysql/{clusterId}/migration/check
>> >
>>
>> ```console
>> body : {
>>    "sourceHost": <hostmane>,
>>    "sourcePassword": <replication user password>,
>>    "sourcePort": 3306,
>>    "sourceSsl": true,
>>    "sourceUsername": <replication user name>
>> }
>> ```
>>
>> Create a task to check if the migration is possible
>>

>> > [!api]
>> >
>> > @api {v1} /cloud GET /cloud/project/{serviceName}/database/mysql/{clusterId}/migration/check
>> >
>>
>> Get the result of the migration check task.
>> If the Success field is true you can continue.
>> If not, you can see the reason in the result field.

>> > [!api]
>> >
>> > @api {v1} /cloud POST /cloud/project/{serviceName}/database/mysql/{clusterId}/migration
>> >
>>
>> ```console
>> body : {
>>    "sourceHost": <hostmane>,
>>    "sourcePassword": <replication user password>,
>>    "sourcePort": 3306,
>>    "sourceSsl": true,
>>    "sourceUsername": <replication user name>
>> }
>> ```
>>
>> Create a task to migrate the external database to the managed database
>>

>> > [!api]
>> >
>> > @api {v1} /cloud GET /cloud/project/{serviceName}/database/mysql/{clusterId}/migration
>> >
>>
>> Get the result of the migration 
>>

>> > [!api]
>> >
>> > @api {v1} /cloud POST /cloud/project/{serviceName}/database/mysql/{clusterId}/migration/stop
>> >
>>
>> When the migration is finished, the task continues to replicate the source database.
>> You need to stop it with this request to fully finish the process.
>> Take care if you do not do it and delete data in the source database, these updates will be replicated to the target database.

### Users

Curently the users are not migrate in this process and need to be recreated in the managed database manually

## Go further

Visit our dedicated Discord channel: <https://discord.gg/ovhcloud>. Ask questions, provide feedback and interact directly with the team that builds our databases services.

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for a custom analysis of your project.

Join our [community of users](/links/community).
