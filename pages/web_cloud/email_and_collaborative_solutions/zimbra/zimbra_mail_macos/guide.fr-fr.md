---
title: "Zimbra Pro - Configurer son compte e-mail via EWS dans Mail sur Mac"
excerpt: "Découvrez comment configurer votre adresse e-mail Zimbra Pro sur l'application Mail sur Mac via le protocole EWS"
updated: 2025-06-24
---

<style>
.h-500 {
  max-height:500px !important;
}
</style>

## Objectif

> [!primary]
> Ce guide nécessite le service [Zimbra Pro](https://www.ovhcloud.com/fr/emails/zimbra-emails/) qui sera disponible en bêta à partir de juillet 2025. 

Les comptes Zimbra Pro peuvent être configurés en utilisant le protocole EWS (Excahnge Web Services) sur un macOS, cela vous permet de configurer l'ensemble des fonctionnalités collaboratives de votre adresse e-mail en une seule fois. L'application Mail sur macOS est disponible nativement.

**Découvrez comment configurer votre adresse e-mail Zimbra Pro sur l'application Mail sur Mac via le protocole EWS**

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
>
> Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [partenaire spécialisé](https://marketplace.ovhcloud.com/c/support-collaboration) et/ou de contacter l'éditeur du service si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section « Aller plus loin » de ce guide.

## Prérequis

- Disposer d’une adresse e-mail [Zimbra Pro](/links/web/zimbra).
- Disposer de l'application Mail sur votre iPhone ou iPad.
- Posséder les identifiants relatifs à l'adresse e-mail que vous souhaitez paramétrer.

## En pratique

### Ajouter le compte <a name="add-account"></a>

- **Lors du premier démarrage de l'application** : un assistant de configuration s'affiche directement et vous invite à choisir votre type de compte.

- **Si un compte a déjà été paramétré** : 
    - Cliquez sur `Mail`{.action} dans la barre de menu en haut de votre écran.
    - Cliquez sur `Comptes`{.action}.
    - Dans la fenêtre « Comptes Internet » qui s'affiche, cliquez sur `Ajouter un compte`{.action}

![mail macOS](images/mail-macos-add-step00.png){.thumbnail .h-500}

Suivez les étapes d'installation en cliquant sur les onglets ci-dessous :

> [!tabs]
> **Etape 1**
>>
>> - Sélectionnez `Microsoft Exchange`{.action}.
>> - Définissez un **nom** et saisissez votre **adresse e-mail**, cliquez ensuite sur `Se connecter`{.action}.
>>
>> ![mail macos](images/mail-macos-add-step01.png){.thumbnail .h-500}
>>
> **Etape 2**
>>
>> - Choisissez `Configurer manuellement`{.action} depuis la fenêtre qui apparait.
>> - Saisissez ensuite le **mot de passe** de votre adresse e-mail en complément des informations déjà saisies
>>
>> ![mail macos](images/mail-macos-add-step02.png){.thumbnail .h-500}
>>
> **Etape 3**
>>
>> Vérifiez et complétez les informations suivantes :
>>
>> - **Adresse E-maill** : saisissez votre adresse e-mail complète.
>> - **Nom d'utilisateur** : votre adresse e-mail complète.
>> - **Mot de pass** : saisissez le mot de passe assossié à l'adresse e-mail.
>> - **URL interne** : saisissez « zimbra1.mail.ovh.net ».
>> - **URL externe** : saisissez « zimbra1.mail.ovh.net ».
>>
>> Pour finaliser la configuration, appuyez sur `Se connecter`{.action} et sélectionnez les fonctionnalités que vous souhaitez explorer sur votre Mac.
>>
>> ![mail macos](images/mail-macos-add-step04.png){.thumbnail .h-500}
>>
>> > [!warning]
>> >
>> > Il est normal de voir apparaître le message en rouge « **Impossible de vérfier le nom ou le mot de passe du compte** » lorsque la fenêtre apparaît la première fois. Néanmoins, si ce message persiste après validation, cela signifie que les informations saisies sont erronées.<br><br>

> [!warning]
>
> Si, après avoir suivi les étapes de configuration ci-dessus, vous rencontrez un défaut d'envoi ou de réception, consultez la rubrique « [Modifier les paramètres existants](#modify-settings) ».

### Utiliser l'adresse e-mail

Une fois l'adresse e-mail configurée, il ne reste plus qu’à l'utiliser ! Vous pouvez dès à présent envoyer et recevoir des messages, mais aussi gérer vos calendriers et tâches.

OVHcloud propose aussi une application web permettant d'accéder à votre adresse e-mail depuis un navigateur internet. Celle-ci est accessible via ce lien : [Webmail](/links/web/email). Vous pouvez vous y connecter grâce aux identifiants de votre adresse e-mail. Pour toute question relative à son utilisation, aidez-vous de notre guide [Utiliser le webmail Zimbra](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_zimbra).

### Comment modifier les paramètres existants ?<a name="modify-settings"></a>

L'application Mail de Mac ne permet pas de modifier les paramètres serveur d'un compte e-mail Exchange.

Si votre compte e-mail est déjà paramétré et que vous souhaitez le paramétrer à nouveau, vous devez alors le supprimer et le recréer :

Suivez les étapes d'installation en cliquant sur les onglets ci-dessous :

1. Cliquez sur `Mail`{.action} dans la barre de menu en haut de votre écran, puis cliquez sur `Comptes`{.action}.
1. Sélectionnez le compte e-mail concerné.
1. Appuyez sur `Supprimer le compte`{.action}.

![mail macos](images/mail-macos-modify-delete-01.png){.thumbnail .h-500}


## Aller plus loin

> [!primary]
>
> Pour plus d'informations sur la configuration d'une adresse e-mail depuis l'application Mail sur macOS, consultez [le centre d'aide Apple](https://support.apple.com/fr-fr/102619).

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre [communauté d'utilisateurs](/links/community).