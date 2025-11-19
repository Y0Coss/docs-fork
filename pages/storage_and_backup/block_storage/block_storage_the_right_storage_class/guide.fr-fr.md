---
title: Choisir la bonne classe de Block Storage
excerpt: Découvrez comment choisir la bonne classe de Block Storage OVHcloud. Comparez performances, coûts et cas d’usage pour optimiser votre stockage en termes de prix et d’efficacité.
updated: 2025-11-24
---

## Objectif

Ce guide vous aide à comprendre les différentes classes de Block Storage OVHcloud et à choisir celle qui correspond le mieux à vos besoins. Vous apprendrez à connaître les niveaux de performance, les considérations tarifaires et les cas d’usage recommandés afin de prendre des décisions de stockage éclairées.

## Présentation du Block Storage

Le Block Storage est une solution de stockage performante, flexible et fiable, conçue pour les workloads critiques. Vous pouvez attacher des volumes directement à vos instances, augmenter la capacité de 10 Go à 12 To, et choisir la classe appropriée : Regional Classic, Classic ou High Speed, selon vos besoins en performance et disponibilité.

Cette solution est idéale pour les bases de données, les machines virtuelles et les applications conteneurisées, avec des fonctionnalités telles que snapshots, sauvegardes et chiffrement.

## Classes Block Storage

Nos classes Block Storage sont conçues pour répondre à différents besoins de vos workloads, en termes de performance, disponibilité et résilience. Choisissez la classe adaptée pour optimiser vitesse, redondance et coût.

### Regional Classic Volume

La classe Regional Classic Volume offre une haute disponibilité en répliquant automatiquement les données sur trois zones de disponibilité (3-AZ) au sein d’une même région. Les volumes reposent sur des disques NVMe over Fabric, garantissant un accès rapide et fiable.

Cette classe est adaptée aux workloads nécessitant une haute disponibilité et une forte résilience, comme les bases de données critiques et les applications distribuées.

### Classic Volume

La classe Classic Volume est idéale pour les besoins applicatifs quotidiens, tels que les bases de données, les machines virtuelles et les sauvegardes. Les données sont répliquées au sein d’une seule zone de disponibilité (1-AZ) ou d’une Local Zone, avec des performances NVMe garanties.

Cette classe convient aux workloads standards où la faible latence et la fiabilité sont importantes, mais où la réplication multi-zone n’est pas nécessaire.

### High Speed Volume

La classe High Speed Volume est proposée en deux générations, offrant des profils de performance différents :

- Gen 1 : jusqu’à 3 000 IOPS et 128 Mo/s – adaptée aux workloads nécessitant une vitesse élevée standard.
- Gen 2 : 30 IOPS/Go (maximum 20 000 IOPS) et 0,5 Mo/s par Go (maximum 320 Mo/s) – recommandée pour les applications intensives nécessitant un maximum d’IO et de débit.

Choisissez Gen 1 pour les workloads haute vitesse classiques, et Gen 2 pour les workloads lourds tels que l’analytique, les grandes bases de données ou le calcul haute performance.

### Tableau comparatif

| Classe de stockage | Cas d’usage | Performance | Régions disponibles | SLA de disponibilité | Réplication | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| **High Speed Volume** | Workloads haute performance, analytique, grandes bases de données | Gen 1 : jusqu’à 3 000 IOPS, 128 Mo/s </br> Gen 2 : 30 IOPS/Go (max 20 000 IOPS), 0,5 Mo/s par Go (max 320 Mo/s) | 3-AZ, 1-AZ, Local Zones | 99,9% | Zonale | NVMe optimisé, performance évolutive |
| **Regional Classic Volume** | Applications critiques, systèmes distribués | 500 IOPS garantis, 64 Mo/s | 3-AZ | 99,99% | Multi-zone | NVMe over Fabric, haute disponibilité |
| **Classic Volume** | Workloads quotidiens, VMs, sauvegardes | 500 IOPS garantis, 64 Mo/s | 1-AZ, Local Zones  | 99,9% | Zonale | NVMe over Fabric, performance standard |

### Détails supplémentaires

#### Durée minimale de stockage

Pour le Block Storage, il n’existe pas de durée minimale de stockage : vous pouvez attacher ou supprimer des volumes à tout moment sans frais supplémentaires. Vous êtes facturé uniquement pour l’utilisation effective du volume pendant la période où il existe.

#### Frais de snapshots et de sauvegardes

Bien que l’utilisation standard des volumes soit facturée par Go/mois, les [snapshots](/pages/public_cloud/compute/creating_a_volume_snapshot) et les [sauvegardes](/pages/public_cloud/compute/volume-backup) stockés sur Object Storage peuvent générer des coûts supplémentaires. Les snapshots permettent de capturer l’état d’un volume à un instant donné, et les sauvegardes assurent la protection et la récupération des données.

#### Gestion du cycle de vie et redimensionnement

Les volumes Block Storage sont entièrement flexibles : vous pouvez [augmenter leur taille](/pages/public_cloud/compute/increase_the_size_of_an_additional_disk) à tout moment, étendre les partitions et attacher les volumes à différentes instances. Ces opérations sont gérées au niveau du volume, vous permettant d’optimiser capacité et performance sans interruption.

#### Volumes chiffrés

Chaque type de volume Block Storage est également disponible en version chiffrée (LUKS). Ces volumes garantissent la confidentialité des données sans impact sur les performances.

Les volumes chiffrés peuvent être créés directement depuis l’espace client OVHcloud ou via les outils CLI/API en précisant le type de volume avec le suffixe `-luks` (par exemple classic-luks ou highspeed-luks). Cela permet de protéger facilement les données sensibles tout en conservant les mêmes performances et fonctionnalités que les volumes standards.

> [!primary]
>
> Les volumes chiffrés n’ont aucun impact sur les performances
>

## Cas d’usage

Le Block Storage prend en charge une grande variété de workloads grâce à ses performances, sa flexibilité et sa résilience. Les cas d’usage courants incluent :

- **Bases de données :** MySQL, PostgreSQL et autres bases relationnelles bénéficient d’un accès rapide avec faible latence et haut débit.
- **Machines virtuelles et applications conteneurisées :** Stockage persistant pour les VMs et conteneurs avec fiabilité élevée et accès rapide.
- **Analytique et workloads IA :** Les volumes High Speed offrent un maximum d’IOPS et de débit pour les applications intensives en données.
- **Sauvegarde et reprise après sinistre :** Créez facilement des snapshots et des sauvegardes pour vos données critiques, garantissant une récupération rapide et sécurisée.

## Considérations sur les zones et la région

Les volumes Block Storage peuvent être déployés avec différentes options de disponibilité selon vos besoins :

- **Regional Classic Volume (3-AZ):** Data is replicated across three availability zones in the same region, providing high resilience and SLA of 99.99%. Ideal for critical, highly available applications. See our guide [Proper Usage and Limitations of Classic Multi-Attach Block Storage in 3AZ Regions](/pages/public_cloud/compute/classic_block_multi_az_limitations).
- **Classic & High Speed Volume (1-AZ or Local Zone):** Data is replicated within a single zone. These options provide low-latency access and high performance, suitable for workloads that do not require multi-zone redundancy.
- **Local Zones:** For applications needing ultra-low latency in a specific geographic location, Local Zones allow you to keep storage close to compute resources.

- **Regional Classic Volume (3-AZ) :** Les données sont répliquées sur trois zones de disponibilité au sein d’une même région, offrant une haute résilience et un SLA de 99,99 %. Idéal pour les applications critiques et très disponibles. Voir notre guide [Utilisation correcte et limitations du stockage Classic Multi-Attach dans les régions 3AZ](/pages/public_cloud/compute/classic_block_multi_az_limitations).
- **Classic & High Speed Volume (1-AZ ou Local Zone) :** Les données sont répliquées dans une seule zone. Ces options offrent un accès à faible latence et de hautes performances, adaptées aux workloads ne nécessitant pas de redondance multi-zone.
- **Local Zones :** Pour les applications nécessitant une latence ultra-faible dans une localisation géographique précise, les Local Zones permettent de conserver le stockage proche des ressources de calcul.

Choisir la bonne option de déploiement garantit des performances optimales, la redondance et une efficacité des coûts adaptée à votre workload et à vos besoins géographiques.

## Aller plus loin

Si vous avez besoin de formation ou d’assistance technique pour mettre en œuvre nos solutions, contactez votre représentant commercial ou cliquez sur [ce lien](/links/professional-services) pour obtenir un devis et demander l’aide des experts de nos Professional Services pour votre cas d’usage spécifique.

[Créer et configurer un disque additionnel sur une instance](/pages/public_cloud/compute/create_and_configure_an_additional_disk_on_an_instance)

[Modifier un Volume Block Storage](/pages/public_cloud/compute/switch_volume_type)

Échangez avec notre [communauté d'utilisateurs](/links/community).