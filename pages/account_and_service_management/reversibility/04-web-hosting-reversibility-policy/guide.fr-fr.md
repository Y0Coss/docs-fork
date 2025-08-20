---
title: Politique de réversibilité du produit Managed Web Hosting
updated: 2025-08-20
---

## Objectif

Ce document est la politique de réversibilité du produit Managed Web Hosting couvrant l’offre commerciale d’OVHcloud Hébergement Web.

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.


## Liste des fonctionnalités

Les fonctionnalités du produit sont réparties en trois catégories :

1. Les **fonctionnalités principales** pour lesquelles nous garantissons la capacité de migration.
2. Les **implémentation OVHcloud** qui nécessitent une adaptation à un nouvel environnement de migration.
3. Les **fonctionnalités spécifiques** qui ne peuvent pas être garanties pour la migration car elles sont liées à l'environnement OVHcloud ou impliquent des développements personnalisés.

### 1. Fonctionnalités principales

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| Package hébergement web standard | Utilisation de composants open source standards : Linux, Apache, MySQL/MariaDB, PHP | SQL, PHP, HTML, JSON, CSV | **Entrante** : copie des fichiers applicatifs, import des bases de données via dump SQL <br>**Sortante** : export des fichiers de données client/dumps de base de données, réutilisables sur tout environnement compatible | [Comment créer un serveur webb Debian ou Ubuntu](/pages/bare_metal_cloud/dedicated_servers/installing_lamp_debian9_ubuntu18) |
| Import et export de fichiers applicatifs | Transfert des fichiers web (PHP, HTML, assets) via FTP/SFTP et rsync pour les offres pro et performance | Tous formats de fichiers  | **Entrante** : chargement direct des fichiers <br>**Sortante** : export direct des fichiers pour migration vers tout autre hébergeur | [Exporter son site web](/pages/web_cloud/web_hosting/exporter-son-site-web) |
| Accès SSH/SFTP à l’environnement client | Accès simple utilisateur à son l’environnement pour transfert de fichiers et automatisation | Fichiers, scripts, dumps | **Entrante** : transfert des fichiers applicatifs, dumps SQL, scripts via FTP/SFTP et rsync/scp/SSH pour les offres pros et performance <br>**Sortante** : Export des fichiers, dumps, scripts via FTP/SFTP et rsync/scp/SSH pour les offres pros et performance vers tout autre hébergeur| [Exporter son site web](/pages/web_cloud/web_hosting/exporter-son-site-web) |


### 2. Implémentations OVHcloud

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |
|Modules en un clic|Installation automatisée de CMS (WordPress, PrestaShop, Joomla!, Drupal)|N/A|**Migration entrante**: Non applicable<br><br>**Migration sortante**: Une fois le module en un clic installé, suivez la procédure de migration standard du site Web (y compris la migration de la base de données)|**Migration sortante**: Voir "Hébergement Web" ci-dessus.|
|Sauvegardes automatiques|Sauvegardes automatisées des sites Web et des bases de données|N/A, restaurez une sauvegarde pour exporter son contenu|**Migration entrante**: Les sauvegardes sont automatiquement activées.<br><br>**Migration sortante**: Activez un plan de sauvegarde avec le nouvel hébergeur après la migration du site.<br><br>Il n'est pas possible d'exporter une sauvegarde en tant que telle : les sauvegardes sont internes et ne sont pas présentées comme un fichier ou une archive. Pour importer le contenu d'un serveur de fichiers (FTP) et d'une base de données, **restaurez la sauvegarde, puis exportez le site Web** comme indiqué ci-dessus.|**Migration entrante**: Voir « Hébergement Web » ci-dessus.<br><br>**Migration sortante**: Voir « Hébergement Web » ci-dessus.|
|Journalisation|Conservation et consultation des logs du site Web. Analyse et représentation graphique de ces logs avec l'application Urchin WebAnalytics.|Texte brut avec un format de logs Apache standard|**Migration entrante**: Non applicable - les logs de l'infrastructure précédente ne sont pas pertinents pour un autre.<br><br>**Migration sortante**: Téléchargez les fichiers de logs à partir de votre [esapce client OVHcloud](/links/manager)|**Migration entrante**: N/A<br><br>**Migration sortante**: [Exportation d'un site Web - récupération des logs](/pages/web_cloud/web_hosting/exporter-son-site-web#etape-3-recuperer-les-logs-de-votre-hebergement-ovhcloud)|
|Planification des tâches |Exécution de tâches automatisées périodiques (cron)|N/A|**Migration entrante**: Les scripts ne sont pas importés tels quels. Récupérez les anciens scripts ou leur structure et réimplémentez-les sur l'hébergement OVHcloud via votre [espace client OVHcloud](/links/manager).<br><br>**Migration sortante**: Les scripts ne sont pas exportés tels quels. Récupérez la structure des scripts dans votre [espace client OVHcloud](/links/manager) et réimplémentez-les dans l'environnement cible.|**Migration entrante et sortante**: [Utilisation de tâches automatisées sur un hébergement Web](/pages/web_cloud/web_hosting/cron_tasks)|

### 3. Fonctionnalités spécifiques

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |
|Pare-feu applicatif|Module serveur HTTP pour le filtrage du contenu Web entrant et sortant|N/A|**Migration entrante**: Activation du pare-feu à partir de votre [espace client OVHcloud](/links/manager).<br><br>**Migration sortante**: Commandez et configurez un pare-feu avec le nouvel hébergeur|**Migration entrante**: [Activation du pare-feu applicatif](/pages/web_cloud/web_hosting/multisites_activating_application_firewall)<br><br>**Migration sortante**: N/A|
| Anti-DDoS | L’anti-DDoS est un ensemble d’outils et de mécanismes conçus pour absorber les attaques par déni de service. Il comprend l'analyse du trafic, le « nettoyage » via un réseau spécialisé et la mitigation grâce à la technologie VAC développée par OVHcloud. | N/A | **Entrant** : le système anti-DDoS fait partie de notre infrastructure et est activé par défaut. Aucune action n'est requise. <br> **Sortant** : commande et configuration un anti-DDoS chez le nouveau fournisseur. | [OVHcloud DDoS Protection](/links/security/antiddos) |

### Liste des architectures

Tous les composants d'un produit Web OVHcloud sont accessibles via votre [espace client OVHcloud](/links/manager). Cela permet de visualiser et de gérer les serveurs Web front-end, les serveurs de fichiers (FTP), les bases de données, les noms de domaine, les e-mails, ... ainsi que les fonctions associées à ces composants.

### Services Partenaires

Les partenaires OVHcloud concernés figurent dans l'annuaire des [partenaires OVHcloud](/links/partner) sous les mots-clés « **Data center expansion and Migration** ».

OVHcloud dispose également d’un service dédié : [OVHcloud Professional Services](/links/professional-services).


### Coût et frais

Aucune facturation supplémentaire n'est prévue à partir d'OVHcloud pour les fonctionnalités de migration répertoriées ici.

### Conservation des données après la résiliation du contrat

Les données sont conservées 45 jours après la fin du service, puis supprimées définitivement.
