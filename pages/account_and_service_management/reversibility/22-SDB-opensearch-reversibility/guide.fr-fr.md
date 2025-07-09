---
title: "Politique de réversibilité du produit Managed Search Engine Software Platform"
updated: 2025-06-27
---

## Objectif

Ce document est la politique de réversibilité du produit Managed Search Engine Software Platform couvrant l'offre commerciale d'OVHcloud Managed OpenSearch.

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.

## Liste des fonctionnalités

Les fonctionnalités du produit sont réparties en trois catégories :

1. Les **fonctionnalités principales** pour lesquelles nous garantissons la capacité de migration.
2. Les **implémentation OVHcloud** qui nécessitent une adaptation à un nouvel environnement de migration.
3. Les **fonctionnalités spécifiques** qui ne peuvent pas être garanties pour la migration car elles sont liées à l'environnement OVHcloud ou impliquent des développements personnalisés.

### 1 - Fonctionnalités principales

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| Platforme as a Service | Moteur NoSQL d’indexation, de recherche de contenu et d’analyse de données entièrement managé par OVHcloud  | JSON (snapshots S3) | **Entrante** : création d’un snapshot source, migration via RFS vers la plateforme  <br>**Sortante** : export de snapshot OVHcloud  vers tout cluster OpenSearch compatible via RFS ou outils natifs  | [OpenSearch-Getting started](/pages/public_cloud/public_cloud_databases/opensearch_02_getting_Started) |
| Accès API REST standard | Accès via API REST OpenSearch (port 9200) | JSON | **Entrante** : connexion directe depuis outils et applications existants. <br>**Sortante** : extraction des données via API pour migration vers un autre cluster.  | [API OVH-OpenSearch](https://eu.api.ovh.com/console/?section=%2Fcloud&branch=v1#get-/cloud/project/-serviceName-/database/opensearch) |
| Snapshots manuels | Création manuelle de snapshots via API ou Dashboard  | JSON (S3, stockage externe) | **Entrante** : restauration d’un snapshot externe <br>**Sortante** : export de snapshot vers tout environnement Opensearch  | [API OVH-OpenSearch](https://eu.api.ovh.com/console/?section=%2Fcloud&branch=v1#get-/cloud/project/-serviceName-/database/opensearch) |
| Plugins standard | Liste de plugins open source (ICU Analysis, Phonetic Analysis, etc.) activables, désactivables et compatibles avec la technologie   | Plugins officiels OpenSearch | **Entrante** : activation des plugins compatibles avec la version cible <br>**Sortante** : réutilisation des plugins s’ils sont supportés par le nouvel environnement | [OpenSearch - Capabilities and Limitations](/pages/public_cloud/public_cloud_databases/opensearch_01_capabilities) |


### 2 - Implémentations OVHcloud

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| Sauvegardes automatiques managées par OVHcloud | Sauvegardes quotidiennes gérées par OVHcloud (rétention variable selon l’offre choisie) | Snapshots internes OVHcloud | **Entrante** : Non applicable. Fonctionnalité disponible par défaut et aucune action requise par l’utilisateur de la plateforme <br>**Sortante** : Création d’un nouveau service, restauration locale d’un snapshot OVHcloud, puis export manuel vers le nouvel environnement   | [Public Cloud Databases - Sauvegardes automatiques ](/pages/public_cloud/public_cloud_databases/databases_05_automated_backups) |
| vRack | Le vRack, ou rack virtuel, est une technologie VLAN privée qui permet la connexion entre les services OVHcloud | NA | **Entrante** : <br>**Sortante** :  | [Création de V(x)LAN Public Cloud Databases](/pages/public_cloud/public_cloud_databases/databases_08_vrack) |
| Access Control List (ACL)  | Gestion des droits d’accès via interface OVHcloud | NA | **Entrante** : création manuelle des règles dans l’interface OVHcloud. <br>**Sortante** : conversion des règles ACL au format du nouveau fournisseur.  | [OpenSearch - Capabilities and Limitations](/pages/public_cloud/public_cloud_databases/opensearch_01_capabilities) |
| Métriques | Collecte de métriques intégrée à l’infrastructure OVHcloud | Prometheus metrics | **Entrante** : envoi des logs via un point d’entrée dédié <br>**Sortante** : export possible, mais reconfiguration nécessaire sur la nouvelle plateforme  | [OpenSearch - Surveillez votre infra ](/pages/public_cloud/public_cloud_databases/opensearch_200_elk_like) |


### 3 - Fonctionnalités spécifiques

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |

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


