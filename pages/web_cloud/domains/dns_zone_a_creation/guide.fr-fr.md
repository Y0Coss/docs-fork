---
title: "Ajouter un enregistrement DNS de type A pour un nom de domaine"
excerpt: "Découvrez comment ajouter un enregistrement DNS de type A dans une zone DNS gérée chez OVHcloud pour votre nom de domaine"
updated: 2025-04-30
---

## Objectif

Vous souhaitez afficher votre site web avec votre nom de domaine ? Pour cela, votre nom de domaine doit pointer vers l'adresse IP du service (hébergement web, serveur dédié, VPS, etc.) où se trouve votre site web. Pour réaliser cela, vous devrez configurer la zone DNS active de votre nom de domaine à l'aide d'un enregistrement DNS de type A.

**Découvrez comment ajouter un enregistrement DNS de type A dans une zone DNS gérée chez OVHcloud pour votre nom de domaine.**

## Prérequis

- Disposer d'un [nom de domaine](/links/web/domains)
- Disposer d'une zone DNS associée à ce nom de domaine chez OVHcloud.
- Être connecté à votre [espace client OVHcloud](/links/manager), partie `Web Cloud`{.action}.

## En pratique

### Ajouter un enregistrement DNS de type A pour un nom de domaine

1. Cliquez sur le menu `Zones DNS`{.action}, puis choisissez le nom de domaine concerné.
2. Sur la page qui s'affiche, cliquez sur sur le bouton `Ajouter une entrée`{.action}.
3. Dans la fenêtre qui s'ouvre, sélectionnez le champs de pointage de type `A`{.action}, puis cliquez sur `Suivant`{.action}.
4. Dans le formulaire intitulé `Cible`, renseignez l'adresse IP (exemple: `203.0.113.0`) du service (hébergement web, serveur dédié, VPS, etc.) où se trouve votre site web, puis cliquez sur `Suivant`{.action}.
5. Vérifiez le résumé, puis cliquez sur `Valider`{.action}. Patientez jusqu'à **24** heures pour que la propagation de l'ajout sur le réseau DNS soit pleinement effectif.

/// details | Cliquez ici pour plus d'informations.

Si vous éprouvez des difficultés, consultez nos guides détaillés :

- [Tout savoir sur les zones DNS](/pages/web_cloud/domains/dns_zone_general_information)
- [Tout savoir sur les enregistrements DNS](/pages/web_cloud/domains/dns_zone_records)
- [Editer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit)
- [Hébergement web - Partager son hébergement entre plusieurs sites](/pages/web_cloud/web_hosting/multisites_configure_multisite).
- [Hébergement web - Modifier un nom de domaine déjà associé](/pages/web_cloud/web_hosting/multisites_modify_domain).

///

### Ajouter un enregistrement DNS de type A pour le sous-domaine d'un nom de domaine

1. Cliquez sur le menu `Zones DNS`{.action}, puis choisissez le nom de domaine concerné.
2. Sur la page qui s'affiche, cliquez sur sur le bouton `Ajouter une entrée`{.action}.
3. Dans la fenêtre qui s'ouvre, sélectionnez le champs de pointage de type `A`{.action}, puis cliquez sur `Suivant`{.action}.
4. Dans le formulaire intitulé `Sous-domaine`, renseignez le sous-domaine concerné (exemple: `www` pour le sous-domaine `www.domain.tld`), puis, dans le formulaire intitulé `Cible`, renseignez l'adresse IP (exemple: `203.0.113.0`) du service (hébergement web, serveur dédié, VPS, etc.) où se trouve votre site web. Cliquez enfin sur `Suivant`{.action}.
5. Vérifiez le résumé, puis cliquez sur `Valider`{.action}. Patientez jusqu'à **24** heures pour que la propagation de l'ajout sur le réseau DNS soit pleinement effectif.

/// details | Cliquez ici pour plus d'informations.

Si vous éprouvez des difficultés, consultez nos guides détaillés :

- [Tout savoir sur les zones DNS](/pages/web_cloud/domains/dns_zone_general_information)
- [Tout savoir sur les enregistrements DNS](/pages/web_cloud/domains/dns_zone_records)
- [Comment créer un sous-domaine ?](/pages/web_cloud/domains/domain_create_subdomains)
- [Editer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit)
- [Hébergement web - Partager son hébergement entre plusieurs sites](/pages/web_cloud/web_hosting/multisites_configure_multisite).
- [Hébergement web - Modifier un nom de domaine déjà associé](/pages/web_cloud/web_hosting/multisites_modify_domain).

///

## Aller plus loin

[Tout savoir sur les zones DNS](/pages/web_cloud/domains/dns_zone_general_information)
[Tout savoir sur les enregistrements DNS](/pages/web_cloud/domains/dns_zone_records)

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner)

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre [communauté d'utilisateurs](/links/community).