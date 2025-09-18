---
title: "Noms de domaine & DNS - FAQ"
excerpt: "Retrouvez les principales questions posées sur les noms de domaine, les serveurs et les zones DNS"
updated: 2025-09-12
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

**Cliquez sur les questions ci-dessous pour afficher les explications.**

## Souscription d'un nom de domaine

/// details | Comment puis-je souscrire à un nom de domaine chez OVHcloud ?



///

/// details | Comment puis-je acheter un nom de domaine sur le marché secondaire ?



///

## Gestion d'un nom de domaine

/// details | Comment savoir si mon nom de domaine est enregistré chez OVHcloud ?



///

/// details | Comment connaître la date d'expiration d'un nom de domaine ?



///

/// details | Comment changer la date d'expiration d'un nom de domaine ?



///

<br>

/// details | Comment puis-je corriger une faute de frappe dans mon nom de domaine ?



///

/// details | Comment modifier un nom de domaine déjà souscrit ?



///

/// details | Comment supprimer un nom de domaine ?



///

/// details | J'ai reçu un e-mail concernant la validation des informations du titulaire associée à mon nom de domaine, que faire ?



///

/// details | Je n'ai pas reçu l'e-mail de validation des informations du titulaire associée à mon nom de domaine et celui-ci est suspendu, que faire ?



///

/// details | Qu'est ce qu'un nom de domaine au format IDN ?



///

/// details | Comment corriger un nom de domaine au format IDN ?



///

/// details | Comment renouveler un seul nom de domaine présent dans un pack Alldom ?



///

## Transfert d'un nom de domaine

/// details | Est-ce que mon nom de domaine est transferable après un changement de propriétaire ?



///

/// details | Mon nom de domaine est bloqué contre le transfert pendant 60 jours, que faire ?



///

/// details | Je ne retrouve pas mon nom de domaine dans mon espace client, que faire ?



///

/// details | Je ne parviens pas à contacter la personne qui gère mon nom de domaine, que faire ?



///

/// details | Puis-je vendre mon nom de domaine ?



///

## Zone DNS

> [!primary]
>
> La modification d'une zone DNS est une manipulation sensible et peut engendrer une interruption des services associés à votre nom de domaine (hébergement web, e-mail, etc.). En cas de doute, n'hésitez pas à contacter un [prestataire spécialisé](/links/partner)

/// details | Qu'est ce qu'une zone DNS ?



///

/// details | Qu'est ce qu'un enregistrement DNS ?



///

/// details | Quels sont les enregistrements DNS disponibles dans une zone DNS OVHcloud ?



///

/// details | Puis-je changer les serveurs DNS déclarés dans ma zone DNS chez OVHcloud ?



///

/// details | Quelle est la différence entre un enregistrement DNS de type A (IPv4) et AAAA (IPv6) ?



///

/// details | Comment configurer un enregistrement PTR pour mon adresse IP externe à OVHcloud ?



///

/// details | Comment changer le TTL par défaut dans ma zone DNS OVHcloud ?



///

/// details | Qu'est ce qu'un enregistrement DNS de type SOA ?



///

<br>

/// details | Comment vérifier la configuration de ma zone DNS ?

Voici différentes solutions pour vérifier la configuration d'une zone DNS :

- **Un outil de vérification en ligne** : Plusieurs outils en ligne permettant de vérifier la configuration de votre zone DNS existent. Retrouvez-les directement grâce à un navigateur Internet (Chrome, Edge, Firefox, Safari, etc.) en saisisant les mots clés adéquats (par exemple : « vérifier propagation DNS ») dans un moteur de recherche.

- **La commande « dig »** : Si vous avez accès à un *terminal* depuis un système d'exploitation Linux ou macOS, vous pouvez utiliser la commande `dig` pour vérifier la configuration sur le réseau DNS de votre zone DNS.

- **La commande « nslookup »** : La commande `nslookup` est disponible sur la plupart des systèmes d'exploitation et permet également de vérifier la configuration de votre zone DNS.

- **Depuis votre espace client OVHcloud** : Pour cela, suivez ces étapes (si la zone DNS active de votre nom de domaine est gérée chez OVHcloud) : 
    1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
    2. Cliquez sur le menu `Zones DNS`{.action}, puis choisissez le nom de domaine concerné.
    3. Dans le tableau de la page qui s'affiche, vous visualiserez l'ensemble des enregistrements DNS déclarés pour votre nom de domaine.

> [!success]
>
> Retrouvez tous les détails dans notre guide « [Éditer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit) ».

///

/// details | Comment vérifier la propagation des modifications effectuées dans ma zone DNS ?

> [!primary]
>
> Avant de poursuivre, sachez que :
>
> - La propagation d'une modification réalisée dans une zone DNS peut prendre jusqu'à **24** heures pour être effective.
> - La propagation d'une modification de serveurs DNS pour un nom de domaine peut prendre jusqu'à **48** heures pour être effective.

Vous pouve cependant vérifier que la propagation DNS s'effectue correctemet à l'aide de l'enregistrement DNS de type **S**tart **O**f **A**uthority (**SOA**).

Dans un premier temps, ouvrez un terminal compatible sur votre ordinateur, puis exécutez la ligne de commande suivante (remplacez `domain.tld` par votre propre nom de domaine):

```bash
dig domain.tld soa
```

> [!primary]
>
> Les systèmes d'exploitation Linux et MacOS disposent nativement d'un terminal compatible pour exécuter ce type de commande. Si vous utilisez un autre système d'exploitation (par exemple : Windows), vous devrez installer au préalable un terminal compatible pour exécuter la commande.
>
> Par ailleurs, sachez qu'il existe aussi des outils disponibles sur Internet pour vérifier la propagation DNS.

Une fois la commande exécutée, vous obtenez un résultat similaire à celui-ci

```
              ;; ANSWER SECTION:                                                                                                     

domain.tld.           3600    IN      SOA     dns200.anycast.me. tech.ovh.net. 2025091801 86400 3600 3600000 300   
```

Dans ce résultat, récupérez le **numéro de série** (dans notre exemple : `2025091801`).

Il a la forme suivante `YYYYMMDDRR` où :

- `YYYYMMDD` représente l'année, le mois et le jour (en résumé la date) de la dernière mise à jour DNS propagée pour le nom de domaine.
- `RR` représente le nombre de mises à jour qui ont été réalisées à la date indiquée. Par exemple, si une seule mise à jour à été effectuée sur une journée, il aura la valeur `00`. Si 2 mises à jour ont été effectuée sur la même journée, il aura alors la valeur `01` et ainsi de suite.

Une fois le numéro de série récupérée, suivez ces étapes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
2. Cliquez sur le menu `Zones DNS`{.action}, puis choisissez le nom de domaine concerné.
3. Sur la droite ou en dessous du tableau, cliquez sur `Modifier en mode textuel`{.action}.
4. Dans la fenêtre qui s'ouvre, repérez la deuxième ligne qui, pour reprendre notre exemple, serait équivalente à celle-ci : `@	IN SOA dns200.anycast.me. tech.ovh.net. (2025091801 86400 3600 3600000 60)`.
5. Comparez le numéro de série récupérée via le terminal avec celui qui s'affiche dans votre espace client OVHcloud.

Cas n°1 - Les deux numéros de série correspondent :

Cela signifie que la propagation DNS s'effectue correctement. Vous n'avez rien d'autre à faire.

Cas n°2 - Les deux numéros de série sont différents : 

Cela signifie que soit :

- La propagation DNS de vos modifications n'est pas totalement terminée (vous êtes encore dans les délais standards de propagations DNS). Dans ce cas, patientez le temps que la propagation DNS soit totalement terminée (**24** heures pour une modification de zone DNS et **48** heures pour une modification des serveurs DNS), puis réitérer l'opération.
- La propagation DNS ne s'effectue pas correctement. Dans ce cas et depuis la fenêtre `Modifier en mode textuel`{.action} qui s'ouverte lors de l'étape **4** précédente, cliquez directement **sans effectuer de modifications** sur le bouton `Suivant`{.action}, puis sur `Valider`{.action}. Une nouvelle propagation DNS sera alors initiée.

///

/// details | Comment restaurer une zone DNS ?

Suivez ces étapes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
2. Cliquez sur le menu `Zones DNS`{.action}, puis choisissez le nom de domaine concerné.
3. Sur la droite ou en dessous du tableau, cliquez sur `Voir l'historique de ma zone DNS`{.action}.
4. Dans le tableau de la page qui s'affiche, identifiez la ligne correspondante à la sauvegarde de la zone DNS de votre choix, puis cliquez sur l'icône présente dans la colonne `Restaurer`{.action}. La configuration actuelle de la zone DNS sera écrasée par la configation qui était présente dans la sauvegarde choisie.

> [!primary]
>
> La propagation de la modification d'une zone DNS peut prendre jusqu'à **24** heures pour être effective.

> [!success]
>
> Retrouvez tous les détails dans notre guide « [Gérer l’historique d'une zone DNS](/pages/web_cloud/domains/dns_zone_history) ».

///

/// details | Comment récupérer une copie de ma zone DNS ?

Suivez ces étapes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
2. Cliquez sur le menu `Zones DNS`{.action}, puis choisissez le nom de domaine concerné.
3. Sur la droite ou en dessous du tableau, cliquez sur `Voir l'historique de ma zone DNS`{.action}.
4. Dans le tableau de la page qui s'affiche, identifiez la ligne correspondante à la sauvegarde de la zone DNS de votre choix, puis cliquez sur l'icône présente dans la colonne `Télécharger`{.action}. La copie de la zone DNS ainsi téléchargée sera au format *.txt*.

> [!success]
>
> Retrouvez tous les détails dans notre guide « [Gérer l’historique d'une zone DNS](/pages/web_cloud/domains/dns_zone_history) ».

///

/// details | Puis-je créer une zone DNS pour un sous-domaine ?

Vous pouvez créer une zone DNS pour un sous-domaine.

Pour créer la zone DNS en elle-même, suivez ces étapes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
2. Cliquez sur le menu `Zones DNS`{.action}, puis cliquez sur le bouton `Commander`{.action} en haut à droite du tableau qui s'affiche.
3. Sur la page qui apparaît, renseignez le sous-domaine (par exemple : *www.domain.tld*) pour lequel vous souhaitez créer une zone DNS OVHcloud. Patientez quelques instants le temps que l'outil effectue des vérifications concernant le sous-domaine.
4. Dès que la vérification aboutit, choisissez d'activer ou non les entrées minimales pour la zone DNS que vous allez créer. Ce choix n'est pas définitif puisque vous pourrez toujours [éditer les enregistrements de la zone DNS](/pages/web_cloud/domains/dns_zone_edit) par la suite.
5. Une fois votre choix effectué, poursuivez les étapes jusqu'à la création de la zone DNS.

Cette zone DNS va être installée sur 2 serveurs DNS OVHcloud. Vous devrez déclarer les noms de ces deux serveurs dans la zone DNS active du nom de domaine de votre sous-domaine (par exemple, *www.domain.tld* est un sous-domaine du nom de domaine *domain.tld*).

Pour récupérer les noms des 2 serveurs DNS, suivez ces étapes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
2. Cliquez sur le menu `Zones DNS`{.action}, puis choisissez le sous-domaine concerné.
3. En haut à gauche de la page qui s'affiche, récupérez les 2 noms des serveurs DNS présents sous la mention `Name Servers`. Ces derniers ont l'une des 2 formes suivantes :<br> - `dnsXXX.ovh.net` et `nsXXX.ovh.net` **ou** `dnsXXX.ovh.ca` et `nsXXX.ovh.ca` (où les `X` représentent des chiffres compris entre `0` et `9`). <br> - `dns200.ovh.me` et `ns200.anycast.me`.

Une fois les 2 serveurs DNS en votre possession, déclarez-les à l'aide de deux enregistrements de type NS dans la zone DNS active du nom de domaine dont provient votre sous-domaine.

Cas n°1 - La zone DNS active du nom de domaine dont provient votre sous-domaine est chez OVHcloud :

Suivez ces étapes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
2. Cliquez sur le menu `Zones DNS`{.action}, puis choisissez le nom de domaine concerné.
3. Sur la droite ou en dessous du tableau, cliquez sur `Ajouter une entrée`{.action} puis sélectionnez le type d'enregistrement DNS de type `NS`{.action} pour déclarer un serveur DNS.
4. Dans la fenêtre qui s'ouvre, écrivez dans le champ `Sous-domaine *`{.action} le sous-domaine concerné (par exemple, écrivez **uniquement** *www* si votre nom de domaine est *domain.tld* et que votre sous-domaine complet doit être *www.domain.tld*).Dans le champ `Cible *`{.action} restant, renseignez **un seul** des 2 serveurs DNS.
5. Cliquez ensuite sur `Suivant`{.action}, puis sur `Valider`{.action}.

Réitérez l'opération pour le second serveur DNS que vous n'aurez pas encore déclaré.

Cas n°2 - La zone DNS active du nom de domaine dont provient votre sous-domaine n'est pas chez OVHcloud :

Vous devrez alors déclarer les 2 serveurs DNS pour votre sous-domaine directement auprès du fournisseur DNS du votre nom de domaine dont provient votre sous-domaine.

> [!primary]
>
> Dans les 2 cas, la propagation de la modification d'une zone DNS peut prendre jusqu'à **24** heures pour être effective.

> [!success]
>
> Retrouvez plus de détails dans les guides suivants :
>
>  - « [Créer une zone DNS OVHcloud pour un nom de domaine](/pages/web_cloud/domains/dns_zone_create) ».
>  - « [Éditer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit) ».

///

/// details | Comment rediriger tous les sous-domaines d'un même nom de domaine vers la même adresse IP ?

Suivez ces étapes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
2. Cliquez sur le menu `Zones DNS`{.action}, puis choisissez le nom de domaine concerné.
3. Sur la droite ou en dessous du tableau, cliquez sur `Ajouter une entrée`{.action} puis sélectionnez le type d'enregistrement DNS de type `A`{.action} pour une IPv4 (par exemple : `203.0.113.0`) ou de type `AAAA`{.action} pour une IPv6 (par exemple : `2001:db8:1:1b00:203:0:113:0`).
4. Dans la fenêtre qui s'ouvre et dans le champ de saisie intitulé `Sous-domaine *`{.action}, écrivez la valeur `*`. L'astérisque `*` représentera l'ensemble des sous-domaines (par exemples : `www.domain.tld` ou encore `ovhcloud.domain.tld`) de votre nom de domaine. Complétez le champ `Cible *`{.action} par l'adresse IP désirée. 
5. Cliquez ensuite sur `Suivant`{.action}, puis sur `Valider`{.action}.

> [!primary]
>
> La propagation de la modification d'une zone DNS peut prendre jusqu'à **24** heures pour être effective.

> [!success]
>
> Retrouvez tous les détails dans notre guide « [Éditer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit) ».

///

/// details | Puis-je mettre en place un wildcard dans ma zone DNS ?

Il est possible de mettre en place un wildcard dans une zone DNS OVHcloud.

Pour cela, suivez ces étapes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
2. Cliquez sur le menu `Zones DNS`{.action}, puis choisissez le nom de domaine concerné.
3. Sur la droite ou en dessous du tableau, cliquez sur `Ajouter une entrée`{.action} puis sélectionnez le type d'enregistrement DNS pour lequel vous souhaitez mettre en place un wildcard.
4. Dans la fenêtre qui s'ouvre et dans le champ de saisie intitulé `Sous-domaine *`{.action}, écrivez la valeur `*`. L'astérisque `*` représentera l'ensemble des sous-domaines (par exemples : `www.domain.tld` ou encore `ovhcloud.domain.tld`) de votre nom de domaine. Complétez les autres champs par les valeurs désirées.
5. cliquez ensuite sur `Suivant`{.action}, puis sur `Valider`{.action}.

> [!primary]
>
> La propagation de la modification d'une zone DNS peut prendre jusqu'à **24** heures pour être effective.

> [!success]
>
> Retrouvez tous les détails dans notre guide « [Éditer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit) ».

///

<br>

/// details | J'ai supprimé accidentellement ma zone DNS et je souhaite la restaurer, que faire ?

OVHcloud envoi un e-mail contenant une copie de la zone DNS au format texte une fois votre zone DNS supprimée, afin que vous puissiez restaurer la zone DNS ultérieurement si besoin.

> [!success]
>
> Si vous n'avez pas reçu cet e-mail, vérifiez dans vos courriers indésirables ou suivez ces étapes :
>
> 1. Connectez-vous à votre [espace client OVHcloud](/links/manager), cliquez sur votre nom en haut à droite, puis sur `Mon Compte`{.action}.
> 2. Sur la page qui s'affiche, cliquez sur l'onglet `Emails reçus`{.action}.
> 3. Dans le tableau qui apparaît et parmi la liste des e-mails reçus, cliquez sur l'email concerné pour en afficher le contenu.

Pour restaurer votre zone DNS, suivez ces étapes :

1. Télécharger le fichier contenant la zone DNS depuis l'e-mail reçu sur l'adresse e-mail associée à votre compte client OVHcloud.
2. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
3. Cliquez sur le menu `Noms de domaine`{.action}, puis choisissez le nom de domaine concerné.
4. Sélectionnez l'onglet `Zone DNS`{.action} une fois positionné sur le nom de domaine concerné. **Si la zone DNS est inactive, activez-la depuis cet onglet.**
5. Sur la droite ou en dessous du tableau, cliquez sur `Modifier en mode textuel`{.action}.
6. Dans la fenêtre qui s'ouvre, remplacez tout le contenu qui s'afiche par la copie de la zone DNS supprimée. Cliquez ensuite sur `Suivant`{.action}, puis sur `Valider`{.action}.

> [!primary]
>
> La propagation de la modification d'une zone DNS peut prendre jusqu'à **24** heures pour être effective.

> [!success]
>
> Retrouvez plus de détails dans les guides suivants :
>
>  - « [Créer une zone DNS OVHcloud pour un nom de domaine](/pages/web_cloud/domains/dns_zone_create) ».
>  - « [Éditer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit) ».
>  - « [Gérer l’historique d'une zone DNS](/pages/web_cloud/domains/dns_zone_history) ».

///

/// details | Comment annuler une demande de suppression de ma zone DNS ?

Pour chaque demande de suppression d'un service, un e-mail demandant la confirmation de suppression est envoyée à l'adresse e-mail associé à votre compte client OVHcloud.

Si vous n'avez pas cliqué sur le lien de confirmation présent dans cet e-mail, rassurez-vous, votre one DNS ne sera pas supprimée.

Dans le cas contraire, la suppression est initiée et ne peut plus être annulée. L'opération de suppression peut prendre jusqu'à 3 jours avant que vous puissiez recréer une zone DNS OVHcloud pour votre nom de domaine.

///

/// details | Je ne parviens pas à activer une zone DNS pour mon nom de domaine, que faire ?

Cette situation survient lorsqu'une zone DNS existe déjà pour votre nom de domaine chez OVHcloud.

Suivez ces étapes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
2. Cliquez sur le menu `Zones DNS`{.action}, puis vérifiez si le nom de domaine concerné apparaît.

Cas n°1 - La zone DNS du nom de domaine apparaît dans la liste :

Cela signifie que la zone DNS du nom de domaine existe déjà dans votre [espace client OVHcloud](/links/manager). Vous pourrez la gérer directement à cet endroit.

Cas n°2 - La zone DNS du nom de domaine n'apparaît pas dans la liste :

Cela signifie que la zone DNS du nom de domaine est gérée par un autre identifiant client OVHcloud que le vôtre.

Conformément à la **R**è**G**lementation sur la **P**rotection des **D**onnées (**RGPD**), l'identifiant client sur lequel se trouve la zone DNS restera confidentiel.

Dans cette situation et si vous ne connaissez pas cet autre identifiant client, nous vous invitons à ouvrir [un ticket d'assistance depuis le Centre d'Aide](https://help.ovhcloud.com/csm?id=csm_get_help) pour récupérer la gestion de la zone DNS.

///

/// details | Pourquoi je ne retrouve pas l'onglet "GLUE" dans mon espace client OVHcloud ?

La fonctionnalité n'est pas disponible avec toutes les extensions de nom de domaine.
Si l'onglet n'apparaît pas dans votre [espace client OVHcloud](/links/manager), c'est que l'option "GLUE" est indisponible pour votre nom de domaine.

> [!success]
>
> Retrouvez tous les détails dans notre guide « [Personnaliser les sereurs DNS d'un nom de domaine (Glue records)](/pages/web_cloud/domains/glue_registry) ».

///

## Serveurs DNS

> [!primary]
>
> La modification des serveurs DNS est une manipulation sensible et peut engendrer une interruption des services associés à votre nom de domaine (hébergement web, e-mail, etc.). En cas de doute, n'hésitez pas à contacter un [prestataire spécialisé](/links/partner)

/// details | Comment modifier mes serveurs DNS ?

Suivez ces étapes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
2. Cliquez sur le menu `Noms de domaine`{.action}, puis choisissez le nom de domaine concerné.
3. Sélectionnez l'onglet `Serveurs DNS`{.action} une fois positionné sur le nom de domaine concerné.
4. Pour modifier les serveurs DNS, cliquez sur le bouton `Modifier les serveurs DNS`{.action} situé à droite du tableau « serveurs DNS ». En fonction de la résolution de votre écran, le bouton peut se trouver en dessous du tableau.

Une nouvelle page apparaît sur laquelle vous pourrez modifier les serveurs DNS pour votre nom de domaine.

> [!success]
>
> Retrouvez tous les détails dans notre guide « [Modifier les serveurs DNS d'un nom de domaine OVHcloud](/pages/web_cloud/domains/dns_server_edit) ».

///

/// details | Comment personnaliser mes serveurs DNS ?

Suivez ces étapes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
2. Cliquez sur le menu `Noms de domaine`{.action}, puis choisissez le nom de domaine concerné.
3. Sélectionnez l'onglet `Serveurs DNS`{.action} une fois positionné sur le nom de domaine concerné.
4. Pour modifier les serveurs DNS, cliquez sur le bouton `Modifier les serveurs DNS`{.action} situé à droite du tableau « serveurs DNS ». En fonction de la résolution de votre écran, le bouton peut se trouver en dessous du tableau.

Une nouvelle page apparaît sur laquelle vous pourrez personnaliser les serveurs DNS pour votre nom de domaine.

> [!success]
>
> Retrouvez tous les détails dans notre guide « [Modifier les serveurs DNS d'un nom de domaine OVHcloud](/pages/web_cloud/domains/dns_server_edit) ».

///

/// details | Comment remplacer mes serveurs DNS par ceux d'OVHcloud ?

Suivez ces étapes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
2. Cliquez sur le menu `Noms de domaine`{.action}, puis choisissez le nom de domaine concerné.
3. Sélectionnez l'onglet `Serveurs DNS`{.action} une fois positionné sur le nom de domaine concerné.
4. Pour modifier les serveurs DNS, cliquez sur le bouton `Modifier les serveurs DNS`{.action} situé à droite du tableau « serveurs DNS ». En fonction de la résolution de votre écran, le bouton peut se trouver en dessous du tableau.

Une nouvelle page apparaît sur laquelle vous pourrez remplacer les serveurs DNS pour votre nom de domaine par ceux d'OVHcloud.

> [!success]
>
> Retrouvez tous les détails dans notre guide « [Modifier les serveurs DNS d'un nom de domaine OVHcloud](/pages/web_cloud/domains/dns_server_edit) ».

///

/// details | Dans mon espace client, j'ai un message d'erreur m'indiquant que je n'utilise pas les serveurs DNS d'OVHcloud pour mon nom de domaine, que faire ?

Dans votre [espace client OVHcloud](/links/manager), ce message indique uniquement que la zone DNS créée pour votre nom de domaine n'est pas sa zone DNS active. 

En d'autres termes, cela signifie que la configuration présente dans cette zone DNS n'est pas celle qui est actuellement appliquée à votre nom de domaine.

Toutefois, vérifiez que les serveurs DNS mentionnés dans le message d'erreur correspondent bien aux serveurs DNS que vous souhaitez appliquer à votre nom de domaine. Vérifiez ensuite la configuration de la zone DNS déclarée sur ces mêmes serveurs DNS auprès de votre fournisseur DNS.

Dans le cas contraire, vous pourrez préparer la configuration DNS de la zone DNS présente chez OVHcloud pour que celle-ci corresponde à vos besoins, puis l'activer pour votre nom de domaine.

> [!success]
>
> Retrouvez plus de détails dans les guides suivants :
>
>  - « [Éditer une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit) ».
>  - « [Modifier les serveurs DNS d'un nom de domaine OVHcloud](/pages/web_cloud/domains/dns_server_edit) ».

///

/// details | Je ne parviens pas à modifier les serveurs DNS d'un nom de domaine depuis mon espace client OVHcloud, que faire ?

Cela signifie que vous ne disposez que de la gestion de la zone DNS du nom de domaine mais pas celle du nom de domaine en lui-même.

Pour le vérifier, suivez ces étapes :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager), puis rendez-vous dans la partie `Web Cloud`{.action}.
2. Cliquez sur le menu `Noms de domaine`{.action}, puis vérifiez si le nom de domaine concerné apparaît.

Cas n°1 - Le nom de domaine n'apparaît pas dans la liste :

Cela signifie que le nom de domaine n'est pas géré depuis votre [espace client OVHcloud](/links/manager). Effectuez une requête [WHOIS](/links/web/domains-whois) avec ce dernier pour connaître l'endroit où il est enregistré.

Vous pourrez ensuite faire l'une des actions suivantes (si vous êtes le titulaire déclaré sur le whois du nom de domaine): 

- Le nom de domaine est enregistré chez OVHcloud : Vous pourrez effectuer une [procédure de récupération des contacts](/links/web/) pour que votre nom de domaine soit géré dans votre [espace client OVHcloud](/links/manager).
- Le nom de domaine n'est pas enregistré chez OVHcloud : Vous pourrez réaliser une opération de [transfert entrant](/pages/web_cloud/domains/transfer_incoming_generic_domain) vers OVHcloud pour que votre nom de domaine soit géré dans votre [espace client OVHcloud](/links/manager).

Cas n°2 - Le nom de domaine apparaît dans la liste :

Cela signifie que vous ne disposez pas des droits suffisants pour gérer le nom de domaine depuis votre [espace client OVHcloud](/links/manager). Effectuez une requête [WHOIS](/links/web/domains-whois) pour vérifier que vous êtes bien déclaré en tant que titulaire du nom de domaine.

Vous pourrez ensuite effectuer une [procédure de récupération des contacts](/links/web/) pour que votre nom de domaine soit entièrement géré dans votre [espace client OVHcloud](/links/manager).

///

## Aller plus loin <a name="go-further"></a>

[E-mails mutualisés MX Plan FAQ](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/faq-emails)

[Hébergement Web - FAQ](/pages/web_cloud/web_hosting/faq-web_hosting)

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre [communauté d'utilisateurs](/links/community).