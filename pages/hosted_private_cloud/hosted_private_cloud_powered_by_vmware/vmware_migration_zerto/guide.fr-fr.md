---
title: Move2Cloud - Migration de charges VMware vers OVHcloud Hosted Private Cloud avec Zerto
excerpt: "Découvrez comment migrer vos charges de travail VMware on-premises vers un environnement Hosted Private Cloud OVHcloud à l’aide de Zerto Virtual Replication."
updated: 2025-07-02
---

## Objectif

Ce guide explique comment migrer vos charges de travail VMware on-premises vers un **environnement OVHcloud Hosted Private Cloud (HPC)** en utilisant **Zerto Virtual Replication**.

>[!warning]
> À partir de mai 2025, **Zerto ne prend pas en charge la réplication de machines virtuelles avec le chiffrement VMEncrypt activé**.  
> Le chiffrement *at rest* de vSAN reste compatible. Vous pouvez également chiffrer les VMs après la migration.

## Prérequis

Avant de commencer, assurez-vous de détenir :

- Un inventaire détaillé de vos VMs : FQDN, adresses IP, OS, dépendances applicatives.
- Un plan de migration par lots applicatifs cohérents.
- Une liste complète des VLANs, sous-réseaux et segments.
- Un HPC OVHcloud configuré avec les ressources nécessaires (hosts, datastores, vSAN, NSX-T).
- Un tunnel VPN IPsec fonctionnel entre votre site source et OVHcloud.
- L'accès à la console Zerto et aux interfaces vCenter des deux côtés.

## En pratique

### Étape 1 : Faire l’inventaire des VMs et de la topologie réseau

- Listez toutes les VMs à migrer avec leur système d’exploitation et version.
- Regroupez-les par application (web/app/db) pour définir des lots cohérents.
- Répertoriez vos VLANs et plages IP pour anticiper la configuration réseau cible.

### Étape 2 : Dimensionner votre HPC cible

- Calculez les besoins en vCPU, RAM et stockage selon votre ratio de consolidation.
- Choisissez entre datastores NFS ou vSAN en fonction des performances attendues.
- Si vous utilisez NSX-T :
  - Planifiez vos segments (VLANs/Overlays) et gateways Tier-0/Tier-1.
  - Préparez vos pare-feux virtuels (Stormshield, FortiVM, Palo Alto).
  - Ajoutez des IP publiques ou migrez vos IP via la [fonction BYOIP](/links/network/byoip).

### Étape 3 : Autoriser l’accès à vCenter OVHcloud

L’accès est bloqué par défaut. Pour l’ouvrir :

- Suivez le guide « [Autoriser des IP à se connecter au vCenter](https://help.ovhcloud.com/csm/en-gb-vmware-authorise-ip-addresses-vcenter?id=kb_article_view&sysparm_article=KB0045321) ».
- Autorisez les IP de votre site on-premise et de vos composants Zerto.

### Étape 4 : Configurer les rôles et permissions

- Activez l’IAM OVHcloud via ce guide :  
  [Présentation de l’IAM OVHcloud](https://help.ovhcloud.com/csm/en-gb-vmware-iam-presentation?id=kb_article_view&sysparm_article=KB0063154)
- Si vous conservez une gestion interne : déployez un contrôleur AD ou Okta, ou configurez ADFS pour SSO :  
  [Configurer SAML avec ADFS](https://help.ovhcloud.com/csm/en-gb-connect-saml-sso-adfs?id=kb_article_view&sysparm_article=KB0043008)

### Étape 5 : Construire votre réseau cible dans HPC

- Créez une **matrice de flux** documentant les communications attendues (VM ↔ VM, VLANs, ports, protocoles).
- Utilisez les VLANs préconfigurés ou ajoutez vos propres segments.
- NSX-T est activé par défaut (Tier-0/1, dFW). Pour commencer :  
  [Premiers pas avec NSX](https://help.ovhcloud.com/csm/en-gb-vmware-nsx-first-steps?id=kb_article_view&sysparm_article=KB0056831)

### Étape 6 : Déployer les services cœur dans l’HPC

Pour limiter la latence :

- **NTP** : utilisez `ntp.ovh.net`
- **DNS** : installez un contrôleur de domaine local si besoin
- **AD** : installez une instance ou configurez la fédération avec votre domaine

### Étape 7 : Installer Zerto dans l’HPC OVHcloud

- Suivez la procédure OVHcloud :  
  [Zerto Virtual Replication sur HPC OVHcloud](https://help.ovhcloud.com/csm/en-gb-vmware-zerto-virtual-replication-customer-to-ovh?id=kb_article_view&sysparm_article=KB0046457)
- Zerto déploiera automatiquement un ZVM, des ZVRAs et une passerelle firewall managée.
- Pour en savoir plus :  
  [Installation Zerto (site officiel)](https://help.zerto.com/bundle/Install.VC.HTML/page/Performing_an_Express_Installation.htm){.external}

### Étape 8 : Installer Zerto sur le site on-premise

- Suivez la même procédure que ci-dessus, côté on-prem.
- Vérifiez la communication entre ZVMs et ZVRAs :  
  - TCP 9071 / 9081 (ZVM ↔ ZVM)  
  - TCP 4007 / 4008 (ZVRA ↔ ZVRA)

### Étape 9 : Créer le tunnel IPsec

- Le VPN est obligatoire pour permettre à Zerto de fonctionner sans NAT.
- Suivez l'exemple avec OPNsense ou tout équipement compatible :  
  [Configurer le VPN IPsec pour Zerto](https://help.ovhcloud.com/csm/en-gb-vmware-zerto-virtual-replication-customer-to-ovh?id=kb_article_view&sysparm_article=KB0046457)

### Étape 10 : Appairer les ZVMs

- Appairez vos ZVMs (on-premise ↔ OVHcloud) comme indiqué à l’étape 5 du guide précédent.

### Étape 11 : Créer les VPG Zerto

- Regroupez les VMs à protéger dans des **VPGs (Virtual Protection Groups)**.
- Consultez la documentation :  
  [Créer un VPG](https://help.zerto.com/bundle/Admin.ZSSP.HTML.10.0_U3/page/Creating_a_VPG.htm){.external}

### Étape 12 : Suivre la réplication

- Surveillez les VPGs dans la console Zerto :  
  [Monitoring des VPGs](https://help.zerto.com/bundle/Admin.ZSSP.HTML.10.0_U3/page/Monitoring_Virtual_Protection_Groups.htm){.external}

### Étape 13 : Tester la migration

- Lancez un **test de failover** sans interruption des services :  
  [Démarrer un test](https://help.zerto.com/bundle/Admin.VC.HTML.10.0_U3/page/StartingFailoverTest.htm){.external}  
  [Arrêter le test](https://help.zerto.com/bundle/Admin.VC.HTML.10.0_U3/page/What_Happens_After_Starting_a_Test.htm){.external}

### Étape 14 : Lancer la migration finale

- Exécutez un **Move** le jour J :  
  [Procédure de migration](https://help.zerto.com/bundle/Admin.ZSSP.HTML.10.0_U3/page/The_Move_Process.htm){.external}
- Paramétrez votre stratégie de commit (automatique, validée manuellement, ou rollback).

### Étape 15 : Vérifier les applications

- Confirmez que toutes les VMs sont démarrées et fonctionnelles.
- Vérifiez la connectivité aux services (AD, DNS, antivirus, services web...).

### Étape 16 : Finaliser la migration

- Si tout est conforme, validez la bascule dans Zerto.
- En cas d’échec, restaurez via la procédure de rollback.

### Étape 17 : Migrer les VMs vers leur stockage cible

- Utilisez **Storage vMotion** pour optimiser le placement des VMs :  
  [VMware Storage vMotion](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vmware_storage_vmotion)

### Étape 18 : Sauvegarder les charges migrées

Protégez les données migrées :

- [Veeam as a Service (HPC)](/pages/storage_and_backup/backup_and_disaster_recovery_solutions/veeam/vmware_veeam_backup_as_a_service)
- [Veeam avec licences Enterprise (Public Cloud)](/pages/storage_and_backup/backup_and_disaster_recovery_solutions/veeam/public_cloud_storage_veeam_backup_replication)

## Aller plus loin

Besoin d’un accompagnement personnalisé ? Contactez votre Technical Account Manager ou sollicitez notre équipe [Professional Services](/links/professional-services).

Participez à notre communauté [Discord](https://discord.gg/ovhcloud){.external} ou posez vos questions sur le [hub communautaire](/links/community).
