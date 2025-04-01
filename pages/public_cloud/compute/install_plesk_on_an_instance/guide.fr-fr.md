---
title: 'Installer Plesk sur une instance'
excerpt: 'Apprenez à mettre en place Plesk sur votre instance Public Cloud'
updated: 2018-03-26
---

## Objectif

Plesk est une interface de gestion de serveurs simple à prendre en main. Vous avez la possibilité de la mettre en place et de l'utiliser sur vos instances Public Cloud OVHcloud.

**Apprenez à installer Plesk sur votre instance Public Cloud.** 

> [!warning]
> 
> OVHcloud met à votre disposition des services dont la responsabilité vous revient. En effet, n’ayant aucun accès à ces machines, nous n’en sommes pas les administrateurs et ne pourrons vous fournir d'assistance. Il vous appartient de ce fait d’en assurer la gestion logicielle et la sécurisation au quotidien.
>
> Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [prestataire spécialisé](https://partner.ovhcloud.com/fr/directory/) si vous éprouvez des difficultés ou des doutes concernant l’administration, l’utilisation ou la sécurisation d’un serveur. N'hésitez pas à vous rendre sur notre [forum communautaire](/links/community) pour échanger avec d'autres utilisateurs.
>

## Prérequis

- [Avoir créé une instance depuis l'espace client OVHcloud](/links/public-cloud/public-cloud).
- [Disposer d'un accès administrateur](/pages/public_cloud/compute/public-cloud-first-steps#connect-instance).

## En pratique

### Étape 1 : installer Plesk

L'installation de Plesk s'effectue facilement depuis une connexion en SSH. Pour cela, téléchargez puis lancez le script d'installation de Plesk en utilisant la commande la plus adaptée à votre situation ci-dessous.

> [!primary]
>
> Selon l’OS de votre instance, la commande sudo seule peut ne pas suffire. Si vous rencontrez une erreur, passez en mode super-utilisateur avant de lancer l’installation :
>
> ```bash
> sudo su
> ```
>

- **Pour une installation par défaut non personnalisée de Plesk** :

```bash
sudo sh <(curl https://autoinstall.plesk.com/one-click-installer || wget -O - https://autoinstall.plesk.com/one-click-installer)
```

- **Pour une installation personnalisée de Plesk** :

```bash
sudo sh <(curl https://autoinstall.plesk.com/plesk-installer || wget -O - https://autoinstall.plesk.com/plesk-installer)
```

Patientez ensuite le temps de l'installation. 

### Étape 2 : finaliser la configuration et ajouter une license

Une fois l'installation terminée, suivez les instructions à l'écran pour compléter la configuration.

![plesk configuration](images/plesk-configuration.png){.thumbnail}

Pour ajouter votre licence Plesk, munissez-vous de la clé qui vous a été transmise par votre prestataire.

> [!primary]
>
> Nous ne commercialisons pas de licences Plesk pour nos offres Public Cloud. Vous pouvez cependant en obtenir une depuis le site de [Plesk](https://www.plesk.com/){.external}.
> 

Si vous souhaitez modifier votre licence, par exemple pour remplacer une clé de test ou pour changer d'offre ? Depuis l'interface Plesk, rendez-vous alors dans la partie `Tools & Settings`{.action}. Dans la section **Plesk**, sélectionnez ensuite `License information`{.action}.

## Aller plus loin

[Documentation officielle de Plesk](https://docs.plesk.com/en-US/obsidian/){.external}.

Échangez avec notre [communauté d'utilisateurs](/links/community).