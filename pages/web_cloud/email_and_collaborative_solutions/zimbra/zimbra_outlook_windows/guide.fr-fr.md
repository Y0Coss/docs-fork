---
title: "Zimbra Pro - Configurer son compte e-mail via ActiveSync sur Outlook pour Windows"
excerpt: "Découvrez comment configurer votre adresse e-mail Zimbra Pro sur Outlook pour Windows via le protocole ActiveSync"
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

Les comptes Zimbra Pro peuvent être configurés en utilisant le protocole Active Sync sur Windows, cela vous permet de configurer l'ensemble des fonctionnalités collaboratives de votre adresse e-mail en une seule fois. l'application Outlook pour Windows permet la consultation de votre compte e-mail Zimbra Pro via le protocole ActivSync.

**Découvrez comment configurer votre adresse e-mail Zimbra Pro sur Outlook pour Windows via le protocole ActiveSync**

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
>
> Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [partenaire spécialisé](https://marketplace.ovhcloud.com/c/support-collaboration) et/ou de contacter l'éditeur du service si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section « Aller plus loin » de ce guide.

## Prérequis

- Disposer d’une adresse e-mail [Zimbra Pro](/links/web/zimbra).
- Disposer de l'application Outlook Classique sur Windows.
- Posséder les identifiants relatifs à l'adresse e-mail que vous souhaitez paramétrer.

## En pratique

> [!warning]
>
> Avant de débuter votre configuration, il est important de noter que l'application Outlook incluse gratuitement avec Windows 11 est incompatible avec le protocole Active Sync, nécessaire à la configuration d'un compte Zimbra Pro. Vous devrez utiliser la version **Outlook classique** pour bénéficier de la prise en charge du protocole Active Sync.
>
> Pour installer Outlook classique sur votre ordinateur Windows, téléchargez et installez celui-ci depuis la page Microsoft, [Installer ou réinstaller Outlook classique sur un PC Windows](https://support.microsoft.com/office/installer-ou-r%C3%A9installer-outlook-classique-sur-un-pc-windows-5c94902b-31a5-4274-abb0-b07f4661edf5).
>
> Une fois l'installation terminée, pour distinguer les deux versions lorsqu'elles sont installées, tapez « Outlook » dans votre barre de recherche Windows. Vous pourrez alors constater la différence comme ci-dessous.
>
> ![outlook Windows](images/outlook-windows-identify01.png){.thumbnail .h-500}


### Ajouter le compte <a name="add-account"></a>

Pour ajouter un compte Zimbra Pro sur Outlook classique, suivez sur les étapes ci-desous en cliquant sur les onglets ci-dessous :

> [!tabs]
> **Etape 1**
>>
>> 1. Dirigez-vous dans le **panneau de configuration** de Windows.
>> 2. Cliquez sur `Comptes d'utilisateurs`{.action}.
>> 3. Cliquez sur `Courrier`{.action}.
>> 4. Cliquez sur `Comptes de messagerie...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step01.png){.thumbnail .h-500}
>>
> **Etape 2**
>>
>> - Depuis la fenêtre **Paramètres du compte**, dans l'onglet `Messagerie`, cliquez sur `Nouveau...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step02.png){.thumbnail .h-500}
>>
> **Etape 3**
>>
>> - Depuis la fenêtre **Ajouter un compte**, sélectionnez `Configuration manuelle ou types de serveurs supplémentaires`{.action}.
>> - Cliquez sur `Suivant`{.action} pour continuer.
>>
>> ![outlook Windows](images/outlook-windows-add-step03.png){.thumbnail .h-500}
>>
> **Etape 4**
>>
>> - Sélectionnez `Exchange ActiveSync`{.action}.
>> - Cliquez sur `Suivant`{.action} pour continuer.
>>
>> ![outlook Windows](images/outlook-windows-add-step04.png){.thumbnail .h-500}
>>
> **Etape 5**
>>
>> Saisissez les informations de connection à votre compte:
>>
>> - **Votre nom**: définissez un nom d'affichage.
>> - **Adresse e-mail**: saisissez votrea dresse e-mail.
>> - **Serveur de courrier** : saisissez « zimbra1.mail.ovh.net ».
>> - **Nom d'utilisateur** : saisissez votre adresse e-mail complète .
>> - **Mot de passe** : saisissez le mot de passe associé à votre adresse e-mail configurée.
>>
>> Cliquez sur `Suivant`{.action} pour finalisez l'ajout du compte.
>>
>> ![outlook Windows](images/outlook-windows-add-step05.png){.thumbnail .h-500}
>>
> **Etape 6**
>>
>> Votre adresse e-mail est maintenant configurée pour Outlook. Pour bénéficier d'une pleine synchronisation des fonctionnalités de votre compte Zimbra Pro, **téléchargez et installez** le module [Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/).
>> 
>> ![outlook Windows](images/outlook-windows-add-step06.png){.thumbnail .h-500}
>>
> **Etape 7**
>>
>> Une fois [Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/) installé, lancez Outlook classique.
>> La première fois, la fenêtre de configuration **Zimbra Server configuration Settings** s'affiche, complétez les informations suivante:
>>
>> - **Server name**: saisissez « zimbra1.mail.ovh.net ».
>> - **Email Addressl**: saisissez votre adresse e-mail.
>> - **Password** : saisissez le mot de passe associé à votre adresse e-mail configurée.
>>
>> Les autres paramètres n'ont pas besoin d'être modifié, cliquez sur `Appliquer`{.action} pour valider les paramètres et s'assurer qu'ils sont conformes. Cliquez enfin sur cliquez sur `OK`{.action} pour basculer sur Outlook et commencer à utiliser votre adresse e-mail
>>
>> ![outlook Windows](images/outlook-windows-add-step07.png){.thumbnail .h-500}

> [!warning]
>
> Si, après avoir suivi les étapes de configuration ci-dessus, vous rencontrez un défaut d'envoi ou de réception, consultez la rubrique « [Modifier les paramètres existants](#modify-settings) ».

### Utiliser l'adresse e-mail

Une fois l'adresse e-mail configurée, il ne reste plus qu’à l'utiliser ! Vous pouvez dès à présent envoyer et recevoir des messages, mais aussi gérer vos calendriers et tâches.

OVHcloud propose aussi une application web permettant d'accéder à votre adresse e-mail depuis un navigateur internet. Celle-ci est accessible via ce lien : [Webmail](/links/web/email). Vous pouvez vous y connecter grâce aux identifiants de votre adresse e-mail. Pour toute question relative à son utilisation, aidez-vous de notre guide [Utiliser le webmail Zimbra](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_zimbra).

### Comment modifier les paramètres existants ?<a name="modify-settings"></a>

Si votre compte e-mail est déjà paramétré et que vous souhaitez les modifier, suivez les instructions ci-dessous :

1. Dirigez-vous dans le **panneau de configuration** de Windows.
1. Cliquez sur `Comptes d'utilisateurs`{.action}.
1. Cliquez sur `Courrier`{.action}.
1. Cliquez sur `Comptes de messagerie...`{.action}.
1. Sélectionnez le compte e-mail concerné dans la liste et cliquez sur `Modifier...`{.action}.

![outlook ios](images/outlook-app-ios-modify-account-01.png){.thumbnail .h-500}

Retrouvez les paramètres à **l'étape 7** du chapitre [Ajouter le compte](#add-account).

### Comment supprimer un compte e-mail ?<a name="delete-account"></a>

Pour pouvoir supprimer votre compte e-mail, suivez les instructions ci-dessous:

1. Dirigez-vous dans le **panneau de configuration** de Windows.
1. Cliquez sur `Comptes d'utilisateurs`{.action}.
1. Cliquez sur `Courrier`{.action}.
1. Cliquez sur `Comptes de messagerie...`{.action}.
1. Sélectionnez le compte e-mail concerné dans la liste et cliquez sur `Supprimer`{.action}.

![outlook ios](images/outlook-app-ios-modify-delete-01.png){.thumbnail .h-500}

> [!warning]
>
> Pour pouvoir supprimer votre compte e-mail, il est necessaire que celui-ci ne soit pas le compte e-mail par défaut.

## Aller plus loin

> [!primary]
>
> Pour plus d'informations sur la configuration d'une adresse e-mail depuis l'application Outlook sur iOS, consultez [le centre d'aide Microsoft](https://support.microsoft.com/office/add-an-email-account-to-outlook-for-windows-6e27792a-9267-4aa4-8bb6-c84ef146101b?ocmsassetID=HA102823161&CorrelationId=778d1d8d-9ac2-449b-9624-1268559fa794#picktab=classic_outlook).

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre [communauté d'utilisateurs](/links/community).