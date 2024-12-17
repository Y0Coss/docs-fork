---
title: "Comparaison et résilience des modes de déploiement - Comprendre les zones 3-AZ / 1-AZ / locales"
excerpt: "Découvrez les modes de déploiement d'OVHcloud"
updated: 2024-12-18
---

<style>
details>summary {
    color:rgb(33, 153, 232) !important;
    cursor: pointer;
}
details>summary::before {
    content:'\25B6';
    padding-right:1ch;
}
details[open]>summary::before {
    content:'\25BC';
}
</style>

## Objectif

OVHcloud propose plusieurs modes de déploiement pour son service, comme avec les [Compute instances](/links/public-cloud/compute), [S3 Object Storage](/links/public-cloud/object-storage), [Containers & Orchestration](/links/public-cloud/kubernetes), chacun adapté à des besoins spécifiques en matière de résilience, de disponibilité, de performance et de latence. Ce document fournit une explication détaillée des caractéristiques de chaque mode de déploiement (1-AZ, 3-AZ, Local Zones), expliquant les avantages et les limites de chacun.

En proposant une comparaison claire et détaillée, ce guide permettra aux utilisateurs de prendre une décision éclairée en fonction de leurs priorités spécifiques, qu'il s'agisse d'assurer une haute disponibilité pour les applications critiques, de minimiser les coûts tout en offrant une tolérance aux pannes, ou de répondre aux exigences de conformité locale et de latence ultra-faible.

En outre, nous mettrons en évidence les défis concrets auxquels les utilisateurs peuvent être confrontés, tels que l'impact sur la continuité des activités, l'évolutivité des services et la gestion des coûts dans chaque mode de déploiement. Ce guide est particulièrement utile pour les architectes cloud, les responsables informatiques et les développeurs qui cherchent à optimiser leur infrastructure en fonction de besoins commerciaux et techniques spécifiques.

## Concepts

OVHcloud fournit une infrastructure robuste et adaptable, conçue pour répondre à une grande variété de cas d'utilisation grâce à des modes de déploiement qui équilibrent la rentabilité, la redondance et la tolérance aux pannes. Cette flexibilité s'étend à l'ensemble du portefeuille de services d'OVHcloud, permettant aux clients de personnaliser les solutions pour répondre à leurs besoins spécifiques.

1. **Région 1-AZ**: Idéal pour les charges de travail générales telles que le stockage, la sauvegarde ou les applications pour lesquelles l'optimisation des coûts est la priorité. Ces régions fournissent une base solide de résilience avec un déploiement à zone unique, en équilibrant la fiabilité et la performance.
2. **Région 3-AZ**: Conçu pour les applications critiques exigeant une haute disponibilité et la pérennité des données. Grâce à la réplication sur trois zones de disponibilité, ce mode minimise les risques de temps d'arrêt et assure la continuité même en cas de perturbations majeures.
3. **Local Zones**: Parfaits pour les cas d'utilisation exigeant une faible latence et une conformité géographique. En hébergeant l'infrastructure au plus près des utilisateurs finaux, les zones locales permettent des performances transparentes pour l'informatique de pointe, les jeux et la diffusion de contenu.

Les principes de résilience et de tolérance aux pannes observés dans ces modèles de déploiement s'étendent à l'ensemble des services d'OVHcloud, notamment :

- **Instances** : Elles offrent des options de basculement et de mise à l'échelle dans des configurations à zone unique ou à zones multiples afin de correspondre aux niveaux de redondance requis par votre charge de travail.
- **Bases de données** : Prise en charge de la haute disponibilité avec des configurations distribuées à travers des régions ou des zones pour les applications critiques.
- **Réseau** : Assurer la connectivité par le biais de divers itinéraires et de mécanismes de reprise après sinistre pour un accès ininterrompu.
- **Conteneurs et orchestrations** : Assurer la résilience des clusters avec des déploiements multizones, en garantissant des performances constantes et l'isolation des pannes.

## Modes de déploiement

> [!primary]
>
> OVHcloud propose plusieurs modes de déploiement régionaux, chacun d'entre eux étant conçu pour répondre aux diverses exigences des entreprises en fournissant différents niveaux de redondance, de tolérance aux pannes et de distribution géographique. Ces modes de déploiement garantissent la flexibilité, l'évolutivité et la résilience de tous les services OVHcloud, permettant ainsi aux clients d'aligner leur infrastructure sur leurs priorités opérationnelles :

### Région 1-AZ

#### Infrastructure et redondance

Une région 1-AZ consiste en une **zone de disponibilité unique qui s'étend sur plusieurs centres de données au sein de la même région**, utilisant une conception de redondance 2N+1. Cette configuration garantit la résilience contre les défaillances des baies de serveurs et des disques, mais elle est vulnérable à une panne complète du centre de données. Alors que les services et les données sont protégés contre les défaillances matérielles locales (par exemple, les problèmes de serveur ou de disque), une panne complète du centre de données peut avoir un impact sur la disponibilité des services, même si les autres centres de données de la même zone de disponibilité restent opérationnels.

#### Caractéristiques

- **Erasure Coding :** met en œuvre des mécanismes tels que la réplication ou l'erasure coding (en fonction du service) pour assurer la continuité en cas de défaillance matérielle. Les données sont réparties sur plusieurs serveurs et unités de stockage au sein de la zone de disponibilité afin d'atténuer l'impact de problèmes localisés.
- **Coût optimisé :** Ce modèle de déploiement est économique et idéal pour les charges de travail générales, les environnements de développement et les sauvegardes. Il donne la priorité à l'accessibilité financière par rapport à la tolérance aux pannes améliorée fournie par les configurations multi-AZ.

#### Limites

- **Risque de panne :** Si un centre de données subit une panne, les données ou les services peuvent devenir indisponibles, en particulier si le centre de données affecté héberge des services critiques. Toutefois, la redondance est maintenue dans la zone de disponibilité pour les pannes matérielles.

> [!success]
>
>  Pour améliorer la résilience des applications critiques dans une région 1-AZ, envisagez d'utiliser la réplication asynchrone pour une protection accrue. Cela permet de renforcer la résilience des applications et des données. Une autre option pour atténuer ce risque consiste à utiliser un [**mode de déploiement 3-AZ**] (#3azregion).

#### Spécifications de redondance - Région 1-AZ

| Spécification         | Description                                                               |
|-------------------|---------------------------------------------------------------------------|
| **Type de redondance**   | 2N+1 entre plusieurs datacenters                                         |
| **Tolérance aux pannes**   | Protège contre les pannes de serveur et de disque ; les pannes du centre de données peuvent avoir un impact sur les services.           |
| **Cas d'utilisation** | Convient aux applications générales, aux tests, au développement et aux sauvegardes.                                    |


#### Mise à l'échelle

Dans une région 1-AZ, les options de mise à l'échelle sont quelque peu limitées en raison de l'existence d'une seule zone de disponibilité. Voici comment fonctionne la mise à l'échelle dans cette configuration :

- **Limité à une seule zone :** La mise à l'échelle horizontale (ajout d'instances dans d'autres zones) n'est pas possible puisqu'il n'y a qu'une seule zone de disponibilité. La mise à l'échelle verticale (augmentation de la capacité d'une instance ou d'un service) est possible mais n'offre pas de tolérance aux pannes entre les régions.
- **Cas d'usages privilégiés :** Convient aux environnements de développement, aux applications ayant de faibles exigences en matière de disponibilité et aux scénarios où la résilience n'est pas une priorité, mais où la redondance interne est toujours nécessaire pour gérer les défaillances matérielles.

#### Exemple d'architecture

/// details | Application de gestion interne

> [!primary]
>
> **Scenario:**
>
> Une organisation utilise le mode Region 1-AZ pour son application de gestion interne et ses services de sauvegarde. Cette configuration est idéale pour les applications qui ne nécessitent pas une haute disponibilité 24 heures sur 24 et 7 jours sur 7, mais qui ont besoin d'une redondance pour se protéger contre les défaillances matérielles.

Architecture:
- **Zone de disponibilité unique (AZ) :** Composée de plusieurs centres de données interconnectés, elle garantit la résilience face aux pannes localisées tout en s'inscrivant dans un modèle adapté à des besoins d'application modérés.
- **Réplication interne :** Les données sont répliquées en interne pour se prémunir contre les pannes de disque ou de serveur dans la zone.
- **Intégration des sauvegardes :** L'application utilise le stockage S3 pour des sauvegardes régulières, ce qui garantit que les données peuvent être restaurées en cas de besoin.
- **Instances :** Les tâches applicatives de base sont gérées par des instances de calcul dans le même AZ, avec une mise à l'échelle automatique pour la gestion des ressources.

///

### Région 3-AZ

#### Infrastructure et redondance

La Région 3-AZ consiste en **trois zones de disponibilité indépendantes**, chacune avec des systèmes d'alimentation, de refroidissement et de réseau isolés, ce qui permet une véritable isolation des pannes. Cette configuration garantit la disponibilité des services même en cas de défaillance de l'ensemble de la zone de disponibilité. L'architecture permet la réplication des données et des services entre les zones, ce qui garantit que si une zone tombe en panne, les autres peuvent continuer à desservir le trafic et à maintenir la performance de l'application.

#### Caractéristiques

- **Haute disponibilité :** Les données restent disponibles pour les opérations de lecture et d'écriture, même en cas de défaillance d'une zone. Cette architecture est idéale pour les applications nécessitant une tolérance aux pannes, car les données sont répliquées dans les trois zones de disponibilité. Même en cas d'interruption dans une zone, la continuité du service est maintenue.
- **Isolation des pannes :** Chaque zone de disponibilité est indépendante en termes d'alimentation, de réseau et de refroidissement, ce qui signifie que les problèmes d'une zone n'auront pas d'impact direct sur les autres. Cela permet d'atteindre un niveau de redondance plus élevé et de minimiser les interruptions de service.

#### Cas d'usages privilégiés

les Régions 3-AZ sont idéales pour les applications critiques et sensibles à la disponibilité où la gouvernance des données exige une disponibilité continue des données, telles que le e-commerce, les plateformes de soins de santé, les services financiers ou les services de media streaming.

> [!success]
>
> Bien que cette configuration offre une protection solide, elle peut ne pas être totalement résiliente dans le cas d'une panne régionale improbable. Pour une disponibilité des données et une résilience encore plus grandes, des solutions telles que la réplication asynchrone multirégionale peuvent être mises en œuvre.

#### Spécifications de performance - Région 3-AZ

| Spécification         | Description                                                               |
|-------------------|---------------------------------------------------------------------------|
| **Connectivité**      | Faible latence entre les zones de disponibilité, garantissant une communication rapide et fiable.                                    |
| **Haute disponibilité** | Les services restent accessibles même en cas de défaillance d'une zone de disponibilité, ce qui garantit une interruption minimale.                      |
| **Cas d'utilisation** | Convient aux applications critiques, media streaming, au e-commerce, au e-santé et à d'autres charges de travail à haute disponibilité. |

#### Mise à l'échelle

Dans une Région 3-AZ, la mise à l'échelle est plus flexible, offrant la possibilité d'une mise à l'échelle horizontale sur plusieurs zones de disponibilité. Voici ce à quoi vous pouvez vous attendre :

- **Mise à l'échelle horizontale optimisée :** Grâce à la réplication et à la distribution des services dans trois zones indépendantes, la mise à l'échelle horizontale devient plus transparente, garantissant une haute disponibilité, des performances optimales et une distribution efficace des ressources.
- **Équilibrage optimisé de la charge :** Avec plusieurs zones de disponibilité, l'équilibrage de la charge et la distribution du trafic sont optimisés, ce qui garantit de meilleures performances et une plus grande résilience.
- **Cas d'usages privilégiés :** Idéal pour les applications critiques nécessitant une haute disponibilité, telles que les plateformes de e-commerce ou les services financiers, qui exigent à la fois des performances constantes et une résilience contre les défaillances de zone.

#### Exemple d'architecture

/// details | Plateforme de e-commerce

> [!primary]
>
> **Scenario:**
>
> Une plateforme de commerce électronique qui exige une disponibilité et des performances élevées. Ce mode de déploiement assure la continuité du service même en cas de défaillance d'une zone de disponibilité entière.

Architecture:
- **Trois zones de disponibilité** (AZs) distribués géographiquement, ce qui permet une véritable isolation des pannes et une redondance.
- **Réplication des données en temps réel** entre les zones garantit un accès continu aux données de l'application, même en cas de défaillance de l'une des zones.
- **Instances redondantes** déployé dans plusieurs zones afin de fournir des capacités de basculement et de garantir des performances constantes.
- **Équilibreurs de charge** pour distribuer efficacement le trafic entre les zones de disponibilité, en maintenant une expérience fluide pour l'utilisateur malgré les perturbations potentielles.

///

### Local Zones

#### Design et flexibilité

Les Local Zones sont conçues pour rapprocher les services OVHcloud des utilisateurs finaux, en réduisant la latence et en aidant à répondre aux exigences de conformité locales. Ces zones sont idéales pour les applications qui exigent des performances à faible latence et un traitement en temps réel.

#### Avantages en matière de coûts et de conformité

- **Réduction des coûts de réseau :** Les zones locales permettent de minimiser la distance de déplacement des données, ce qui réduit les coûts du réseau et améliore les performances.
- **Stockage localisé :** Il permet de se conformer aux exigences régionales en matière de localisation des données, ce qui le rend idéal pour les applications soumises à des cadres réglementaires spécifiques.
- 
#### Limitations

- **Limitation à une seule zone:** Les zones locales sont limitées à une seule zone de disponibilité et n'offrent pas de redondance entre les zones, ce qui limite les options de récupération des données en cas de sinistre.

#### Cas d'utilisation - Local Zones

| Avantage        | Description                                           |
|------------------|-------------------------------------------------------|
| **Performance**      | Très faible latence, garantissant des performances optimales pour les applications en temps réel.             |
| **Conformité des données**  | Facilite la conformité avec les exigences régionales en matière de localisation des données et de réglementation. |
| **Cas d'utilisation**| Idéal pour les jeux en ligne, les vidéoconférences, l'informatique de pointe et d'autres applications sensibles à la latence. |

#### Mise à l'échelle

Dans les zones locales, la mise à l'échelle est conçue pour répondre aux exigences des applications à faible latence tout en étant limitée à une seule zone de disponibilité. Voici comment la mise à l'échelle est structurée :

- **Réduction de la latence, mais avec des contraintes :** La mise à l'échelle dans une zone locale vise principalement à minimiser la latence pour les applications en temps réel. Cependant, comme elle est limitée à une seule zone de disponibilité, la mise à l'échelle doit être soigneusement planifiée pour maximiser les performances tout en évitant les risques de défaillance locale.
- **Cas d'usages privilégiés :** Parfait pour les applications à très faible latence telles que les jeux en ligne, la réalité augmentée ou le streaming vidéo en direct, où chaque milliseconde compte et où une faible latence est cruciale pour l'expérience de l'utilisateur.

#### Exemple d'architecture

/// details | Plateforme de jeux en ligne

> [!primary]
>
> **Scenario:**
>
> Plate-forme de jeux en ligne en temps réel qui nécessite une latence ultra-faible et des performances élevées pour les utilisateurs d'une région géographique spécifique.

Architecture:
- **Local Zones :** Situés à proximité de la base d'utilisateurs, ce qui permet de réduire considérablement la latence et d'améliorer les performances globales.
- **Serveurs de traitement et stockage :** Déployé dans les zones locales pour un accès rapide aux données et une grande réactivité.
- **Données réglementées :** Stocké dans les zones locales pour respecter les lois sur la localisation des données, ce qui réduit les coûts de la bande passante.
- **Équilibreurs de charge :** Rediriger le trafic vers une autre zone locale ou une zone de disponibilité en cas de panne, afin de minimiser les temps d'arrêt et d'assurer la continuité du service.

///

### Comparaison des modes de déploiement

| Caractéristiques        | Région 1-AZ                         | Région 3-AZ                     | Local Zones                              |
|------------------------|-------------------------------------|---------------------------------|------------------------------------------|
| **Structure de déploiement**   | Zone de disponibilité unique            | Trois zones indépendantes | Zone de disponibilité unique               |
| **Redondance**             | 2N+1 interne                       | Redondance inter-zones            | Triple réplication locale               |
| **Disponibilité des données**      | Limité pendant les pannes du centre de données, protégé contre les pannes de serveur/disque | Maintenue dans toutes les zones, résiliente aux pannes de zone | Limité pendant les pannes du centre de données, protégé contre les pannes de serveur/disque |
| **Latence**                | Faible pour les utilisateurs finaux proches                            | Faible pour les utilisateurs finaux proches et très faible entre les zones de disponibilité   | Faible pour les utilisateurs finaux proches |
| **Cas d'utilisation**        | Développement, environnements de transition, applications sensibles aux coûts, services non critiques | Applications à haute disponibilité, services commerciaux essentiels, reprise après sinistre et charges de travail critiques | Applications en temps réel, informatique de pointe, jeux, flux vidéo, services conformes à la réglementation |
| **Coût**                   | Optimisé                               | Plus élevé en raison de la redondance accrue | Dépend des zones locales spécifiques et de la performance requise en matière de latence. |

## Go Further

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en œuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](/links/professional-services) pour obtenir un devis et une analyse personnalisée de votre projet.

Échangez avec notre [communauté d'utilisateurs](/links/community) et notre communauté sur [Discord](https://discord.gg/ovhcloud).
