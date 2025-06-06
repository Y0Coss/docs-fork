---
titre : «Politique de réversbilité du produit Managed Document Database»
mise à jour : 2025-06-06
---

**Objectif**

Ce document décrit la politique de réversibilité de la gamme de produits Managed Document Database couvrant l'offre OVHcloud MongoDB.

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.

**Liste des fonctionnalités**

Les fonctionnalités du Produit sont réparties en trois catégories :

* Les principales fonctionnalités pour lesquelles nous vous garantissons la possibilité de migrer.
* OVHcloud est actuellement opérationnel et la migration nécessitera des adaptations à un nouvel environnement.
* Fonctionnalités spécifiées dont la migration en tant que telle est impossible à garantir car elles sont liées à l'environnement OVHcloud ou à des développements spécifiques.

**Caractéristiques principales**

| **Fonction** | **Description** | **Formats** **Disponible** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| Base de données orientée document | Stockage de données JSON/BSON flexible pour une grande évolutivité | BSON, JSON, CSV | **Entrant** : import via mongorestore/mongoimport ; **Sortant** : export via mongodump/mongoexport | [MongoDB documentation](https://docs.mongodb.com/) |
| Compatibilité Open-source MongoDB | Version standard de MongoDB sans modification, facilitant la portabilité | Standard MongoDB (CLI, API, outils) | **Entrant** : intégration directe; **Sortant** : export complet sans adaptation |[MongoDB](https://help.ovhcloud.com/csm/en-gb-documentation-public-cloud-databases-mongodb?id=kb_browse_cat&kb_id=574a8325551974502d4c6e78b7421938&kb_category=7165a1f6259c6110f0782e7048ecedec&spa=1)|
| Haute disponibilité | Jeux de réplicas assurant la redondance et la récupération automatique | N/A | **Entrant** : configuration des réplicas à l'import ; **Sortant** : export et déploiement sur un autre cluster | [Replication](https://docs.mongodb.com/manual/replication/)|
| Sauvegardes automatiques | Sauvegardes quotidiennes avec possibilité de restauration | Snapshots MongoDB | **Entrant** : restauration possible ; **Sortant :** téléchargement/exportation manuel requis | [MongoDB Backups] (docs/pages/public_cloud/public_cloud_databases/mongodb_06_howto_backup_restore)|

** Implémentation OVHcloud **

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| OVHcloud Dashboard | Interface de gestion et de monitoring des clusters MongoDB | N/A | **Entrant** : configuration initiale via l'interface ; **Sortant** : administration interrompue après résiliation | [MongoDB](https://help.ovhcloud.com/csm/en-gb-documentation-public-cloud-databases-mongodb?id=kb_browse_cat&kb_id=574a8325551974502d4c6e78b7421938&kb_category=7165a1f6259c6110f07787e&dec88e&8888e spa=1)|
| Monitoring intégré | Suivi des performances via des métriques dans l'interface | N/A | **Entrant** : configuration des alertes; **Sortant** : à reconfigurer dans un autre environnement | [MongoDB](https://help.ovhcloud.com/csm/en-gb-documentation-public-cloud-databases-mongodb?id=kb_browse_cat&kb_id=574a8325551974502d4c6e78b7421938&kb_category=7165a1f6259c6110f0782e7048ecedec&spa=1)|
| Sécurité réseau (ACL) | Filtrage IP, TLS/SSL, accès restreint par vRack | IP, TLS/SSL | **Entrant** : définition des règles de sécurité ; **Sortant** : configuration export | [MongoDB](https://help.ovhcloud.com/csm/en-gb-documentation-public-cloud-databases-mongodb?id=kb_browse_cat&kb_id=574a8325551974502d4c6e78b7421938&kb_category=7165a1f6259c6110f0782e7048ecedec&spa=1)|

**Caractéristiques particulières**

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| Réseau privé OVHcloud (vRack) | Connexion avec d’autres services OVHcloud en réseau privé | N/A | **Entrant** : config vRack; **Sortant** : fonctionnalité non transférable | [vRack](docs/pages/public_cloud/public_cloud_databases/databases_08_vrack) |
| Mises à jour gérées par OVHcloud | Versionning MongoDB par OVHcloud | N/A | **Entrant** : vérifier la compatibilité ; **Sortant** : migration sous la responsabilité du client | [MongoDB](https://help.ovhcloud.com/csm/en-gb-documentation-public-cloud-databases-mongodb?id=kb_browse_cat&kb_id=574a8325551974502d4c6e78b7421938&kb_category=7165a1f6259c6110f0782e7048ecedec&spa=1) |
| Anti-DDoS | L’anti-DDoS est un ensemble d’équipements et de moyens mis en place pour absorber les attaques par déni de service. Il comprend l'analyse du trafic, une somme de â€oeaspirationâ€  vers un réseau dédié et la mitigation, fournis par la technologie VAC développée par OVHcloud. | N/A | **Migration entrante** : Le système anti-DDoS fait partie de notre infrastructure et est activé par défaut. Aucune action n'est requise.   **Migration sortante** : Commandez et configurez un anti-DDoS chez le nouveau fournisseur. | [OVHcloudDDoS Protection](https://www.ovh.com/fr/anti-ddos/) |

** Liste des architectures**

Managed MongoDB repose sur une architecture distribuée avec des jeux de réplicas pour assurer une haute disponibilité. Les données sont réparties sur plusieurs nœuds grâce à des sauvegardes régulières, une surveillance continue et des outils de sécurité intégrés.

**Services partenaires**

Les partenaires OVHcloud sont répertoriés avec le mot-clé **Cloud Migration** dans le [répertoire dédié](https://partner.ovhcloud.com/fr/directory/).

OVHcloud dispose également d’un service dédié : [OVHcloud Professional Services](https://www.ovhcloud.com/fr/professional-services/)

**Coût et coûts**

Les fonctionnalités décrites dans les tableaux sont gratuites sauf mention contraire et sont librement utilisables par le client

La facturation est basée sur la taille du cluster, la capacité de stockage et les sauvegardes. Il n'y a pas de frais de sortie, mais les données doivent être exportées avant la résiliation car elles seront supprimées.

**Conservation des données après résiliation du contrat**

Après résiliation, toutes les données de l'instance sont définitivement supprimées, y compris les sauvegardes effectuées par OVHcloud. Il appartient au client de réaliser l’exportation avant la fin du service, OVHcloud ne conservant aucune copie.

OVHcloud ne garantit pas l’utilisation et la disponibilité des sauvegardes pour restaurer les données du client après la résiliation du service*.*

Les instances primaires sont immédiatement supprimées et les sauvegardes sont conservées entre 2 jours et 1 mois selon les options spécifiées dans le contrat.
