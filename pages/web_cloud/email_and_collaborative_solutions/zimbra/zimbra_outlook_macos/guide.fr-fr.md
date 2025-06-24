---
title: "Zimbra Pro - Configurer son compte e-mail via EWS sur Outlook pour Mac"
excerpt: "Découvrez comment configurer votre adresse e-mail Zimbra Pro sur Outlook pour macOS via le protocole EWS"
updated: 2025-06-24
---

<style>
.h-500 {
  max-height:500px !important;
}
</style>

## Objectif

Les comptes Zimbra Pro peuvent être configurés en utilisant le protocole EWS (Exchange Web Services) sur un Mac, cela vous permet de configurer l'ensemble des fonctionnalités collaboratives de votre adresse e-mail en une seule fois. L'application [Outlook sur macOS](https://apps.apple.com/fr/app/microsoft-outlook/id985367838?mt=12) est disponible sur l'App Store d'Apple.

**Découvrez comment configurer votre adresse e-mail Zimbra Pro sur Outlook pour macOS via le protocole EWS**

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
>
> Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [partenaire spécialisé](https://marketplace.ovhcloud.com/c/support-collaboration) et/ou de contacter l'éditeur du service si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section « Aller plus loin » de ce guide.

## Prérequis

- Disposer d’une adresse e-mail [Zimbra Pro](/links/web/zimbra).
- Disposer de l'application [Outlook sur macOS](https://apps.apple.com/fr/app/microsoft-outlook/id985367838?mt=12).
- Posséder les identifiants relatifs à l'adresse e-mail que vous souhaitez paramétrer.

## En pratique

### Ajouter le compte <a name="add-account"></a>

- **Lors du premier démarrage de l'application** : un assistant de configuration s'affiche directement et vous invite à saisir la première adresse e-mail que vous souhaitez ajouter.

- **Si un compte a déjà été paramétré** : 
    1. Cliquez sur `Outils`{.action} dans la barre de menu en haut de votre écran.
    2. Cliquez sur `Comptes`{.action}.
    3. Depuis la fenêtre « Comptes » qui s'affiche, cliquez sur `+`{.action} en bas à gauche, puis cliquez sur `Nouveau compte`{.action}.

![mail macOS](images/outlook-macos-add-step00.png){.thumbnail .h-500}

Suivez les étapes d'installation en cliquant sur les onglets ci-dessous :

> [!tabs]
> **Etape 1**
>>
>> Saisissez votre adresse e-mail sous la mention « Adresse de courrier », puis cliquez sur `Continuer`{.action}.
>>
>> ![mail macos](images/outlook-macos-add-step01.png){.thumbnail .h-500}
>>
> **Etape 2**
>>
>> - **Si la fenêtre IMAP/POP apparait**, cliquez sur `Ce n'est pas un compte POP/IMAP`{.action}, puis choisissez `Exchange`{.action} depuis la fenêtre « Choisir le fourniseur »
>> - **Si vous tombez directement sur « Choisir le fourniseur »**, choisissez `Exchange`{.action}
>>
>> ![mail macos](images/outlook-macos-add-step02.png){.thumbnail .h-500}
>>
> **Etape 3**
>>
>> Vérifiez et complétez les informations suivantes :
>>
>> - **Méthode** : Laissez `Nom d'utilisateur et mot de passe`.
>> - **Adresse de courrier** : saisissez votre adresse e-mail complète.
>> - **DOMAINE\Nom d'utilisateur ou adresse de courrier** : saisissez votre adresse e-mail complète.
>> - **Mot de pass** : saisissez le mot de passe assossié à l'adresse e-mail.
>> - **Serveur** : saisissez « zimbra1.mail.ovh.net ».
>>
>> Pour finaliser la configuration, appuyez sur `Ajouter un compte`{.action} et sélectionnez les fonctionnalités que vous souhaitez explorer sur votre Mac.
>>
>> ![mail macos](images/outlook-macos-add-step03.png){.thumbnail .h-500}
>>

> [!warning]
>
> Si, après avoir suivi les étapes de configuration ci-dessus, vous rencontrez un défaut d'envoi ou de réception, consultez la rubrique « [Modifier les paramètres existants](#modify-settings) ».

### Utiliser l'adresse e-mail

Une fois l'adresse e-mail configurée, il ne reste plus qu’à l'utiliser ! Vous pouvez dès à présent envoyer et recevoir des messages, mais aussi gérer vos calendriers et tâches.

OVHcloud propose aussi une application web permettant d'accéder à votre adresse e-mail depuis un navigateur internet. Celle-ci est accessible via ce lien : [Webmail](/links/web/email). Vous pouvez vous y connecter grâce aux identifiants de votre adresse e-mail. Pour toute question relative à son utilisation, aidez-vous de notre guide [Utiliser le webmail Zimbra](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_zimbra).

### Comment modifier les paramètres existants ?<a name="modify-settings"></a>

Si votre compte e-mail est déjà paramétré et que vous souhaitez le paramétrer à nouveau, suivez les étapes d'installation en cliquant sur les onglets ci-dessous :

1. Cliquez sur `Outils`{.action} dans la barre de menu en haut de votre écran.
1. Cliquez sur `Comptes`{.action}.
1. Sélectionnez votre comptre dans la colonne de gauche.
1. Cliquez sur `Avancé...`{.action} en bas à droite.

![outlook ios](images/outlook-app-ios-modify-account-01.png){.thumbnail .h-500}

Retrouvez les paramètres à **l'étape 3** du chapitre [Ajouter le compte](#add-account).

### Comment supprimer un compte e-mail ?<a name="delete-account"></a>

1. Cliquez sur `Outils`{.action} dans la barre de menu en haut de votre écran.
1. Cliquez sur `Comptes`{.action}.
1. Sélectionnez votre comptre dans la colonne de gauche.
1. Cliquez sur `-`{.action} en bas à gauche

![outlook ios](images/outlook-app-ios-modify-delete-01.png){.thumbnail .h-500}


## Aller plus loin

> [!primary]
>
> Pour plus d'informations sur la configuration d'une adresse e-mail depuis l'application Mail sur macOS, consultez [le centre d'aide Apple](https://support.apple.com/fr-fr/102619).

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre [communauté d'utilisateurs](/links/community).