---
title: Politique de réversibilité du produit Managed Dedicated Cloud
updated: 2025-08-07
---

## Objectif

Ce document est la politique de réversibilité du produit Managed Dedicated Cloud correspondant à l'offre commerciale VMware on OVHcloud.

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.


## Liste des fonctionnalités

Les fonctionnalités du produit sont réparties en trois catégories :

1. Les **fonctionnalités principales** pour lesquelles nous garantissons la capacité de migration.
2. Les **implémentation OVHcloud** qui nécessitent une adaptation à un nouvel environnement de migration.
3. Les **fonctionnalités spécifiques** qui ne peuvent pas être garanties pour la migration car elles sont liées à l'environnement OVHcloud ou impliquent des développements personnalisés.


### 1. Fonctionnalités principales

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| Virtualisation | Gestion des VM via vSphere, vCenter, vMotion, et support de formats standards VMware | OVA, OVF | **Entrante** : import de VM, disques, snapshots via l’interface vSphere ou les outils spécialisés (exemple Veeam, Zerto, etc …)  <br>**Sortante** : export des VM, disques via vSphere, et réutilisation sur tout environnement VMware ou compatible. Des outils spécialisés peuvent être utilisés (exemple Veeam, Zerto, etc …) | [Se connecter à l’interface web vSphere](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vsphere_interface_connexion)<br><br>[Déploiement d’une machine virtuelle](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/deploiement_d_une_machine_virtuelle)<br><br>[Comment connecter une image ISO à une VM](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/how_to_connect_an_iso_image_to_a_vm) <br><br>[Création de cluster et activation EVC](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/create_cluster_enable_evc) |
| Gestion des utilisateurs et droits | Création, gestion et suppression des utilisateurs, gestion des permissions et rôles via l’interface utilisateur  | JSON, CSV (exports)  | **Entrante** : import manuel ou automatisé des utilisateurs et des /permissions <br>**Sortante** : export des listes d’utilisateurs, permissions et adaptation sur la cible.  | [IAM pour VMware on OVHcloud](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vmware_iam_getting_started) |
| Gestion des réseaux virtuels  | Configuration réseau via NSX, gestion des VLAN, routage, firewall, sécurité des réseaux via API ou UI | YAML, JSON, scripts | **Entrante** : définition des réseaux, VLAN, règles firewall <br>**Sortante** : export des configurations réseau à travers les API VMWare disponibles  | [Premiers pas avec NSX](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/nsx-01-first-steps) |


### 2. Implémentations OVHcloud

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
|---|---|---|---|---|
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |
|vRack|Le vRack, ou rack virtuel, est une technologie VLAN privée qui permet la connexion entre les services OVHcloud|N/A|**Migration entrante**: Les services Hosted private Cloud sont inclus par défaut dans vRack.<br><br>**Migration sortante**: Prenez note de l'architecture réseau et reproduisez-la avec des VLAN.|[Utiliser le Hosted Private Cloud au sein d’un vRack](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/using_private_cloud_in_vrack)<br><br>[Création de V(x)LAN](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/creation_vlan)|
|vROps|Solution standard de Monitoring VMware.|N/A|**Migration entrante**: vROps est inclus par défaut avec chaque Hosted Private Cloud.<br><br>**Migration sortante**: Installer et configurer vROps dans un environnement vSphere.|[First connection on vROps](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vrops_introduction)|
|Managed Veeam backup|Solution de sauvegarde en tant que service pour vos VMs|VBK, VIB, VBM|**Migration entrante**: Activez une option de sauvegarde Veeam dans l'[espace client OVHcloud](/links/manager).<br><br>**Migration sortante**: Importez des sauvegardes manuellement, puis restaurez-les.|[Activer et utiliser Veeam Managed Backup](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/veeam_backup_as_a_service)<br><br>[Importer des sauvegardes](https://helpcenter.veeam.com/docs/backup/hyperv/importing_backups.html?ver=110)(EN)|
|Zerto|Plateforme de continuité et de reprise d'activité après sinistre.|N/A|**Migration entrante**: Activez le service Zerto dans l'[espace client OVHcloud](/links/manager) ou directement dans l'interface de réplication Zerto fournie.<br><br>**Migration sortante**:  Exportez les paramètres VPG de Zerto et importez-les dans le nouvel environnement.|[Mise en oeuvre de Zerto Virtual Replication pour votre PRA](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/zerto_virtual_replication_as_a_service)<br><br>[Exporter les paramètres VPG Zerto](https://www.zerto.com/myzerto/knowledge-base/exporting-and-importing-vpg-settings-with-zerto-diagnostic-tool/)(EN)|

### 3. Fonctionnalités spécifiques

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
|---|---|---|---|---|
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |
|Anti-DDoS|L'anti-DDoS est un ensemble d'équipements et de moyens mis en place pour absorber les attaques par déni de service. Il comprend une analyse du trafic, « l’aspiration » vers un réseau spécialisé et la mitigation, assurée par la technologie VAC développée par OVHcloud.|N/A|**Migration entrante**: Le système anti-DDoS est un composant de notre infrastructure, activé par défaut. Aucune action n'est requise.<br><br>**Migration sortante**: Commandez et configurez un anti-DDoS avec le nouveau fournisseur.|[Protection anti-DDoS OVHcloud](/links/security/antiddos)|
|Sécurité avancée pour SDDC|Ensemble de fonctionnalités améliorant la sécurité, telles que l'implémentation de Sécurité Zero Trust, MFA, IDS pour l'accès vSphere...|N/A|**Migration entrante**: Commandez l'activation de la sécurité avancée depuis l'[espace client OVHcloud](/links/manager).<br><br>**Migration sortante**: Commandez et configurez les fonctionnalités de sécurité appropriées avec le nouveau fournisseur.|[SDDC Advanced Security Pack](https://www.ovhcloud.com/fr/enterprise/products/hosted-private-cloud/safety-compliance/sddc/)|

### Liste des architectures

xxxxxxxxx


### Services Partenaires

Les partenaires OVHcloud concernés figurent dans l'annuaire des [partenaires OVHcloud](/links/partner) sous les mots-clés « **Data center expansion and Migration** ».

OVHcloud dispose également d’un service dédié : [OVHcloud Professional Services](/links/professional-services).

### Coût et frais

Aucune facturation supplémentaire n'est prévue de la part de OVHcloud pour les fonctionnalités de migration répertoriées ici.

### Conservation des données après la résiliation du contrat

Les données sont conservées jusqu'à la fin du mois suivant la résiliation du service, puis supprimées définitivement.

## Aller plus loin

[Migrer une infrastructure vers Hosted Private Cloud](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/service-migration).
