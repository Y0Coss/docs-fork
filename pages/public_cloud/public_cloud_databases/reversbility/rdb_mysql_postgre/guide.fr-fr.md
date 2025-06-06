---
Titre : « Politique de reversibilité du produit Managed Relational Database »
mise à jour : 2025-06-06
---

## Objectif

Ce document présente la politique de réversibilité du produits Managed Relational Database couvrant les offres OVHcloud : Managed MySQL et Managed PostgreSQL .

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.



## Liste des fonctionnalités

Les caractéristiques du produit sont réparties en trois catégories :

- **Fonctionnalités principales** pour lesquelles nous garantissons la capacité de migration.
- **Implémentations OVHcloud** qui nécessitent une adaptation à un nouvel environnement de migration.
- **Fonctionnalités spécifiques** qui ne peuvent pas être garanties pour la migration car elles sont liées à l'environnement OVHcloud ou impliquent des développements personnalisés.



## Fonctionnalités principales

| Fonction                  | Description                                  | Formats       | Modèle de migration                                                                                                                                           | Documentation disponible |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| **Export/Import - PostgreSQL** | Use of `pg_dump`/`pg_restore` for native data transfer.                                                       | SQL, CSV, BINAIRE     | **Entrant** : Restauration via CLI avec ajustement des droits. <br> **Sortant** : Exportation du dump standard.                     | [OVH - How to Migrate](https://support.us.ovhcloud.com/hc/en-us/articles/21485451623059-PostgreSQL-Tutorial-How-to-Migrate-an-On-Premises-Database-to-Cloud-Databases)                      |
| **Export/Import - MySQL**      | Exportez et importez à l'aide des outils MySQL natifs (`mysqldump`, `mysql`, etc.).                                      | SQL, CSV             | **Entrant** : Exportez depuis la source (SQL dump), puis importez dans Managed MySQL via `mysql` ou l'interface utilisateur OVHcloud. <br> **Sortant** : SQL dump via `mysqldump`, puis importez dans l'environnement cible (cloud ou on-premises). | [MySQL - Capabilities and Limitations](https://support.us.ovhcloud.com/hc/en-us/articles/20887483746067-MySQL-Capabilities-and-Limitations)                      |
| **Accès au service - MySQL**     | Accès à la base de données via le protocole MySQL standard sur un port dynamique mis à disposition dans le Manager OVHcloud.   | N/A                  | **Entrant** : Connexion à partir d'outils ou d'applications existants. <br> **Sortant** : Connectez-vous à partir de n’importe quel client MySQL standard pour l’extraction ou la migration des données. | [MySQL - Se connecter en ligne de commande (CLI)](https://support.us.ovhcloud.com/hc/en-us/articles/20805146473875-MySQL-Connect-with-CLI)<br>[MySQL - Se connecter à PHP](https://support.us.ovhcloud.com/hc/en-us/articles/20815696722963-MySQL-Connect-with-Python-<Pyps>[MySQL](Connect-with-SQL)://support.us.ovhcloud.com/hc/en-us/articles/20840434483219-MySQL-Connect-with-Python)<br>[MySQL - Connect with MySQL Workbench](https://support.us.ovhcloud.com/hc/en-us/articles/20845437747987-MySQL-Connect-with-MySQL-Workbench)|
| **Service Access - PostgreSQL**| Accès via le protocole PostgreSQL, compatible avec les clients et outils standards.                                    | N/A                  | **Entrant** : Connexion directe depuis les outils/applications existants. <br> **Sortant** : Connexion standard pour l'extraction ou la migration. | [PostgreSQL - Connect via Command Line (CLI)](https://support.us.ovhcloud.com/hc/en-us/articles/21410499182995-PostgreSQL-Connect-with-CLI)<br>[PostgreSQL - Connect with PHP](https://support.us.ovhcloud.com/hc/en-us/articles/20898939497107-gre-Connect with PostgreSQL<PostgreSQL>) SQL - Connect with Python](https://support.us.ovhcloud.com/hc/en-us/articles/21408187602451-PostgreSQL-Connect-with-Python)<br>[PostgreSQL - Connect with pgAdmin](https://support.us.ovhcloud.com/hc/en-us/articles/21489279019155-PostgreSQL-Connect-with-Python)|
| **Sauvegarde manuelle**              | Possibilité de générer une sauvegarde complète de la base de données à la demande.                                                          | SQL, CSV, tar        | **Entrant** : Restaurer à partir du vidage SQL existant. <br> **Outgoing** : dump SQL généré depuis l’instance OVHcloud, utilisable sur tout environnement MySQL compatible. | [dump MySQL](https://dev.mysql.com/doc/refman/8.4/fr/mysqldump.html)                |


## Implémentation OVHcloud

| Fonction         | Description                                                                                                       | Formats disponibles | Modèle de migration                                                                                                                          | Documentation disponible |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| **Sauvegardes automatiques OVHcloud**   | Sauvegardes gérées par OVHcloud, non directement exportables en dehors de l'écosystème OVH.                                          | Snapshots internes | **Entrant** : Non applicable à l'importation directe. <br> **Sortant** : Nécessite une restauration sur l'instance OVHcloud, puis une exportation manuelle (dump SQL) pour la migration. | [Databases & Analytics - Sauvegardes automatisées](https://support.us.ovhcloud.com/hc/en-us/articles/20735484294547-Databases-Analytics-Automated-backups)     |
| **Point in Time Recovery (PITR)**| Restaurer à un instant précis à l'aide de snapshots internes OVHcloud.                                                   | Snapshots internes | **Entrant** : Non applicable à l'importation directe, restauration préalable requise. <br> **Sortant** : Exportez le snapshot restauré en tant que dump SQL, puis importez manuellement dans l'environnement cible. | [Databases & Analytics - Sauvegardes automatisées](https://support.us.ovhcloud.com/hc/en-us/articles/20735484294547-Databases-Analytics-Automated-backups)     |
| **API OVHcloud**                 | Gestion des bases de données via API REST ou interface graphique OVHcloud.                                                           | N/A                | **Entrant** : Création et importation automatisées d'instances. <br> **Sortant** : Export de données via API ou scripts de dump automatisés. |[Premiers pas avec les API OVHcloud](https://help.ovhcloud.com/csm/fr-api-getting-started-ovhcloud-api?id=kb_article_view&sysparm_article=KB0042789)     |
| **Regroupement des connexions OVHcloud** | Regroupement automatique des connexions PostgreSQL, non directement portable.                                                          | N/A                | **Entrant** : Peut nécessiter une adaptation en fonction de la configuration de la source. <br> **Sortant** : Le pooling doit être reconfiguré sur l’infrastructure cible. | [PostgreSQL - Create and Use-Connection-Pools](https://support.us.ovhcloud.com/hc/en-us/articles/21419624594323-PostgreSQL-Create-and-Use-Connection-Pools)                |
| **Observabilité**               | Collecte de métriques via Prometheus intégré à OVHcloud.                                                                   | Métriques Prometheus | **Entrant** : Adapter les tableaux de bord et métriques à l’environnement OVHcloud. <br> Sortant : exportation possible des métriques, nécessite une adaptation sur une nouvelle plateforme de monitoring. | [MySQL - Capabilities and Limitations](https://support.us.ovhcloud.com/hc/en-us/articles/20887483746067-MySQL-Capabilities-and-Limitations)<br>[PostgresSQL â€« Capabilities and Limitations »](https://support.us.ovhcloud.com/hc/en-us/articles/21485451623059-PostgreSQL-Tutorate-On-Tutorate-How mises-Database-to-Cloud-Databases     |
| **vRack**                          | La baie virtuelle (vRack) est une technologie de VLAN privé qui relie les services OVHcloud.                           | N/A                   | **Entrant** Les services MySQL et PostgreSQL sont inclus par défaut dans le vRack. <br> **Sortant:** Enregistrez l’architecture réseau et répliquez-la à l’aide de VLAN.               | [V(x)LAN creation](https://help.ovhcloud.com/csm/fr-vmware-vlan-creation?id=kb_article_view&sysparm_article=KB0045480)<br>[Public Cloud Databases](https://help.ovhcloud.com/csm/fr-public-cloud-databases-configure-vrack?id=kb_article_view&sysparm_article=KB0048824) |
| **Adaptation des rôles et des autorisations**| Aucun superutilisateur (par exemple, `postgres`) ; les rôles doivent être adaptés à `avnadmin` ou équivalent.                                     | N/A                | **Entrant** : Modifiez le dump pour remplacer les rôles superuser par des rôles compatibles OVH. <br> **Sortant** : Adaptation inverse basée sur les privilèges de l’environnement cible. | [PostgresSQL â€« Capacités et limitations](https://support.us.ovhcloud.com/hc/en-us/articles/21485451623059-PostgreSQL-Tutorial-How-to-Migrate-an-On-Premises-Database-to-Cloud-Databases)                |
| **Gestion des ACL OVHcloud**      | Droits d’accès gérés via l’interface OVHcloud.                                                                       | N/A                | **Entrant** : Recréez manuellement des règles dans l'interface OVHcloud. <br> **Sortant** : Convertissez les règles ACL au nouveau format providerâ€™s. | [MySQL - Capabilities and Limitations](https://support.us.ovhcloud.com/hc/en-us/articles/20887483746067-MySQL-Capabilities-and-Limitations)<br>[PostgresSQL â€« Capabilities and Limitations »](https://support.us.ovhcloud.com/hc/en-us/articles/21485451623059-PostgreSQL-Tutorate-On-Tutorate-How mises-Database-to-Cloud-Databases     |


## Fonctionnalités spécifiques

| Fonction               | Description                                                                           | Formats disponibles | Modèle de migration                                                                                   | Documentation disponible |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| **Database Forking OVHcloud**    | Duplication instantanée d’une base de données via la fonctionnalité native « fork » d’OVHcloud.                                                  | interne OVHcloud   | **Entrant** : fonctionnalité non disponible pour l'importation. <br> **Sortant** : non portable â€ » nécessite l’exportation manuelle de données pour pouvoir être répliqué ailleurs. | [Databases & Analytics - Restore a backup](https://support.us.ovhcloud.com/hc/en-us/articles/20584170298515-Databases-Analytics-Restore-a-backup) |
| **Infrastructure as Code** | Déploiement automatisé via les modules Terraform spécifiques à OVHcloud                           | N/A                | **Entrant:** Les scripts doivent être adaptés pour d'autres fournisseurs. <br> **Résultat :** Réécriture de la configuration requise pour Terraform.                             | [Terraform](https://registry.terraform.io/providers/ovh/ovh/latest/docs)                      |
| **Mises à jour gérées par OVHcloud**     | Le versionnage et les mises à jour MySQL ou PostgreSQL sont gérés par OVHcloud.                                                     | N/A                 | **Entrant** : assurez la compatibilité. <br> **Sortant** : la responsabilité de la migration incombe au client.                | [MySQL - Capabilities and Limitations](https://support.us.ovhcloud.com/hc/en-us/articles/20887483746067-MySQL-Capabilities-and-Limitations)<br>[PostgresSQL â€« Capabilities and Limitations »](https://support.us.ovhcloud.com/hc/en-us/articles/21485451623059-PostgreSQL-Tutorate-On-Tutorate-How mises-Database-to-Cloud-Databases     |
| **Anti-DDoS** | L’anti-DDoS est un ensemble d’outils et de mécanismes conçus pour absorber les attaques par déni de service. Il comprend l'analyse du trafic, le « nettoyage » via un réseau spécialisé et la mitigation grâce à la technologie VAC développée par OVHcloud.                                                  | N/A                | **Entrant :** Le système anti-DDoS fait partie de notre infrastructure et est activé par défaut. Aucune action n'est requise. <br> **Sortant:** Commander et configurer un service anti-DDoS chez le nouveau fournisseur.             | [Protection anti-DDoS](https://www.ovh.com/fr/anti-ddos/)<br>[Technologie anti-DDoS](https://www.ovh.com/fr/anti-ddos/technologie-anti-ddos.xml)                        |



## Liste des architectures

**Managed MySQL et Managed PostgreSQL** prennent en charge différentes architectures en fonction du niveau de service sélectionné.
Les plans **Business** et **Enterprise** offrent **haute disponibilité** avec plusieurs nœuds et **réplication asynchrone automatique**.



## Services Partenaires

Les partenaires OVHcloud sont répertoriés sous le mot-clé **« Migration vers le cloud »** dans l'annuaire des partenaires dédiés.

OVHcloud propose également un service dédié : [**OVHcloud Professional Services**](https://www.ovhcloud.com/fr/professional-services/).



## Coût et frais

- **Pas de frais de résiliation** : Il n'y a pas de frais supplémentaires liés à la migration des données par défaut.
- La facturation s'arrête dès la résiliation du service.



## Conservation des données après résiliation du contrat

OVHcloud **ne conserve aucune donnée** après la suppression d'un cluster Managed Data Visualization.
**Les snapshots automatiques et manuels sont supprimés définitivement**.
Une **exportation manuelle** doit être effectuée à l'avance si des données doivent être préservées.
Les instances primaires sont **supprimées immédiatement** et les **sauvegardes sont conservées pendant une période allant de 2 jours à 1 mois**
> **Important :** Les clients ne peuvent pas compter sur ces sauvegardes pour la restauration des données.
> OVH ne garantit pas la facilité d’utilisation ou la disponibilité des sauvegardes pour la restauration des données du client après la résiliation du service.


