---
title: 'MX Plan / Zimbra Starter : ajouter un compte e-mail sur Outlook nouvelle version / Courrier pour Windows'
excerpt: "Apprenez à configurer votre adresse e-mail sur l'application Outlook ou Courrier pour Windows"
updated: 2025-08-27
---

<style>
.w-400 {
  max-width:400px !important;
}
</style>

## Objectif

Les adresses e-mail de l'offre MX Plan et [Zimbra](/links/web/emails-zimbra) Starter peuvent être configurées sur un logiciel de messagerie compatible. Cela vous permet d'envoyer et de recevoir vos messages depuis l'application de votre choix.

**Apprenez à configurer votre adresse e-mail MX Plan sur l'application Courrier pour Windows.**

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
> 
> Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [partenaire spécialisé](https://marketplace.ovhcloud.com/c/support-collaboration) et/ou de contacter l'éditeur du service si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section « Aller plus loin » de ce guide.
> 

## Prérequis

- Disposer d'une solution e-mail OVHcloud préalablement configurée, parmi les suivantes :
    - **MX Plan** proposée avec nos [offres d’hébergement web](/links/web/hosting) ou incluse dans un [hébergement gratuit 100M](/links/web/domains-free-hosting).
    - [Zimbra](/links/web/emails-zimbra) Starter (uniquement).
- Disposer de la [nouvelle version d'Outlook](https://support.microsoft.com/office/getting-started-with-the-new-outlook-for-windows-656bb8d9-5a60-49b2-a98b-ba7822bc7627) ou [Courrier](https://support.microsoft.com/office/set-up-email-in-the-mail-app-7ff79e8b-439b-4b47-8ff9-3f9a33166c60) installée sur votre Windows.
- Posséder les identifiants relatifs à l'adresse e-mail que vous souhaitez paramétrer.

## En pratique


### Ajouter le compte <a name="add-account"></a>

> [!warning]
>
> Il est nécessaire de choisir l'onglet de l'étape 3 correspondant à votre localisation (**EUROPE** ou **AMERIQUE / ASIE-PACIFIQUE**) pour obtenir les bonnes valeures .

> [!tabs]
> **Etape 1**
>> - Ouvrez Outlook, dans la colonne de gauche, cliquez sur `Ajouter un compte`{.action} pour démarrer la configuration.
>>
>> ![outlook](images/configuration-newoutlook-windows-01.png){.thumbnail .w-400}
>>
> **Etape 2**
>> - Saisissez votre adresse e-mail puis cliquez sur `Continuer`{.action}.
>> - Saisissez votre mot de passe et cliquez sur le bouton `Afficher plus`{.action}.
>>
>> ![outlook](images/configuration-newoutlook-windows-02.png){.thumbnail .w-400}
>>
> **Etape 3 EUROPE**
>> - Saisissez les paramêtres suivant:
>>    - **Serveur d'entrée IMAP**: imap.mail.ovh.net **ou** ssl0.ovh.net.
>>    - **Port**: 993
>>    - **Type de connexion sécurisée**: SSL/TLS
>>    - **Nom d'utilisateur SMTP**: adresse e-mail que vous ajoutez.
>>    - **Serveur sortant SMTP**: smtp.mail.ovh.net **ou** ssl0.ovh.net.
>>    - **Port**: 465
>>    - **Type de connexion sécurisée**: SSL/TLS
>>    - **Mot de passe**: ne rien saisir, le mot de passe saisie précédement sera utilisé.
>> - Cliquez sur `Continuer`{.action} pour finaliser la configuration.
>>
>> ![outlook](images/configuration-newoutlook-windows-03.png){.thumbnail .w-400}
>>
> **Etape 3 AMERIQUE / ASIE-PACIFIQUE**
>> - Saisissez les paramêtres suivant:
>>    - **Serveur d'entrée IMAP**: imap.mail.ovh.ca
>>    - **Port**: 993
>>    - **Type de connexion sécurisée**: SSL/TLS
>>    - **Nom d'utilisateur SMTP**: adresse e-mail que vous ajoutez.
>>    - **Serveur sortant SMTP**: smtp.mail.ovh.ca
>>    - **Port**: 465
>>    - **Type de connexion sécurisée**: SSL/TLS
>>    - **Mot de passe**: ne rien saisir, le mot de passe saisie précédement sera utilisé.
>> - Cliquez sur `Continuer`{.action} pour finaliser la configuration.
>>
>> ![outlook](images/configuration-newoutlook-windows-03ca.png){.thumbnail .w-400}

> [!warning]
>
> Depuis Windows 10, si vous n'avez pas encore migré votre logiciel de messagerie « Courrier » vers la nouvel version Outlook, cliquez sur la mention **Configuration Courrier Windows** ci-dessous.

<a name="add-account-mail"></a>

/// details | Configuration Courrier Windows

Une fois l'application Courrier lancée sur votre appareil, l'ajout d'un compte peut être effectué de deux manières différentes.

- **Lors du premier démarrage de l'application** : une fenêtre vous invite à cliquer sur `Ajouter un compte`{.action}.

- **Si un compte a déjà été paramétré** : cliquez sur `Comptes`{.action} dans la barre de menu à gauche de l'application, puis sur `Ajouter un compte`{.action} dans le menu qui apparaît à droite.

![outlook](images/configuration-mail-windows-step1.png){.thumbnail .w-400}

Dans la fenêtre qui s'affiche, cliquez sur `Configuration avancée`{.action}, puis choisissez `Courrier Internet`{.action} comme type de compte.

Renseignez à présent les informations demandées :

> [!warning]
>
> Il est nécessaire de bien relever la valeur correspondante à votre localisation (**EUROPE** ou **AMERIQUE / ASIE-PACIFIQUE**).

- **Adresse de courrier** : Renseignez l'adresse e-mail complète.
- **Nom d'utilisateur** : Indiquez l'adresse e-mail complète.
- **Mot de passe** : Renseignez le mot de passe de l'adresse e-mail.
- **Nom du compte** : Précisez le nom vous permettant de reconnaître ce compte parmi d'autres affichés dans votre application Courrier.
- **Envoyer vos messages en utilisant ce nom** : Renseignez le nom qui s'affichera dans le champ d'expéditeur lorsque des e-mails seront envoyés avec cette adresse.
 - **Serveur de courrier entrant IMAP** :<br>- **Nom d'hôte IMAP** : pour l'**EUROPE**, saisissez `imap.mail.ovh.net` ou `ssl0.ovh.net`. Pour l'**AMERIQUE/ASIE**, saisissez `imap.mail.ovh.ca`<br>- **Port** : 993<br>- **Type de sécurité** : SSL/TLS<br>- **Nom d'utilisateur IMAP** : votre adresse e-mail complète<br>- **Mot de passe IMAP** : celui de votre adresse e-mail
- **Type de compte** : Nous vous conseillons une utilisation en **IMAP4**. Vous pouvez cependant sélectionner **POP** (stockage des e-mails en local sur votre application Mail) dans le menu déroulant.
- **Serveur de courrier entrant SMTP** :<br>- **Nom d'hôte SMTP** : pour l'**EUROPE**, saisissez `smtp.mail.ovh.net` ou `ssl0.ovh.net` . Pour l'**AMERIQUE/ASIE**, saisissez `smtp.mail.ovh.ca`<br>- **Port** : 465<br>- **Type de sécurité** : SSL/TLS<br>- **Nom d'utilisateur SMTP** : votre adresse e-mail complète<br>- **Mot de passe SMTP** : celui de votre adresse e-mail

Assurez-vous que les cases sont bien cochées pour les choix suivants :

- « Le serveur sortant requiert l'authentification » ;
- « Utiliser le même nom d'utilisateur et mot de passe pour l'envoi du courrier » ;
- « Exiger le protocole SSL pour le courrier entrant » ;
- « Exiger le protocole SSL pour le courrier sortant ».

Une fois les informations complétées, cliquez sur `Se connecter`{.action}. Si les informations renseignées sont correctes, la connexion au compte réussira.

Vous pouvez effectuer un test d'envoi pour vérifier que le compte est correctement paramétré.

![outlook](images/configuration-mail-windows-step2.png){.thumbnail .w-400}

///

### Utiliser l'adresse e-mail <a name="use-account"></a>

Une fois l'adresse e-mail configurée, il ne reste plus qu’à l'utiliser ! Vous pouvez dès à présent envoyer et recevoir des messages.

OVHcloud propose une application web permettant d'accéder à votre adresse e-mail depuis votre navigateur internet accessible sur l’adresse [Webmail](/links/web/email). Vous pouvez vous y connecter grâce aux identifiants relatifs à votre adresse e-mail.

### Modifier les paramètres existants <a name="modify-settings"></a>

L'application Outlook ne permet pas de modifier les paramètres serveur de votre compte e-mail.

Si votre compte e-mail est déjà paramétré et que vous souhaitez le paramétrer à nouveau, vous devez alors le supprimer et le recréer :

- Cliquez sur l'icöne de réglage « &#9965; » dans le bas de la colonne de gauche.
- Dans la section « Vos comptes » cliquez sur `Gérer` à droite de l'adresses e-mail concernée.

![outlook](images/configuration-newoutlook-windows-04.png){.thumbnail .w-400}

- Descendez dans le bas de la page.
- Cliquez sur `Remove`{.action} pour lancer la suppression.
- Déterminez si vous souhaitez supprimer seulement sur cet appareil ou sur les autres appareils utilisant Outlook.

![outlook](images/configuration-newoutlook-windows-05.png){.thumbnail .w-400}

> [!success]
>
> Une fois votre compte e-mail supprimé, suivez les instructions de la partie « [Ajouter le compte](#add-account) » sur cette documentation.

### Paramètre généraux d'envoi et de réception <a name="settings-account"></a>

#### Paramètres de réception IMAP et POP <a name="imap-pop"></a>

Pour la réception des e-mails, lors du choix du type de compte, nous vous conseillons une utilisation en **IMAP**. Vous pouvez cependant sélectionner **POP**.

> [!warning]
>
> Il est nécessaire de bien relever la valeur correspondante à votre localisation (**EUROPE** ou **AMERIQUE / ASIE-PACIFIQUE**).

Sélectionnez l'onglet correspondant à votre type de configuration :

> [!tabs]
> **Configuration IMAP**
>>
>> - **Nom d'utilisateur** : Renseignez l'adresse e-mail **complète**.
>> - **Mot de passe** : Renseignez le mot de passe de l'adresse e-mail.
>> - **Serveur EUROPE (entrant)** : imap.mail.ovh.net **ou** ssl0.ovh.net.
>> - **Serveur AMERIQUE/ASIE-PACIFIQUE (entrant)** : imap.mail.ovh.ca.
>> - **Port** : 993.
>> - **Type de sécurité** : SSL/TLS.
>>
> **Configuration POP**
>>
>> - **Nom d'utilisateur** : Renseignez l'adresse e-mail **complète**.
>> - **Mot de passe** : Renseignez le mot de passe de l'adresse e-mail.
>> - **Serveur EUROPE (entrant)** : pop.mail.ovh.net **ou** ssl0.ovh.net.
>> - **Serveur AMERIQUE/ASIE-PACIFIQUE (entrant)** : pop.mail.ovh.ca.
>> - **Port** : 995.
>> - **Type de sécurité** : SSL/TLS.

#### Paramètres d'envoi SMTP <a name="smtp"></a>

Pour l'envoi des e-mails, retrouvez ci-dessous les paramètres **SMTP** à utiliser :

**Configuration SMTP**

- **Nom d'utilisateur** : Renseignez l'adresse e-mail **complète**.
- **Mot de passe** : Renseignez le mot de passe de l'adresse e-mail.
- **Serveur EUROPE (sortant)** : smtp.mail.ovh.net **ou** ssl0.ovh.net.
- **Serveur AMERIQUE/ASIE-PACIFIQUE (sortant)** : smtp.mail.ovh.ca.
- **Port** : 465.
- **Type de sécurité** : SSL/TLS.

## Aller plus loin

> [!primary]
>
> Pour plus d'informations sur la configuration d'une adresse e-mail depuis le client de messagerie Courrier sur Windows, consultez [le centre d'aide de Mircrosoft](https://support.microsoft.com/fr-fr/office/configurer-l-e-mail-dans-l-application-courrier-7ff79e8b-439b-4b47-8ff9-3f9a33166c60).

[Configurer son compte E-mail Pro sur l'application Courrier pour Windows](/pages/web_cloud/email_and_collaborative_solutions/email_pro/how_to_configure_windows_10)

[Configurer son compte Exchange sur l'application Courrier pour Windows](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/how_to_configure_windows_10)

Échangez avec notre [communauté d'utilisateurs](/links/community).