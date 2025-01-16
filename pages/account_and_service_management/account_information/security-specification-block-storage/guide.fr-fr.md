---
title : Spécification de sécurité du service Block Storage
excerpt : Présentation de la sécurité du stockage par bloc (aka Block Storage)
mise à jour : 16/01/2025
---

## Objectif

En complément au [modèle de responsabilité du service Block Storage entre le client et OVHcloud](/pages/block_storage/responsabilitémodel-block-storage), cette fiche a pour objectif de présenter les particularités et fonctions de sécurité propres à ce service. Elle met aussi en avant des bonnes pratiques qui permettront au client de l'exploiter au mieux. 
### 1. Certifications

- ISO/IEC 27001
- ISO/IEC 27701
- ISO/IEC 27017
- ISO/IEC 27018
- HDS
- SOC 1 type II
- SOC 2 type II
- CSA type II
- C5 type II

### 2. Recommandations une fois le service livré

Une fois inscrit au service Instances, vous pouvez ajouter vos volumes Block Storage. Vous pouvez gérer les droits des utilisateurs via la section Utilisateurs et rôles dans l'espace client en suivant
ce [guide](/pages/public_cloud/compute/create_and_delete_a_user).


### 3. Service Level Agreement (SLA)

Le SLA varie entre 99,999% et 99,5% et diffère entre les offres et les gammes. Reportez-vous aux conditions particulières de service pour plus de détails.

### 4. Backups



#### 4.2 Sauvegarde des données clients

Vous devez mettre en œuvre un dispositif de sauvegarde supplémentaire basé sur les outils du client ou les options proposées par OVHcloud, comme le Second serveur, le basculement d'IP, etc.

| **Option** | **Granularité** | **RPO** | **RTO** | **Documentation** |
| --- | --- | --- | --- | --- |
| Volume backup | Le volume Block Storage | Dépend de la date de la dernière sauvegarde et du temps de résolution de l'incident | Dépend de la taille du volume| [Création d'une sauvegarde de volume](/pages/public_cloud/compute/volume-backup)|


### 5. Logs

| **Source** | **Contenu** | **Documentation** |
| --- | --- | --- |
| Espace Client | Logs des interactions des contacts administrateur, technique ou facturation dans l’espace client et des services auxquels ils ont accès, grâce aux appels API. |- <https://api.ovh.com/console/#/me> (voir `/me/api/logs`)<br>- [Liste des appels API effectués avec votre compte](https://api.ovh.com/console/#/me/api/logs/self~GET)<br>- [Liste des appels API effectués sur les services auxquels vous avez accès](https://api.ovh.com/console/#/me/api/logs/services~GET)<br>- [Obtenir vos journaux d'audit](https://api.ovh.com/console/console/#/audit/#~me) |

### 6. API

| **Nom** | **Capacité** | **Documentation** |
| --- | --- | --- |
| Espace client et service | Gérer les comptes clients et les services sur lesquels chaque compte dispose de droits d'accès. | [Gestion des volumes dans l’API OpenStack](/pages/public_cloud/compute/starting_with_manage_volumes_openstack_api)|

### 7. Comptes - Utilisateur

#### 7.1 Control plane

Depuis votre espace client, vous pouvez gérer votre service en utilisant [trois contacts différents](/pages/account_and_service_management/account_information/manage_contacts).<br>
OVHcloud utilise un autre compte avec un NIC interne pour référencer un client ayant souscrit à plusieurs services.

Pour appliquer l'accès sécurisé à votre compte sur l'espace client, nous vous recommandons d'activer un [mécanisme d'authentification à deux facteurs](/pages/account_and_service_management/account_information/secure-ovhcloud-account-with-2fa) ou [SSO (Single Sign-On) authentication](/pages/account_and_service_management/account_information/ovhcloud-account-connect-saml-adfs).


#### Plan de données 7.2

Une fois que vous avez obtenu vos informations d'identification, vous êtes autonome pour créer des comptes d'utilisateurs sur votre système d'exploitation et les applications que vous avez installées.

### 8. Fonctionnalités et options disponibles lors de la livraison du service


Option #### 8.1 HDS

L’option HDS peut être activée sur le service.<br>
La souscription au [niveau de support Business](https://www.ovhcloud.com/en/support-levels/business/)est obligatoire, au moins pour respecter les exigences nécessaires.

### 9. Réversibilité

Pour assurer la réversibilité du service, vous pouvez suivre la [politique de réversibilité spécifique](/pages/account_and_service_management/reversibilite/03-public-cloud-reversibilite-policy) pour importer et exporter vos données en toute autonomie.

#### 9.1 Effacement des données client

Une fois votre projet Public Cloud détruit, dans l’espace client OVHcloud, toutes les ressources allouées sont libérées.
