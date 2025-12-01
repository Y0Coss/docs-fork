---
title: Extension d'un réseau privé OVHcloud à travers les régions Public Cloud
excerpt: Découvrez comment configurer un réseau privé multi-régions OVHcloud, gérer les VLAN et les pools d'IP pour éviter les conflits, et l'intégrer avec d'autres produits OVHcloud.
updated: 2025-12-02
---

## Objectif

L'objectif de ce guide est d'aider les utilisateurs OVHcloud à configurer et à étendre un réseau privé à travers plusieurs régions Public Cloud, tout en évitant les conflits d'IP et en assurant la stabilité du réseau. Il couvre les bonnes pratiques pour :

- Attribuer des pools d'IP distincts par région.
- Gérer les VLAN à travers les régions ou d'autres produits OVHcloud.
- Utiliser le DHCP en tant que service pour d'autres infrastructures, comme les serveurs Bare Metal.
- Fournir des instructions détaillées en utilisant l'espace client OVHcloud, Horizon, l'OpenStack CLI et Terraform.

**En suivant ce guide, les utilisateurs seront capables de déployer un réseau privé multi-régions sécurisé et fiable avec OVHcloud.**

## Contexte et aperçu de la solution

### Défis

Lorsqu'un réseau privé est étendu à travers plusieurs régions Public Cloud OVHcloud ou connecté à d'autres produits OVHcloud via un vRack, un défi majeur surgit en raison de la manière dont l'adressage IP est géré.

Les instances Public Cloud reçoivent automatiquement leurs adresses IP privées via le DHCP OpenStack ou cloud-init, et ce mécanisme ne peut pas être désactivé. En même temps, tous les réseaux privés utilisant le même VLAN à l'intérieur d'un vRack doivent partager un espace d'adressage commun. Cela signifie qu'en l'absence d'une planification appropriée, le même VLAN peut finir par attribuer des adresses IP chevauchantes ou identiques à travers les régions ou entre différents services OVHcloud.

Pour illustrer ce problème, le diagramme suivant montre un exemple de ce qu'il faut éviter :

![image problématique](images/problematic_image.png){.thumbnail}

Dans cet exemple, deux instances Public Cloud situées dans des régions différentes et un serveur Bare Metal partagent le même ID VLAN et ont été attribués la même adresse IP.

Lorsque plusieurs machines partagent la même IP sur le même VLAN, le réseau devient instable. Les paquets ne peuvent pas déterminer de manière fiable vers quelle machine ils devraient aller. Par exemple, tout trafic envoyé à 10.1.0.2 peut atterrir sur un hôte imprévisible, entraînant une connectivité irrégulière, des erreurs de routage et une interruption de service.

Ce problème devient plus grave lorsque les environnements s'étendent à travers plusieurs régions ou produits. Par conséquent, une approche structurée de l'allocation d'IP, telle que la division du sous-réseau en pools dédiés par région, est essentielle pour maintenir un réseau vRack stable, prévisible et sans conflit.

### Aperçu de la solution

Pour éviter les conflits d'IP et assurer une communication stable à travers un réseau vRack étiré, chaque région Public Cloud doit utiliser un pool d'IP dédié au sein du même sous-réseau privé. En segmentant le sous-réseau en plages d'allocation non chevauchantes, OVHcloud garantit que les services DHCP OpenStack dans différentes régions n'attribuent jamais des adresses IP en double, même lorsque tous les réseaux partagent le même ID VLAN.

Le diagramme ci-dessous illustre la configuration corrigée :

![image solution](images/solution_image.png){.thumbnail}

Chaque région utilise le même ID VLAN mais tire les IPs d'une plage d'allocation distincte au sein du sous-réseau partagé, éliminant ainsi tout risque de chevauchement.

Avec cette approche :

- Toutes les régions restent parties intégrantes du même réseau privé L2 via le vRack.
- Le DHCP continue à fonctionner normalement dans chaque région, car OpenStack attribue des IPs uniquement depuis sa plage désignée.
- D'autres produits OVHcloud (tels que Bare Metal, Serveurs dédiés ou Private Cloud) peuvent rejoindre le même VLAN sans créer de conflits d'adresses.
- Les charges de travail multi-régions, les migrations et les déploiements hybrides fonctionnent de manière fiable sur un réseau privé unifié.

Cette solution préserve la flexibilité d'un seul VLAN étiré tout en imposant une gestion d'IP prévisible et sans conflit. La section suivante explique comment configurer ce déploiement en utilisant l'espace client OVHcloud, Horizon, l'OpenStack CLI ou Terraform.

## Exemples d'utilisation

Voici quelques scénarios pratiques où l'étendre un réseau privé OVHcloud à travers des régions ou l'intégrer à d'autres produits OVHcloud peut résoudre des défis réels.

- **Base de données sur Bare Metal & Application sur Public Cloud :** Connecter un serveur de base de données Bare Metal avec des applications exécutées dans des régions Public Cloud en utilisant le même VLAN sans conflits d'IP.
- **DHCP en tant que service pour les serveurs Bare Metal :** Attribuer des IPs depuis les réseaux Public Cloud aux serveurs Bare Metal via le DHCP pour une intégration transparente.
- **Migration entre les régions Public Cloud :** Déplacer des charges de travail d'une région à une autre tout en maintenant le réseau privé cohérent et en évitant les conflits d'IP.
- **Services multi-régions :** Exécuter des services distribués à travers plusieurs régions Public Cloud avec un réseau privé unifié pour une communication sécurisée.
- **Intégration avec d'autres produits OVHcloud :** Connecter des instances Public Cloud avec Private Cloud, Serveurs dédiés ou d'autres services OVHcloud via vRack.

## Prérequis

- Un [projet Public Cloud](/pages/public_cloud/public_cloud_cross_functional/create_a_public_cloud_project) dans votre compte OVHcloud
- Connaissances de base en réseau
- Accès à l'[espace client OVHcloud](/links/manager)
- Accès à l'[interface Horizon](/pages/public_cloud/public_cloud_cross_functional/introducing_horizon)

## Instructions

Cette section fournit des instructions pas à pas pour configurer un réseau privé étiré à travers plusieurs régions Public Cloud OVHcloud. Vous pouvez utiliser l'espace client OVHcloud & Horizon, l'OpenStack CLI ou Terraform.

### Configuration pour Public Cloud

Ajouter le projet Public Cloud à un vRack :

![Ajouter un projet Public Cloud à Vrack](images/add_pcp_to_vrack.png){.thumbnail}

> [!tabs]
> Via l'espace client OVHcloud et Horizon
>> **1. Créer des réseaux privés dans chaque région**
>>
>> Créer un réseau privé dans chaque région souhaitée en utilisant le même ID VLAN.
>>
>> ![Ajouter un projet Public Cloud à Vrack](images/add_pcp_to_vrack.png){.thumbnail}
>>
>> > [!tabs]
>> >
>> > **Note :** À ce stade, l'utilisation du même ID VLAN à travers les régions sans pools d'IP distincts est exactement ce qu'il faut éviter.
>> >
>>
>> **2. Configurer les sous-réseaux et les pools d'IP**
>>
>> Modifier chaque sous-réseau dans Horizon, configurer l'IP de passerelle réservée et le pool d'IP.
>>
>> **- Première région :**
>>
>> ![Modifier le sous-réseau région 1](images/configure_subnet_region1.png){.thumbnail}
>>
>> ![Modifier le sous-réseau région 1 - 2](images/configure_subnet_region1_2.png){.thumbnail}
>>
>> **- Deuxième région :**
>>
>> ![Modifier le sous-réseau région 2](images/configure_subnet_region2.png){.thumbnail}
>>
>> ![Modifier le sous-réseau région 2 - 2](images/configure_subnet_region2_2.png){.thumbnail}
>>
>> **3. Actualiser l'état du réseau**
>>
>> Retourner à l'espace client OVHcloud et actualiser la page du réseau.
>>
>> ![Actualiser la page de liste du vrack](images/refresh_vrack_list_page.png){.thumbnail}
>>
>> Vous devriez maintenant voir un seul VLAN étiré à travers plusieurs régions, chacune avec son propre pool d'IP.
>>
> Via l'Openstack CLI
>> > [!primary]
>> >
>> > **Requis :** Authentification OpenStack configurée dans les variables d'environnement
>> >
>>
>> **1. Charger les informations d'identification OpenStack :**
>>
>> ```bash
>> source openrc.sh
>> ```
>>
>> **2. Sélectionner la première région**
>>
>> ```bash
>> export OS_REGION_NAME=RBX-A
>> openstack network create --provider-network-type vrack --provider-segment 1 stretch-private-network-vlan-1
>> openstack subnet create --network stretch-private-network-vlan-1 --subnet-range 10.1.0.0/16 --dhcp \
>> --allocation-pool start=10.1.1.2,end=10.1.1.254 --dns-nameserver 213.186.33.99 --gateway 10.1.1.1 stretch-private-subnet
>> ```
>>
>> **3. Sélectionner la deuxième région**
>>
>> ```bash
>> export OS_REGION_NAME=GRA11
>> openstack network create --provider-network-type vrack --provider-segment 1 stretch-private-network-vlan-1
>> openstack subnet create --network stretch-private-network-vlan-1 --subnet-range 10.1.0.0/16 --dhcp \
>> --allocation-pool start=10.1.2.2,end=10.1.2.254 --dns-nameserver 213.186.33.99 --gateway 10.1.2.1 stretch-private-subnet
>> ```
>>
> Via Terraform
>> > [!primary]
>> >
>> > **Requis :** Clé d'application OVHcloud configurée dans les variables d'environnement
>> >
>>
>> 1. Créer un fichier de configuration principal Terraform (par exemple, `main.tf`) avec le contenu suivant :
>>
>> ```hcl
>> resource "ovh_cloud_project_network_private" "private-net" {
>>  name    = "stretch-private-network-vlan-${var.private_network_vlan_id}"
>>  vlan_id = var.private_network_vlan_id
>>  regions = var.regions
>> }
>>
>> resource "ovh_cloud_project_network_private_subnet_v2" "private-subnet" {
>>   count             = length(var.regions)
>>   name              = "stretch-private-subnet-vlan-${var.private_network_vlan_id}"
>>   network_id        = tolist(ovh_cloud_project_network_private.private-net.regions_attributes[*].openstackid)[count.index]
>>   region            = element(var.regions, count.index)
>>   gateway_ip        = "10.${var.private_network_vlan_id}.${count.index + 1}.1"
>>   cidr              = "10.${var.private_network_vlan_id}.0.0/16"
>>   dns_nameservers   = ["213.186.33.99"]
>>   dhcp              = true
>>   enable_gateway_ip = true
>>
>>   allocation_pools {
>>     start = "10.${var.private_network_vlan_id}.${count.index + 1}.2"
>>     end   = "10.${var.private_network_vlan_id}.${count.index + 1}.254"
>>   }
>> }
>> ```
>>
>> 2. Créer un fichier de variables (par exemple, `variables.tf`) avec le contenu suivant :
>>
>> ```hcl
>> variable regions {
>>   type    = list
>>   default = ["RBX-A", "GRA11"]
>> }
>>
>> variable private_network_vlan_id {
>>   type    = string
>>   default = "1"
>> }
>> ```
>>
>> 3. Appliquer la configuration
>>
>> ```bash
>> terraform apply
>> ```
>>
>> Terraform créera le réseau privé, les sous-réseaux et les pools d'IP d'allocation dans chaque région comme défini.
>> 

### DHCP pour les serveurs Bare Metal (DHCP en tant que service)

Cette section explique comment fournir des adresses IP DHCP Public Cloud aux serveurs Bare Metal en les intégrant à un réseau privé étiré.

Le projet Public Cloud et le serveur Bare Metal doivent être ajoutés au même vRack :

![Ajouter un serveur Bare Metal à Vrack](images/add_baremetal_to_vrack.png){.thumbnail}

> [!tabs]
> Via l'espace client OVHcloud et Horizon
>> **1. Créer un réseau privé Public Cloud**
>>
>> ![Créer un réseau privé Public Cloud](images/create_private_network.png){.thumbnail}
>>
>> > [!primary]
>> >
>> > **Note :** Utiliser le même ID VLAN qui sera utilisé pour le serveur Bare Metal.
>> >
>>
>> **2. Obtenir l'adresse MAC de l'interface privée du serveur Bare Metal.**
>>
>> ![Obtenir l'adresse MAC](images/obtain_mac_address.png){.thumbnail}
>>
>> **3. Créer un port virtuel sur le réseau privé Public Cloud en utilisant l'adresse MAC du serveur Bare Metal.**
>>
>> ![Créer un port virtuel](images/create_virtual_port.png){.thumbnail}
>>
>> **4. Installer un système d'exploitation sur le serveur Bare Metal (par exemple, Ubuntu 24.04).**
>>
>> ```bash
>> cat <<EOF | sudo tee /etc/netplan/90-private-interface.yaml
>> network:
>>   version: 2
>>   ethernets:
>>     privint:
>>       match:
>>         macaddress: "74:56:3c:85:7e:40"
>>       dhcp4: false
>>       dhcp6: false
>>   vlans:
>>     vlan1:
>>       id: 1
>>       link: privint
>>       dhcp4: true
>> EOF
>>
>> sudo chmod 600 /etc/netplan/90-private-interface.yaml
>> sudo netplan apply
>> ```
>>
>> > [!warning]
>> >
>> > **Note :** Les scripts post-installation peuvent avoir besoin d'être mis à jour avec l'adresse MAC correcte et l'ID VLAN.
>> >
>>
> Via l'Opentsack CLI
>> > [!primary]
>> >
>> > **Requis :** Authentification OpenStack configurée dans les variables d'environnement
>> >
>>
>> **1. Charger les informations d'identification OpenStack.**
>>
>> ```bash
>> source openrc.sh
>> ```
>>
>> **2. Sélectionner la région :**
>>
>> ```bash
>> export OS_REGION_NAME=RBX-A
>> ```
>>
>> 3. Créer le réseau privé et le sous-réseau :
>>
>> ```bash
>> openstack network create --provider-network-type vrack --provider-segment 1 stretch-private-network-vlan-1
>>
>> openstack subnet create --network stretch-private-network-vlan-1 --subnet-range 10.1.0.0/16 --dhcp \
>> --allocation-pool start=10.1.0.2,end=10.1.254.254 --dns-nameserver 213.186.33.99 --gateway 10.1.0.1 stretch-private-subnet
>> ```
>>
>> **4. Créer un port virtuel pour le serveur Bare Metal.**
>>
>> ```bash
>> openstack port create --network stretch-private-network-vlan-1 <BARE_METAL_MAC_ADDRESS> bare_metal_port
>> ```
>>
>> 5. Installer le système d'exploitation sur le serveur Bare Metal (Ubuntu 24.04 utilisé dans cet exemple).
>>
>> ```bash
>> cat <<EOF | sudo tee /etc/netplan/90-private-interface.yaml
>> network:
>>   version: 2
>>   ethernets:
>>     privint:
>>       match:
>>         macaddress: "74:56:3c:85:7e:40"
>>       dhcp4: false
>>       dhcp6: false
>>   vlans:
>>     vlan1:
>>       id: 1
>>       link: privint
>>       dhcp4: true
>> EOF
>>
>> sudo chmod 600 /etc/netplan/90-private-interface.yaml
>> sudo netplan apply
>> ```
>>
>> > [!warning]
>> >
>> > **Note :** Les scripts post-installation peuvent avoir besoin d'être mis à jour avec l'adresse MAC correcte et l'ID VLAN.
>> >
>>
> Via Terraform
>> > [!primary]
>> >
>> > **Requis :** Clé d'application OVHcloud configurée dans les variables d'environnement
>> >
>>
>> **1. Créer le fichier de variables Terraform `variables.tf`**
>>
>> Définir toutes les variables nécessaires pour le déploiement :
>>
>> ```hcl
>> variable "region" {
>>   type    = string
>>   default = "RBX-A"
>> }
>>
>> variable "private_network_vlan_id" {
>>   type    = string
>>   default = "1"
>> }
>>
>> variable "bare_metal_server_name" {
>>   type    = string
>>   default = "