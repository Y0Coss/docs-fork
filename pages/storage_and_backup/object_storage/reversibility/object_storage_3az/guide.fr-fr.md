---
title : Politique de réversibilité des produits Object Storage 3AZ
updated: 2025-06-09
---

**Objectif**

Ce document décrit la politique de réversibilité pour le produit Object Storage 3AZ.

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.

**Liste des fonctionnalités**

The functionalities of the Product are divided into three categories:

* The main [features for which we guarantee you the possibility to migrate.](https://help.ovhcloud.com/csm)
* OVHcloud is currently in operation, and [the migration will require adaptations to a new environment.](https://help.ovhcloud.com/csm)
* Specified functionalities whose migration as such is impossible to guarantee because they are linked to the OVHcloud environment or specific developments.

**Principales fonctionnalités**

| **Fonctionnalité** | **Description** | **Formats** **Disponible** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| Compatibilité API S3 | Interface compatible S3 (API RESTful standard, outils CLI AWS, SDK, etc.) | S3 (REST, JSON, upload multipart) | **Entrant** : Téléchargement direct via **API S3** compatible, outils CLI, SDK ou migration depuis tout autre stockage compatible S3. Sortant : chargement/exportation direct via API S3, CLI ou SDK vers tout autre fournisseur compatible S3. | [S3 API](https://help.ovhcloud.com/csm/en-public-cloud-storage-pcs-s3-swift-rest-api-compatibility?id=kb_article_view&sysparm_article=KB0047191) |
| Export/import massif d'objets | Importation/exportation de données par lots via les outils S3 (sync, cp, etc.) | S3 (objets, dossiers) | **Entrant** : Utilisez rclone ou des outils équivalents pour migrer des données depuis une autre solution **Sortant** : Exportation massive via les mêmes outils vers une autre plateforme S3 ou compatible. | [Manage buckets](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-getting-started-object-storage?id=kb_article_view&sysparm_article=KB0047348) |
| Versionning des objets | Gestion native des versions des objets (stockage de chaque version lors de l'édition / marketing) | S3 (versioning) | **Entrant** : Importe **objets versionnés** d'un autre S3. Sortant : Exporter les versions via API/CLI, compatible avec les autres S3. | [Getting started with versioning](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-versioning?id=kb_article_view&sysparm_article=KB0063856) |
| Cryptage côté serveur (SSE-S3/SSE-C) | Chiffrement natif des objets au repos, compatible avec les standards S3 | S3 (HSSE-S3, HSSE-C) | **Entrant** : Upload de données chiffrées ou non, gestion transparente. **Sortie** : Export sans adaptation, chiffrement maintenu ou retraité par la cible. | [Object Storage Encryption](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-encrypt-objects-sse-c?id=kb_article_view&sysparm_article=KB0047314) |
| Interopérabilité avec des solutions tierces | Support natif pour Veeam, HYCU, Nextcloud, Kubernetes, etc. | S3 (API, JSON, objets) | **Entrant** : Intégration directe via des plugins ou des connecteurs. **Sortie** : Exportez les données vers la cible via des outils natifs ou l’API S3. | [Object storage with Veeam](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-veeam?id=kb_article_view&sysparm_article=KB0047693) |

**Implementation OVHcloud**

| **Functionality** | **Description** | **Available formats** | **Migration model** | **Documentation available** |
| --- | --- | --- | --- | --- |
| Réplication hors site OVHcloud | Réplication automatique des données vers une région OVHcloud 1-AZ distincte | S3 (objets répliqués) | **Entrant** : Non applicable à l'importation directe, nécessite une configuration OVHcloud. **Sortie** : Restauration manuelle à partir de la région répliquée, puis exportation vers la cible externe (nécessite une adaptation si la cible ne dispose pas d’un mécanisme équivalent). | [Cross-region replication](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-asynchronous-replication-buckets?id=kb_article_view&sysparm_article=KB0062418) |
| Verrouillage d'objet | Immuabilité des objets (WORM), empêche la suppression/modification pendant une période définie | S3 (object lock) | **Entrant** : la source doit prendre en charge le verrouillage d'objet S3.</b> **Sortie : exportation possible, mais la cible doit prendre en charge le verrouillage S3 ou l'ajustement manuel des stratégies d'immuabilité.** | [Object storage ObjectLock](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-manage-object-lock?id=kb_article_view&sysparm_article=KB0047404) |
| ACL et gestion avancée des autorisations | Gestion des droits via ACL S3, ou politiques spécifiques | S3 (ACL, politiques) | **Entrant** : Adaptation des permissions en fonction de la structure cible. **Sortant** : Export d'objets, mais reconfiguration d'ACL/de stratégies requise sur la plateforme de destination | [Gestion des accès](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-bucket-acl?id=kb_article_view&sysparm_article=KB0057089) |

**Fonctionnalités spécifiques**

| **Functionnalité** | **Description** | **Available formats** | **Migration model** | **Documentation available** |
| --- | --- | --- | --- | --- |
| Gestion via OVHcloud Manager / API OVH | Interface graphique et API propriétaires d’OVHcloud pour la gestion du stockage | N/A | **Entrant** : Non applicable. **Sortie** : Scripts/API à réécrire pour l'environnement cible. | [Manage-buckets](https://help.ovhcloud.com/csm/en-public-cloud-storage-s3-getting-started-object-storage?id=kb_article_view&sysparm_article=KB0047348) |

**Liste des architectures**

Object Storage 3-AZ by OVHcloud is based on a multi-AZ architecture, with automatic distribution of data to three physically separated availability zones (data centers several kilometers apart). This architecture uses erasure coding to ensure local redundancy and tolerance for loss of a complete zone, thus ensuring high availability (SLA 99.99%) and continuity of service even in the event of major outages. Asynchronous inter-region replication is available as an option (Offsite Replication), allowing automatic data backup to another 1-AZ OVHcloud region

**Services partenaires**

Les partenaires OVHcloud sont répertoriés avec le mot-clé â€oeCloud Migrationâ€  dans le [répertoire dédié](https://partner.ovhcloud.com/en/directory/).

**Coüts et frais**

Aucun frais de résiliation : Pas de sur facturation à l’usage. Le service est stoppé immédiatement après suppression du service.

**Conservation des données après résiliation du contrat**
Les données sont supprimées par action du client lui-même. OVHcloud ne conserve aucune donnée. Une exportation manuelle préalable est obligatoire pour préserver les données.

Un point d’attention concernant la feature ObjectLock. Plus d’informations à retrouver sur la documentation associée.

Une fois le service resilié par le client, OVHCloud libère les ressources qui étaient allouées.
