---
title: "Récupération de l’état de santé des serveurs"
excerpt: Récupérer l’état des serveurs
updated: 2022-03-29
---

## Objectif

Le service **OVHcloud Load Balancer** agit par défaut comme un mandataire ou « Proxy ». Il répartit la charge (les requêtes) qu'il reçoit entre tous les serveurs de la ferme désirée.

Chaque serveur peut être configuré pour que le répartiteur de charge vérifie son état fréquemment.

Dès qu'un serveur est détecté comme « indisponible » (malade), le répartiteur de charge cesse de lui envoyer des données et répartit la charge entre les serveurs restants.

Cette fonctionnalité est utile dans le cas d'une maintenance planifiée : on « sort » le serveur de la ferme, on effectue la maintenance, puis on le réintègre dans la ferme.

Cependant, lorsqu'un serveur est « sorti » de la ferme par le répartiteur de charge indépendamment de notre volonté, il est important d'en être informé et d'en connaître la raison.

Ce tutoriel explique comment connaître l'état de santé de chaque serveur pour chaque instance de votre **OVHcloud Load Balancer**.

## Prérequis

- Posséder une offre [OVHcloud Load Balancer](/links/network/load-balancer) dans votre compte OVHcloud.
- Être connecté à votre [espace client OVHcloud](/links/manager).
- Être connecté à l'[API OVHcloud](/links/api).
- Posséder une ferme configurée
- Posséder un *frontend* configuré

## En pratique

### Depuis l'API OVHcloud

Dans l'API, l'état de santé des serveurs est disponible dans le tableau `serverState` :

> [!api]
>
> @api {v1} /ipLoadbalancing GET /ipLoadbalancing/{serviceName}/http/farm/{farmId}/server/{serverId}
> 

> [!api]
>
> @api {v1} /ipLoadbalancing GET /ipLoadbalancing/{serviceName}/tcp/farm/{farmId}/server/{serverId}
> 

#### Résultat

![Résultat état de santé des serveurs via l'API](images/result_serversStateApi.png){.thumbnail}

L'image ci-dessus illustre le résultat de la commande dans l'API.

### Depuis l'espace client OVHcloud

Dans l'onglet `Fermes de serveurs`{.action}, après avoir sélectionné l'une d'entre elles, l'état de chacun de ses serveurs est affiché sur la ligne correspondante.

#### Résultat

![Résultat état de santé des serveurs via l'espace client OVHcloud](images/farm_server_health.png){.thumbnail}

Afin d'obtenir les détails sur l'état de santé d'un serveur, il suffit de cliquer sur le pictogramme dans la colonne "**Status**".

![Résultat état de santé des serveurs via l'espace client OVHcloud (détails)](images/server_health_detail.png){.thumbnail}

### Explications des détails obtenus

Comme expliqué précédemment, nous avons récupéré l'état de santé du serveur pour chaque instance de votre **OVHcloud Load Balancer**.

Pour chaque instance, nous disposons des informations suivantes :

|Champ|Description|
|---|---|
|Status|État du serveur|
|Check code|Code de retour de la sonde de vérification|
|Check status|État de la sonde de vérification|
|Last check content|Contenu du retour de la sonde|
|Check time|Date et heure d'exécution de la sonde|

## Annexe

### Récupérer la liste des instances de votre OVHcloud Load Balancer

> [!api]
>
> @api {v1} /ipLoadbalancing GET /ipLoadbalancing/{serviceName}/instancesState
> 

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).