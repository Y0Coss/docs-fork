---
title: 'OVHcloud Load Balancer FAQ'
excerpt: 'Frequently Asked Questions on the OVHcloud Load Balancer'
updated: 2018-03-26
---

## Objectif

Ce document fournit un ensemble des questions les plus fréquemment posées et des instructions correspondantes pour effectuer des tâches de gestion et de configuration courantes sur votre service OVHcloud Load Balancer.

## FAQ

### Comment configurer mon pare-feu pour accepter le trafic provenant de l'OVHcloud Load Balancer ?

Lorsque vous utilisez le Load Balancer, vos clients ne se connectent pas directement à vos serveurs. Une bonne pratique consiste à configurer un pare-feu permettant uniquement le trafic provenant du service OVHcloud Load Balancer.

#### Via l'API OVHcloud

Pour déterminer les adresses IP que vous devez autoriser dans votre pare-feu, vous pouvez utiliser l'appel API suivant :

> [!api]
>
> @api {v1} /ipLoadbalancing GET /ipLoadbalancing/{serviceName}/natIp
> 

#### Via l'espace client OVHcloud

Dans votre service Load Balancer, accédez à l'onglet `Home`{.action}, et trouvez la section **Information**. Sur la ligne **Outbound IPv4**, cliquez sur les points de suspension, puis sélectionnez "Read".
Une fenêtre s'ouvrira, listant les adresses IP que vous devez autoriser dans votre pare-feu.

### Comment savoir le statut de mon service ?

Parfois, il peut être utile de connaître le statut de votre OVHcloud Load Balancer.

#### Via l'API OVHcloud

Pour déterminer le statut de votre service, vous pouvez utiliser l'appel API suivant :

> [!api]
>
> @api {v1} /ipLoadbalancing GET /ipLoadbalancing/{serviceName}/instancesState
> 

Les différents statuts de l'OVHcloud Load Balancer peuvent être `running`{.action} (Actif), `reload`{.action} (Mise à jour en cours), `unknown`{.action} (Non encore démarré), ou `dead`{.action} (inactif).

#### Via l'espace client OVHcloud

Dans votre service Load Balancer, accédez à l'onglet `Home`{.action}, et trouvez la section **Status**, qui liste le nom interne de votre Load Balancer et son statut.

### Comment ajouter une Additional IP à l'OVHcloud Load Balancer ?

Une Additional IP est une adresse IP secondaire qui peut être associée à votre service en plus de votre adresse IP principale. L'Additional IP peut être transférée d'un serveur à un autre en quelques secondes.

#### Via l'API OVHcloud

- Pour ajouter une Additional IP à un service OVHcloud Load Balancer :

> [!api]
>
> @api {v1} /ip POST /ip/{ip}/move
> 

- Appliquez le changement :

> [!api]
>
> @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/refresh
> 

#### Via l'espace client OVHcloud

Dans votre service Load Balancer, accédez à l'onglet `Front-ends`{.action}, et sélectionnez `Add a front-end`{.action}.
Ensuite, développez `Advanced settings`{.action}, et sélectionnez les Additional IPs que vous souhaitez ajouter à votre front-end *(listées sur l'interface comme "Dedicated failover IP")*.

### Comment lister les Additional IPs routées vers l'OVHcloud Load Balancer ?

> [!api]
>
> @api {v1} /ipLoadbalancing GET /ipLoadbalancing/{serviceName}/failover
> 

### Comment commander un certificat SSL gratuit ?

#### Via l'espace client OVHcloud

Dans votre service Load Balancer, accédez à l'onglet `SSL certificates`{.action}, et sélectionnez `Order an SSL certificate`{.action}.
Remplissez le FQDN dans le champ dédié, puis sélectionnez `Order`{.action}.

Pour que la commande soit validée, il est nécessaire que le nom de domaine pointe vers votre OVHcloud Load Balancer.

#### Via l'API OVHcloud

Il est possible de commander un certificat SSL gratuit pour l'OVHcloud Load Balancer.

- Pour commander un certificat SSL gratuit, vous pouvez utiliser l'appel API suivant et entrer votre domaine dans le champ `fqdn` :

> [!api]
>
> @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/freeCertificate
> 

Il est possible de commander un certificat multi-domaines ; le champ `fqdn` accepte une entrée de type chaîne de caractères.

Pour que la commande soit validée, il est nécessaire que le nom de domaine pointe vers votre OVHcloud Load Balancer.

### Comment lister les certificats SSL associés à l'OVHcloud Load Balancer ?

#### Via l'espace client OVHcloud

Dans votre service Load Balancer, accédez à l'onglet `SSL certificates`{.action}, où vous trouverez un tableau listant les certificats associés à ce Load Balancer.

Pour obtenir les détails d'un certificat SSL, cliquez sur le bouton de points de suspension à droite du certificat souhaité, puis sélectionnez `See a preview`{.action}.

#### Via l'API OVHcloud

- Pour lister les certificats SSL associés à l'OVHcloud Load Balancer, vous pouvez utiliser l'appel API suivant :

> [!api]
>
> @api {v1} /ipLoadbalancing GET /ipLoadbalancing/{serviceName}/ssl
>

Les certificats SSL commandés (gratuits ou non) apparaîtront comme `built`. Ceux ajoutés par vous-même apparaîtront comme `custom`.

Un certificat SSL apparaissant comme `built_not_routed` est un certificat qui a été commandé et livré, mais dont le domaine ne peut pas être validé. Cela est généralement dû au fait que le domaine ne pointe plus vers le Load Balancer OVHcloud.

- Pour obtenir les détails d'un certificat SSL, vous pouvez utiliser l'appel API suivant :

> [!api]
>
> @api {v1} /ipLoadbalancing GET /ipLoadbalancing/{serviceName}/ssl/{id}
>

## Aller plus loin

Trouvez les détails de tous les appels d'API liés à l'OVHcloud Load Balancer dans [ce guide](/pages/network/load_balancer/use_api_details).

Rejoignez notre [communauté d'utilisateurs](/links/community).