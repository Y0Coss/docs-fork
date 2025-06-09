---
title : Politique de réversibilité du produit Object Storage 3AZ
updated: 2025-06-09
---

**Objectif**

Ce document décrit la politique de réversibilité pour le produit Object Storage 3AZ.

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.

**Liste des fonctionnalités**

Les fonctionnalités du « Produit » sont réparties en trois catégories :

* Les principales fonctionnalités pour lesquelles nous vous garantissons la possibilité de migrer.
* La mise en œuvre d’OVHcloud dont la migration nécessitera des adaptations à un nouvel environnement.
* Les fonctionnalités spécifiques dont la migration en tant que telle est impossible à garantir car elles sont liées à l'environnement OVHcloud ou à des développements spécifiques.

**Principales fonctionnalités**

| **Fonctionnalité** | **Description** | **Formats** **Disponible** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| Compatibilité API S3 | Interface compatible S3 (API RESTful standard, outils AWS CLI, SDK, etc.) | S3 (REST, JSON, multipart upload) | **Entrant** : Upload direct via API S3 compatible, outils CLI, SDK ou migration depuis tout autre stockage compatible S3. <br> **Sortant** : Téléchargement/export direct via API S3, CLI ou SDK vers tout autre fournisseur compatible S3.. | [S3 API](https://help.ovhcloud.com/csm/en-public-cloud-storage-pcs-s3-swift-rest-api-compatibility?id=kb_article_view&sysparm_article=KB0047191) |
| Export/import massif d'objets | Import/export de données par lots via les outils S3 (sync, cp, etc.) | S3 (objets, dossiers) | **Entrant** : Utilisation des outils type rclone ou équivalent pour migrer des données depuis une autre solution <br> **Sortant** : Export massif via les mêmes outils vers une autre plateforme S3 ou compatible. | [Manage buckets](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-getting-started-object-storage?id=kb_article_view&sysparm_article=KB0047348) |
| Versionning d'objet | Gestion native des versions d’objets (stockage de chaque version lors de la modification/suppression) | S3 (versioning) | **Entrant** : Upload de données chiffrées ou non, gestion transparente.<br> **Sortant** : Export des versions via API/CLI, compatible avec d’autres S3. | [Getting started with versioning](/pages/storage_and_backup/object_storage/s3_versioning) |
| Chiffrement côté serveur (SSE-S3/SSE-C) | Chiffrement natif des objets au repos, compatible avec standards S3 | S3 (HSSE-S3, HSSE-C) | **Entrant** : Upload de données chiffrées ou non, gestion transparente.<br> **Sortant** :Export sans adaptation, chiffrement maintenu ou retraité par la cible.| [Object Storage Encryption](/pages/storage_and_backup/object_storage/s3_encrypt_your_objects_with_sse_c) |
| Interopérabilité avec des solutions tierces | Support natif de Veeam, HYCU, Nextcloud, Kubernetes, etc. | S3 (API, JSON, objets) | **Entrant** : Intégration directe via des plugins ou des connecteurs.<br> **Sortant** : Export des données via outils natifs ou API S3 vers la cible. | [Object storage with Veeam](/pages/storage_and_backup/object_storage/s3_veeam) |

**Implementation OVHcloud**

| **Functionalité** | **Description** | **Available formats** | **Migration model** | **Documentation available** |
| --- | --- | --- | --- | --- |
| Offsite Replication OVHcloud | Réplication automatique des données vers une région OVHcloud 1-AZ distincte | S3 (objets répliqués) | **Entrant** : Non applicable à l'importation directe, nécessite une configuration OVHcloud.<br> **Sortant** : Restauration manuelle depuis la région répliquée, puis export vers la cible externe (nécessite adaptation si la cible n’a pas de mécanisme équivalent). | [Cross-region replication](/pages/storage_and_backup/object_storage/s3_asynchronous_replication) |
| Object Lock (verrouillage d’objet) | Immuabilité des objets (WORM), empêche suppression/modification pendant une période définie | S3 (object lock) | **Entrant** : Nécessite que la source supporte l’Object Lock S3.</b> <br>**Sortant** : Export possible, mais la cible doit supporter le verrouillage S3 ou adaptation manuelle des politiques d’immuabilité. | [Object storage ObjectLock](/pages/storage_and_backup/object_storage/s3_managing_object_lock) |
| ACL et gestion avancée des accès | Gestion des droits d'accès via ACL S3, ou politiques spécifiques | S3 (ACL, politiques) | **Entrant** : Adaptation des droits en fonction de la structure cible.<br> **Sortant** :Export des objets, mais reconfiguration des ACL/politiques nécessaire sur la plateforme de destination  | [Gestion des accès](/pages/storage_and_backup/object_storage/s3_bucket_acl) |

**Fonctionnalités spécifiques**

| **Functionnalité** | **Description** | **Available formats** | **Migration model** | **Documentation available** |
| --- | --- | --- | --- | --- |
| Gestion via l'espace client OVHcloud / API OVHcloud | Interface graphique et API propriétaires OVHcloud pour la gestion du stockage | N/A | **Entrant** : Non applicable.<br> **Sortant** : Scripts/API à réécrire pour l'environnement cible. | [Manage-buckets](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage) |

**Liste des architectures**

Object Storage 3-AZ d’OVHcloud repose sur une architecture multi-AZ, avec distribution automatique des données sur trois zones de disponibilité physiquement séparées (data centers distants de plusieurs kilomètres). Cette architecture utilise l’erasure coding pour assurer la redondance locale et la tolérance à la perte d’une zone complète, garantissant ainsi une haute disponibilité et une continuité de service même en cas de panne majeure. La réplication asynchrone inter-région est disponible en option (Offsite Replication), permettant la sauvegarde automatique des données vers une autre région 1-AZ OVHcloud

**Services partenaires**

Les partenaires OVHcloud sont répertoriés avec le mot-clé "Cloud Migration" dans le [répertoire dédié](https://partner.ovhcloud.com/en/directory/).
OVHcloud propose également un service dédié : [OVHcloud Professional Services](https://www.ovhcloud.com/fr/professional-services/).

**Coüts et frais**

Aucun frais de résiliation : Pas de sur facturation à l’usage. Le service est stoppé immédiatement après suppression du service.

**Conservation des données après résiliation du contrat**

Les données sont supprimées par action du client lui-même. OVHcloud ne conserve aucune donnée. Une exportation manuelle préalable est obligatoire pour préserver les données.
Un point d’attention concernant la fonctionnalité Object Lock. Plus d’informations à retrouver sur la documentation associée.
Une fois le service resilié par le client, OVHCloud libère les ressources qui étaient allouées.

