---
title: Utiliser les outils de mise en réseau disponibles pour les clients OVHcloud
excerpt: Découvrez comment utiliser les outils de mise en réseau disponibles pour les clients OVHcloud
updated: 2025-xx-xx
---

## Objectif

OVHcloud fournit plusieurs outils aux clients et aux prospects pour tester et évaluer leur connectivité réseau avec les services OVHcloud. Dans cet article, nous verrons comment utiliser ces outils.

## Topics

- [Looking Glass](#lookingglass)
- [Proof](#proof)
- [Smokeping](#smokeping)
- [Weathermap](#weathermap)


### Looking Glass <a name="lookingglass"></a>

[Looking Glass](https://lg.ovh.net/) est un outil qui vous permet d’exécuter un traceroute ou de visualiser la table de routage vers n’importe quelle IP comme si vous utilisiez une machine dans un datacenter OVHcloud. Cet outil est idéal si vous êtes un client potentiel d'OVHcloud ou si vous envisagez d'étendre votre présence à d'autres centres de données. Cela permettra de s’assurer que le réseau est suffisant pour vos besoins. L'interface utilisateur est très simple.

1\. Instructions pour les différentes commandes que vous pouvez exécuter.
2\. Sélectionnez le datacenter dans lequel vous souhaitez exécuter le test.
3\. Sélectionnez la commande que vous souhaitez exécuter ainsi que l'IP/URL vers laquelle vous souhaitez obtenir l'itinéraire.
4\. Historique récent de vos requêtes pour vous permettre de les relancer rapidement.


![looking glass](images/networktools1.png){.thumbnail}

### Proof <a name="proof"></a>

[Proof](https://proof.ovh.us/) est un test de vitesse pour le réseau d'OVHcloud. Proof vous propose trois options : un test de vitesse générique, des fichiers arbitraires à télécharger pour tester la vitesse, et un test de vitesse de preuve (vous permettant de choisir le datacenter).

![proof](images/networktools2.png){.thumbnail}

La première fois que vous accédez au site, vous êtes redirigé vers l'onglet **Speedtest**. Il s'agit d'un test de vitesse normal. Si vous cliquez sur Fichiers, vous serez redirigé vers la page suivante :

![test de vitesse](images/networktools3.png){.thumbnail}

Choisissez la taille du fichier que vous souhaitez tester et téléchargez le fichier pour tester votre vitesse de téléchargement sur le réseau d'OVHcloud. Le dernier onglet est l'onglet **Épreuves**. Dans le menu déroulant, sélectionnez le datacenter à tester. Vous serez ensuite soumis au test de vitesse avec ce datacenter sélectionné.

![choix du datacenter](images/networktools4.png){.thumbnail}

### Smokeping <a name="smokingping"></a>

[Smokeping](https://smokeping.ovh.net/smokeping) est un outil de surveillance permettant de vérifier l’accessibilité ICMP, la latence et le changement de chemin de trafic (traceroute) pour les datacenters externes AS/internes OVH, via FPing, à l'aide d'un exemple d'adresse IP/IPv6 (ajouté manuellement).

Des serveurs Smokeping Probe sont installés dans chaque datacenter OVH pour collecter les logs.

Une fois que vous avez accédé à l'outil Smokeping, vous verrez un menu de navigation supérieur (où un datacenter peut être sélectionné) et un menu de navigation latéral avec les options suivantes :

1\. **OVH :** Surveille une adresse IP spécifique dans les destinations DC, POP et Anycast OVH.
2\. **ANYCAST :** Destinations Anycast mondiales telles que DNS Google et DNS CloudFlare plus destinations d'autres fournisseurs de CDN.
3\. **EMEA :** Fournisseurs de services, de contenus et/ou de cloud en Europe.
4\. **USA / CANADA :** Fournisseurs de services, de contenus et/ou de cloud aux États-Unis et au Canada.
5\. **SA :** Fournisseurs de services, de contenus et/ou de cloud en Amérique du Sud
6\. **APAC :** Fournisseurs de services, de contenus et/ou de cloud en Asie / Océanie

![smokeping](images/networking_tools01_.png){.thumbnail}

Pour afficher les résultats de la latence pour une région entière, cliquez sur [code]3. EMEA, puis le nom de la région. Vous pouvez afficher la perte de latence/ping pour l'ASN surveillé dans cette région spécifique.

![latency results](images/networking_tools02_.png){.thumbnail}

Vous pouvez utiliser la zone de recherche dans le coin supérieur droit pour vérifier les résultats d'un AS/Nom spécifique. Tous les résultats seront affichés sur le côté gauche de la page.

![ASN](images/networking_tools03_.png){.thumbnail}

Si vous cliquez sur le nom du fournisseur dans les résultats de la recherche, vous verrez l'historique des résultats de latence et de traceroute, jusqu'à la dernière année.

![Historique des résultats](images/networking_tools04_.png){.thumbnail}

### Weathermap <a name="weathermap"></a>

Le [weathermap OVHcloud](https://weathermap.ovh.net/) permet de visualiser le backbone du réseau. Permet de visualiser le pourcentage de charge de trafic sur chaque lien.

1\. Choix du datacenter
2\. Rechercher dans les zones et ajuster la période
3\. Charger la légende de l'échelle
4\. Conseils de navigation
5\. Voir les détails du lien

![weathermap](images/networking_tools05_.png){.thumbnail}

Pour plus d'informations et de tutoriels, veuillez consulter nos autres [guides d’assistance sur la mise en réseau et la sécurité](/products/network) ou explorer les [guides for other OVHcloud products and services](https://help.ovhcloud.com/csm/fr-documentation?id=kb_home).

## Aller plus loin

Rejoignez notre [communauté d'utilisateurs](/links/community).