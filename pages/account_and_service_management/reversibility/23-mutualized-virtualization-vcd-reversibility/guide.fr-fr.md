---
title: "Politique de réversibilité du produit Managed Mutualized Virtualization "
updated: 2025-06-27
---

## Objectif

Ce document est la politique de réversibilité du produit Managed Mutualized Virtualization correspondant à l’offre commerciale d’OVHcloud VMware Cloud Director.

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.

## Liste des fonctionnalités

Les fonctionnalités du produit sont réparties en trois catégories :

1. Les **fonctionnalités principales** pour lesquelles nous garantissons la capacité de migration.
2. Les **implémentation OVHcloud** qui nécessitent une adaptation à un nouvel environnement de migration.
3. Les **fonctionnalités spécifiques** qui ne peuvent pas être garanties pour la migration car elles sont liées à l'environnement OVHcloud ou impliquent des développements personnalisés.

### 1 - Fonctionnalités principales

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| Images VM standards  | Import/export d’images VM aux formats standards pris en charge par l’hyperviseur OVF | OVF | **Entrante** : import d’images via l’API ou l’interface utilisateur <br>**Sortante** : export des images VM, réutilisables sur tout environnement compatible  | [Les concepts fondamentaux de VCD ](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vcd-get-concepts) <br><br>[VMware Cloud Director - Migration depuis VMware vSphere on OVHcloud](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vcd_migration_use-cases) <br><br>[OVHF Tool](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/ovf_tool) |



### 2 - Implémentations OVHcloud

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| Gestion avec l’API OVHcloud | Gestion des VM via API | JSON, YAML, scripts | **Entrante** : déploiement, gestion et import automatisés <br>**Sortante** : export des configurations, scripts et automatisations utilisables sur d'autres plateformes  | [Connexion à l’API OVH](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/connexion_a_l_api_ovh) |
| Sauvegarde et restauration manuelle | Snapshots, sauvegardes et restaurations à la demande via interface utilisateur ou API | Snapshots, images disques | **Entrante** : import d’image VM standard <br>**Sortante** :  Pas d’accès aux fichiers natifs de sauvegarde. L’export n’est pas possible dans un nouvel environnement d’hébergement  | [Sauvegardes avec Veeam et restaurations](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vcd-backup) |
| Gestion des réseaux virtuels | Configuration réseaux (subnets, security groups) spécifique à OVHcloud | NA | **Entrante** : <br>**Sortante** :  | [VMware Cloud Director - Concepts réseaux et bonnes pratiques]() <br><br>[VMware Cloud Director - Création de composants réseaux via Public VCF as-a-Service]() |


### 3 - Fonctionnalités spécifiques

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| Anti-DDoS | L’anti-DDoS est un ensemble d’outils et de mécanismes conçus pour absorber les attaques par déni de service. Il comprend l'analyse du trafic, le « nettoyage » via un réseau spécialisé et la mitigation grâce à la technologie VAC développée par OVHcloud. | N/A | **Entrant** : le système anti-DDoS fait partie de notre infrastructure et est activé par défaut. Aucune action n'est requise. <br> **Sortant** : commande et configuration un anti-DDoS chez le nouveau fournisseur. | [OVHcloud DDoS Protection](/links/security/antiddos) |

## Liste des architectures

blabla
Le produit est décliné en deux offres de service : 
- xxxxx
- xxxxx

## Services partenaires

Les partenaires OVHcloud concernés figurent dans l'annuaire des [partenaires OVHcloud](/links/partner) sous les mots-clés « **Data center expansion and Migration** ».

OVHcloud dispose également d’un service dédié : [OVHcloud Professional Services](/links/professional-services).

## Coûts et frais


## Conservation des données après résiliation du contrat


