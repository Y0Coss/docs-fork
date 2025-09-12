---
title: 'Exchange - Configurer son adresse e-mail sur Thunderbird pour macOS'
excerpt: 'Découvrez comment configurer votre adresse e-mail Exchange sur Thunderbird pour macOS'
updated: 2025-09-12
---

<style>
details>summary {
    color:rgb(255,165,0) !important;
    cursor: pointer;
}
details>summary::before {
    content:'\25B6';
    padding-right:1ch;
}
details[open]>summary::before {
    content:'\25BC';
}
.w-400 {
  max-width:400px !important;
}
</style>

## Objectif

Les comptes Exchange peuvent être configurés sur différents logiciels de messagerie compatibles. Cela vous permet d’utiliser votre adresse e-mail depuis l’appareil de votre choix. Thunderbird est un client de messagerie libre et gratuit.

**Découvrez comment configurer votre adresse e-mail Exchange sur Thunderbird pour macOS.**

## Prérequis

- Disposer d’une adresse e-mail [Hosted Exchange](/links/web/emails-hosted-exchange) ou [Private Exchange](/links/web/emails-private-exchange).
- Disposer du logiciel Thunderbird installé sur votre mac.
- Posséder les identifiants relatifs à l'adresse e-mail que vous souhaitez paramétrer.

/// details | Informations relatives à la gestion et configuration des services OVHcloud

OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.

Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [partenaire spécialisé](https://marketplace.ovhcloud.com/c/support-collaboration) et/ou de contacter l'éditeur du service si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section « Aller plus loin » de ce guide.

///

## En pratique

> [!warning]
>
> Dans notre exemple, nous utilisons la mention serveur : ex?.mail.ovh.net. Vous devrez remplacer le « ? » par le chiffre désignant le serveur de votre service Exchange.
>
> 1. Connectez-vous à votre [espace client OVHcloud](/links/manager).
> 1. Rendez-vous dans la partie `Web Cloud`{.action}.
> 1. Dans la rubrique `MICROSOFT`, cliquez sur `Exchange`{.action}.
> 1. Sélectionnez la plateforme concernée.
> 1. Le nom du serveur est visible dans le cadre **Connexion** de l'onglet `Informations Générales`{.action}.
>

### Ajouter le compte

- **Lors du premier démarrage de l'application** : un assistant de configuration s'affiche et vous invite à renseigner votre adresse e-mail.

- **Si un compte a déjà été paramétré** :

    1. Cliquez sur le menu « &#9776; » dans la barre horizontale supérieure.
    2. Cliquez sur `Nouveau Compte`{.action}.
    3. Cliquez sur `Adresse E-mail`{.action} .

![thunderbird](images/configuration-thunderbird-mac-01.png){.thumbnail .w-400}

Complétez les paramètres du serveur :

> [!tabs]
> **Étape 1**
>> Dans la fenêtre qui s'affiche, saisissez les 3 informations suivantes:
>>
>> - Votre nom complet (Nom d'affichage)
>> - Adresse E-mail 
>>
>> Cliquez sur `Continuer`{.action} pour compléter les paramètres.
>>
>> ![thunderbird](images/configuration-thunderbird-exchange-02.png){.thumbnail .w-400}
>>
> **Étape 2**
>>
>> Lorsque Thunderbird détecte un nom de domaine OVHcloud, une configuration automatique relative à l'offre MX Plan est proposée. Cliquez sur `MODIFIER LA CONFIGURATION`{.action}.
>>
>> ![thunderbird](images/configuration-thunderbird-ssl0-03.png){.thumbnail .w-400}
>>
> **Étape 3**
>> Paramètres du serveur de réception :<br>
>> - **Protocole** IMAP
>> - **Nom d'hôte** ex?.mail.ovh.net (remplacez bien «?» par le numéro de votre serveur)
>> - **Port** 993
>> - **Sécurité de la connexion** SSL/TLS
>> - **Méthode d'authentification** Mot de passe normal
>> - **Nom d'utilisateurs** votre adresse e-mail complète
>>
>> ![thunderbird](images/configuration-thunderbird-exchange-04.png){.thumbnail .w-400}
>>
> **Étape 4**
>> Paramètres du serveur d'envoi :<br>
>> - **Protocole** SMTP 
>> - **Nom d'hôte** ex?.mail.ovh.net (remplacez bien «?» par le numéro de votre serveur)
>> - **Port** 587
>> - **Sécurité de la connexion** STARTTLS
>> - **Méthode d'authentification** Mot de passe normal
>> - **Nom d'utilisateurs** votre adresse e-mail complète
>> 
>> 1. Cliquez sur `Tester`{.action} pour vérifier les paramètres saisies.
>> 2. Cliquez sur `Continuer`{.action} pour valider les paramètres.
>>
>> ![thunderbird](images/configuration-thunderbird-exchange-05.png){.thumbnail .w-400}
>>
> **Étape 5**
>> Saisir le mot de passe associé à l'adresse e-mail, puis cliquez sur `Continuer`{.action} pour finaliser la configuration.
>>
>> ![thunderbird](images/configuration-thunderbird-password-06.png){.thumbnail .w-400}
>>

> [!primary]
>
> **Configuration POP**
>
> Si vous souhaitez une configuration POP pour votre adresse e-mail, remplacez les paramètres de **l'étape 4** par les suivants
>
> Paramètres du serveur de réception :<br>
> - **Protocole** POP3
> - **Nom d'hôte** ex?.mail.ovh.net (remplacez bien «?» par le numéro de votre serveur)
> - **Port** 995
> - **Sécurité de la connexion** SSL/TLS
> - **Méthode d'authentification** Mot de passe normal
> - **Nom d'utilisateurs** votre adresse e-mail complète


### Utiliser l'adresse e-mail

Une fois l'adresse e-mail configurée, il ne reste plus qu’à l'utiliser ! Vous pouvez dès à présent envoyer et recevoir des messages.

OVHcloud propose également une application web permettant d'accéder à votre adresse e-mail depuis un navigateur internet. Celle-ci est accessible à l’adresse [Webmail](/links/web/email). Vous pouvez vous y connecter grâce aux identifiants de votre adresse e-mail.

### Récupérer une sauvegarde de votre adresse e-mail

Si vous devez effectuer une manipulation qui risquerait d'entrainer la perte des données de votre compte e-mail, nous vous conseillons d'effectuer une sauvegarde préalable du compte e-mail concerné. Pour ce faire, consultez le paragraphe « **Exporter** » dans la partie « **Thunderbird** » de notre guide [Migrer manuellement votre adresse e-mail](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration#exporter).

### Modifier les paramètres existants

Si votre compte e-mail est déjà paramétré et que vous devez accéder aux paramètres du compte pour les modifier :

1. Cliquez sur le menu « &#9776; » dans la barre horizontale supérieure.
2. Cliquez sur `Paramètre des comptes`{.action}.

![Thunderbird](images/configuration-thunderbird-mac-07.png){.thumbnail}

- Pour modifier les paramètres liés à la **réception** de vos e-mails, cliquez sur `Paramètres serveur`{.action} dans la colonne de gauche sous votre adresse e-mail.

![thunderbird](images/configuration-thunderbird-exchange-mac-08.png){.thumbnail .w-400}

- Pour modifier les paramètres liés à **l'envoi** de vos e-mails, cliquez sur `Serveur sortant (SMTP)`{.action} tout en bas de la colonne de gauche.
- Cliquez sur l'adresse e-mail concernée dans la liste , puis cliquez sur `Modifier`{.action}.

![thunderbird](images/configuration-thunderbird-exchange-mac-09.png){.thumbnail .w-400}

## Aller plus loin

> [!primary]
>
> Pour plus d'informations sur la configuration d'une adresse e-mail depuis le client de messagerie Thunderbird, consultez [le centre d'aide de Mozilla](https://support.mozilla.org/products/thunderbird).

[Premiers pas avec le service Hosted Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_hosted)

[Premiers pas avec le service Private Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_private)

Pour des prestations spécialisées (référencement, développement, etc.), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre [communauté d'utilisateurs](/links/community).