---
title : Politique de réversibilité du produit Orchestration
updated: 2025-06-10
---

## Objectif

Ce document décrit la politique de réversibilité pour la gamme de produits (Managed Orchestration) correspondant aux offres de services OVHcloud : Kubernetes et Rancher.

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.

## Liste des fonctionnalités

Les caractéristiques du product  sont réparties en trois catégories :

- **Fonctionnalités principales** pour lesquelles nous garantissons la capacité de migration.
- **Implémentations OVHcloud ** qui nécessitent une adaptation à un nouvel environnement de migration.
- **Fonctionnalités spécifiques** qui ne peuvent pas être garanties pour la migration car elles sont liées à l'environnement OVHcloud ou impliquent des développements personnalisés.



## Fonctionnalités principales

| Fonctionnalité| Description | Formats | Modèle de migration | Documentation disponible |
| --- | --- | --- | --- | --- |
| **Orchestration via Kubernetes** | Gestion des clusters via API Kubernetes (kubectl, Helm, CI/CD, etc.), conforme CNCF| YAML, JSON, OCI | **Entrant** : Déploiement de manifests, Helm charts, images OCI via API standard Kubernetes.<br>**Sortant** : Export des manifests, Helm charts, images via API standard, réutilisables sur tout cluster Kubernetes compatible. | [Creating a cluster](/pages/public_cloud/containers_orchestration/managed_kubernetes/creating-a-cluster)|
| **Orchestration via Rancher** | Orchestration de conteneurs simplifiant le déploiement, la gestion et la mise à l'échelle des applications conteneurisées. | YAML, JSON, OCI | **Entrant** : Import de manifests, Helm charts, images OCI ou cluster via API et interface utilisateur.<br>**Sortant** : Export des manifests, Helm charts, images via API, réutilisables sur tout cluster Kubernetes compatible. | [Getting Started with Managed Rancher Service](/pages/public_cloud/containers_orchestration/managed_rancher_service/getting-started)
| **Export/Import de manifests** | Déploiement, export et migration de ressources via fichiers YAML/JSON standard Kubernetes | YAML, JSON | **Entrant** : Import direct des manifests existants.<br>**Sortant** : Export des manifests via kubectl get -o yaml/json, utilisables sur tout cluster Kubernetes compatible. |[Deploying an application](/pages/public_cloud/containers_orchestration/managed_kubernetes/deploying-an-application)|
| **IAM** | Gestion de l'identité et des accès aux ressources du cluster par Rancher via un fournisseur d’identité externe. | Active Directory, LDAP, OpenLDAP, Azure AD… | **Entrant** : Import ou création de rôles et politiques d’accès via API ou interface utilisateur..<br>**Sortant** : Export des configurations via API ou interface utilisateur.| [Configuring authentication](https://ranchermanager.docs.rancher.com/guides-pratiques/guides-nouveaux-utilisateurs/permissions-authentification-et-configuration-globale/authentication-config)|

## Implémentation OVHcloud
| Fonctionnalité| Description | Formats | Modèle de migration | Documentation disponible |
| --- | --- | --- | --- | --- |
| **Liaison entre Identity Provider et cluster**  | Connexion entre l'identity provider et le cluster | JSON | **Entrant** : Adaptation des configurations au format OVH avant import via CLI ou IHM.<br>**Sortant** : Export des configurations au format OVH, réadaptation à l’environnement cible nécessaire. | [Configuring the OIDC provider on an OVHcloud Managed Kubernetes cluster](/pages/public_cloud/containers_orchestration/managed_kubernetes/configuring-oidc-provider-config) |
| **Configuration du Control Plane**| Possibilité de modifier certains paramètres pour personnaliser le cluster. | N/A | **Entrant** : : Configuration de certains paramètres du Control Plane Kubernetes via une API spécifique OVH.<br>**Sortant** : Non exportable directement, réécriture des paramètres dans l’environnement cible.| [Creating a cluster](    /pages/public_cloud/containers_orchestration/managed_kubernetes/creating-a-cluster) |
| **Réseau privé et vRack** | Le vRack, ou rack virtuel, est une technologie VLAN privée qui permet la connexion entre les services OVHcloud disponible sur le dataplane du service Managed Kubernetes  | N/A | **Entrant** : : Les services Managed Kubernetes sont inclus par défaut dans vRack.<br>**Sortant** : Prendre note de l'architecture réseau et reproduisez-la avec des VLAN.| [ Using vRack Private Network ](/pages/public_cloud/containers_orchestration/managed_kubernetes/using-vrack) |
| **Journalisation** | Traçabilité des actions dans kubernetes.Les logs Rancher ne sont pas accessible au client.| N/A | **Entrant** : N/A<br>**Sortant** : Un transfert des logs peut être configuré avec une nécessité d’une intégration au service OVHcloud Log Data Platfom. | [Managed Kubernetes Service Audit Logs Forwarding](/pages/public_cloud/containers_orchestration/managed_kubernetes/forwarding-audit-logs-to-logs-data-platform) |
| **Add-ons et opérateurs spécifiques** | Certains opérateurs/add-ons déployés via OVHcloud Marketplace ou spécifiques à OVHcloud | YAML, JSON, Helm | **Entrant** : Installation possible si compatible avec.<br>**Sortant** : Adaptation ou remplacement par des équivalents sur la cible (limitation à Rancher standard pour Rancher). |
| **Pool de nœuds** | Possibilité de créer un pool de nœud.| N/A | **Entrant** :Configuration du pool de nœud via l’interface OVH.<br>**Sortant** : Réutilisation du format du pool de nœud dans un environnement équivalent |[Managing nodes and node pools](/pages/public_cloud/containers_orchestration/managed_kubernetes/managing-nodes) |


## Fonctionnalités spécifiques
| Fonctionnalité| Description | Formats | Modèle de migration | Documentation disponible |
| --- | --- | --- | --- | --- |
| **OVHcloud Manager/API**| Gestion via OVHcloud Manager/API| N/A | **Entrant** : N/A<br>**Sortant** : Scripts et API à réécrire pour l'environnement cible, gestion manuelle nécessaire.  | [Spécification API OVHcloud ](https://eu.api.ovh.com/console/?section=%2FallDom&branch=v1)|
| **Rancher OVHcloud Edition** | Offre d’utilisation limité de Rancher dans OVH. | N/A | **Entrant** : : Configuration des fonctionnalités si disponible.<br>**Sortant** : Scripts/API à réécrire pour la cible, gestion manuelle nécessaire.| [Managed Rancher Service](https://www.ovhcloud.com/fr/public-cloud/managed-rancher-service/) |
| **Infrastructure as Code** | Déploiement automatisé via modules Terraform spécifiques à OVHcloud pour les services managés ou via module Terraform Kubernetes ou Rancher pour les services opensource. | N/A | **Entrant :** Scripts à adapter pour d’autres fournisseurs <br> **Sortant :** Réécriture nécessaire des configurations Terraform. | [Terraform](https://registry.terraform.io/providers/ovh/ovh/latest/docs) |
| **Anti-DDoS** | L'anti-DDoS est un ensemble d'équipements et de moyens mis en place pour absorber les attaques par déni de service. Il comprend une analyse du trafic, « l’aspiration » vers un réseau spécialisé et la mitigation, assurée par la technologie VAC développée par OVHcloud. | N/A | **Entrant :** Le système anti-DDoS est un composant de notre infrastructure, activé par défaut. Aucune action n'est requise. <br> **Sortant:** Commander et configurer un anti-DDoS avec le nouveau fournisseur.| [Protection anti-DDoS](https://www.ovh.com/fr/anti-ddos/)<br>[Technologie anti-DDoS](https://www.ovh.com/fr/anti-ddos/technologie-anti-ddos.xml) |



## Liste des architectures

Managed Orchestration d’OVHcloud repose sur des clusters Kubernetes managés, multi-nœuds, avec haute disponibilité, auto-scaling, gestion centralisée, et intégration réseau privée (vRack). Intégration des principaux outils de monitoring, logging et CI/CD. Les architectures supportent la migration multi-cloud et le déploiement hybride.

Le service managé d’orchestration tourne sur une seule région parmi plusieurs régions, au choix, rendu disponible par OVH. Il est possible de gérer plusieurs clusters dans plusieurs régions (fournis par OVH ou par d’autres fournisseurs) via le service Rancher tournant dans une seule région.


## Services Partenaires

Les partenaires OVHcloud sont répertoriés sous le mot-clé **« Migration vers le cloud »** dans l'annuaire des partenaires dédiés.

OVHcloud propose également un service dédié : [**OVHcloud Professional Services**](https://www.ovhcloud.com/fr/professional-services/).



## Coût et frais

Facturation en mode pay as you go. La facturation s’arrête lorsque le client ne consomme plus de ressources. Aucun frais de résiliation spécifique n’est appliqué : la suppression du service arrête la facturation immédiatement. Les crédits OVHcloud éventuellement associés ne sont pas transférables. 

Suite à la résiliation du service, une libération des ressources est opérée par OVH qui engendre une incapacité à récupérer les données. Il incombe au client d’exporter ses configurations, manifests et images avant la résiliation, en raison de la libération des ressources.

Dans le cas de l’utilisation de Rancher, la facturation inclura un montant minimal même dans le cas où il n’orchestrerait aucun cluster.


## Rétention des données après résiliation du contrat

Après suppression du service ou résiliation du contrat, OVHcloud libère les ressources du cluster. Il est donc impératif d’exporter toutes les données et configurations nécessaires avant suppression, aucune restauration n’étant possible après coup.
