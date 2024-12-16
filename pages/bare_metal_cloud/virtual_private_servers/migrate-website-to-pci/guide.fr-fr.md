---
title: "Comment migrer un site web d'un VPS vers un serveur dédié ou une instance PCI"
excerpt: "Découvrez comment migrer votre site web d'un VPS vers un serveur dédié ou une instance Public Cloud (PCI)"
updated: 2024-12-20
---

## Objectif

Votre site web se développe, et les ressources d’un VPS peuvent rapidement devenir insuffisantes pour répondre à vos besoins croissants en matière de performances, de gestion de trafic ou de traitement de tâches complexes. Migrer vers un serveur dédié ou une instance Public Cloud (PCI) vous permet de bénéficier d’une infrastructure plus puissante, personnalisable et adaptée à des charges de travail plus exigeantes. Ce guide se concentre sur les étapes essentielles pour effectuer cette migration efficacement, tout en garantissant la continuité de service.

**Découvrez comment migrer votre site web d’un VPS vers un serveur dédié ou une instance PCI.**

## Prérequis

- Disposer d'un accès administrateur au [VPS](/links/bare-metal/vps) source (via SSH).
- Un [serveur dédié](/links/bare-metal/bare-metal) ou une instance [Public Cloud](https://www.ovhcloud.com/fr-ca/public-cloud/) dans votre compte OVHcloud.
- Accès administrateur au serveur de destination (via SSH).
- Une connaissance des bases de la gestion de serveur (Apache/Nginx, bases de données, etc.).

## En pratique

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
> 
> Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Cependant, nous vous recommandons de faire appel à un [prestataire spécialisé](/links/partner) si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section [« Aller plus loin »](#go-further) de ce guide.
>

### Étape 1 - Sauvegarder les fichiers et la base de données de votre site web <a name="step1"></a>

La première étape consiste à sauvegarder l'ensemble des fichiers de votre site web.

#### Étape 1.1 - Sauvegarder les fichiers via SSH <a name="step1.1"></a>

Connectez-vous via SSH au VPS et archivez les fichiers de votre site web :

```bash
ssh <user>@<vps_ip>
cd /var/www/html
tar -czf site_backup.tar.gz *
```

Remplacez :

- `<user>` : par l'utilisateur que vous utilisez pour vous connecter au VPS.
- `<vps_ip>` : par l'adresse IP de votre VPS.

#### Étape 1.2 - Sauvegarder la base de données <a name="step1.2"></a>

Si votre site web utilise une base de données, utilisez les lignes de commandes selon votre SGBD (Système de gestion de base de données).

> [!tabs]
> MySQL et MariaDB
>> ```bash
>> mysqldump -u <db_user> -p <db_name> > database_backup.sql
>> ```
>> 
>> Remplacez :
>> 
>> - `<db_user>` : par le nom d’utilisateur de la base de données.
>> - `<db_name>` : par le nom de la base de données.
> PostgreSQL
>> Pour exporter votre base de données, référez-vous à la [documentation officielle de PostgreSQL](https://www.postgresql.org/docs/){.external}
>>
> MongoDB
>> Pour exporter votre base de données, référez-vous à la [documentation officielle de MongoDB](https://docs.mongodb.com/manual/){.external}
>>
> Redis® open source
>> Pour exporter votre base de données, référez-vous à la [documentation officielle de Redis](https://redis.io/documentation){.external}

Si vous utilisez un autre SGBD, consultez sa documentation officielle pour trouver les commandes de sauvegarde de la base de données.




