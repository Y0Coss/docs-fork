---
title: "Ajouter un enregistrement DNS de type CNAME pour un sous-domaine"
excerpt: "Découvrez comment ajouter un enregistrement DNS de type CNAME dans une zone DNS gérée chez OVHcloud pour le sous-domaine d'un nom de domaine"
updated: 2025-06-20
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

Un enregistrement CNAME (**C**anonical **NAME**) est un type d’enregistrement DNS permettant d’associer un sous-domaine à un nom de domaine ou sous-domaine, au lieu de le faire pointer directement vers une adresse IP.
On parle alors d’« alias » : le sous-domaine alias reprend automatiquement l'adresse IP du nom de domaine ou sous-domaine cible.
Par exemple, si l'on indique via un enregistrement CNAME présent dans la zone DNS active du nom de domaine **domain.tld**, que *www.domain.tld* est un alias de *domain.tld*, alors *www.domain.tld* utilisera l'adresse IP de *domain.tld*.

Les enregistrements de type CNAME sont très utiles pour éviter d'avoir à retenir ou à modifier les adresses IP cibles pour vos différents sous-domaines.
Par ailleurs, ils peuvent aussi être utilisés pour valider certaines associations de services, comme la configuration de serveurs e-mail.

**Découvrez comment ajouter un enregistrement DNS de type CNAME dans une zone DNS gérée chez OVHcloud pour le sous-domaine d'un nom de domaine.**

> [!alert]
>
> Pour un même sous-domaine source, il est recommandé de ne pas avoir d'enregistrement TXT déjà configuré si vous souhaitez utiliser un enregistrement CNAME avec ce dernier. Si tel est la cas, la résolution DNS des deux enregistrements se ferait aléatoirement car la zone DNS ne peut renvoyer qu'un seul résultat par demande.
>
> Un enregistrement TXT associé au même nom de domaine ou sous-domaine qu’un enregistrement CNAME peut compromettre le bon fonctionnement de ce dernier. Votre enregistrement CNAME ne fonctionnera alors que partiellement ou pas du tout.

> [!primary]
>
> Pour modifier ou supprimer un enregistrement DNS de type CNAME d'une zone DNS OVHcloud, suivez notre guide « [Éditer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit) ».

## Prérequis

- Disposer d'un [nom de domaine](/links/web/domains).
- Disposer d'une zone DNS associée à ce nom de domaine chez OVHcloud.
- Être connecté à votre [espace client OVHcloud](/links/manager), partie `Web Cloud`{.action}.

## En pratique

> [!warning]
>
> L'ajout, la modification ou la suppression d'enregistrements DNS dans une zone DNS active est une manipulation sensible. En cas de doute, contactez un [prestataire spécialisé](/links/partner).
>
> De plus, par convention, **les enregistrements de type CNAME ne peuvent pas être utilisés sur un nom de domaine dans sa propre zone DNS**. En effet, le nom de domaine doit obligatoirement pointer directement vers une adresse IP avec un enregistrement de type [A](/pages/web_cloud/domains/dns_zone_a_record_creation) pour une IPv4, ou [AAAA](/pages/web_cloud/domains/dns_zone_aaaa_record_creation) pour une IPv6.
> 
> Pour reprendre l’exemple donné plus haut, vous ne pourrez donc pas créer un enregistrement de type CNAME pour le nom de domaine *domain.tld* dans la zone DNS que vous avez créée pour celui-ci.
> Vous pourrez cependant créer des enregistrements de type CNAME pour tous les sous-domaines (par exemple : *subdomain.domain.tld* ou *www.domain.tld*) du nom de domaine *domain.tld* dans la zone DNS créée pour *domain.tld*.

### Ajouter un enregistrement DNS de type CNAME pour le sous-domaine d'un nom de domaine

1. Cliquez sur le menu `Zones DNS`{.action}, puis choisissez le nom de domaine concerné.
2. Sur la page qui s'affiche, cliquez sur le bouton `Ajouter une entrée`{.action}.
3. Dans la fenêtre qui s'ouvre, sélectionnez le champ de pointage de type `CNAME`{.action}.
4. Renseignez ensuite dans le champ `Sous-domaine` le sous-domaine concerné (par exemple : `www` pour le sous-domaine `www.domain.tld`), et, dans le champ `Cible *`, le nom de domaine ou sous-domaine (par exemple : `domain.tld`) que vous souhaitez cibler à l'aide de l'enregistrement de type CNAME. Cliquez enfin sur `Suivant`{.action}.
5. Vérifiez le résumé, puis cliquez sur `Valider`{.action}. Patientez jusqu'à **24** heures pour que la propagation de l'ajout sur le réseau DNS soit pleinement effective.

/// details | Cliquez ici pour plus d'informations.

Consultez nos guides détaillés :

- [Tout savoir sur les zones DNS](/pages/web_cloud/domains/dns_zone_general_information)
- [Tout savoir sur les enregistrements DNS](/pages/web_cloud/domains/dns_zone_records)
- [Comment créer un sous-domaine ?](/pages/web_cloud/domains/domain_create_subdomains)
- [Éditer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit)
- [Hébergement web - Partager son hébergement entre plusieurs sites](/pages/web_cloud/web_hosting/multisites_configure_multisite)
- [Hébergement web - Modifier un nom de domaine déjà associé](/pages/web_cloud/web_hosting/multisites_modify_domain)

///

## Aller plus loin

[Tout savoir sur les zones DNS](/pages/web_cloud/domains/dns_zone_general_information)

[Tout savoir sur les enregistrements DNS](/pages/web_cloud/domains/dns_zone_records)

Pour des prestations spécialisées (référencement, développement, etc.), contactez les [partenaires OVHcloud](/links/partner).
 
Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).
 
Échangez avec notre [communauté d'utilisateurs](/links/community).