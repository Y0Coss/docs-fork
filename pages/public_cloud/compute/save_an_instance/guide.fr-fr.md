---
title: 'Sauvegarder une instance'
excerpt: 'Découvrez comment sauvegarder une instance Public Cloud depuis votre espace client OVHcloud ou via OpenStack'
updated: 2025-06-10
---

<style>
details>summary {
    color:rgb(33, 153, 232) !important;
    cursor: pointer;
}
details>summary::before {
    content:'\25B6';
    padding-right:1ch;
}
details[open]>summary::before {
    content:'\25BC';
}
</style>

## Objectif

Vous pouvez créer une sauvegarde unique d'une instance ou configurer un planning afin d'automatiser les sauvegardes de vos instances. Les sauvegardes peuvent être utilisées pour restaurer votre instance à un état antérieur ou pour créer une nouvelle instance identique.

**Ce guide explique comment créer des sauvegardes manuelles et automatiques d'une instance Public Cloud.**

## Prérequis

- Avoir une instance [Public Cloud](/links/public-cloud/public-cloud) dans votre compte OVHcloud.
- Être connecté à votre [espace client OVHcloud](/links/manager).
- CLI OpenStack. Consultez notre guide « [Préparer l'environnement pour utiliser l'API OpenStack](/pages/public_cloud/public_cloud_cross_functional/prepare_the_environment_for_using_the_openstack_api) ». (optionnel)

## En pratique

### Créer une sauvegarde d'une instance

> [!warning]
> Cette option est uniquement disponible via un **Cold Snapshot** pour les instances Metal. L'instance Metal passera en mode rescue et, une fois la sauvegarde effectuée, l'instance sera redémarrée en mode normal.
>

> [!tabs]
>>
> Via l'espace client OVHcloud
>>
>> Connectez-vous à [l’espace client d’OVHcloud](/links/manager), accédez à la section `Public Cloud`{.action} et sélectionnez le projet Public Cloud concerné.<br>
>> Cliquez ensuite sur `Instances`{.action} dans le menu de gauche.<br>
>> Une fois sur la page des instances, cliquez sur le bouton `...`{.action} à droite de l'instance et sélectionnez `Créer un backup`{.action}.
>>
>> ![public-cloud-instance-backup](images/createbackup1.png){.thumbnail}
>>
>> > [primary]
>> >
>> > Deux types de sauvegardes sont disponibles :
>> > - Locale : Une sauvegarde locale est stockée dans la même région que votre instance.
>> > - Distante : Une sauvegarde distante crée automatiquement une copie de la sauvegarde locale dans une autre région de votre choix.
>> >
>> > Chaque sauvegarde est facturée séparément. La sauvegarde distante sera facturée selon la tarification du stockage dans la région distante sélectionnée.
>> >
>>
>> /// details | Sauvegarde locale
>>
>> Renseignez un nom pour la sauvegarde. Prenez connaissance des informations tarifaires et cliquez sur `Confirmer`{.action}.
>>
>> ![public-cloud-instance-backup](images/createbackup2bis.png){.thumbnail}
>>
>> ///
<!-- >>
>> /// details | Sauvegarde distante
>>
>> Renseignez un nom pour la sauvegarde locale dans le champ `Saisissez le nom de votre backup :`.
>>
>> ![public-cloud-instance-distant-backup](images/createdistantbackup1.png){.thumbnail}
>>
>> Ensuite, `activez`{.action} l’option permettant d’ajouter une sauvegarde distante, puis indiquez le nom de cette sauvegarde, sélectionnez sa région de destination et cliquez sur `Confirmer`{.action}.
>>
>> /// -->
>>
>> Il n'est pas possible de suivre la progression de la sauvegarde en temps réel. Cependant, vous pouvez consulter le statut de la sauvegarde dans la section `Instance Backup`{.action} sous la rubrique **Compute** du menu de gauche, où l'état `Backup en cours` sera affiché pendant le processus.
>>
>> ![public-cloud-instance-backup](images/backup_in_progress.png){.thumbnail}
>>
>> Une fois la sauvegarde terminée, celle-ci sera disponible dans la section `Instance Backup`{.action} sous la rubrique **Compute** dans le menu de gauche.
>>
>> ![public-cloud-instance-backup](images/createbackup3.png){.thumbnail}
>>
> Via l'API OVHcloud <a name="createinstanceviaapi"></a>
>>
>> Utilisez l'appel API suivant :
>>
>> > [!api]
>> >
>> > @api {v1} /cloud POST /cloud/project/{serviceName}/region/{regionName}/instance/{instanceId}/snapshot
>> >
>>
>> Renseignez les variables :
>>
>> - **serviceName** : Identifiant du projet OVHcloud.
>> - **regionName** : Nom de la région où se situe l’instance source.
>> - **instanceId** : Identifiant unique de l’instance concernée.
>> - **snapshotName** : Nom du snapshot (sauvegarde locale) à créer.
>> - **distantRegionName (optionnel)** : Nom de la région distante où le backup sera stocké.
>> - **distantSnapshotName (optionnel)** : Nom du backup distant à créer dans la région distante.
>>
>> > [!primary]
>> >
>> > Ne créez un backup distant que si les paramètres relatifs à la région distante (**distantRegionName** et **distantSnapshotName**) sont renseignés.
>> >
>>
> Via OpenStack
>>
>> Exécutez la commande suivante pour afficher la liste des instances :
>>
>> ```bash
>> $ openstack server list
>>
>> +--------------------------------------+-----------+--------+--------------------------------------------------+--------------+
>> | ID | Name | Status | Networks | Image Name |
>> +--------------------------------------+-----------+--------+--------------------------------------------------+--------------+
>> | aa7115b3-83df-4375-b2ee-19339041dcfa | Server 1 | ACTIVE | Ext-Net=51.xxx.xxx.xxx, 2001:41d0:xxx:xxxx::xxxx | Ubuntu 16.04 |
>> +--------------------------------------+-----------+--------+--------------------------------------------------+--------------+
>> ```
>>
>> /// details | Sauvegarde locale
>>
>> Exécutez ensuite la commande suivante pour créer une sauvegarde de votre instance :
>>
>> ```bash
>> $ openstack server image create --name snap_server1 aa7115b3-83df-4375-b2ee-19339041dcfa
>> ```
>>
>> ///
>>
>> /// details | Sauvegarde distante
>>
>> Exécutez la commande suivante après avoir suivi l'étape de la sauvegarde locale :
>>
>> ```bash
>> $ openstack workflow execution create ovh.glance.glance_download '{"src_image_id": "<image_id>", "src_region": "<current_region>", "dst_region": "<remote_region>"}'
>> ```
>>
>> ///
>>
> Via Horizon
>>
>> Cliquez sur le menu `Compute`{.action} à gauche puis sélectionnez `Instances`{.action}.<br>
>> Cliquez ensuite sur le bouton `Create Snapshot`{.action} situé à droite de la ligne correspondant à l’instance concernée.
>>
>> ![public-cloud-instance-backup-horizon1](images/createbackuphorizon1.png){.thumbnail}
>>
>> Renseignez le nom du backup et appuyez sur le bouton `Create Snapshot`{.action}.
>>
>> ![public-cloud-instance-backup-horizon2](images/createbackuphorizon2.png){.thumbnail}
>>

### Créer une sauvegarde automatisée d’une instance

> [!primary]
>
> Si vous souhaitez automatiser cette fonctionnalité directement via OpenStack, vous pouvez créer un workflow Mistral associé à un cron trigger.
>

Cliquez sur le bouton `...`{.action} à droite de l'instance et sélectionnez `Créer une sauvegarde automatisée`{.action}.

![public-cloud-instance-backup](images/createbackup4.png){.thumbnail}

Vous pourrez alors configurer les paramètres de sauvegarde suivants :

#### **Le workflow** 

Actuellement, un seul workflow existe. Il créera une sauvegarde pour l'instance et son volume principal.

![public-cloud-instance-backup](images/createbackup5.png){.thumbnail}

#### **La ressource** 

Vous pouvez sélectionner l'instance à sauvegarder.

![public-cloud-instance-backup](images/createbackup6.png){.thumbnail}

#### **Le planning** 

Vous pouvez définir une planification de sauvegarde personnalisée ou choisir l'une des fréquences par défaut :

- Sauvegarde quotidienne avec rétention des 7 dernières sauvegardes
- Sauvegarde quotidienne avec rétention des 14 dernières sauvegardes

![public-cloud-instance-backup](images/createbackup7.png){.thumbnail}

Si vous activez l’option de sauvegarde distante, vous pourrez définir un nom pour la sauvegarde et sélectionner son emplacement.

![public-cloud-instance-distant-backup-workflow](images/createdistantbackup3.png){.thumbnail}

#### **Le nom** 

Entrez un nom pour la planification de la sauvegarde automatique. Prenez connaissance des informations de tarification et créez le planning en cliquant sur le bouton `Créer`{.action}.
 
![public-cloud-instance-backup](images/createbackup8.png){.thumbnail}

### Gestion des sauvegardes et des plannings

Les planifications peuvent être créées et supprimées dans la section `Workflow Management`{.action} qui se trouve sous la rubrique **Compute** dans le menu de gauche.

![public-cloud-instance-backup](images/createbackup9.png){.thumbnail}

Les sauvegardes de vos instances sont gérées dans la section `Instance Backup`{.action} qui se trouve sous la rubrique **Compute** dans le menu de gauche.

![public-cloud-instance-backup](images/createbackup10.png){.thumbnail}

> [!warning]
> L'option de sauvegarde de l'instance doit être supprimée séparément si vous ne souhaitez plus qu'elle vous soit facturée. La suppression d'une instance ne supprime pas les options qui y sont attachées.
>

> [!warning]
> **Notez que vous ne pouvez pas supprimer une sauvegarde d'instance si une instance qui a été générée à partir de cette sauvegarde est en cours d'exécution au moment de l'action de suppression.**

Découvrez comment utiliser les sauvegardes pour cloner ou restaurer des instances dans [ce guide](/pages/public_cloud/compute/create_restore_a_virtual_server_with_a_backup).

## Aller plus loin

[Créer / restaurer un serveur virtuel a partir d’une sauvegarde](/pages/public_cloud/compute/create_restore_a_virtual_server_with_a_backup)

Échangez avec notre [communauté d'utilisateurs](/links/community).
