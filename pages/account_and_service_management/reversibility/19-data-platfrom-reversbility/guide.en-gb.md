**Politique de rÃ©versibilitÃ© du Produit Unified Data Platform (DATAP)**

**Objectif**

Ce document est la politique de rÃ©versibilitÃ© de la gamme de produits Unified Data Platform (DATAP)[.](https://www.ovhcloud.com/fr/enterprise/products/secnumcloud/)

Cette politique vise Ã  mettre en Å“uvre les principes gÃ©nÃ©raux de rÃ©versibilitÃ© et notre conformitÃ© avec le [Code de conduite SWIPO IaaS pour les fournisseurs de cloud](https://swipo.eu/download-section/copyrighted-downloads/).

**Liste des fonctionnalitÃ©s**

Les fonctionnalitÃ©s du Â«Â ProduitÂ Â» sont rÃ©parties en trois catÃ©gories :

*   Les [principales fonctionnalitÃ©s](https://help.ovhcloud.com/csm) pour lesquelles nous vous garantissons la possibilitÃ© de migrer.
*   La [mise en Å“uvre dâ€™OVHcloud](https://help.ovhcloud.com/csm) dont la migration nÃ©cessitera des adaptations Ã  un nouvel environnement.
*   Les fonctionnalitÃ©s spÃ©cifiques dont la migration en tant que telle est impossible Ã  garantir car elles sont liÃ©es Ã  l'environnement OVHcloud ou Ã  des dÃ©veloppements spÃ©cifiques

**Principales fonctionnalitÃ©s**

| FonctionnalitÃ© | Description | FormatsDisponible | ModÃ¨le de migration | Documentation disponible |
| --- | --- | --- | --- | --- |
| Data Catalog | IntÃ©gration de plus de 60 connecteurs pour centraliser les sources de donnÃ©es. | CSV, JSON, XML, Parquet, Avro, JDBC, Kafka, REST, FTP, etc. | Entrante : Configuration de connecteurs standard via interface web.Sortante : export des mÃ©tadonnÃ©es et donnÃ©es via API. | Data Catalog |
| Lakehouse Manager | Stockage unifiÃ© basÃ© sur Apache Iceberg et Trino. | Parquet, ORC, Avro, Iceberg | Entrante : Manuelle via interface web.Sortante : export via Trino, Spark, ou API. | Lakehouse Manager |
| Data Processing Engine | Orchestration de pipelines ETL/ELT avec Spark et Python. | Python, PySpark, | Entrante : manuelle via interface web ou connexion de repository git.Sortante : export des workflows via Git ou API. | Data processing engine |
| Analytics Manager | CrÃ©ation de tableaux de bord avec Ã©diteur no-code ou SQL (Trino). | SQL, JSON | Entrante : manuelle via interface web.Sortante : export des requÃªtes/visualisations via API. | Analytics Manager |
| Applications Services | DÃ©ploiement d'applications web et APIs (Node.js, Python, Docker). | Node.js, Python, Docker, REST | Entrante : Manuelle via interface web ou via repository git.Sortante : export via Git/API. | Applications services |

**ImplÃ©mentation OVHcloud**

| FonctionnalitÃ© | Description | Formats disponibles | ModÃ¨le de migration | Documentation disponible |
| --- | --- | --- | --- | --- |
| Data Processing Engine | Orchestration de pipelines ETL/ELT avec Spark et Python. | Format spÃ©cifique Ã  la plateforme OVH, pas de standard | Entrante : DonnÃ©es importÃ©es depuis data catalog avec configuration manuelle ou automatique des jobsSortante : Pas dâ€™export possible | Data processing engine |
| Gestion des identitÃ©s et des accÃ¨s | Gestion des comptes et accÃ¨s utilisateurs sur la data platform | N/A | EntranteÂ : configuration via lâ€™interface WebSortanteÂ : export des comptes utilisateurs au format CSV | DATAP IAM |
| Control Center | Gestion centralisÃ©e des performances et workflows. | N/A | Entrante : N/A (Pas de donnÃ©es importÃ©es)Sortante : Non exportable actuellement (Logs et infos de monitoring de la plateforme) | Control center |

**  
FonctionnalitÃ©s spÃ©cifiques**

| Fonction | Description | Formats disponibles | ModÃ¨le de migration | Documentation disponible |
| --- | --- | --- | --- | --- |
| API OVHcloud | Automatisation via API propriÃ©taires. | JSON | Entrante : CrÃ©ation du serviceSortante : Pas dâ€™export de donnÃ©e | API OVH |
| Monitoring intÃ©grÃ© | Outils de surveillance OVHcloud intÃ©grÃ©s. | N/A | Entrante : N/A (Pas de donnÃ©es importÃ©es)Sortante : Non exportable actuellement (Logs et infos de monitoring de la plateforme) | Control center |

**Liste des architectures**

Le service OVHcloud Unified Data Platform repose sur des technologies open source comme Trino, Apache Iceberg, et Kubernetes. Il est compatible avec les architectures Cloud public OVHcloud.

**Services partenaires**

Les partenaires OVHcloud sont rÃ©pertoriÃ©s avec le mot clÃ© Â« Cloud Migration Â» dans le [rÃ©pertoire dÃ©diÃ©](https://partner.ovhcloud.com/fr/directory/).

OVHcloud dispose Ã©galement dâ€™un service dÃ©diÃ©Â : [Les Professional Services dâ€™OVHcloud](https://www.ovhcloud.com/fr/professional-services/)

**CoÃ»t et frais**

Les fonctionnalitÃ©s dÃ©crites dans les tableaux sont disponibles sans couts et frais sauf mentions contraires, et sont librement utilisables par le client.

OVHcloud applique une tarification Ã  lâ€™usage, sans frais de sortie ni pÃ©nalitÃ©. La facturation est interrompue immÃ©diatement Ã  la suppression des services, permettant un contrÃ´le souple des coÃ»ts

**Conservation des donnÃ©es aprÃ¨s rÃ©siliation du contrat**

Une fois le service rÃ©siliÃ©, toutes les donnÃ©es du client sont supprimÃ©es de maniÃ¨re irrÃ©versible. Il incombe au client de rÃ©aliser une sauvegarde ou migration complÃ¨te avant rÃ©siliation.
