---
title: File Storage Service - Getting started (Alpha)
excerpt: "Learn how to set up and manage OVHcloud’s File Storage Service with your OpenStack project. This guide covers CLI setup, share creation, client access, and mounting on your VMs."
updated: 2025-10-14
---

## Objective

OVHcloud provides a File Storage Service powered by OpenStack Manila. This service offers managed NFS shares on private networks, supporting ReadWriteMany (RWX) access across multiple instances or Kubernetes pods.

It can be accessed via OpenStack CLI, API, Manila CSI, and Terraform.

> [!warning]
>
> This service is currently in Alpha, available only in the **SBG5** region, and limited to registered Alpha customers. Features and availability may change.
>

## Requirements

- Your project is authorized for Manila Alpha (register [here](https://labs.ovhcloud.com/en/file-storage/))
- You already have a [private network](/pages/public_cloud/public_cloud_network_services/getting-started-07-creating-vrack) available in your project.
- A [Public Cloud instance](/links/public-cloud/public-cloud) in your OVHcloud account
- An [OpenStack CLI ready environment](/pages/public_cloud/public_cloud_cross_functional/prepare_the_environment_for_using_the_openstack_api)

## Instructions

> [!primary]
>
> Currently, the File Storage Service can only be accessed and managed via OpenStack CLI with the Manila plugin. Other interfaces will be supported in the future.
>

> [!tabs]
> Via the OpenStack CLI with the Manila plugin
>> **1\. Install the Manila CLI Plugin**
>>
>> If the Manila commands are not yet available, install the plugin:
>>
>> ```bash
>> sudo apt update && sudo apt install -y python3-manilaclient
>> ```
>>
>> Verify the installation:
>>
>> ```bash
>> openstack share --help
>> ```
>>
>> You should see commands such as:
>>
>> - share create
>> - share list
>> - share network create
>> - share access create
>>
>> **2\. Check Available Share Types**
>>
>> List the share types available in your region:
>>
>> ```bash
>> openstack share type list --os-region-name <REGION_NAME>
>> ```
>>
>> Expected output:
>>
>> ```bash
>> +----------+-----------+------------+------------+
>> | ID       | Name      | Visibility | Is Default |
>> +----------+-----------+------------+------------+
>> | acceb7b4 | generic_0 | public     | True       |
>> +----------+-----------+------------+------------+
>> ```
>>
>> > [!primary]
>> >
>> > Note: For the generic_0 type, you must always select a share network, otherwise the share cannot be created.
>> >
>>
>> **3\. Create a Share Network**
>>
>> Identify your private network and subnet:
>>
>> ```bash
>> openstack network list --os-region-name <REGION_NAME>
>> openstack subnet list --os-region-name <REGION_NAME>
>> ```
>>
>> Retrieve their IDs:
>>
>> ```bash
>> openstack network show --os-region-name <REGION_NAME> -c id -f value <PRIVATE_NETWORK_NAME>
>> openstack subnet show --os-region-name <REGION_NAME> -c id -f value <PRIVATE_SUBNET_NAME>
>> ```
>>
>> > [!primary]
>> >
>> > Both network and subnet IDs should look like: **abc12345-def6-4abc-8def-123456abcdef**
>> >
>>
>> Create a share network linked to your private network:
>>
>> ```bash
>> openstack share network create \
>>   --os-region-name <REGION_NAME> \
>>   --name <my-share-network-name> \
>>   --neutron-net-id <NETWORK_ID> \
>>   --neutron-subnet-id <SUBNET_ID>
>> ```
>>
>> > [!primary]
>> >
>> > Note: Replace `<my-share-network-name>` with your chosen name for the share network.
>> >
>>
>> Verify the share network:
>>
>> ```bash
>> openstack share network list --os-region-name <REGION_NAME>
>> ```
>>
>> **4\. Create an NFS Share**
>>
>> Create a 150 GB NFS share:
>>
>> ```bash
>> openstack share create \
>>   --os-region-name <REGION_NAME> \
>>   --share-type generic_0 \
>>   --share-network <my-share-network-name> \
>>   --name <my-first-share-name> \
>>   NFS 150
>> ```
>>
>> > [!primary]
>> >
>> > Note: Replace <my-first-share-name> with the name you want to assign to your share.
>> >
>>
>> Monitor the share status until it becomes `available`:
>>
>> ```bash
>> openstack share list --os-region-name <REGION_NAME>
>> ```
>>
>> **5\. Authorize a Client VM**
>>
>> Ensure your client VM is in the same private network as the share.
>>
>> Retrieve the VM’s private IP address:
>>
>> ```bash
>> openstack server show --os-region-name <REGION_NAME> <VM_NAME> -c addresses -f value
>> ```
>>
>> Example output:
>>
>> ```bash
>> {'my-private-net': ['10.1.0.123', '57.123.88.111']}
>> ```
>>
>> Grant access to the share using the VM’s private IP (e.g., 10.1.0.123):
>>
>> ```bash
>> openstack share access create \
>>   --os-region-name <REGION_NAME> \
>>   <my-first-share-name> \
>>   ip 10.1.0.123
>> ```
>>
>> Verify access:
>>
>> ```bash
>> openstack share access list --os-region-name <REGION_NAME> <my-first-share-name>
>> ```
>>
>> **6\. Retrieve the Export Path**
>>
>> Get the NFS export location:
>>
>> ```bash
>> openstack share export location list --os-region-name <REGION_NAME> <my-first-share-name>
>> ```
>>
>> Example output:
>>
>> ```bash
>> 10.1.0.12:/shares/share-abc12345-def6-4abc-8def-123456abcdef
>> ```
>>
>> > [!primary]
>> >
>> > Note: This export path is used to mount the share on your client VM.
>> >
>>
>> **7\. Mount the Share on Your Client VM**
>>
>> Connect to your VM and install NFS utilities:
>>
>> ```bash
>> sudo apt update && sudo apt install -y nfs-common
>> ```
>>
>> Create a mount point and mount the share:
>>
>> ```bash
>> sudo mkdir -p /mnt/share
>> sudo mount -t nfs4 10.1.0.12:/shares/share-abc12345-def6-4abc-8def-123456abcdef /mnt/share
>> ```
>>
>> Verify the mount:
>>
>> ```bash
>> df -h /mnt/share
>> ```
>>
>> > [!primary]
>> >
>> > Note: Replace the export path with the one retrieved for your share.
>> >
>>
>> **8\. Check capacity and usage**
>>
>> Display available space on the mounted share:
>>
>> ```bash
>> df -h /mnt/share
>> ```
>>
>> Example output:
>>
>> ```bash
>> Example:
>> Filesystem                          Size  Used  Avail Use% Mounted on
>> 10.1.0.12:/shares/share-abc1...     150G  100M   150G   1% /mnt/share
>> ```
>>
>> > [!primary]
>> >
>> > Note: This lets you monitor the storage capacity and usage of your NFS share.
>> >
>>
>> **9\. Manage the share lifecycle**
>>
>> Resize the share:
>>
>> > [!warning]
>> >
>> > Only extending a share is allowed for now; shrinking is not supported.
>> >
>>
>> ```bash
>> openstack share resize --os-region-name <REGION_NAME> <my-first-share-name> 200
>> ```
>>
>> Delete a share:
>>
>> ```bash
>> openstack share delete --os-region-name <REGION_NAME> <my-first-share-name>
>> ```
>>
>> Delete the share network:
>>
>> ```bash
>> openstack share network delete --os-region-name <REGION_NAME> <my-share-network-name>
>> ```
>>
>> > [!primary]
>> >
>> > Note: Ensure no active shares are using the network before deleting it.
>> >
>>
>> **10\. Troubleshooting**
>>
>> | Symptom	                  | Cause	                           | Solution                                                           |
>> | --------------------------- | ---------------------------------- | ------------------------------------------------------------------ |
>> | `Unknown command ['share']` | Manila CLI not installed           | Install it with `sudo apt install python3-manilaclient`            |
>> | `Share network must be set` | Using a DHSS=True share type       | Provide `--share-network`                                          |
>> | Cannot mount NFS            | IP not authorized or wrong network | Ensure VM is in the same private subnet and access rule is created |
>> | `403 Forbidden`             | Project not whitelisted for Manila | Ensure you are registered to Alpha                                 |
>> | Share stuck in creating     | Invalid network ID or subnet       | Check `NETWORK_ID` and `SUBNET_ID`                                 |
>>
> Via Manila CSI in K8s environment
>> **1\. Additional Requirements**
>>
>> - Helm CLI installed on your local machine.
>> - OpenStack CLI configured and ready to use.
>> - Krew (kubectl plugin manager) installed.
>> - Stern (kubectl log tailing plugin) installed via Krew.
>> - A Kubernetes cluster deployed in a private network within a PCI region where Manila endpoints are accessible.
>>
>> **2\. Installing Helm command line**
>>
>> ```bash
>> curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
>> chmod 700 get_helm.sh
>> ./get_helm.sh
>> ```
>>
>> **3\. Installing Krew and Stern tools**
>>
>> Run the following command to install Krew in your environment:
>>
>> ```bash
>> (
>>   set -x; cd "$(mktemp -d)" &&
>>   OS="$(uname | tr '[:upper:]' '[:lower:]')" &&
>>   ARCH="$(uname -m | sed -e 's/x86_64/amd64/' -e 's/\(arm\)\(64\)\?.*/\1\2/' -e 's/aarch64$/arm64/')" &&
>>   KREW="krew-${OS}_${ARCH}" &&
>>   curl -fsSLO "https://github.com/kubernetes-sigs/krew/releases/latest/download/${KREW}.tar.gz" &&
>>   tar zxvf "${KREW}.tar.gz" &&
>>   ./"${KREW}" install krew
>> )
>> export PATH="${KREW_ROOT:-$HOME/.krew}/bin:$PATH"
>> ```
>>
>> Once Krew is installed, install Stern with:
>>
>> ```bash
>> kubectl krew install stern
>> ```
>>
>> **4\. Installing Openstack CLI**
>>
>> Prepare your environment to use the OpenStack API by installing python-openstackclient, following [this guide](/pages/public_cloud/public_cloud_cross_functional/prepare_the_environment_for_using_the_openstack_api).
>>
>> Install the Manila client to manage File Storage shares:
>>
>> ```bash
>> pip install python-manilaclient
>> ```
>>
>> Don’t forget to update your shell completion script to enable OpenStack `share` autocompletion.
>>
>> **5\. Install the CSI NFS driver**
>>
>> Add the Helm chart repository:
>>
>> ```bash
>> helm repo add csi-driver-nfs https://raw.githubusercontent.com/kubernetes-csi/csi-driver-nfs/master/charts
>> helm repo update
>> ```
>>
>> List available releases of the NFS CSI chart:
>>
>> ```bash
>> helm search repo -l csi-driver-nfs
>> ```
>>
>> Install the chosen Helm chart release:
>>
>> > [!primary]
>> >
>> > Replace the optional flags `--wait -v=5 --debug` as needed for debugging or synchronous installation.
>> >
>>
>> ```bash
>> helm install csi-driver-nfs csi-driver-nfs/csi-driver-nfs \
>>   --namespace kube-system \
>>   --version v4.11.0 \
>>   [--wait -v=5 --debug]
>> ```
>>
>> Follow the NFS CSI logs:
>>
>> ```bash
>> kubectl stern -n kube-system -l app.kubernetes.io/instance=csi-driver-nfs
>> ```
>>
>> **6\. Install the Manila CSI driver**
>>
>> Add the Helm chart repository:
>>
>> ```bash
>> helm repo add cpo https://kubernetes.github.io/cloud-provider-openstack
>> helm repo update
>> ```
>>
>> List available releases of the Manila CSI:
>>
>> ```bash
>> helm search repo -l openstack-manila-csi
>> ```
>>
>> Install the chosen Helm chart release:
>>
>> ```bash
>> helm install manila-csi cpo/openstack-manila-csi --version 2.33.1 --namespace kube-system [--values ./csi-config/helm-chart-values.yaml]
>> ```
>>
>> Follow the Manila CSI logs:
>>
>> ```bash
>> kubectl stern -n kube-system -l app=openstack-manila-csi
>> ```
>>
>> **7\. Preparing OpenStack Resources for Manila CSI**
>>
>> 1. Create a dedicated OpenStack user for Manila
>>
>> You need a separate OpenStack user to manage Manila resources. This user can be created:
>>
>> - Through the OVHcloud Control Panel (Public Cloud > Settings > Users & Roles)
>> - Or via the OVHcloud CLI
>>
>> > [!primary]
>> >
>> > This new user must have the role share_operator or administrator.
>> >
>>
>> 2. Collect OpenStack project and user details
>>
>> Download your project’s openrc file from the OVHcloud control panel and note the following credentials:
>>
>> - os-userName
>> - os-password
>> - os-domainName
>> - os-projectDomainID
>> - os-projectName
>> - os-projectDomainID
>>
>> > [!primary]
>> >
>> > Once you have these values, populate the csi-config/secrets.yaml file. This Kubernetes secret will allow the Manila CSI driver to manage Manila resources in your cluster.
>> >
>>
>> ```bash
>> curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
>> chmod 700 get_helm.sh
>> ./get_helm.sh
>> ```
>>
>> Create the secret in your MKS cluster:
>>
>> ```bash
>> # Apply OpenStack credentials for Manila
>> kubectl apply -f ./csi-config/secrets.yaml
>> ```
>>
>> 3. Configure the OpenStack shared network
>>
>> Manila requires a share network because the driver is configured with `DHSS=true` (`driver_handles_share_servers`).
>>
>> This resource is managed by the owner of the OpenStack project.
>>
>> ```bash
>> # List private networks attached to your MKS cluster
>> openstack --os-region-name SBG5 network list
>>
>> # Retrieve the network ID
>> openstack --os-region-name SBG5 network show -c id -f value <PRIVATE_NETWORK_NAME>
>>
>> # Retrieve the subnet ID linked to this network
>> openstack --os-region-name SBG5 subnet show -c id -f value <PRIVATE_SUBNET_NAME>
>>
>> # Create the Manila share network
>> openstack --os-region-name SBG5 share network create \
>>   --name mks-manila-csi-tests \
>>   --neutron-net-id <PRIVATE_NETWORK_ID> \
>>   --neutron-subnet-id <PRIVATE_SUBNET_ID>
>> ```
>>
>> Example output:
>>
>> ```bash
>> +-----------------------------------+----------------------------------------------------------+
>> | Field                             | Value                                                    |
>> +-----------------------------------+----------------------------------------------------------+
>> | created_at                        | 2025-10-04T14:12:25.111776                               |
>> | description                       | None                                                     |
>> | id                                | 07363bc7-be2a-4a7d-b675-09844b344b3b                     |
>> | name                              | mks-manila-csi-tests                                     |
>> | network_allocation_update_support | True                                                     |
>> | project_id                        | <PROJECT_ID>                                             |
>> | security_service_update_support   | True                                                     |
>> | share_network_subnets             |                                                          |
>> |                                   | id = 90cf66fc-23eb-4dce-80a3-bf8fa3a912c3                |
>> |                                   | availability_zone = None                                 |
>> |                                   | created_at = 2025-10-04T14:12:25.126327                  |
>> |                                   | updated_at = None                                        |
>> |                                   | segmentation_id = None                                   |
>> |                                   | neutron_net_id = <PRIVATE_NETWORK_NAME>                  |
>> |                                   | neutron_subnet_id = <PRIVATE_SUBNET_NAME>                |
>> |                                   | ip_version = None                                        |
>> |                                   | cidr = None                                              |
>> |                                   | network_type = None                                      |
>> |                                   | mtu = None                                               |
>> |                                   | gateway = None                                           |
>> | status                            | active                                                   |
>> | updated_at                        | None                                                     |
>> +-----------------------------------+----------------------------------------------------------+
>> ```
>>
>> **8\. Configure the Manila CSI driver**
>>
>> Once the OpenStack share network is created, and before configuring the Manila CSI driver, you need to define the CIDR range used by your MKS nodes. This ensures that the nodes can access the Manila shares.
>>
>> Edit the runtime ConfigMap:
>>
>> Open `csi-config/manila-runtime-configmap.yaml` and update the `nfs.matchExportLocationAddress` field to match your cluster’s CIDR.
>>
>> Example:
>>
>> ```bash
>> nfs:
>>   matchExportLocationAddress: 10.42.0.0/16
>> ```
>>
>> Apply the ConfigMap to your Kubernetes cluster:
>>
>> ```bash
>> # Optional if runtime config is already defined in Helm values
>> kubectl apply -f ./csi-config/manila-runtime-configmap.yaml
>> ```
>>
>> **9\. Creating NFS Shares via Dynamic Provisioning**
>>
>> To enable the Manila CSI driver to dynamically create Manila shares and use them as Kubernetes volumes, you must define a StorageClass in your cluster. This StorageClass specifies the shared network that will be used to create and grant access to NFS exports.
>>
>> Retrieve the shared network ID, using the OpenStack CLI to get the ID of your shared network:
>>
>> ```bash
>> openstack --os-region-name SBG5 share network list -f value -c ID
>> ```
>>
>> Configure the StorageClass:
>>
>> - Edit the csi-config/dynamic-storageclass.yaml file.
>> - Update the parameter.shareNetworkID value with the shared network ID retrieved in the previous step.
>>
>> Create the dynamic StorageClass, applying the StorageClass to your cluster:
>>
>> ```bash
>> # A StorageClass cannot be updated. If modifications are needed, delete and recreate it.
>> kubectl apply -f poc/v2/nfs/dynamic-provisioning/dynamic-storageclass.yaml
>> ```
>>
>> Once the StorageClass is created, create a `PersistentVolumeClaim` (PVC) using it. For example, claim a 15Gi volume with `ReadWriteMany` (RWX) access:
>>
>> ```bash
>> kubectl apply -f poc/v2/nfs/dynamic-provisioning/nfs-pvc.yaml
>> ```
>>
>> After applying the PVC, list the newly created Manila shares in your Public Cloud project:
>>
>> ```bash
>> openstack --os-region SBG5 share list
>> ```
>>
>> Example output:
>>
>> ```bash
>> +--------------------------------------+------------------------------------------+------+-------------+-----------+-----------+-----------------+------+-------------------+
>> | ID                                   | Name                                     | Size | Share Proto | Status    | Is Public | Share Type Name | Host | Availability Zone |
>> +--------------------------------------+------------------------------------------+------+-------------+-----------+-----------+-----------------+------+-------------------+
>> | 9484d5f3-7bf7-486b-b88e-40bbedeet9f3 | pvc-78135a68-c6f4-48fe-8644-454b387a3ad4 |   15 | NFS         | available | False     | generic_0       |      | nova              |
>> +--------------------------------------+------------------------------------------+------+-------------+-----------+-----------+-----------------+------+-------------------+
>> ```
>>
>> Deploy a Kubernetes Deployment for a web server with 2 replicas. The pods will mount and share the previously created `RWX` volume:
>>
>> ```bash
>> kubectl apply -f poc/v2/nfs/dynamic-provisioning/nfs-deployment.yaml
>> ```
>>
>> You can verify the RWX functionality by connecting to one pod using`kubectl exec` command and creating a file in the mounted directory (e.g., `/var/lib/www/`). Then, connect to the second pod and check that the file is visible. If it is, your Manila share exposed through NFS is functioning correctly.
>>
>> **10\. Mounting an Existing Manila Share as a Volume in Pods**
>>
>> As shown earlier, a Kubernetes StorageClass can dynamically create Manila shares exposed via NFS. Alternatively, you can use a pre-provisioned Manila share and mount it directly in a Pod.
>>
>> Create a new share with the OpenStack CLI:
>>
>> ```bash
>> openstack --os-region SBG5 share create \
>>   --share-type <SHARE_TYPE> \
>>   --share-network <SHARE_NETWORK_ID> \
>>   --name <NFS_SHARE_NAME> \
>>   SHARE_PROTOCOL SHARE_SIZE
>> ```
>>
>> Where:
>>
>> - `SHARE_TYPE` is `generic_0` by default. You can check existing share types with:
>>
>> ```bash
>> openstack --os-region SBG5 share type list
>> ```
>>
>> - `SHARE_NETWORK_ID` is the identifier of your shared network.
>> - `NFS_SHARE_NAME` is the name of your NFS share.
>> - `SHARE_PROTOCOL` is the protocol to use (currently, only NFS is supported).
>> - `SHARE_SIZE` is the size to allocate to your NFS volume (in GiB).
>>
>> Create a share access rule:
>>
>> ```bash
>> openstack --os-region SBG5 share access create <NFS_SHARE_NAME> ip <SUBNET_CIDR>
>> ```
>>
>> Where:
>>
>> - `SHARE_ACCESS_NAME` is the name of the share.
>> - `SUBNET_CIDR` is the CIDR used when configuring the Manila CSI runtime.
>>
>> Retrieve the NFS share ID and the share access ID, then update the `volumeAttributes.shareID` and `volumeAttributes.shareAccessID` parameters in the `poc/v2/nfs/static-provisioning/static-provisioning.yaml` file.
>>
>> Apply the manifest to create a PersistentVolume and its PersistentVolumeClaim using the pre-provisioned NFS share. The Manila share will be used only if the pod claiming the PVC is deployed in your cluster:
>>
>> ```bash
>> kubectl apply -f poc/v2/nfs/static-provisioning/static-provisioning.yaml
>> ```
>>
>> Deploy a pod that mounts this share:
>>
>> ```bash
>> kubectl apply -f poc/v2/nfs/static-provisioning/pod.yaml
>> ```
>>
>> You can now use `kubectl exec` to access the pod and run `df -h` to verify that the pre-created Manila share is properly mounted. 
>>
>> ### Useful CLI
>>
>> With your OpenStack credentials loaded in the environment, you can manage Manila shares using the OpenStack CLI. Common commands include:
>>
>> ```bash
>> openstack share list # List all shares
>> openstack share type list # List available share types
>> openstack share access list|create|delete [${SHARE_ID}] # Manage access rules for a specific share
>> openstack share list|create|delete [${SHARE_ID}] # Create, list, or delete a share by its ID
>> openstack share message list # to see error related to Manila resources
>> ```
>>
>> ### Useful resources
>>
>> [Your ReadWriteMany (RWX) Storage in k8s with Manila CSI](https://www.youtube.com/watch?v=WSMZDKx4JAI){.external}
>> [Manila/Concepts](https://wiki.openstack.org/wiki/Manila/Concepts#share_type){.external}
>> [Generic approach for share provisioning](https://docs.openstack.org/manila/latest/admin/generic_driver.html){.external}
>> [Official Manila CSI Plugin on GitHub](https://github.com/kubernetes/cloud-provider-openstack/tree/master/examples/manila-csi-plugin){.external}
>>
> Via Terraform (coming soon)
>>
>> > [!primary]
>> >
>> > The configuration via Terraform will soon be detailed here.
>> >
>>

## Go further

Join our [community of users](/links/community).