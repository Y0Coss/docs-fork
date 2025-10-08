---
title: "File Storage Service - Premiers pas (Alpha)"
excerpt: "Découvrez comment configurer et gérer le service File Storage d’OVHcloud avec votre projet OpenStack. Ce guide couvre l’installation de la CLI, la création de partages, l’accès des clients et le montage sur vos machines virtuelles."
updated: 2025-10-08
---

## Objectif

OVHcloud propose un service File Storage basé sur OpenStack Manila. Ce service fournit des partages NFS gérés sur des réseaux privés, avec un accès ReadWriteMany (RWX) possible depuis plusieurs instances ou pods Kubernetes.

Il est accessible via OpenStack CLI, API, Manila CSI et Terraform.

> [!warning]
>
> Ce service est actuellement en Alpha, disponible uniquement dans la région **SBG5** et réservé aux clients Alpha enregistrés. Les fonctionnalités et la disponibilité peuvent évoluer.
>

## Prérequis

- Votre projet est autorisé pour Manila Alpha (inscrivez-vous [ici](https://labs.ovhcloud.com/en/file-storage/))
- Vous disposez déjà d’un [réseau privé](/pages/public_cloud/public_cloud_network_services/getting-started-07-creating-vrack) dans votre projet Public Cloud
- Une [instance Public Cloud](/links/public-cloud/public-cloud) dans votre compte OVHcloud
- Un [environnement CLI OpenStack prêt à l’emploi](/pages/public_cloud/public_cloud_cross_functional/prepare_the_environment_for_using_the_openstack_api)

## En pratique

> [!primary]
>
> Actuellement, le service File Storage ne peut être consulté et géré que via la CLI OpenStack avec le plugin Manila. D’autres interfaces seront disponibles à l’avenir.
>

> [!tabs]
> Via la CLI OpenStack avec le plugin Manila
>> **1\. Installer le plugin CLI Manila**
>>
>> Si les commandes Manila ne sont pas encore disponibles, installez le plugin :
>>
>> ```bash
>> sudo apt update && sudo apt install -y python3-manilaclient
>> ```
>>
>> Vérifiez l’installation :
>>
>> ```bash
>> openstack share --help
>> ```
>>
>> Vous devriez voir des commandes telles que :
>>
>> - share create
>> - share list
>> - share network create
>> - share access create
>>
>> **2\. Vérifier les types de partages disponibles**
>>
>> Listez les types de partages disponibles dans votre région :
>>
>> ```bash
>> openstack share type list --os-region-name <REGION_NAME>
>> ```
>>
>> Sortie attendue :
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
>> > Remarque : Pour le type generic_0, vous devez obligatoirement choisir un share network, sinon le partage ne pourra pas être créé.
>> >
>>
>> **3\. Créer un Share Network**
>>
>> Identifiez votre réseau privé et votre sous-réseau :
>>
>> ```bash
>> openstack network list --os-region-name <REGION_NAME>
>> openstack subnet list --os-region-name <REGION_NAME>
>> ```
>>
>> Récupérez leurs IDs :
>>
>> ```bash
>> openstack network show --os-region-name <REGION_NAME> -c id -f value <PRIVATE_NETWORK_NAME>
>> openstack subnet show --os-region-name <REGION_NAME> -c id -f value <PRIVATE_SUBNET_NAME>
>> ```
>>
>> > [!primary]
>> >
>> > Les IDs du réseau et du sous-réseau devraient ressembler à : **abc12345-def6-4abc-8def-123456abcdef**
>> >
>>
>> Créez un share network lié à votre réseau privé :
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
>> > Remarque : Remplacez `<my-share-network-name>` par le nom que vous souhaitez donner à votre share network.
>> >
>>
>> Vérifiez le share network :
>>
>> ```bash
>> openstack share network list --os-region-name <REGION_NAME>
>> ```
>>
>> **4\. Créer un partage NFS**
>>
>> Créez un partage NFS de 150 Go :
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
>> > Remarque : Remplacez <my-first-share-name> par le nom que vous souhaitez donner à votre partage.
>> >
>>
>> Surveillez l’état du partage jusqu’à ce qu’il devienne `available` :
>>
>> ```bash
>> openstack share list --os-region-name <REGION_NAME>
>> ```
>>
>> **5\. Autoriser une VM cliente**
>>
>> Assurez-vous que votre VM cliente se trouve dans le même réseau privé que le partage.
>>
>> Récupérez l’adresse IP privée de la VM :
>>
>> ```bash
>> openstack server show --os-region-name <REGION_NAME> <VM_NAME> -c addresses -f value
>> ```
>>
>> Exemple de sortie :
>>
>> ```bash
>> {'my-private-net': ['10.1.0.123', '57.123.88.111']}
>> ```
>>
>> Autorisez l’accès au partage en utilisant l’IP privée de la VM (par exemple, 10.1.0.123) :
>>
>> ```bash
>> openstack share access create \
>>   --os-region-name <REGION_NAME> \
>>   <my-first-share-name> \
>>   ip 10.1.0.123
>> ```
>>
>> Vérifiez les accès :
>>
>> ```bash
>> openstack share access list --os-region-name <REGION_NAME> <my-first-share-name>
>> ```
>>
>> **6\. Récupérer le chemin d’export**
>>
>> Obtenez l’emplacement d’export NFS :
>>
>> ```bash
>> openstack share export location list --os-region-name <REGION_NAME> <my-first-share-name>
>> ```
>>
>> Exemple de sortie :
>>
>> ```bash
>> 10.1.0.12:/shares/share-abc12345-def6-4abc-8def-123456abcdef
>> ```
>>
>> > [!primary]
>> >
>> > Remarque : Ce chemin d’export est utilisé pour monter le partage sur votre VM cliente.
>> >
>>
>> **7\. Monter le partage sur votre VM cliente**
>>
>> Connectez-vous à votre VM et installez les utilitaires NFS :
>>
>> ```bash
>> sudo apt update && sudo apt install -y nfs-common
>> ```
>>
>> Créez un point de montage et montez le partage :
>>
>> ```bash
>> sudo mkdir -p /mnt/share
>> sudo mount -t nfs4 10.1.0.12:/shares/share-abc12345-def6-4abc-8def-123456abcdef /mnt/share
>> ```
>>
>> Vérifiez le montage :
>>
>> ```bash
>> df -h /mnt/share
>> ```
>>
>> > [!primary]
>> >
>> > Remarque : Remplacez le chemin d’export par celui récupéré pour votre partage.
>> >
>>
>> **8\. Vérifier la capacité et l’utilisation**
>>
>> Affichez l’espace disponible sur le partage monté :
>>
>> ```bash
>> df -h /mnt/share
>> ```
>>
>> Exemple de sortie :
>>
>> ```bash
>> Example:
>> Filesystem                          Size  Used  Avail Use% Mounted on
>> 10.1.0.12:/shares/share-abc1...     150G  100M   150G   1% /mnt/share
>> ```
>>
>> > [!primary]
>> >
>> > Remarque : Cela vous permet de suivre la capacité de stockage et l’utilisation de votre partage NFS.
>> >
>>
>> **9\. Gérer le cycle de vie du partage**
>>
>> Redimensionner le partage :
>>
>> > [!warning]
>> >
>> > Seule l’extension d’un partage est autorisée pour le moment ; la réduction n’est pas supportée.
>> >
>>
>> ```bash
>> openstack share resize --os-region-name <REGION_NAME> <my-first-share-name> 200
>> ```
>>
>> Supprimer un partage :
>>
>> ```bash
>> openstack share delete --os-region-name <REGION_NAME> <my-first-share-name>
>> ```
>>
>> Supprimer le share network :
>>
>> ```bash
>> openstack share network delete --os-region-name <REGION_NAME> <my-share-network-name>
>> ```
>>
>> > [!primary]
>> >
>> > Remarque : Assurez-vous qu’aucun partage actif n’utilise le réseau avant de le supprimer.
>> >
>>
>> **10\. Dépannage**
>>
>> | Symptôme	                 | Cause	                                        | Solution                                                                                   |
>> | --------------------------- | ------------------------------------------------ | ------------------------------------------------------------------------------------------ |
>> | `Unknown command ['share']` | CLI Manila non installée                         | Installez-la avec `sudo apt install python3-manilaclient`                                  |
>> | `Share network must be set` | Utilisation d’un type de partage DHSS=True       | Fournissez `--share-network`                                                               |
>> | Cannot mount NFS            | IP non autorisée ou réseau incorrect             | Assurez-vous que la VM est sur le même sous-réseau privé et que la règle d’accès est créée |
>> | `403 Forbidden`             | Projet non autorisé pour Manila                  | Assurez-vous d’être inscrit à l’Alpha                                                      |
>> | Share stuck in creating     | ID de réseau ou sous-réseau invalide             | Vérifiez `NETWORK_ID` et `SUBNET_ID`                                                       |
>>

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).
