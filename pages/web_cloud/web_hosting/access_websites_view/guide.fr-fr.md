---
title: "Visualiser et gérer tous ses sites web depuis son espace client OVHcloud"
excerpt: "Découvrez comment consulter et gérer l'ensemble de vos sites web depuis votre espace client OVHcloud"
updated: 2025-05-26
---

## Objectif

La vue `Sites internet` (ou `Websites`) permet de centraliser l'affichage de l'ensemble de vos sites web, indépendamment de leur hébergement. Elle facilite le suivi des fonctionnalités activées pour chaque site web et donne un accès rapide aux actions essentielles. Cette interface est particulièrement utile pour les agences ou les professionnels du web qui gèrent un grand nombre de domaines répartis sur plusieurs hébergements.

**Découvrez comment visualiser et gérer tous vos sites web depuis votre espace client**

## Prérequis

- Être connecté à votre [espace client OVHcloud](/links/manager).
- Posséder une [offre d'hébergement web](/links/web/hosting).

## En pratique

### Accéder à la vue `Sites internet`

Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}. Dans le menu de gauche, cliquez sur `Websites`{.action}. Un tableau s'affiche, regroupant l'ensemble de vos sites web et de leurs principales informations.

#### Domaine

Affiche le nom de domaine principal du site web, tel qu’il est configuré dans l’onglet Multisite de votre hébergement. Au clic, vous êtes redirigé vers l'onglet `Multisite`{.action} de l'hébergement concerné.

#### Diagnostic

Vous informe si votre nom de domaine pointe correctement vers l'hébergement web associé. Pour chaque nom de domaine, trois résultats de diagnostic sont possibles :

- `A/AAAA` vert
- `A/AAAA` jaune
- `A/AAAA` gris

Pour plus de détails concernant le diagnostic, consultez la section « Diagnostiquer vos noms de domaine » de notre guide « [Partager son hébergement entre plusieurs sites](/pages/web_cloud/web_hosting/multisites_configure_multisite) ».

Au clic, vous êtes redirigé vers l'onglet `Multisite`{.action} de l'hébergement concerné.

#### Dossier racine

Indique le répertoire de votre hébergement (ex. www, app, public_html) vers lequel le domaine pointe. Au clic, vous êtes redirigé vers l'onglet `Multisite`{.action} de l'hébergement concerné.

#### Nom du service

Nom technique du service d’hébergement web sur lequel le site est configuré, sous forme `abcdv.clusterXX`.ovh.net. Au clic, vous êtes redirigé vers l'onglet `Informations générales`{.action} de l'hébergement concerné.

#### Nom d'affichage

Alias personnalisé défini par le client pour mieux identifier son service dans l'espace client. Au clic, vous êtes redirigé vers l'onglet `Informations générales`{.action} de l'hébergement concerné.

#### Offre

Affiche le type d’offre associée à l’hébergement : Starter, Perso, Pro, Performance. Au clic, vous êtes redirigé vers l'onglet `Informations générales`{.action} de l'hébergement concerné.

#### Git

Affiche le statut de l’intégration Git sur le site web :

- Actif : le dépôt Git est connecté.
- Inactif : non activé.
- En cours : en cours de configuration.
- Erreur : erreur détectée dans la configuration.

Au clic, vous êtes redirigé vers l'onglet `Multisite`{.action} de l'hébergement concerné.

#### Logs séparés

Indique si un espace de logs est activé sur le domaine sélectionné. Au clic, vous êtes redirigé vers l'onglet `Multisite`{.action} de l'hébergement concerné.

Apprenez-en plus grâce à [notre page sur les statistiques détaillées](/links/web/hosting-traffic-analysis){.external}.

> [!warning]
>
> Vous ne pouvez pas activer les logs séparés pour un nom de domaine externe. Cette option est uniquement disponible pour les domaines enregistrés chez OVHcloud.
>

#### CDN

Affiche le statut du CDN (**C**ontent **D**elivery **N**etwork) sur le nom de domaine.

- Actif : le CDN est en fonctionnement.
- Inactif : désactivé.
- N/A : non applicable (offre non compatible).

Le CDN permet de mettre en cache des éléments statiques de votre site web, comme des images. Apprenez-en plus grâce à [notre page CDN](/links/web/hosting-options-cdn){.external}.

Au clic, vous êtes redirigé vers l'onglet `Multisite`{.action} de l'hébergement concerné.

#### SSL

Indique si le SSL est activé ou non sur le nom de domaine concerné. Au clic, vous êtes redirigé vers l'onglet `Multisite`{.action} de l'hébergement concerné.

Le SSL vous permet de bénéficier d'une connexion sécurisée (HTTPS://) sur le nom de domaine sélectionné. Apprenez-en plus grâce à [notre page SSL](/links/web/hosting-options-ssl){.external}.

#### Firewall

Indique si le pare-feu applicatif est activé ou non sur le domaine. Au clic, vous êtes redirigé vers l'onglet `Multisite`{.action} de l'hébergement concerné.

Apprenez-en plus grâce à [notre page ModSecurity](/links/web/hosting-options){.external}.

#### Boost

Indique si l'option boost est activée ou non sur votre hébergement web. L'option Boost permet d'augmenter temporairement les ressources CPU et RAM de votre hébergement web.

Pour plus de détails concernant l'option Boost, consultez la section « Booster temporairement votre hébergement Performance » de notre guide « [Hébergement web - Comment faire évoluer son offre](/pages/web_cloud/web_hosting/how_to_upgrade_web_hosting_offer) ».

Au clic, vous êtes redirigé vers l'onglet `Booster mon offre`{.action} de l'hébergement concerné.

## Aller plus loin

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre [communauté d'utilisateurs](/links/community)