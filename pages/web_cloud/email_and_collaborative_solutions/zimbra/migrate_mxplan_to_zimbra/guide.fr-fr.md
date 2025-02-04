---
title: 'Migrer une adresse e-mail MX Plan vers un compte Zimbra OVHcloud'
excerpt: 'Découvrez comment migrer une adresse e-mail MX Plan vers un compte Zimbra OVHcloud.'
updated: 2025-02-04
---

## Objectif

Dans le cadre de la transition progressive des comptes MX Plan vers Zimbra, il est possible d'anticiper cette migration et effectuer vous-mêmes le transfert de comptes e-mail avant la mise en place d’un outil automatisé par OVHcloud. Ce guide vous explique comment effectuer cette migration manuellement.

**Découvrez comment migrer une adresse e-mail MX Plan vers un compte Zimbra OVHcloud.**

## Prérequis

- Disposer d'une adresse e-mail MX Plan (via l'offre MX Plan ou incluse dans une offre d'[hébergement web OVHcloud](/links/web/hosting)).
- Disposer d'un compte e-mail Zimbra OVHcloud.
- **Ne pas avoir paramétré de redirection sur l'adresse e-mail MX Plan que vous souhaitez migrer**.
- Être connecté à votre [espace client OVHcloud](/links/manager).

## En pratique

La migration d'un compte e-mail MX Plan vers un compte e-mail Zimbra se fait en 2 temps. Pour éviter de couper la réception sur l'adresse e-mail d'origine, il est nécessaire de réspecter le processus suivant :

1. **Transférer le contenu du compte MX Plan vers un compte Zimbra**
    - [1.1 - Création d’une adresse e-mail Zimbra](#step11)
    - [1.2 - Migration des e-mails](#step12)
    - [1.3 - Sauvegarde des e-mails du compte source (optionnelle)](#step13)

2. **Supprimer le compte MX Plan d'origine et réassigner son adresse au compte Zimbra**
    - [2.1 - Suppression de l'ancienne adresse e-mail MX Plan](#step21)
    - [2.2 - Renommer l'adresse e-mail Zimbra](#step22)

Dans l'exemple ci-dessous nous migrons l'adresse `contact@mydomain.ovh`{.action}, pour cela nous allons créer le compte Zimbra sous le nom `contact2@mydomain.ovh`{.action}.

![zimbra](images/zimbra_migration_mxplan.png){.thumbnail}

### 1.1 - Création d’une adresse e-mail Zimbra <a name="step11"></a>

> [!primary]
>
> Si vous disposez déjà d'une adresse e-mail Zimbra, passez à la [Migration des e-mails](#step12).

Créez dans un premier temps une adresse e-mail avec un nom provisoire. Vous pouvez créer, par exemple, l'adresse `contact2@mydomain.ovh`{.action} si vous devez migrer l'adresse `contact@mydomain.ovh`{.action}.

Pour créer une adresse e-mail Zimbra, consultez la section « Créer un compte e-mail » depuis notre guide [Premiers pas avec l'offre Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra).

### 1.2 - Migration des e-mails <a name="step12"></a>

Utilisez l’outil de migration [**O**VH **M**ail **M**igrator](https://omm.ovh.net/) (**OMM**) pour transférer le contenu du compte MX Plan d'origine vers le nouveau compte de destination Zimbra, si nous gardons l'exemple précédement vu dans le schéma:

- Compte e-mail source : `contact@mydomain.ovh`{.action} (compte MX Plan)
- Compte e-mail de destination : `contact2@mydomain.ovh`{.action} (compte Zimbra)

Pour plus de détails sur l'utilisation d'OMM, suivez notre guide « [Migrer des comptes e-mail via OVH Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm)».

> [!primary]
>
> Le délai de migration dépend de la quantité de contenu à migrer vers votre nouveau compte. Celui-ci peut varier de quelques minutes à plusieurs heures. Une fois la migration terminée, vérifiez que tous les e-mails sont bien migrés.

### 1.3 - Sauvegarde des e-mails du compte source (optionnelle) <a name="step13"></a>

> [!warning]
>
> Avant de supprimer votre compte MX Plan, **effectuez une sauvegarde de vos e-mails** pour éviter toute perte de données.

Utilisez les options d'export de votre client de messagerie. Vous trouverez les détails d'export manuel d'une adresse e-mail depuis un client de messagerie, depuis notre guide [Migrer manuellement votre adresse e-mail](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration).

### 2.1 - Suppression de l'ancienne adresse e-mail MX Plan <a name="step21"></a>

Pour supprimer l'adresse e-mail MX Plan (exemple: `contact@mydomain.ovh`{.action}), suivez notre guide « [Supprimer un compte e-mail](/pages/web_cloud/email_and_collaborative_solutions/common_email_features/email_reset_account)».

### 2.2 - Renommer l'adresse e-mail Zimbra <a name="step22"></a>

Dans votre espace client OVHcloud, accédez à votre service Zimbra Starter et renommez l'adresse de votre compte e-mail Zimbra avec le nom du compte e-mail migré (par exemple : `contact2@mydomain.ovh`{.action} en `contact@mydomain.ovh`{.action}).

### Conclusion <a name="conclusion"></a>

Votre compte e-mail est maintenant entièrement migré vers Zimbra Starter. Vous pouvez désormais utiliser Zimbra pour gérer votre messagerie.

> [!warning]
>
> Si votre compte e-mail gère des informations sensibles ou si vous rencontrez des problèmes lors de la migration, nous vous recommandons d’attendre la mise en place de l’outil d’automatisation prévu dans l’espace client OVHcloud.

## Aller plus loin <a name="go-further"></a>

[Premiers pas avec l'offre Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra)

[Configurer son adresse e-mail Zimbra sur un logiciel de messagerie](/pages/web_cloud/email_and_collaborative_solutions/zimbra/zimbra_mail_apps)

[FAQ sur la solution Zimbra OVHcloud](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/faq-zimbra)

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre [communauté d'utilisateurs](/links/community).