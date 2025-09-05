---
title: 'MX Plan - Configurer son adresse e-mail sur Thunderbird pour Windows'
excerpt: 'Retrouvez ici les informations pour configurer votre adresse e-mail sur Thunderbird.'
updated: 2024-10-01
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

Les comptes MX Plan peuvent être configurés sur différents logiciels de messagerie compatibles. Cela vous permet d’utiliser votre adresse e-mail depuis l’appareil de votre choix. Thunderbird est un client de messagerie libre et gratuit.

**Découvrez comment configurer votre adresse e-mail MX Plan sur Thunderbird pour Windows.**

## Prérequis

- Disposer d’une adresse e-mail MX Plan (comprise dans l’offre MX Plan ou dans une offre d’[hébergement web OVHcloud](/links/web/hosting)).
- Disposer du logiciel Thunderbird installé sur votre Windows.
- Posséder les identifiants relatifs à l'adresse e-mail que vous souhaitez paramétrer.

/// details | Informations relatives à la gestion et configuration des services OVHcloud

OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.

Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [partenaire spécialisé](https://marketplace.ovhcloud.com/c/support-collaboration) et/ou de contacter l'éditeur du service si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section « Aller plus loin » de ce guide.

///

## En pratique

### Ajouter le compte

- **Lors du premier démarrage de l'application** : un assistant de configuration s'affiche et vous invite à renseigner votre adresse e-mail.

- **Si un compte a déjà été paramétré** :

    1. Cliquez sur le menu « &#9776; » dans la barre horizontale supérieure.
    2. Cliquez sur `Nouveau Compte`{.action}.
    3. Cliquez sur `Adresse E-mail`{.action} .

![thunderbird](images/configuration-thunderbird-windows-mxplan-01.png){.thumbnail .w-400}

Dans la fenêtre qui s'affiche, saisissez les 3 informations suivantes:

- Votre nom complet (Nom d'affichage)
- Adresse E-mail 
- Mot de passe.

Cliquez sur `Configuration Manuelle`{.action} pour compléter les paramètres.

![thunderbird](images/configuration-thunderbird-windows-mxplan-02.png){.thumbnail .w-400}

Complétez les paramètres du serveur :

> [!warning]
>
> Il est nécessaire de bien relever la valeur correspondante à votre localisation (**EUROPE** ou **AMERIQUE / ASIE-PACIFIQUE**).

Sélectionnez l'onglet correspondant à votre type de configuration :

> [!tabs]
> **SERVEUR ENTRANT (IMAP)**
>> - **Protocole** : IMAP
>> - **Nom d'hôte (EUROPË)** : imap.mail.ovh.net **ou** ssl0.ovh.net
> - **Nom d'hôte (MERIQUE/ASIE-PACIFIQUE )** : imap.mail.ovh.ca
>> - **Port** : 993
>> - **Sécurité de la connexion** : SSL/TLS
>> - **Authentification** : Mot de passe normal
>> - **Identifiant** : votre adresse e-mail complète
>>
> **SERVEUR ENTRANT (POP)**
>> - **Protocole** : POP3
>> - **Nom d'hôte (EUROPË)** : pop.mail.ovh.net **ou** ssl0.ovh.net
>> - **Nom d'hôte (MERIQUE/ASIE-PACIFIQUE )** : pop.mail.ovh.ca
>> - **Port** : 995
>> - **Sécurité de la connexion** : SSL/TLS
>> - **Authentification** : Mot de passe normal
>> - **Identifiant** : votre adresse e-mail complète

**SERVEUR SORTANT (SMTP)**
- **Nom d'hôte (EUROPË)** :smtp.mail.ovh.net **ou** ssl0.ovh.net
- **Nom d'hôte (MERIQUE/ASIE-PACIFIQUE )** :smtp.mail.ovh.ca
- **Port** 465
- **Sécurité de la connexion** SSL/TLS
- **Méthode d'authentification** Mot de passe normal
- **Identifiant** votre adresse e-mail complète

Cliquez sur `Terminé`{.action} pour finaliser la configuration.

![thunderbird](images/configuration-thunderbird-windows-mxplan-03.png){.thumbnail .w-400}

### Utiliser l'adresse e-mail

Une fois l'adresse e-mail configurée, il ne reste plus qu’à l'utiliser ! Vous pouvez dès à présent envoyer et recevoir des messages.

OVHcloud propose aussi une application web permettant d'accéder à votre adresse e-mail depuis un navigateur internet. Celle-ci est accessible à l’adresse [Webmail](/links/web/email). Vous pouvez vous y connecter grâce aux identifiants de votre adresse e-mail.

### Récupérer une sauvegarde de votre adresse e-mail

Si vous devez effectuer une manipulation qui risquerait d'entrainer la perte des données de votre compte e-mail, nous vous conseillons d'effectuer une sauvegarde préalable du compte e-mail concerné. Pour ce faire, consultez le paragraphe « **Exporter** » dans la partie « **Thunderbird** » de notre guide [Migrer manuellement votre adresse e-mail](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration#exporter).

### Modifier les paramètres existants

Si votre compte e-mail est déjà paramétré et que vous devez accéder aux paramètres du compte pour les modifier :

1. Cliquez sur le menu « &#9776; » dans la barre horizontale supérieure.
2. Cliquez sur `Paramètre du compte`{.action}.

![Thunderbird](images/configuration-thunderbird-windows-mxplan-04.png){.thumbnail}

- Pour modifier les paramètres liés à la **réception** de vos e-mails, cliquez sur `Paramètres serveur`{.action} dans la colonne de gauche sous votre adresse e-mail.

![Thunderbird](images/configuration-thunderbird-windows-mxplan-05.png){.thumbnail}

- Pour modifier les paramètres liés à **l'envoi** de vos e-mails, cliquez sur `Serveur sortant (SMTP)`{.action} tout en bas de la colonne de gauche.
- Cliquez sur l'adresse e-mail concernée dans la liste , puis cliquez sur `Modifier`{.action}.

![Thunderbird](images/configuration-thunderbird-windows-mxplan-06.png){.thumbnail}
## Aller plus loin

> [!primary]
>
> Pour plus d'informations sur la configuration d'une adresse e-mail depuis l'application Thunderbird sur Windows, consultez [le centre d'aide Mozilla](https://support.mozilla.org/fr/kb/configurer-un-compte-manuellement#thunderbird:win10:tb115).

[Utiliser le webmail Roundcube](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_roundcube)

[Utiliser le webmail Zimbra](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_zimbra)

[Utiliser le webmail Outlook Web App (OWA)](/pages/web_cloud/email_and_collaborative_solutions/using_the_outlook_web_app_webmail/email_owa)

Pour des prestations spécialisées (référencement, développement, etc.), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre [communauté d'utilisateurs](/links/community).

Échangez avec notre [communauté d'utilisateurs](/links/community).