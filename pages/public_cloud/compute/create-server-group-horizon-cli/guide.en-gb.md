---
title: 'Creating and using a server group in Horizon and CLI'
excerpt: 'Find out how to create a server group and use it for Public Cloud instance'
updated: 2025-09-16
---

This documentation explains how to use the server groups feature to control the scheduling of a group of servers (instances).

**Using Server groups to provide a mechanism to group servers according to a certain policy**

## Prerequisites

In order to use server groups you must use the OpenStack Dashboard or the Openstack CLI. Make sure you have [enabled it](../../getting-started/enable-openstack-cli.md).

### Definition

#### Policies

A server group can have one of four different policies: **affinity**, **soft-affinity**, **anti-affinity** or **soft-anti-affinity**.

##### **Affinity**

A server group with the policy of `affinity` will make sure that all the servers in that group are **always** placed on the same physical compute node.

##### **Soft-affinity**

A policy of `soft-affinity` will **try to** make sure that all the servers in that group are placed on the same physical compute node, but ultimately will allow it if otherwise not possible.

##### **Anti-affinity**

A server group with the policy of `anti-affinity` will make sure that the servers in that group are **never** placed on the same physical compute node.

##### **Soft anti-affinity**

A policy of `soft-anti-affinity` will **try to** make sure that all the servers in that group are not placed on the same physical compute node, but ultimately will allow it if otherwise not possible.

### Step 1: Creating server groups

> [!tabs]
>
> **Openstack Dashboard**
>> >![Keystone](images/Create_Server_Groups_OpenStack_Dashboard.png){.thumbnail}
>> >
>> >* Log in to the [Horizon interface](https://horizon.cloud.ovh.net/auth/login/).
>> >* Select the appropriate region from the drop down menu at the top left.
>> >* On the Project tab, open the `Compute`{.action} tab and click the `Server Groups`{.action} category.
>> >* Click on `Create Server Group`{.action}.
>> >* In the popup window you will be taken to a form where you may setup your virtual machine. You can customize the Server Group with adding one from Available to Allocated to add the instance(s) to the server groups.
>> >* Click `Launch Instance`{.action}.
>>
> **CLI**
>> To create a server group, use the following command:
>>
>> ```bash
>> openstack server group create \ --policy [affinity|soft-affinity|anti-affinity|soft-anti-affinity] \<server_group_name>
>>```

### Step 2: Creating servers using server groups

> [!tabs]
> Openstack Dashboard
>> >
>> > Horizon can create, read, update, and delete and also get a list of server groups for a tenant to allow specification of a group when booting a VM.  
>> >
>> >* Log in to the [Horizon interface](https://horizon.cloud.ovh.net/auth/login/).
>> >* Select the appropriate region from the drop down menu at the top left.
>> >* On the Project tab, open the `Compute`{.action} tab and click the `Instances`{.action} category.
>> >* In the popup window that appears in the Server Group tab and select the Policy for the Server Group, and click on `Submit`{.action} to create the group.
>> > ![create_an_server_with_server_group_OpenStack_Dashboard](images/create_an_server_with_server_group_OpenStack_Dashboard.png){.thumbnail}>> >
>> >* Click on `Launch Instances`{.action}.
>> >
> CLI
>> >
>> > To apply a server group policy, you must specify the group when creating a server, as a *scheduling hint.*  
>> > To do that, use the `--hint` parameter in the following command
>> >
>> > ```bash
>> > openstack server create --hint group=<server_group_id> [...] <server_name>
>> >```

If you subsequently launch more servers referencing the same server group, the scheduler concentrates or distributes them according to the server group's policy.

### Modifiying a server group

![List_Server_Groups_OpenStack_Dashboard](images/List_Server_Groups_OpenStack_Dashboard.png){.thumbnail}

> [!alert]
>
> Once created, a server group cannot be modified.  
>
> In addition, a server cannot move between server groups.  
>
> In both cases, this is because doing so would require potentially moving the server to satisfy the server group policy.

### Troubleshooting common issues

> [!warning]
>
> If you keep creating servers within a server group with a policy of `anti-affinity`, you will eventually exceed the total amount of physical compute nodes in the region.  
>
> The command will still succeed, but the server will subsequently fail to be scheduled to a compute node.  

Instead, it will assume the `ERROR` status with the following `fault` message: _No valid host was found. There are not enough hosts available.

```bash
$ openstack server show -c fault -c status <server_id>
+--------+--------------------------------------------------+
| Field  | Value                                            |
+--------+--------------------------------------------------+
| fault  | {'code': 500, 'created': '2025-09-15T11:21:33Z', |
|        | 'message': 'No valid host was found.             |
|        | There are not enough hosts available.'}          |
| status | ERROR                                            |
+--------+--------------------------------------------------+
```

![Server_group_instances_error_OpenStack_Dashboard](images/Server_group_instances_error_OpenStack_Dashboard.png){.thumbnail}

Another reason is that Openstack cannot schedule the server on a different physical compute node because there is already a server in the server group on every node.

The same scheduling error and "fault" message will occur when using a server group with a policy of `affinity` as well, when you create more servers than a physical compute node can host.

However when using a soft-affinity policy, such as `soft-affinity` or `soft-anti-affinity`, the scheduler is allowed to break the server group's policy if it is unable to uphold it.

### Checking Server in a Server group

This means you may want to verify that your servers are on the same or on different physical compute nodes by looking at the _hostId_ value of your servers. We have deployed four instances two named `anti_affinity_server` with an `anti_affinity server group` and two named `affinity_server` with an `affinity server group`.

```bash
openstack server list 
+------------------------+--------+-----------+--------+
| Name                   | Status | Image     | Flavor |
+------------------------+--------+-----------+--------+
| affinity_server-2      | ACTIVE | Debian 13 | d2-4   |
| affinity_server-1      | ACTIVE | Debian 13 | d2-4   |
| anti_affinity_server-1 | ACTIVE | Debian 13 | d2-2   |
| anti_affinity_server-2 | ACTIVE | Debian 13 | d2-2   |
+------------------------+--------+-----------+--------+
```

You can confirm the scheduler was done following the policy of the server group with the following command:

```bash
openstack server show -c hostId xSERVER_IDx
```

With the 4 instances created, you will obtain the following output example:

```bash
openstack server show -c hostId affinity_server-2
+--------+----------------------------------------------------------+
| Field  | Value                                                    |
+--------+----------------------------------------------------------+
| hostId | c53cff4ce860b94139db559cfeafc08d228b48925ca00f1b05f3a23d |
+--------+----------------------------------------------------------+
openstack server show -c hostId affinity_server-1
+--------+----------------------------------------------------------+
| Field  | Value                                                    |
+--------+----------------------------------------------------------+
| hostId | c53cff4ce860b94139db559cfeafc08d228b48925ca00f1b05f3a23d |
+--------+----------------------------------------------------------+
openstack server show -c hostId anti_affinity_server-1
+--------+----------------------------------------------------------+
| Field  | Value                                                    |
+--------+----------------------------------------------------------+
| hostId | 66e9f9525487cad5cab2da65a51542d5a9bc0ca4bdb9fea7cdce8424 |
+--------+----------------------------------------------------------+
openstack server show -c hostId anti_affinity_server-2
+--------+----------------------------------------------------------+
| Field  | Value                                                    |
+--------+----------------------------------------------------------+
| hostId | 2c2907e312fec85fd92929a5afcc2ca4ac22c09c85480eea95b4fc08 |
+--------+----------------------------------------------------------+
```

`hostId` is a unique identifier for each physical compute node. By comparing this value on your different servers you can be sure if your server group policy is being upheld or not.

> [!primary]
>
> It's not possible to compare `hostId` between different projects because the values are unique for each project.
>

### Server group quota

> [!primary]
>
> You have to use or specify --os-compute-api-version 2.50 or higher to see server-groups and server-group-members output for a given quota class.
>

Regarding quota, Server Groups and Server Groups Members are in the Compute Service Quotas.

| Quota | Description | Property name |
| ----------- | ------------------------------------------------------ | ------------------------------------------------------|
| Server Groups | Number of server groups per project. | server_groups |
| Server Group Members | Number of servers per server group. |server_group_members |

```bash
openstack quota show --compute <PROJECT>
```

Here is an output example

```bash
openstack quota show <project> |grep -i server-group
| server-group-members        | 10                               |
| server-groups               | 10                               |
```

## Go further

Join our [community of users](/links/community).