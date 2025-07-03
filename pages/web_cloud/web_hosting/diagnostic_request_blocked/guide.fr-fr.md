---
title: "Que faire en cas de page « Your request has been blocked » ?"
excerpt: "Découvrez comment remettre votre site web en ligne s'il affiche une page « Your request has been blocked »"
update: 2025-07-01
---

## Objectif

L'infrastructure mutualisée où se trouvent les hébergements web OVHcloud dispose de plusieurs systèmes de sécurité.
Si votre site web affiche une page « Your request has been blocked », cela signifie que l'une des requêtes que vous tentez d'exécuter depuis votre site web a été bloquée par nos systèmes de sécurité.

![your-request-has-been-blocked](/pages/assets/screens/other/browsers/errors/your-request-has-been-blocked.png){.thumbnail}

**Découvrez comment remettre votre site web en ligne s'il affiche une page « Your request has been blocked ».**

## Prérequis

- Disposer d'une [offre d'hébergement web](/links/web/hosting) OVHcloud.
- Disposer des [identifiants de connexion](/pages/web_cloud/web_hosting/ftp_connection) à l'espace de stockage FTP de votre hébergement web.
- Être connecté à votre [espace client OVHcloud](/links/manager).

## En pratique

La page « Your request has been blocked » peut s'afficher pour diverses raisons (liste non exhaustive) :

- La requête est effectuée depuis un navigateur Internet (Firefox, Chrome, Safari, Edge, etc.) non mis à jour.
- Un très grand nombre de requêtes, similaires ou non, est demandé dans un délai extrêmement court.
- La requête demandée tente d'exécuter des actions non autorisées sur l'infrastructure mutualisée où se trouve votre hébergement web.

### 1 - Vérifier que votre navigateur Internet est à jour

Rendez-vous dans les paramètres de votre navigateur Internet, puis vérifiez si une mise à jour est disponible.

/// details | Cliquez ici pour plus d'informations sur la mise à jour de votre navigateur Internet

Retrouvez ci-dessous les processus de mise à jour des principaux navigateur Internet (documentations fournies par leurs éditeurs):

- [Firefox](https://support.mozilla.org/fr/kb/mettre-jour-firefox-derniere-version){.external}.
- [Chrome](https://support.google.com/chrome/answer/95414?hl=fr&co=GENIE.Platform%3DDesktop&oco=0){.external}.
- [Safari](https://support.apple.com/fr-fr/102665){.external}.
- [Edge](https://support.microsoft.com/fr-fr/topic/param%C3%A8tres-de-mise-%C3%A0-jour-de-microsoft-edge-af8aaca2-1b69-4870-94fe-18822dbb7ef1){.external}.

Si votre navigateur Internet n'est pas dans la liste ci-dessus, recherchez sur Internet de la documentation à son sujet ou contactez le support de son éditeur.

///

Dès lors où votre navigateur Internet est à jour, tentez à nouveau d'accéder à votre site web. Si la situation persiste, poursuivez la lecture de ce guide.

### 2 - Récupérer les informations présentes sur la page « Your request has been blocked » et contactez le support

Le système de sécurité qui bloque vos requêtes se trouve en amont de votre hébergement web. Par conséquent et dans ce cas précis, vous n'aurez pas accès aux logs de ce système de sécurité depuis votre espace client OVHcloud.

#### 2.1 - Récupérer les informations présentes sur la page « Your request has been blocked »

Dans un premier temps, récupérez les 3 informations suivantes qui s'affichent sur la page « Your request has been blocked » :

- `IP address` (exemple : 203.0.113.0).
- `Date` (exemple : 2025-07-01T16:30:45:150Z).
- `Request ID` (exemple : AbCdEf-your-request-ID-GhIjKlM).

### 2.2 - Contactez le support

Une fois les éléments récupérés, créer [un ticket d'assistance](https://help.ovhcloud.com/csm?id=csm_get_help) depuis le Centre d'Aide OVHcloud en y précisant :

- La page rencontrée (« Your request has been blocked »)
- Les 3 éléments récupérés précédemment.
- L'URL depuis laquelle vous rencontrez la page (par exemple : `https://www.domain.tld/index.php`).
- Le navigateur Internet utilisé.

Le support reviendra vers vous dans les plus brefs délais en vous indiquant plus de précisions sur l'origine de ce blocage.

## Aller plus loin

[Cas d'usage - Conseils suite au piratage de votre site Web](/pages/web_cloud/web_hosting/cms_what_to_do_if_your_site_is_hacked)

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre [communauté d'utilisateurs](/links/community).