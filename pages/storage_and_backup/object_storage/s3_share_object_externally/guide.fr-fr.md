---
title: Object Storage – Comment partager un objet/fichier en externe
excerpt: Découvrez comment partager en toute sécurité des fichiers Object Storage en externe dans OVHcloud, en utilisant des URLs signées, des objets public-read ou des politiques de bucket pour un accès contrôlé.
updated: 2025-11-03
---

## Objectif

Ce guide explique comment partager en toute sécurité des fichiers ou objets stockés dans l'Object Storage OVHcloud avec des utilisateurs externes, couvrant l'accès temporaire, les objets public-read et les politiques de bucket, tout en mettant en évidence les types d'URL et les bonnes pratiques.

### Scénarios d'utilisation

Les scénarios d'utilisation courants pour partager des objets dans l'Object Storage OVHcloud incluent :

- Vous souhaitez fournir un lien de téléchargement temporaire à un partenaire ou client sans accorder un accès complet au bucket.
- Vous avez besoin de rendre certains objets publics, tels que des images ou des documents produits, tout en gardant le reste du bucket privé.
- Vous souhaitez accorder un accès contrôlé à certains fichiers pour des collaborateurs ou utilisateurs externes.

## Comparaison des types d'URL

Lorsque vous partagez des objets dans l'Object Storage OVHcloud, il est important de comprendre la différence entre les **URL Path-style** et les **URL Virtual-hosted-style**.

| Fonctionnalité             | URL Path-style                                                                | URL Virtual-hosted-style                                     |
| -------------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------ |
| Format                     | `https://s3.<region>.io.cloud.ovh.net/<bucket>/<object-key>/<generated-code>` | `https://<bucket>.s3.<region>.io.cloud.ovh.net/<object-key>` |
| Utilisation typique        | URLs signées générées via l'API                                               | URLs provenant du panneau de configuration ou des objets publics                |
| Emplacement du nom de bucket | Dans le chemin de l'URL                                                       | Dans le sous-domaine                                             |
| Meilleur pour              | Accès temporaire ou programmation                                              | Partage public ou liens stables                               |
| Contrôle d'accès           | Limité par l'expiration de l'URL signée                                           | Contrôlé par les ACL ou les politiques de bucket                        |

**Points clés :**

- Utilisez les URL de type chemin pour un accès temporaire ou programmé.
- Utilisez les URL Virtual-hosted-style pour le partage public ou à long terme, car elles sont plus standardisées et plus faciles à gérer.

## Prérequis

- Un bucket
- Un utilisateur et les droits d'accès requis définis sur le bucket

Consultez notre guide [Commencer avec Object Storage](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage).

## En pratique

L'Object Storage OVHcloud propose trois principales méthodes pour partager des objets en externe. Choisissez la méthode en fonction de vos besoins : accès temporaire, accès public ou partage contrôlé.

> [!tabs]
> Via des URLs signées
>> Les URLs signées offrent un accès temporaire à un objet privé sans modifier les permissions du bucket.
>>
>> Étapes :
>>
>> - Générez une URL signée via l'API OVHcloud ou un SDK compatible S3.
>> - Définissez une date d'expiration.
>> - Partagez l'URL avec l'utilisateur externe.
>>
>> Exemple (compatible AWS CLI) :
>>
>> ```bash
>> aws s3 presign s3://my-bucket/reports/data.csv --expires-in 3600 \
>>  --endpoint-url https://s3.gra.io.cloud.ovh.net
>> ```
>>
>> Cette commande retourne un lien temporaire valide pendant 1 heure.
>>
>> Après l'expiration, l'accès est automatiquement bloqué et l'objet reste privé.
>>
> Via des objets publics
>> Des objets spécifiques peuvent être rendus publics en appliquant une ACL public-read. Seuls ces objets deviennent publics. le bucket et sa liste restent privés.
>>
>> Étapes :
>>
>> - Sélectionnez l'objet via l'API.
>> - Appliquez l'ACL public-read.
>> - Partagez l'URL de l'objet.
>>
>> Exemple (compatible AWS CLI) :
>>
>> ```bash
>> aws s3api put-object-acl \
>>  --bucket my-bucket \
>>  --key docs/manual.pdf \
>>  --acl public-read \
>>  --endpoint-url https://s3.gra.io.cloud.ovh.net
>> ```
>>
>> L'objet devient accessible à l'adresse : `https://my-bucket.s3.gra.io.cloud.ovh.net/docs/manual.pdf`
>>
> Via des politiques de bucket
>> Les politiques de bucket permettent un partage à long terme ou structuré en définissant des règles d'accès pour des objets, des préfixes ou des plages d'IP spécifiques.
>>
>> Étapes :
>>
>> - Écrivez une politique JSON spécifiant les actions autorisées et les objets.
>> - Appliquez la politique au bucket via le panneau de configuration ou l'API.
>> - Partagez l'URL ou les identifiants appropriés selon la règle.
>>
>> Exemple : Autoriser l'accès public en lecture sur un dossier/préfixe spécifique
>>
>> ```json
>> {
>>   "Version": "2012-10-17",
>>   "Statement": [
>>     {
>>       "Effect": "Allow",
>>       "Principal": "*",
>>       "Action": "s3:GetObject",
>>       "Resource": "arn:aws:s3:::my-bucket/public/*"
>>     }
>>   ]
>> }
>> ```
>>
>> Une fois appliquée, tout objet sous le préfixe `public/` devient publiquement lisible, tandis que le reste du bucket reste privé.
>>

## Aller plus loin

Si vous avez besoin de formation ou d'une assistance technique pour mettre en œuvre nos solutions, contactez votre représentant commercial ou cliquez sur [ce lien](/links/professional-services) pour obtenir un devis et demander à nos experts de Services Professionnels de vous aider dans le cadre de votre cas d'utilisation spécifique ou de votre projet.

Échangez avec notre [communauté d'utilisateurs](/links/community).