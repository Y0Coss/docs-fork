---
title: "Politique de réversibilité du produit Managed Database System for Web Hosting"
updated: 2025-08-21
---

## Objectif

Ce document est la politique de réversibilité du produit Managed Database System for Web Hosting couvrant l’offre commerciale d’OVHcloud Hébergement Web.

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.

## Liste des fonctionnalités

Les fonctionnalités du produit sont réparties en trois catégories :

1. Les **fonctionnalités principales** pour lesquelles nous garantissons la capacité de migration.
2. Les **implémentation OVHcloud** qui nécessitent une adaptation à un nouvel environnement de migration.
3. Les **fonctionnalités spécifiques** qui ne peuvent pas être garanties pour la migration car elles sont liées à l'environnement OVHcloud ou impliquent des développements personnalisés.

### 1. Fonctionnalités principales

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| Package de bases de données pour un hébergement web standard| Utilisation de composants open source standards | SQL, NoSQL | **Entrante** : copie des fichiers applicatifs, import des bases de données via dump SQL, configuration standard <br>**Sortante** : export des fichiers/dumps, réutilisables sur tout environnement compatible. | [Créer une base de données sur son hébergement web](/pages/web_cloud/web_hosting/sql_create_database) |
| Export/Import base de données | Sauvegarde et restauration des bases via API ou espace client OVHcloud  | SQL, CSV | **Entrante** : import d’un dump SQL existant <br>**Sortante** : Export d’un dump SQL, importable sur tout serveur MySQL/MariaDB/PostgreSQL  | [Importer une sauvegarde dans la base de données d'un hébergement web](/pages/web_cloud/web_hosting/sql_importing_mysql_database) |
| Utilisateurs et permissions | Système d’utilisateur et de gestion des droits stockés dans la base de données | NA | **Entrante** : import des utilisateurs et des permissions via le dump e la base de données <br>**Sortante** : export des utilisateurs et des permissions via le dump de la base de données | [Modifier le mot de passe de la base de données d'un hébergement web](/pages/web_cloud/web_hosting/sql_change_password) |

### 2. Implémentations OVHcloud

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |


### 3. Fonctionnalités spécifiques

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


