---
title: "File Storage Service - Premiers pas (Alpha)"
excerpt: "Découvrez comment configurer et gérer le service File Storage d’OVHcloud avec votre projet OpenStack. Ce guide couvre l’installation de la CLI, la création de partages, l’accès des clients et le montage sur vos machines virtuelles."
updated: 2025-10-14
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
> Via Manila CSI dans l'environnement K8s
>> **1. Prérequis supplémentaires**
>>
>> - Helm CLI installé sur votre machine locale.
>> - OpenStack CLI configuré et prêt à l'emploi.
>> - Krew (gestionnaire de plugins kubectl) installé.
>> - Stern (plugin de suivi des logs kubectl) installé via Krew.
>> - Un cluster Kubernetes déployé dans un réseau privé au sein d'une région PCI où les points de terminaison Manila sont accessibles.
>>
>> **2. Installation de la ligne de commande Helm**
>>
>> ```bash
>> curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
>> chmod 700 get_helm.sh
>> ./get_helm.sh
>> ```
>>
>> **3. Installation des outils Krew et Stern**
>>
>> Exécutez la commande suivante pour installer Krew dans votre environnement :
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
>> Une fois Krew installé, installez Stern avec :
>>
>> ```bash
>> kubectl krew install stern
>> ```
>>
>> **4. Installation de la CLI OpenStack**
>>
>> Préparez votre environnement pour utiliser l'API OpenStack en installant python-openstackclient, en suivant [ce guide](/pages/public_cloud/public_cloud_cross_functional/prepare_the_environment_for_using_the_openstack_api).
>>
>> Installez le client Manila pour gérer les partages de stockage de fichiers :
>>
>> ```bash
>> pip install python-manilaclient
>> ```
>>
>> N'oubliez pas de mettre à jour votre script de complétion de shell pour activer l'autocomplétion OpenStack `share`.
>>
>> **5. Installation du driver CSI NFS**
>>
>> Ajoutez le référentiel de chart Helm :
>>
>> ```bash
>> helm repo add csi-driver-nfs https://raw.githubusercontent.com/kubernetes-csi/csi-driver-nfs/master/charts
>> helm repo update
>> ```
>>
>> Listez les versions disponibles du chart CSI NFS :
>>
>> ```bash
>> helm search repo -l csi-driver-nfs
>> ```
>>
>> Installez la version choisie du chart Helm :
>>
>> > [!primary]
>> >
>> > Remplacez les flags facultatifs `--wait -v=5 --debug` selon vos besoins pour le débogage ou l'installation synchrone.
>> >
>>
>> ```bash
>> helm install csi-driver-nfs csi-driver-nfs/csi-driver-nfs \
>>   --namespace kube-system \
>>   --version v4.11.0 \
>>   [--wait -v=5 --debug]
>> ```
>>
>> Suivez les logs du driver CSI NFS :
>>
>> ```bash
>> kubectl stern -n kube-system -l app.kubernetes.io/instance=csi-driver-nfs
>> ```
>>
>> **6. Installation du driver CSI Manila**
>>
>> Ajoutez le référentiel de chart Helm :
>>
>> ```bash
>> helm repo add cpo https://kubernetes.github.io/cloud-provider-openstack
>> helm repo update
>> ```
>>
>> Listez les versions disponibles du driver CSI Manila :
>>
>> ```bash
>> helm search repo -l openstack-manila-csi
>> ```
>>
>> Installez la version choisie du chart Helm :
>>
>> ```bash
>> helm install manila-csi cpo/openstack-manila-csi --version 2.33.1 --namespace kube-system [--values ./csi-config/helm-chart-values.yaml]
>> ```
>>
>> Suivez les logs du driver CSI Manila :
>>
>> ```bash
>> kubectl stern -n kube-system -l app=openstack-manila-csi
>> ```
>>
>> **7. Préparation des ressources OpenStack pour Manila CSI**
>>
>> 1. Créez un utilisateur OpenStack dédié pour Manila
>>
>> Vous avez besoin d'un utilisateur OpenStack séparé pour gérer les ressources Manila. Cet utilisateur peut être créé :
>>
>> - Via le panneau de contrôle OVHcloud (Public Cloud > Paramètres > Utilisateurs & Rôles)
>> - Ou via la CLI OVHcloud
>>
>> > [!primary]
>> >
>> > Ce nouvel utilisateur doit avoir le rôle share_operator ou administrateur.
>> >
>>
>> 2. Collectez les détails du projet et de l'utilisateur OpenStack
>>
>> Téléchargez le fichier openrc de votre projet depuis le panneau de contrôle OVHcloud et notez les informations suivantes :
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
>> > Une fois que vous avez ces valeurs, remplissez le fichier csi-config/secrets.yaml. Ce secret Kubernetes permettra au driver CSI Manila de gérer les ressources Manila dans votre cluster.
>> >
>>
>> ```bash
>> curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
>> chmod 700 get_helm.sh
>> ./get_helm.sh
>> ```
>>
>> Créez le secret dans votre cluster MKS :
>>
>> ```bash
>> # Appliquez les informations d'identification OpenStack pour Manila
>> kubectl apply -f ./csi-config/secrets.yaml
>> ```
>>
>> 3. Configurez le réseau partagé OpenStack
>>
>> Manila nécessite un réseau partagé car le driver est configuré avec `DHSS=true` (`driver_handles_share_servers`).
>>
>> Cette ressource est gérée par le propriétaire du projet OpenStack.
>>
>> ```bash
>> # Listez les réseaux privés attachés à votre cluster MKS
>> openstack --os-region-name SBG5 network list
>>
>> # Récupérez l'ID du réseau
>> openstack --os-region-name SBG5 network show -c id -f value <PRIVATE_NETWORK_NAME>
>>
>> # Récupérez l'ID de la sous-réseau liée à ce réseau
>> openstack --os-region-name SBG5 subnet show -c id -f value <PRIVATE_SUBNET_NAME>
>>
>> # Créez le réseau partagé Manila
>> openstack --os-region-name SBG5 share network create \
>>   --name mks-manila-csi-tests \
>>   --neutron-net-id <PRIVATE_NETWORK_ID> \
>>   --neutron-subnet-id <PRIVATE_SUBNET_ID>
>> ```
>>
>> Exemple de sortie :
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
>> **8. Configuration du driver CSI Manila**
>>
>> Une fois le réseau partagé OpenStack créé, et avant de configurer le driver CSI Manila, vous devez définir la plage de CIDR utilisée par vos nœuds MKS. Cela garantit que les nœuds peuvent accéder aux partages Manila.
>>
>> Éditez la ConfigMap de runtime :
>>
>> Ouvrez `csi-config/manila-runtime-configmap.yaml` et mettez à jour le champ `nfs.matchExportLocationAddress` pour qu'il corresponde à la plage de CIDR de votre cluster.
>>
>> Exemple :
>>
>> ```bash
>> nfs:
>>   matchExportLocationAddress: 10.42.0.0/16
>> ```
>>
>> Appliquez la ConfigMap à votre cluster Kubernetes :
>>
>> ```bash
>> # Optionnel si la configuration de runtime est déjà définie dans les valeurs Helm
>> kubectl apply -f ./csi-config/manila-runtime-configmap.yaml
>> ```
>>
>> **9. Création de partages NFS via provisionnement dynamique**
>>
>> Pour permettre au driver CSI Manila de créer dynamiquement des partages Manila et de les utiliser comme volumes Kubernetes, vous devez définir une classe de stockage (StorageClass) dans votre cluster. Cette classe de stockage spécifie le réseau partagé qui sera utilisé pour créer et accorder l'accès aux exports NFS.
>>
>> Récupérez l'ID du réseau partagé en utilisant la CLI OpenStack pour obtenir l'ID de votre réseau partagé :
>>
>> ```bash
>> openstack --os-region-name SBG5 share network list -f value -c ID
>> ```
>>
>> Configurez la classe de stockage :
>>
>> - Éditez le fichier csi-config/dynamic-storageclass.yaml.
>> - Mettez à jour la valeur du paramètre shareNetworkID avec l'ID du réseau partagé récupéré à l'étape précédente.
>>
>> Créez la classe de stockage dynamique en appliquant la classe de stockage à votre cluster :
>>
>> ```bash
>> # Une classe de stockage ne peut pas être mise à jour. Si des modifications sont nécessaires, supprimez-la et recréez-la.
>> kubectl apply -f poc/v2/nfs/dynamic-provisioning/dynamic-storageclass.yaml
>> ```
>>
>> Une fois la classe de stockage créée, créez une demande de volume persistant (PersistentVolumeClaim, PVC) en utilisant celle-ci. Par exemple, demandez un volume de 15 Gi avec un accès en lecture/écriture multiple (RWX) :
>>
>> ```bash
>> kubectl apply -f poc/v2/nfs/dynamic-provisioning/nfs-pvc.yaml
>> ```
>>
>> Après avoir appliqué la demande de volume, listez les nouveaux partages Manila créés dans votre projet Public Cloud :
>>
>> ```bash
>> openstack --os-region SBG5 share list
>> ```
>>
>> Exemple de sortie :
>>
>> ```bash
>> +--------------------------------------+------------------------------------------+------+-------------+-----------+-----------+-----------------+------+-------------------+
>> | ID                                   | Name                                     | Size | Share Proto | Status    | Is Public | Share Type Name | Host | Availability Zone |
>> +--------------------------------------+------------------------------------------+------+-------------+-----------+-----------+-----------------+------+-------------------+
>> | 9484d5f3-7bf7-486b-b88e-40bbedeet9f3 | pvc-78135a68-c6f4-48fe-8644-454b387a3ad4 |   15 | NFS         | available | False     | generic_0       |      | nova              |
>> +--------------------------------------+------------------------------------------+------+-------------+-----------+-----------+-----------------+------+-------------------+
>> ```
>>
>> Déployez un déploiement Kubernetes pour un serveur web avec 2 répliques. Les pods monteront et partageront le volume RWX créé précédemment :
>>
>> ```bash
>> kubectl apply -f poc/v2/nfs/dynamic-provisioning/nfs-deployment.yaml
>> ```
>>
>> Vous pouvez vérifier la fonctionnalité RWX en vous connectant à un pod en utilisant la commande `kubectl exec` et en créant un fichier dans le répertoire monté (par exemple, `/var/lib/www/`). Ensuite, connectez-vous au deuxième pod et vérifiez que le fichier est visible. Si c'est le cas, votre partage Manila exposé via NFS fonctionne correctement.
>>
>>
>> **10. Montage d'un partage Manila existant comme volume dans les pods**
>>
>> Comme indiqué précédemment, une classe de stockage Kubernetes peut créer dynamiquement des partages Manila exposés via NFS. Alternativement, vous pouvez utiliser un partage Manila pré-provisionné et le monter directement dans un pod.
>>
>> Créez un nouveau partage avec la CLI OpenStack :
>>
>> ```bash
>> openstack --os-region SBG5 share create \
>>   --share-type <SHARE_TYPE> \
>>   --share-network <SHARE_NETWORK_ID> \
>>   --name <NFS_SHARE_NAME> \
>>   SHARE_PROTOCOL SHARE_SIZE
>> ```
>>
>> Où :
>>
>> - `SHARE_TYPE` est `generic_0` par défaut. Vous pouvez vérifier les types de partage existants avec :
>>
>> ```bash
>> openstack --os-region SBG5 share type list
>> ```
>>
>> - `SHARE_NETWORK_ID` est l'identifiant de votre réseau partagé.
>> - `NFS_SHARE_NAME` est le nom de votre partage NFS.
>> - `SHARE_PROTOCOL` est le protocole à utiliser (actuellement, seul NFS est pris en charge).
>> - `SHARE_SIZE` est la taille à allouer à votre volume NFS (en GiB).
>>
>> Créez une règle d'accès au partage :
>>
>> ```bash
>> openstack --os-region SBG5 share access create <NFS_SHARE_NAME> ip <SUBNET_CIDR>
>> ```
>>
>> Où :
>>
>> - `SHARE_ACCESS_NAME` est le nom du partage.
>> - `SUBNET_CIDR` est le CIDR utilisé lors de la configuration du runtime Manila CSI.
>>
>> Récupérez l'ID du partage NFS et l'ID de l'accès au partage, puis mettez à jour les paramètres `volumeAttributes.shareID` et `volumeAttributes.shareAccessID` dans le fichier `poc/v2/nfs/static-provisioning/static-provisioning.yaml`.
>>
>> Appliquez le manifeste pour créer un volume persistant et sa demande de volume persistant en utilisant le partage NFS pré-provisionné. Le partage Manila ne sera utilisé que si le pod qui réclame la demande de volume est déployé dans votre cluster :
>>
>> ```bash
>> kubectl apply -f poc/v2/nfs/static-provisioning/static-provisioning.yaml
>> ```
>>
>> Déployez un pod qui monte ce partage :
>>
>> ```bash
>> kubectl apply -f poc/v2/nfs/static-provisioning/pod.yaml
>> ```
>>
>> Vous pouvez maintenant utiliser `kubectl exec` pour accéder au pod et exécuter `df -h` pour vérifier que le partage Manila pré-créé est correctement monté.
>>
>> ### CLI utiles
>>
>> Avec vos informations d'identification OpenStack chargées dans l'environnement, vous pouvez gérer les partages Manila en utilisant la CLI OpenStack. Les commandes courantes incluent :
>>
>> ```bash
>> openstack share list # Liste tous les partages
>> openstack share type list # Liste les types de partage disponibles
>> openstack share access list|create|delete [${SHARE_ID}] # Gérez les règles d'accès pour un partage spécifique
>> openstack share list|create|delete [${SHARE_ID}] # Créez, listez ou supprimez un partage par son ID
>> openstack share message list # pour voir les erreurs liées aux ressources Manila
>> ```
>>
>> ### Ressources utiles
>>
>> [Votre stockage ReadWriteMany (RWX) dans k8s avec Manila CSI](https://www.youtube.com/watch?v=WSMZDKx4JAI){.external}
>> [Manila/Concepts](https://wiki.openstack.org/wiki/Manila/Concepts#share_type){.external}
>> [Approche générique pour le provisionnement de partage](https://docs.openstack.org/manila/latest/admin/generic_driver.html){.external}
>> [Plugin officiel Manila CSI sur GitHub](https://github.com/kubernetes/cloud-provider-openstack/tree/master/examples/manila-csi-plugin){.external}
>>
> Via Terraform (bientôt disponible)
>>
>> > [!primary]
>> >
>> > La configuration via Terraform sera bientôt détaillée ici.
>> >
>>

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).