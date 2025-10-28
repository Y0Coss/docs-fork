---
title: Known limits
excerpt: 'Requirements and limits to respect'
updated: 2025-04-30
---

<style>
 pre {
     font-size: 14px;
 }
 pre.console {
   background-color: #300A24;
   color: #ccc;
   font-family: monospace;
   padding: 5px;
   margin-bottom: 5px;
 }
 pre.console code {
   b   font-family: monospace !important;
   font-size: 0.75em;
   color: #ccc;
 }
 .small {
     font-size: 0.75em;
 }
</style>

## Nodes and pods

### Free Plan

We have tested our OVHcloud Managed Kubernetes service Free Plan with up to **100 nodes per cluster** and **100 pods per node**.

While higher configurations might work, we recommend staying under these limits for optimal stability.

Nodepools using anti-affinity are limited to 5 nodes per pool. You can create multiple nodepools with the same instance flavor if needed.

To ensure high availability for your workloads, it is recommended to have sufficient compute capacity to handle the workload even if one node becomes unavailable.

Any operation requested to our services, such as node deletions or rolling updates, follows a **graceful draining procedure** respecting [Pod Disruption Budgets](https://kubernetes.io/docs/tasks/run-application/configure-pdb/) for a maximum duration of 10 minutes. After this period, nodes are forcefully drained to allow operations to continue.

Worker nodes (added manually or through the Cluster Autoscaler) are generally ready within a few minutes.

> [!primary]
>
> GPU worker nodes (t1 and t2 flavors) may take more than one hour to reach a ready state.
>  

As a fully managed service, you will **not have SSH access** to the nodes. All OS and component updates are handled automatically.

### Standard Plan

The Standard Plan has been tested with up to **500 nodes per cluster**, maintaining the same **100 pods per node** limit.

Nodepools with anti-affinity are also limited to 5 nodes per pool, but multiple nodepools with the same flavor can be created.

To ensure high availability, your cluster should have enough compute resources to handle workloads even if one or more nodes fail or become unavailable.

> [!primary]
>  
> Operations such as node deletions or rolling updates follow the same **graceful draining procedure** as Free Plan, respecting PDBs for up to 10 minutes. Nodes are forcefully drained afterwards if necessary.
>

Worker nodes are created within a few minutes, except GPU nodes (t1 and t2 flavors), which may take longer than an hour to become ready.

> [!primary]
>  
> SSH access is not provided, similar to the Free Plan.
>

## Data persistence

### Free Plan

If an incident is detected by the OVHcloud monitoring, as part of auto-healing, or in case of a version upgrade, the nodes can be fully reinstalled.

It is recommended to save your data in Persistent Volumes (PV), not directly on nodes, to avoid data loss.
Follow our [guide about how to setup and manage Persistent Volumes on OVHcloud Managed Kubernetes](/pages/public_cloud/containers_orchestration/managed_kubernetes/setting-up-a-persistent-volume) for more information.

### Standard Plan

For Standard Plan clusters, Persistent Volumes are provisioned using **zone-specific StorageClasses**:

- `csi-cinder-high-speed`
- `csi-cinder-high-speed-gen2`

> [!primary]
>
> A PVC provisioned in a given zone will only be accessible from nodes in that same zone.
>

Classic multi-attach is **not supported** for multi-AZ clusters, as attaching volumes to multiple instances in different zones can lead to data corruption.

Standard Plan clusters also have a **dedicated etcd** with a **quota of 8 GB** per cluster. Real-time monitoring of etcd usage is not yet supported.

## LoadBalancer

Creating a Kubernetes service of type LoadBalancer triggers the creation of a Public Cloud Load Balancer based on OpenStack Octavia.  
The lifespan of the external Load Balancer (and the associated IP address, if not explicitly specified to keep it) is linked to the lifespan of the Kubernetes resource.  

This behavior applies to both Free and Standard Plans.  
For more information, see [expose services through a LoadBalancer](/pages/public_cloud/containers_orchestration/managed_kubernetes/expose_your_applications_using_a_load_balancer).

## OpenStack & Quota

Our Managed Kubernetes service is based on OpenStack, and your nodes, persistent volumes and load balancers are built on it, using OVHcloud Public Cloud. As such, you can see them in the `Compute` > `Instances` section of your [OVHcloud Public Cloud Control Panel](/links/manager). Though it doesn't mean that you can deal directly with these nodes and persistent volumes the same way you can do it for other Public Cloud instances.

Also, MKS Cluster's quota relies on your project's quota. Consult [this documentation](/pages/public_cloud/public_cloud_cross_functional/increasing_public_cloud_quota) to increase your quota.

The *managed* part of OVHcloud Managed Kubernetes Service means that we have configured those nodes and volumes to be part of our Managed Kubernetes.  
Please refrain from manipulating them from the *OVHcloud Public Cloud Control Panel* (modifying ports left opened, renaming, resizing volumes...), as you could break them.

There is also a limit of __20__ Managed Kubernetes Services by Openstack project (also named Openstack tenant).


Managed Kubernetes clusters are based on OpenStack. Nodes, persistent volumes, and load balancers are built on it using OVHcloud Public Cloud. As such, you can see them in the `Compute` > `Instances` section of your [OVHcloud Public Cloud Control Panel](/links/manager).

> [!primary]
>
> This does not mean you can manage them directly as other Public Cloud instances. The nodes and volumes are fully managed as part of OVHcloud Managed Kubernetes.
>

MKS Cluster quotas rely on your project's quota. Consult [this documentation](/pages/public_cloud/public_cloud_cross_functional/increasing_public_cloud_quota) to increase your quota if necessary.

> [!warning]
> Do not manipulate nodes or volumes directly through the OVHcloud Public Cloud Control Panel (e.g., modifying ports, renaming, resizing volumes), as this may break your cluster.

There is also a limit of **20 Managed Kubernetes Services per OpenStack project**.

### Node naming

Due to known limitations currently present in the `Kubelet` service, be careful to set __a unique name__ to all your Openstack instances running in your tenant __including__ your "Managed Kubernetes Service" nodes and the instances that your start directly on Openstack through manager or API.  

The usage of the __period (`.`)__ character is forbidden in node name. Please, prefer the __dash__ (`-`) character instead.

## Ports

To ensure proper operation of your OVHcloud Managed Kubernetes cluster, certain ports must remain open.

### Ports to open from public network (INPUT)

| Port(s)       | Protocol | Usage |
| ------------- | -------- | ----- |
| 22            | TCP      | SSH access for node management by OVHcloud |
| 30000–32767   | TCP      | needed for [NodePort](https://kubernetes.io/docs/concepts/services-networking/service/#nodeport) and [LoadBalancer](https://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer) services |
| 111           | TCP      | rpcbind (only if using NFS client) |

### Ports to open from instances to public network (OUTPUT)

| Port(s)                 | Protocol | Usage                                                |
| ----------------------- | -------- | ---------------------------------------------------- |
| 443                     | TCP      | Kubelet communication with the kubernetes API server |
| 80 (169.254.169.254/32) | TCP      | Init service (OpenStack metadata)                    |
| 25000–31999             | TCP      | TLS tunnel between pods and kubernetes API server    |
| 8090                    | TCP      | Internal (OVHcloud) node management service          |
| 123                     | UDP      | NTP servers synchronization (systemd-timesync)       |
| 53                      | TCP/UDP  | Allow domain name resolution (systemd-resolve)       |
| 111                     | TCP      | rpcbind (only if using NFS client)                   |
| 4443                    | TCP      | Metrics server communication                         |

### Ports to open from others worker nodes (INPUT/OUPUT)

| Port(s)       | Protocol | Usage |
| ------------- | -------- | ----- |
| 8472          | UDP      | Flannel overlay network (for communication between pods) |
| 4789          | UDP      | Kubernetes DNS internal usage |
| 10250         | TCP      | Needed for [communication between apiserver and worker nodes](https://kubernetes.io/docs/concepts/architecture/master-node-communication/#apiserver-to-kubelet) (kubelet) |

> [!warning]
>
> Blocking any of the above ports may cause cluster malfunction.
>
> For Standard Plan clusters, the same rules apply.
>
> Keep the default OpenStack security group unchanged to avoid disconnecting nodes; only add application-specific rules carefully.
>

### About OpenStack security groups

In case you want to apply OpenStack security groups onto your nodes, it is mandatory to add the above ports in a ruleset concerning the `0.0.0.0/0` CIDR.

> [!warning]
> If you remove the default rules accepting all input and output when creating a new security group, make sure to allow the ports needed by your application, as well as the mandatory ports mentioned above.
>

> [!primary]
> In order to simplify your policy, you can add these rules which do not specify any port and will allow all internal traffic between pods and services within the cluster:
>> | Direction | Ether Type | IP Protocol | Port Range | Remote IP Prefix | Description |
>> |---|---|---|---|---|---|
>> | Ingress | IPv4 | TCP | Any | 10.2.0.0/16 | Allow traffic from pods|
>> | Ingress | IPv4 | TCP | Any | 10.3.0.0/16 | Allow traffic from services|
>
> It allows you to trust the internal traffic between pods and services within the cluster.

For more details, please refer to the [Creating and configuring a security group in Horizon documentation](/pages/public_cloud/compute/setup_security_group).

## Private Networks

### Free Plan

The `vRack` feature is currently available and fully compatible with OVHcloud Managed Kubernetes Free Plan.

To prevent network conflicts, it is recommended to **keep the DHCP service running** in your private network.

> [!warning]
>
> At the moment, MKS worker nodes cannot use provided subnet DNS nameservers.
>

> [!warning]
>
> If your cluster was created using an OpenStack Private Network, do **not change** the private network name or the subnet name.
>
> The OpenStack Cloud Controller Manager (CCM) relies on these names to create private network connectivity inside the cluster and to link nodes to the private network.
>
> Changing either the network or subnet name may prevent new nodes from being deployed correctly. Nodes will have a `"uninitialized=true:NoSchedule"` taint, which prevents the kube-scheduler from deploying pods on these nodes.
>
> Nodes affected in this way will also lack an External-IP.
>

### Standard Plan

Standard Plan clusters use **zone-specific networking** and include reserved IP ranges that **must not be used elsewhere** in your private network:

- **Reserved subnets for cluster resources:**

```text
10.240.0.0/13 # Subnet used by pods
10.3.0.0/16   # Subnet used by services
```

> [!warning]
>
> These ranges are fixed for now but will be configurable in a future release. Do not use them elsewhere in your private network.
>

> [!primary]
>
> For Standard Plan clusters, careful planning of IP allocation is required when scaling or adding nodes. Volumes and pods are tied to their respective zones, so overlapping subnets can cause failures in multi-AZ deployments.
>

### Known not compliant IP ranges

The following subnets are not compliant with the `vRack` feature and can generate some incoherent behaviours with our used overlay networks:

```text
10.2.0.0/16 # Subnet used by pods
10.3.0.0/16 # Subnet used by services
172.17.0.0/16 # Subnet used by the Docker daemon
```

> [!primary]
>
> These subnets must be avoided in your private network to prevent networking issues.
>

## Cluster health

The command `kubectl get componentstatus` is reporting the scheduler, the controller manager and the etcd service as unhealthy. This is a limitation due to our implementation of the Kubernetes control plane as the endpoints needed to report the health of these components are not accesible.

## Persistent Volumes

Kubernetes `Persistent Volume Claims` resizing only allows to __expand__ volumes, not to __decrease__ them.  
If you try to decrease the storage size, you will get a message like:

```bash
The PersistentVolumeClaim "mysql-pv-claim" is invalid: spec.resources.requests.storage: Forbidden: field can not be less than previous value
```

For more details, please refer to the [Resizing Persistent Volumes documentation](/pages/public_cloud/containers_orchestration/managed_kubernetes/resizing-persistent-volumes).

The Persistent Volumes are using our Cinder-based block-storage solution through Cinder CSI.  
A worker node can have a maximum of 254 persistent volumes attached to it, and a persistent volume can only be attached to a single worker node.  
You can manually [configure multi-attach persistent volumes with NAS-HA](/pages/public_cloud/containers_orchestration/managed_kubernetes/configuring-multi-attach-persistent-volumes-with-ovh-nas-ha).

## Go further

- If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

- Join our [community of users](/links/community).
