---
title: "Zimbra Pro - Configurer son compte e-mail via Active Sync sur Outlook pour Android"
excerpt: "Découvrez comment configurer votre adresse e-mail Zimbra Pro sur l'application mobile Outlook pour Android via le protocole Active Sync"
updated: 2025-06-24
---

<style>
.h-500 {
  max-height:500px !important;
}
</style>

## Objectif

Les comptes Zimbra Pro peuvent être configurés en utilisant le protocole Active Sync sur un mobile Android, cela vous permet de configurer l'ensemble des fonctionnalités collaboratives de votre adresse e-mail en une seule fois. L'application Outlook de Microsoft sur Android est disponible gratuitement depuis le Google Play Store.

**Découvrez comment configurer votre adresse e-mail Zimbra Pro sur l'application mobile Outlook pour Android via le protocole Active Sync**

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
>
> Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [partenaire spécialisé](https://marketplace.ovhcloud.com/c/support-collaboration) et/ou de contacter l'éditeur du service si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section « Aller plus loin » de ce guide.

## Prérequis

- Disposer d’une adresse e-mail [Zimbra Pro](/links/web/zimbra).
- Disposer de l'application Outlook sur votre appareil mobile [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=fr).
- Posséder les identifiants relatifs à l'adresse e-mail que vous souhaitez paramétrer.

> [!primary]
>
> Cette documentation a été réalisée depuis un appareil utilisant la version 14 d'Android.

## En pratique

### Ajouter le compte <a name="add-account"></a>

- **Lors du premier démarrage de l'application** : un assistant de configuration s'affiche, appuyez sur `Ajouter un compte`{.action}.

![outlook android](images/outlook-app-android-add01.png){.thumbnail .h-500}

- **Si un compte a déjà été paramétré** :
    - Appuyez sur l'enveloppe « &#9993; » dans la partie supérieure gauche de votre écran.
    - Appuyez ensuite sur le bouton `+`{.action} dans la barre verticale de gauche.
    - Appuyez sur `Ajouter un compte`{.action}.

![outlook android](images/outlook-app-android-add02.png){.thumbnail .h-500}

Suivez les étapes d'installation en cliquant sur les onglets ci-dessous :

> [!tabs]
> **Etape 1**
>>
>> Saisissez votre adresse e-mail et appuyez sur `Continuer`{.action}.
>>
>> ![outlook android](images/outlook-app-android-add-step01.png){.thumbnail .h-500}
>>
> **Etape 2**
>>
>> ![outlook android](images/zimbra-activesync-outlook-android03.png){.thumbnail .h-500}
>>
>> - Sélectionnez **Exchange** dans la liste des types de compte.
>> - **Ou** si vous optenez une fenêtre vous demandant de sélectionnez entre **IMAP** ou **POP3**, appuyez sur l'un ou l'autre. Sur la fenêtre suivante, appuyez sur le bouton `?` dans le coin supérieur droit de l'écran, puis choisissez `Changer de fournisseur de compte`{.action}. Sélectionnez alors `Exchange`.
>>
>> ![outlook android](images/outlook-app-android-add-step021.png){.thumbnail .h-500}
>>
> **Etape 3 - IMAP**
>>
>> Dans la fenêtre suivante, cochez `Paramètres avancés`{.action} et  complétez les informations suivantes :
>>
>> - **Adresse e-mail** : saisissez votre adresse e-mail complète
>> - **Description** : saisissez un nom permettant d'identifier ce compte parmis vos autres comptes e-mail enregistrés sur Outlook.
>> - **Serveur** : saisissez « zimbra1.mail.ovh.net »
>> - **Domaine** : laissez vide
>> - **Nom d'utilisateur** : votre adresse e-mail complète
>>
>> Pour finaliser la configuration, appuyez sur le bouton « &#10003; »
>>
>> ![outlook android](images/outlook-app-android-add-step03.png){.thumbnail .h-500}
>>

### Utiliser l'adresse e-mail

Une fois l'adresse e-mail configurée, il ne reste plus qu’à l'utiliser ! Vous pouvez dès à présent envoyer et recevoir des messages, mais aussi gérer vos calendriers et tâches.

OVHcloud propose aussi une application web permettant d'accéder à votre adresse e-mail depuis un navigateur internet. Celle-ci est accessible via ce lien : [Webmail](/links/web/email). Vous pouvez vous y connecter grâce aux identifiants de votre adresse e-mail. Pour toute question relative à son utilisation, aidez-vous de notre guide [Utiliser le webmail Zimbra](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_zimbra).

### Comment modifier les paramètres existants ?<a name="modify-settings"></a>

L'application Outlook ne permet pas de modifier les paramètres serveur de votre compte e-mail.

Si votre compte e-mail est déjà paramétré et que vous souhaitez le paramétrer à nouveau, vous devez alors le supprimer et le recréer :

1. Appuyez sur l'enveloppe « &#9993; » dans la partie supérieure gauche de votre écran.
1. Appuyez sur l'icöne de réglage « &#9965; » dans le bas de la colonne de gauche.
1. Dans la section « Général » appuyez sur `Comptes` pour visualiser l'ensemble des adresses e-mail configurées sur l'application.

![outlook android](images/outlook-app-android-delete-account-01.png){.thumbnail .h-500}

- Sélectionnez le compte e-mail concerné.
- Appuyez sur `Supprimer le compte`{.action}.
- Appuyez sur `Supprimer`{.action} à la question  « Voulez-vous supprimer le compte ? ».

![outlook android](images/outlook-app-android-delete-account-02.png){.thumbnail .h-500}

> [!success]
>
> Une fois votre compte e-mail supprimé, suivez les instructions de la partie « [Ajouter le compte](#add-account) » sur cette documentation.

## Aller plus loin

> [!primary]
>
> Pour plus d'informations sur la configuration d'une adresse e-mail depuis l'application Outlook sur Android, consultez [le centre d'aide Microsoft](https://support.microsoft.com/office/configurer-le-courrier-%C3%A9lectronique-%C3%A0-l-aide-de-l-application-outlook-pour-android-886db551-8dfa-4fd5-b835-f8e532091872).

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre [communauté d'utilisateurs](/links/community).