---
title: "Résilience 3AZ - Mécanismes et architectures de référence"
excerpt: "Comprenez les mécanismes de résilience 3AZ et explorez les architectures de référence OVHcloud."
updated: 2025-03-15
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

Ce guide a pour objectif d’éduquer et d’accompagner les clients sur les principes de résilience en **3AZ** et les architectures de référence associées. Il détaille comment les services OVHcloud sont conçus pour fonctionner dans un environnement multi-AZ, les bonnes pratiques de déploiement et les mécanismes permettant d'assurer une haute disponibilité. Un tableau des spécifications des services **3AZ** est fourni, ainsi que des exemples d’architectures en **2AZ** pour aider les utilisateurs à structurer leurs infrastructures de manière résiliente.

## Déploiement et résilience des services en 3AZ

Dans un environnement cloud, la disponibilité et la résilience des services sont essentielles pour garantir la continuité des opérations, même en cas de panne d’une zone de disponibilité (AZ). Ce document présente les différentes offres cloud et leurs mécanismes de résilience lorsqu’elles sont déployées sur trois zones de disponibilité (3AZ).

Le tableau ci-dessous répertorie les services proposés, leur portée (zonal, régional ou global), ainsi que les bonnes pratiques de configuration permettant d’assurer une résilience optimale. Enfin, il détaille les comportements attendus en cas de panne d'une AZ, afin d'aider les clients à anticiper les risques et à mettre en place des architectures adaptées.

| Service | Zonal/Local | Régional | Global | Architecture/Bonnes pratiques de configuration | en cas de panne de l'AZ                                                              |
| ------- | ----------- | -------- | ------ | ---------------------------------------------- | ------------------------------------------------------------------------------------ |
| Instances | X | | | Les instances étant des services zonaux, elles ne sont déployées que dans une seule zone d'activité. Pour assurer la résilience, les clients doivent répartir manuellement leurs instances sur plusieurs AZ et utiliser des Load Balancers régionaux pour une architecture 3AZ.| En cas de défaillance de l'AZ, la VM sera perdue. Si le client n'a pas mis en place de résilience avec un Load Balancer régional et une VM2 dans l'AZ2, il y aura une interruption de service. En revanche, avec un Load Balancer régional et une VM2 dans l'AZ2, le Load Balancer rééquilibrera automatiquement la charge sur la VM2. Lorsque l'AZ1 sera rétablie, la VM1 sera dans son état initial. |
| Private Network | | X | | | Les agents DHCP/DNS fonctionnent dans deux AZ. En cas de défaillance d'une AZ, ils seront automatiquement réactivés dans l'AZ où ils ne sont pas déjà en cours d'exécution. |
| Public Cloud Load Balancer ( Octavia ) | | X | | Le Load Balancer régional se compose d'une Load Balancer actif et d'un Load Balancer passive, chacune étant déployée dans une AZ distincte. | Le service restera disponible sans interruption. En cas de défaillance d'une AZ contenant un nœud de Load Balancer, celui-ci sera automatiquement déplacé vers la dernière AZ. Le service régional sera réactivé automatiquement par OVHcloud une fois l'AZ rétablie. |
| Gateway | | X | | La Gateway régionale se compose d'une Gateway active et d'une Gateway passive, chacune étant déployée dans une AZ distincte.| Le service restera disponible sans interruption. En cas de défaillance d'une AZ contenant un nœud de Gateway, celui-ci ne sera **PAS** recréé dans une autre AZ. |
| Floating Ip | | X | | Le client peut attacher une IP flottante multi-AZ à n'importe quelle instance ou à n'importe quel Load Balancer dans n'importe quelle AZ. | Le service restera disponible sans interruption. Il sera automatiquement réactivé par OVHcloud dès que l'AZ sera rétablie. |
| Object Storage ( Standard class) | X | | | L’Object Storage est un service régional offrant des options avancées de protection des données, dont la réplication hors site intégrée via le panneau de contrôle et la réplication asynchrone compatible S3 via l’API pour une configuration personnalisée. | Aucun impact sur le service Object Storage ni sur les données. Les données restent disponibles pour les opérations de lecture et d'écriture, même en cas de défaillance d'une AZ. Cette configuration est idéale pour les applications à haute disponibilité et tolérance de pannes. Une fois l'AZ rétablie, les blocs sont déplacés vers l'AZ affectée. |
| Block storage High Speed gen 1/2 | X | | | L'offre HighSpeed (Gen1 et Gen2) est un service zonal avec une triple réplication au sein d'une seule AZ. Pour assurer la résilience, les clients doivent déployer manuellement le Block Storage HighSpeed sur plusieurs AZ et mettre en place un mécanisme de réplication applicatif, avec au minimum un backup de volume dans une autre AZ ou région. | En cas de panne, les données resteront disponibles et le service Block Storage reprendra dès la fin de l'incident. En cas d'incident majeur, le client pourrait perdre ses données et devra recréer son volume Block lorsque l'AZ sera rétablie. |
| Block storage Classic Multi-Zone | | X | | Le Block Storage Classic est un service régional utilisant le codage par effacement réparti sur plusieurs AZ. Une réplication hors site est recommandée pour se prémunir contre une défaillance régionale. | Les données du Block Storage resteront disponibles sans impact ni temps d'arrêt. En cas d'incident majeur, les chunks seront recréés dès que l'AZ sera rétablie. |
| File storage | | | | Le File Storage est un service zonal avec réplication EC/triple au sein d’une seule AZ. Il est recommandé de mettre en place une sauvegarde ou un instantané dans une autre AZ. | Les Files Storage à l'intérieur de l'AZ seront perdus. <br> Le client serait en mesure de re-spawner un fichier à partir d'une sauvegarde lorsque l'AZ sera à nouveau disponible. |
| Managed K8s | | X | | Avec l'offre "Premium", le control plane est réparti sur 3 AZ. Le client doit déployer des worker nodes sur plusieurs AZ et utiliser le Block Storage Multi-Zone Classic pour les volumes persistants. | En cas de défaillance d'une AZ, le control plane reste disponible et le workload du client est reprogrammé sur les nœuds d'une autre AZ disponible. Notez que les workloads utilisant des volumes persistants de classes mono-zone ne peuvent pas être migrés vers d'autres AZ. Lorsque l'AZ sera rétablie, le control plane redeviendra disponible dans l'AZ et le workload non migré reprendra. |
| Private Registry | | X | | Basé sur S3, avec un control plane distribué sur plusieurs zones géographiques. Une réplication hors site est recommandée en cas de défaillance régionale. | En cas de défaillance de l'AZ, le registre reste disponible. <br> Sur la base du stockage S3 3AZ/régional, les données resteront disponibles sans impact. <br> Les chunks seront recréés une fois que l'AZ sera à nouveau opérationnelle. |
| Rancher | | | X | Le service Rancher géré est un service "global" . | Pas d'impact |
| DBaaS | | X | | Les nœuds de base de données sont répartis sur plusieurs nœuds dans différentes AZ. Le backup est utile en cas de défaillance régionale ou pour une base de données à un seul nœud. | En cas d'interruption, les données resteront disponibles et les services de base de données reprendront dès la fin de l'incident. En cas de défaillance de l'AZ, les clients Business et Enterprise ne perdront pas leurs données. Pour l'offre Essential, les données peuvent être perdues si aucune sauvegarde n'a été effectuée. |

## Architecture de référence pour un déploiement Multi-AZ

> [!warning]
>
> Lors du déploiement d'un service zonal/local (ex: instances Compute 3AZ), cela signifie qu'il est compatible avec les régions 3AZ, mais pas automatiquement déployé dans chacune de ces AZ.
>
> - Pour une architecture 2AZ, vous devez manuellement créer une instance en AZ-a et AZ-b.
> - Pour une architecture 3AZ, il faut en créer une en AZ-a, AZ-b et AZ-c.
>

Cette section présente des architectures de référence pour un déploiement multi-AZ, illustrant différents scénarios de résilience face à la défaillance d’une AZ. À travers des schémas détaillés et des explications techniques, nous mettons en avant les bonnes pratiques pour concevoir des infrastructures robustes, garantir la disponibilité des services et optimiser la reprise après incident.

> [!primary]
>
> Le Public Cloud Control Plane, présent dans l’ensemble des Availability Zones (AZ), joue un rôle clé dans la gestion et l’orchestration des services cloud. Il assure la répartition des charges, la gestion du réseau privé, ainsi que la coordination des ressources et du stockage.
> 
> Durant l’incident sur l’AZ-a, le Control Plane reste opérationnel depuis les autres AZ, garantissant ainsi la continuité des services critiques. Cela permet au Floating IP et au Load Balancer d’adapter dynamiquement le trafic vers les instances toujours disponibles, assurant une expérience utilisateur ininterrompue.
> 
> Lors du rétablissement de l’AZ-a, le Control Plane permet de réintégrer progressivement les ressources et les instances concernées dans l’infrastructure globale. Toutefois, si des données ont été perdues, leur récupération dépend de la mise en place d’une stratégie de sauvegarde. En l’absence de backup, une partie des données récentes peut rester irrécupérable, sauf pour les services tels que le Block Storage Classic Multi-Zone ou l'Object Storage, qui disposent de mécanismes de résilience intégrés.
>

/// details | **Déploiement en 2 AZ-avec Storage régional**

![2az with regional storage](images/2az-with-regional-storage.png){.thumbnail}

Ce schéma illustre une application déployée sur deux zones de disponibilité (AZ) en s’appuyant sur un service Storage régional pour assurer la résilience.

**Fonctionnement Normal** (Côté gauche) :

- L’application est répartie sur deux AZ (A et B).
- Les 2 AZ sont dans le même Private Networks.
- L'instance 1 fonctionne sur l’AZ-a et l'instance 2 sur l’AZ-b.
- Un Load Balancer actif répartit le trafic sur l’AZ-a, avec un Load Balancer passif en attente sur l’AZ-b.
- Le service Storage est régional, partagé entre les AZ.
- La connectivité est assurée par une Floating IP et une Gateway (dont une deuxième disponible en cas de panne de la première).

**Incident sur l’AZ-a** (Côté droit) :

- L’AZ-a tombe en panne, rendant l’Instance 1 et le Load Balancer actif indisponibles.
- La Gateway de l'AZ-a devient innacessible mais une seconde se trouvant dans une autre AZ prend le relais.
- Le Load Balancer passif devient actif pour assurer la continuité du service.
- La Floating IP bascule dynamiquement grâce au Private Networks vers l'AZ-b pour permettre l'accès continue à l'application.
- L’Instance 2 (qui se trouve dans l’AZ-b) prend automatiquement le relais.
- L’application reste disponible, mais l’application ne fonctionne plus en mode haute disponibilité (High Availability - HA).

![2az with regional storage end of incident](images/2az-with-regional-storage-end-of-incident.png){.thumbnail width="900"}

Ce schéma illustre deux scénarios de reprise après l'incident précédent sur l'AZ-a.

Dans les deux cas, une fois l’AZ-a rétablie, l’application retrouve son état initial et redevient totalement opérationnelle. Grâce au transfert dynamique des services entre les zones de disponibilité, l’application est restée active tout au long de l’incident, sans interruption pour les utilisateurs.

Si le service Storage régional a permis de préserver les données, l’incident n’aura eu aucun impact sur les utilisateurs. En revanche, si des données ont été perdues durant l’interruption, leur récupération dépendra de la présence d’un mécanisme de sauvegarde. En l’absence de backup, une partie des données récentes sera irrémédiablement perdue.

Cette situation souligne l’importance d’une stratégie de sauvegarde adaptée pour garantir l’intégrité des données en cas de défaillance d’une zone de disponibilité.

///

/// details | **Déploiement en 2 AZ-avec Storage local**

Ce schéma illustre une architecture de déploiement en 2 AZ-avec du service Storage local.

![2az with local storage](images/2az-with-local-storage.png){.thumbnail}

**Fonctionnement Normal** (Côté gauche) :

- L’application est répartie sur deux AZ (A et B).
- L'instance 1 fonctionne sur l’AZ-a, et Instance 2 sur l’AZ-b.
- Un Load Balancer actif répartit le trafic sur l’AZ-a, avec un Load Balancer passif en attente sur l’AZ-b.
- Le service Storage est local, ce qui signifie que chaque instance dispose de son propre volume attaché à son AZ et non partagé avec l'autre AZ.
- Les 2 AZ sont dans le même Private Networks.
- La connectivité est assurée par une Floating IP et une Gateway (dont une deuxième disponible en cas de panne de la première).

**Incident sur l’AZ-a** (Côté droit) :

- L’AZ-a tombe en panne, rendant l’Instance 1 et le Load Balancer actif indisponibles.
- La Gateway de l'AZ-a devient innacessible mais une seconde se trouvant dans une autre AZ prend le relais
- Le Load Balancer passif devient actif pour assurer la continuité du service.
- La Floating IP bascule dynamiquement grâce au Private Networks vers l'AZ-b pour permettre l'accès continue à l'application.
- L’Instance 2 (qui se trouve dans l’AZ-b) prend automatiquement le relais.
- L’application reste disponible, mais l’application ne fonctionne plus en mode haute disponibilité (High Availability - HA).
- Puisque le service Storage est local et non régional, les données stockées sur l’instance de l’AZ-a sont temporairement perdues tant que la zone n’est pas restaurée.

![2az with local storage end of incident](images/2az-with-local-storage-end-of-incident.png){.thumbnail width="900"}

Ce schéma illustre deux scénarios de reprise après l'incident précédent sur l'AZ-a :

**Retour à la normale sans perte de données** (schéma du haut) :

- L’AZ-a redevient opérationnelle.
- L’instance et son service Storage sont récupérés sans perte de données.
- L’application retrouve son mode haute disponibilité, avec un fonctionnement normal sur les deux AZ.

**Retour à la normale avec perte de données** (schéma du bas) :

- L’application reste disponible pour les utilisateurs mais elle n’est plus en haute disponibilité tant que l’AZ-a n’est pas complètement restaurée.
- L’instance de l’AZ-a doit être restaurée manuellement pour retrouver un état normal.
- L’AZ-a redevient opérationnelle, mais les données locales stockées sur cette AZ-avant l’incident sont perdues.
- Un Backup programmé au préalable permettrait de récupérer les données perdues, sinon elles sont définitivement perdues.

Dans les deux cas, l’application est restée accessible aux utilisateurs grâce au transfert dynamique des services vers l’AZ-b. Cependant avec un service Storage local, l’absence de réplication entre les AZ expose au risque de perte de données en cas d’incident majeur.

///

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en œuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](/links/professional-services) pour obtenir un devis et une analyse personnalisée de votre projet.

Échangez avec notre [communauté d'utilisateurs](/links/community) et notre communauté sur [Discord](https://discord.gg/ovhcloud).
