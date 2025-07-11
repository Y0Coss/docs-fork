---
title: 'Migration d’instances entre zones de disponibilité (AZ)'
excerpt: 'Ce guide décrit comment migrer une instance Public Cloud OVHcloud entre deux zones de disponibilité (AZ), en 1AZ ou 3AZ. Il couvre les étapes de sauvegarde, transfert et recréation, avec instructions via le Manager, Horizon ou la CLI OpenStack.'
updated: 2025-07-20
---

## Objectifs

Ce guide explique comment migrer une instance Public Cloud d’une zone de disponibilité (AZ) à une autre, de 1AZ vers 3AZ ou inversement. Il centralise les étapes clés — backup, transfert et recréation — et redirige vers les guides détaillés pour chaque élément.

## prérequis

- Avoir une instance [Public Cloud](https://www.ovhcloud.com/fr/public-cloud/) dans votre compte OVHcloud.
- Être connecté à votre [espace client OVHcloud](/links/manager).

## En pratique

> [!primary]
>
> Avant d’effectuer une migration d’instance, il est important de bien comprendre les différences entre les types de déploiement proposés dans le Public Cloud OVHcloud. Chaque mode — 1AZ, 3AZ ou Local Zones — a un impact direct sur la résilience, la disponibilité et la conception de votre infrastructure.
>
> Pour en savoir plus, consultez la documentation : [Comparaison et résilience des modes de déploiement - Comprendre les régions 3-AZ / 1-AZ / Local Zones.](/pages/public_cloud/public_cloud_cross_functional/deployment_modes_comparison_resilience_details)
>

### Étape 1. Sauvegarder son instance

Commencez par créer une sauvegarde de votre instance à migrer, ou utilisez-en une déjà existante si elle est toujours valide.

OVHcloud propose deux types de sauvegardes, avec des comportements différents selon le type de migration souhaité :

- Sauvegarde locale : nécessitent un transfert manuel si vous migrez vers une autre région ou AZ.
- Sauvegarde distante (backup distant) - recommandée : gérée automatiquement par OVHcloud, elle est répliquée dans la région (AZ) choisi. Aucun transfert manuel n’est requis.

> [!tabs]
> Via l'espace client OVHcloud
>> Pour créer une sauvegarde d'une instance à partir de l'espace client OVHcloud, suivez [cette section](/pages/public_cloud/compute/save_an_instance#createinstanceviamanager) de notre guide sur la création de la sauvegarde d'une instance.
>>
> Via la CLI Openstack
<!-- >> Pour créer une sauvegarde d’une instance depuis la CLI OpenStack, suivez [cette section](/pages/public_cloud/compute/save_an_instance#createinstanceviaopenstack) de notre guide sur la création de la sauvegarde d'une instance. -->
<!-- need PR sur le backup distant -->
>>
> via Horizon
<!-- >> Pour créer une sauvegarde d’une instance depuis Horizon, suivez [cette section](/pages/public_cloud/compute/save_an_instance#createinstanceviahorizon) de notre guide sur la création de la sauvegarde d'une instance. -->
<!-- >> a faire dans la pr sur le backup distant -->

### Étape 2. Migrer sa sauvegarde vers une autre région

> [!primary]
>
> Si vous avez utilisé une sauvegarde distante, vous pouvez passer directement à l'[étape 3. Restaurer l’instance dans la nouvelle région.](#step3recreateinstance)
>

> [!tabs]
> Via la CLI Openstack
>> Pour transférer votre sauvegarde d'une AZ à une autre via la CLI Openstack, veuillez suivre notre guide : [Télécharger et transférer la sauvegarde d'une instance d'une région OpenStack à une autre](/pages/public_cloud/compute/transfer_instance_backup_from_one_datacentre_to_another)
>>

### Étape 3. Restaurer l’instance dans la nouvelle région <a name="step3recreateinstance"></a>

> [!tabs]
> Via l'espace client OVHcloud
>> Pour créer une instance à partir d'un backup existant, veuillez suivre [cette section](/pages/public_cloud/compute/create_restore_a_virtual_server_with_a_backup#createinstanceviamanager) de notre guide : Créer / restaurer un serveur virtuel a partir d’une sauvegarde.
>>
> Via la CLI Openstack
>> Pour créer une instance à partir d'un backup existant via la CLI Openstack, suivez [cette section](/pages/public_cloud/compute/create_restore_a_virtual_server_with_a_backup/#createinstanceviaopenstack) de notre guide : Créer / restaurer un serveur virtuel a partir d’une sauvegarde.
>>
> Via Horizon
>> Pour créer une instance à partir d'un backup existant via Horizon, suivez [cette section](/pages/public_cloud/compute/create_restore_a_virtual_server_with_a_backup/#createinstanceviahorizon) de notre guide : Créer / restaurer un serveur virtuel a partir d’une sauvegarde.
>>

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).