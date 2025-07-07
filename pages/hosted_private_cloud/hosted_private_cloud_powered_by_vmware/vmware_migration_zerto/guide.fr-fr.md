---
title: Move2Cloud - Migration de charges VMware vers OVHcloud Hosted Private Cloud avec Zerto
excerpt: "Découvrez comment migrer vos charges de travail VMware on-premises vers un environnement Hosted Private Cloud OVHcloud à l’aide de Zerto Virtual Replication."
updated: 2025-07-07
---
## Objectif

Ce guide explique comment migrer vos charges de travail VMware on-premises vers un **Hosted Private Cloud (HPC) d’OVHcloud** en utilisant **Zerto Virtual Replication**.

> [!primary]
> **Ce guide s’applique aux environnements Hosted Private Cloud standards qui ne sont pas qualifiés SecNumCloud (SNC), PCI-DSS ou HDS.**  
> Certaines fonctionnalités comme **OVHcloud IAM** ou les fonctions avancées de **NSX-T** peuvent ne pas être disponibles dans ces environnements.  
> Pour les environnements SecNumCloud, consultez le guide dédié :  
> [Move2Cloud - Migration des charges de travail VMware vers le Hosted Private Cloud SecNumCloud avec Zerto](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vmware_migration_zerto_secnumcloud)

## Prérequis

Avant de commencer, assurez-vous d'avoir :

- Un inventaire complet de vos machines virtuelles (VM) : FQDN, adresse IP, version du système d'exploitation, dépendances applicatives
- Un plan de migration par lots regroupés par pile applicative
- Une liste complète des VLAN, sous-réseaux et segments du réseau cible
- Un environnement HPC correctement dimensionné (hosts, datastores, vSAN, NSX-T)
- Un tunnel VPN IPsec fonctionnel entre votre infrastructure sur site et OVHcloud
- Un accès à la console Zerto et aux interfaces vCenter sur les deux environnements

> [!warning]
> Depuis mai 2025, **Zerto ne prend pas en charge la réplication des machines virtuelles avec le chiffrement VMEncrypt activé**.  
> Le chiffrement au repos de vSAN est pris en charge. Vous pouvez également chiffrer vos VM après la migration.

## En pratique

![Move2CloudZerto](images/Move2Cloud-Zerto.png){.thumbnail}

## Étape 1 à Étape 4  
_(Déjà en place ci-dessus)_

## Étape 5 : Construire le réseau cible

### Étape 5.1 : Recréer les VLAN et segments

Utilisez le `vRack`{.action} pour créer vos VLAN dans le locataire HPC. Reproduisez les schémas IP et les plages définis lors de l’inventaire.

Si vous utilisez NSX-T, définissez les segments nécessaires (VLAN ou Overlay) selon votre segmentation applicative.

### Étape 5.2 : Configurer les gateways et le routage NSX-T

Avec NSX-T, les gateways Tier-0 et Tier-1 sont pré-déployées. Vérifiez ou modifiez leur configuration depuis `NSX Manager`{.action}.

Définissez les routes, les services d’overlay, et la connectivité avec l’extérieur selon la matrice de flux identifiée à l’étape 1.

### Étape 5.3 : Préparer les règles de pare-feu

Le pare-feu distribué NSX-T permet de contrôler les flux est-ouest entre VMs. Configurez des règles par rôle ou zone applicative.

Si vous utilisez un pare-feu virtuel externe (Stormshield, FortiVM, Palo Alto), implémentez les mêmes règles manuellement.

Voir : [NSX-T – Premières étapes](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/nsx-01-first-steps)

## Étape 6 : Déployer les services essentiels dans le HPC

### Étape 6.1 : NTP

Configurez `ntp.ovh.net` comme source de temps pour toutes vos VMs.

### Étape 6.2 : DNS

Déployez un serveur DNS local dans le HPC. Il peut s’agir d’un contrôleur AD ou d’un serveur DNS dédié.

### Étape 6.3 : Authentification

Déployez un contrôleur de domaine Active Directory dans le HPC, ou établissez un lien sécurisé avec votre domaine source.

## Étape 7 : Installer Zerto dans le locataire OVHcloud

### Étape 7.1 : Activation

Dans `Hosted Private Cloud`{.action}, allez dans `Reprise d’activité`{.action} > `Activer Zerto Virtual Replication`{.action}.

Cela déclenche le déploiement des composants suivants :

- ZVM OVHcloud
- ZVRA sur chaque hôte ESXi
- Firewall NSX-T avec règles prêtes à l’emploi

Voir : [Zerto Virtual Replication OVHcloud](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vmware_zerto_virtual_replication_customer_to_ovh)

## Étape 8 : Installer Zerto sur le site source

Suivez la procédure officielle Zerto : [Installation express](https://help.zerto.com/bundle/Install.VC.HTML/page/Performing_an_Express_Installation.htm){.external}

- Installez le ZVM sur un serveur Windows avec accès vSphere
- Déployez les ZVRA sur chaque hôte ESXi
- Ouvrez les ports TCP 9071/9081 (ZVM) et 4007/4008 (ZVRA)

## Étape 9 : Configurer le VPN IPsec

Zerto nécessite une communication directe entre les composants ZVM/ZVRA. Le NAT est interdit.

Créez un tunnel IPsec standard depuis votre pare-feu vers OVHcloud. Les paramètres sont documentés ici :  
[Zerto VPN Setup OVHcloud](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vmware_zerto_virtual_replication_customer_to_ovh)

## Étape 10 : Coupler les sites et créer les VPG

1. Dans le ZVM source, ajoutez le site cible OVHcloud
2. Créez vos Virtual Protection Groups (VPGs), chacun regroupant les VMs d’une application

Voir : [Créer un VPG](https://help.zerto.com/bundle/Admin.ZSSP.HTML.10.0_U3/page/Creating_a_VPG.htm){.external}

## Étape 11 : Suivre la réplication

Dans l’interface Zerto :

- Vérifiez l’état de chaque VPG
- Suivez le RPO
- Résolvez toute alerte avant test

Voir : [Suivi des VPGs](https://help.zerto.com/bundle/Admin.ZSSP.HTML.10.0_U3/page/Monitoring_Virtual_Protection_Groups.htm){.external}

## Étape 12 : Lancer un test de basculement

Effectuez un `Failover Test` dans Zerto pour valider le comportement des VMs répliquées sans impact sur la production.

- [Démarrer le test](https://help.zerto.com/bundle/Admin.VC.HTML.10.0_U3/page/StartingFailoverTest.htm){.external}
- [Arrêter le test](https://help.zerto.com/bundle/Admin.VC.HTML.10.0_U3/page/What_Happens_After_Starting_a_Test.htm){.external}

## Étape 13 : Lancer la migration planifiée

1. Utilisez l’option `Move` pour basculer les VPGs
2. Choisissez la politique de commit (automatique, manuelle, ou rollback)

Voir : [Procédure de migration](https://help.zerto.com/bundle/Admin.ZSSP.HTML.10.0_U3/page/The_Move_Process.htm){.external}

## Étape 14 : Vérifier les applications

- Vérifiez que toutes les VMs sont sous tension
- Testez la connectivité (AD, DNS, Internet, Bastion)
- Vérifiez le bon fonctionnement applicatif

## Étape 15 : Valider ou annuler la migration

- Si tout fonctionne : `Commit`
- Sinon : `Rollback`

Voir : [Validation finale](https://help.zerto.com/bundle/Admin.ZSSP.HTML.10.0_U3/page/Moving_Protected_Virtual_Machines_to_the_Remote_Site.htm){.external}

## Étape 16 : Utiliser Storage vMotion

Pour optimiser le placement des VMs sur le bon stockage (NFS ou vSAN) :

1. Faites un clic droit sur la VM > `Migrer`{.action}
2. Choisissez `Modifier le stockage uniquement`{.action}
3. Sélectionnez la destination

Voir : [Storage vMotion](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vmware_storage_vmotion)

## Étape 17 : Sauvegarder les workloads migrés

### Option 1 : Veeam as a Service
[Service Veeam OVHcloud](/pages/storage_and_backup/backup_and_disaster_recovery_solutions/veeam/vmware_veeam_backup_as_a_service)

### Option 2 : Veeam autogéré
[Serveur Veeam avec licences BYOL](/pages/storage_and_backup/backup_and_disaster_recovery_solutions/veeam/public_cloud_storage_veeam_backup_replication)

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en œuvre de nos solutions, contactez votre Technical Account Manager ou demandez une analyse personnalisée de votre projet à nos experts de l’équipe [Professional Services](/links/professional-services).

Posez des questions, donnez votre avis et interagissez directement avec l’équipe qui construit nos services Hosted Private Cloud sur le canal [Discord](https://discord.gg/ovhcloud){.external} dédié.

Échangez avec notre [communauté d'utilisateurs](/links/community).