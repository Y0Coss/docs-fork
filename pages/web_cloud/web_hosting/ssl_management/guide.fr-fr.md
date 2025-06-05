---
title: "Hébergement web - Nouvelle gestion des certificats SSL"
excerpt: "Découvrez, grâce à notre nouvelle interface de gestion, comment gérer un certificat SSL sur votre hébergement web OVHcloud"
updated: 2025-06-04
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

Les certificats Secure Socket Layer (SSL) permettent de chiffrer les échanges effectués depuis ou vers votre site web. Cela évite qu'une personne ou un robot malveillant ne vienne « écouter » clairement les requêtes envoyées depuis votre site web.

OVHcloud propose plusieurs types de certificats SSL sur nos offres d'[hébergement mutualisé OVHcloud](/links/web/hosting). Ils vous sont présentés plus bas dans ce guide. Les certificats SSL sont incontournables pour la sécurité de votre site web.

Trois types de certificats SSL existent :

- Domain Validation (DV)
- Organization validation (OV)
- Extended Validation (EV)

Les niveaux de chiffrement SSL sont identiques entre ces trois types de certificat.

La principale différence réside dans le niveau de vérifications qui sera réalisé par l'Autorité de Certification (AC) qui délivre le certificat SSL et atteste de son authenticité.

Disposer d'un certificat SSL pour son site web est incontournable pour l'utiliser en HTTPS.

**Découvrez, grâce à notre nouvelle interface de gestion, comment gérer un certificat SSL sur votre hébergement web OVHcloud**

## Prérequis

- Être connecté à votre [espace client OVHcloud](/links/manager).
- Posséder un [hébergement web OVHcloud](/links/web/hosting).
- Avoir enregistré au moins un [nom de domaine](/links/web/domains).

## En pratique

> [!warning]
>
> **Avant de poursuivre**, vérifiez que **le(s) nom(s) de domaine et/ou sous-domaine(s)** concerné(s) par votre futur certificat SSL :
>
> - pointe(nt) vers l'adresse IP de votre hébergement web ; 
> - est (sont) déclaré(s) en multisite sur votre hébergement web.
>
> Pour vous en assurer, vous pouvez consulter nos guides :
>
> - [Partager son hébergement entre plusieurs sites](/pages/web_cloud/web_hosting/multisites_configure_multisite) ;
> - [Liste des adresses IP des clusters et hébergements web](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP) ;
> - [Éditer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit).

### Accéder à la gestion des certificats SSL depuis votre hébergement web

> [!primary]
>
> La suite de ce guide concerne uniquement les clients dont les services d'hébergement web ont déjà basculé sur la nouvelle interface de gestion des certificats SSL. Si, une fois positionné sur votre hébergement web dans votre espace client OVHcloud, vous ne retrouvez pas l'onglet `Certificats SSL` indiqué plus bas dans ce guide, c'est que votre service n'a pas encore basculé sur la nouvelle interface de gestion. Dans ce cas consultez directement [ce guide](/pages/web_cloud/web_hosting/ssl_on_webhosting) pour gérer votre certificat SSL.
>
> En effet, pour des raisons techniques, l'ensemble des services d'hébergement web ne peut pas être basculée en une seule fois. Cette bascule est donc répartie sur quelques semaines et se fait automatiquement sans aucune incidence sur le fonctionnement de vos services d'hébergement web. De plus cete intervention ne nécessite aucune action de votre part. 
>
> A terme, tous les services d'hébergement web fonctionneront avec la nouvelle interface de gestion des certificats SSL.

Pour accéder à la gestion des certificats SSL depuis votre hébergement web, effectuez les étapes suivantes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager).
2. Cliquez sur l'onglet `Web Cloud`{.action}.
3. Dans la colonne de gauche, cliquez sur le menu `Hébergements`{.action}.
4. Sélectionnez l'hébergement web concerné.
5. Sur la page qui s'affiche, cliquez sur l'onglet `Certificats SSL`{.action}.

C'est à cet endroit que vous pourrez gérer intégralement votre (vos) certificat(s) SSL pour votre (vos) sous-domaine(s) associé(s) à votre hébergement web.

### Activer un certificat SSL sur son hébergement web <a name="ssl-enable"></a>

OVHcloud propose 4 solutions pour activer/installer un certificat SSL sur un hébergement web.

**Cliquez ci-dessous sur le certificat SSL de votre choix pour afficher les explications.**

/// details | Activer le certificat SSL gratuit Let's Encrypt (DV)

Le certificat SSL gratuit Let's Encrypt (DV) peut inclure jusqu'à **99** noms de domaines/sous-domaines déclarés sur un hébergement web.

1. Connectez-vous à votre [espace client OVHcloud](/links/manager).
2. Cliquez sur l'onglet `Web Cloud`{.action}.
3. Dans la colonne de gauche, cliquez sur le menu `Hébergements`{.action}.
4. Sélectionnez l'hébergement web concerné.
5. Sur la page qui s'affiche, cliquez sur l'onglet `Certificats SSL`{.action}.
6. Sur la nouvelle page qui apparaît, sélectionnez via le formulaire présent dans l'encadré gris situé en dessous de la mention `Activer SSL Let's Encrypt`, le nom de domaine/sous-domaine pour lequel vous souhaitez activer le certificat SSL gratuit Let's Encrypt (DV).
7. Cliquez ensuite sur le bouton `Activer SSL Let's Encrypt`{.action}.

> [!success]
>
> Pour les noms de domaine/sous-domaines récemment déclarés en multisite sur votre hébergement web, un certificat SSL Let's Encrypt est automatiquement généré pour ce dernier. Pour vous en assurer, vérifier que votre nom de domaine/sous-domaine apparaît bien dans le tableau présent en bas de la page `Certificats SSL`{.action}.

///

/// details | Activer le certificat SSL payant Sectigo (DV)

Le certificat SSL payant Sectigo (DV) n'est valable pour un seul nom de domaine + son sous-domaine en « www » (exemple : `domain.tld` et `www.domain.tld`) ou **uniquement** un sous-domaine (exemple : `sub.domain.tld`).

1. Connectez-vous à votre [espace client OVHcloud](/links/manager).
2. Cliquez sur l'onglet `Web Cloud`{.action}.
3. Dans la colonne de gauche, cliquez sur le menu `Hébergements`{.action}.
4. Sélectionnez l'hébergement web concerné.
5. Sur la page qui s'affiche, cliquez sur l'onglet `Certificats SSL`{.action}.
6. Sur la nouvelle page qui apparaît, cliquez sur le bouton `Commander un certificat SSL Sectigo`{.action}.
7. Dans la nouvelle fenêtre qui s'ouvre, sélectionnez le nom de domaine/sous-domaine concerné à l'aide du menu déroulant, puis cliquez sur `Valider`{.action} pour être redirigé vers le bon de commande de votre certificat SSL Sectigo DV.

Poursuivez la commande jusqu'au paiement afin de valider la demande de création du certificat SSL Sectigo DV pour votre nom de domaine/sous-domaine sur votre hébergement web.

> [!alert]
>
> Une fois la commande validée, la demande de certificat SSL Sectigo DV est envoyée à l'autorité de certification Sectigo.
>
> Dès lors, aucun remboursement du SSL Sectigo DV n'est possible.

///

/// details | Activer le certificat SSL payant Sectigo (EV)

Le certificat SSL payant Sectigo (EV) n'est valable pour un seul nom de domaine + son sous-domaine en « www » (exemple : `domain.tld` et `www.domain.tld`) ou **uniquement** un sous-domaine (exemple : `sub.domain.tld`).

> [!warning]
>
> Les certificats SSL payant Sectigo (EV) ont des conditions d'éligibilités spécifiques:
>
> - Commander ou disposer d'un [nom de domaine](/links/web/domains) et disposer des droits exclusifs sur son utilisation. Le nom de domaine ne doit pas déjà être lié à un certificat SSL.
> - Être une organisation (entreprise, agence gouvernementale, ...) enregistrée auprès d'un registre officiel.
> - Disposer de l'autorisation de votre organisation à commander un certificat SSL Sectigo EV.
> - Être en capacité de justifier avec exactitude les informations et coordonnées relatives à votre organisation.
>
> Pour vérifier si vous êtes éligible à la souscription d'un certificat SSL Sectigo EV, rendez-vous sur [ce lien](https://help.sectigostore.com/support/solutions/articles/22000218717-extended-validation-ev-){.external}.

1. Connectez-vous à votre [espace client OVHcloud](/links/manager).
2. Cliquez sur l'onglet `Web Cloud`{.action}.
3. Dans la colonne de gauche, cliquez sur le menu `Hébergements`{.action}.
4. Sélectionnez l'hébergement web concerné.
5. Sur la page qui s'affiche, cliquez sur l'onglet `Certificats SSL`{.action}.
6. Sur la nouvelle page qui apparaît, cliquez sur le bouton `Commander un certificat SSL Sectigo`{.action}.
7. Dans la nouvelle fenêtre qui s'ouvre, sélectionnez le nom de domaine/sous-domaine concerné à l'aide du menu déroulant, puis cliquez sur `Valider`{.action} pour être redirigé vers le bon de commande de votre certificat SSL Sectigo EV.

Sélectionnez le **Certificat SSL Sectigo EV** une fois arrivé dans le tunnel de commande, puis poursuivez la commande.

Renseignez avec exactitude les informations demandées par **Sectigo** avant que ne vous soit délivré le certificat SSL Sectigo EV. 

![SSL EV form](/pages/assets/screens/website/order/ssl-ev-step-2.png){.thumbnail}

Cliquez sur `Continuer`{.action} une fois **tous les éléments** correctement renseignés.

Poursuivez la commande jusqu'au paiement afin de valider la demande de création du certificat SSL.

> [!alert]
>
> Une fois la commande validée, la demande de certificat SSL Sectigo EV est envoyée à l'autorité de certification **Sectigo**.
>
> Assurez-vous impérativement de votre éligibilité à la souscription d'un certificat SSL Sectigo EV **avant de payer le certificat**.
>
> En effet, aucun remboursement du SSL Sectigo EV ne sera possible, **même si la procédure de vérification auprès de Sectigo n'aboutit pas**.
>

///

/// details | Installer un certificat SSL personnalisé

Cette solution vous permet d'installer votre propre certificat SSL si vous en disposez déjà d'un pour votre nom de domaine ou si aucune des 3 solutions précédentes ne correspond à votre besoin.

1. Connectez-vous à votre [espace client OVHcloud](/links/manager).
2. Cliquez sur l'onglet `Web Cloud`{.action}.
3. Dans la colonne de gauche, cliquez sur le menu `Hébergements`{.action}.
4. Sélectionnez l'hébergement web concerné.
5. Sur la page qui s'affiche, cliquez sur l'onglet `Certificats SSL`{.action}.
6. Sur la nouvelle page qui apparaît, cliquez sur le bouton `Import de votre propre certificat SSL`{.action}.
7. Dans la fenêtre qui s'ouvre, remplissez les 3 formulaires demandés, puis cliquez sur `Valider`{.action} pour terminer l'importation du certificat SSL personnalisé sur votre hébergement web.

> [!success]
>
> Pour retrouvez les éléments à renseigner dans les 3 formulaires, consultez uniquement les étapes **1** et **2** de notre guide « [Hébergement web - Installer un certificat SSL personnalisé](/pages/web_cloud/web_hosting/ssl_custom) ».

///

### Désactiver un certificat SSL sur un hébergement web <a name="delete-ssl"></a>

> [!warning]
>
> Si vous souhaitez supprimer un certificat SSL de votre hébergement web et **avant de poursuivre**, assurez-vous que la suppression du certificat SSL ne rendra pas vos sites web inaccessibles. Le cas échéant, vos utilisateurs rencontreront une erreur de sécurité lorsqu'ils essaieront d'accéder à votre site web en « HTTPS ».

Cette vérification étant inhérente aux paramètres de votre ou vos sites web, nous vous recommandons de contacter un prestataire de services spécialisé si vous rencontrez des difficultés. Nous ne serons pas en mesure de vous fournir une assistance à ce sujet.

Pour supprimer le certificat SSL installé sur votre hébergement web, effectuez les actions suivantes : 

1. Connectez-vous à votre [espace client OVHcloud](/links/manager).
2. Cliquez sur l'onglet `Web Cloud`{.action}.
3. Dans la colonne de gauche, cliquez sur le menu `Hébergements`{.action}.
4. Sélectionnez l'hébergement web concerné.
5. Sur la page qui s'affiche, cliquez sur l'onglet `Certificats SSL`{.action}.
6. Dans le tableau présent en bas de la nouvelle page qui s'affiche, cliquez sur le bouton `...`{.action}, situé à droite de la ligne correspondant au nom de domaine concerné, puis cliquez sur `Désactiver SSL`{.action}.
7. Dans la fenêtre qui s'ouvre, confirmez la désactivation en cliquant sur `Valider`{.action}.


Celle-ci sera effective sous quelques heures au maximum.

> [!warning]
>
> La suppression d'un certificat SSL payant **Sectigo** (DV ou EV) est définitive, même si le certificat n'avait pas encore expiré. Aucun remboursement au prorata du temps restant ne pourra être effectué. Si vous souhaitez réinstaller un certificat SSL **Sectigo** (DV ou EV), vous devrez donc obligatoirement réaliser une nouvelle commande et payer l'intégralité du nouveau certificat SSL souscrit.
>

## Aller plus loin

[Hébergement web - Passer son site web en HTTPS](/pages/web_cloud/web_hosting/ssl-activate-https-website).

[Erreurs courantes liées à la sécurisation de votre site web avec le SSL](/pages/web_cloud/web_hosting/ssl_avoid_common_pitfalls_of_making_website_secure).
 
Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner).
 
Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).
 
Échangez avec notre [communauté d'utilisateurs](/links/community).