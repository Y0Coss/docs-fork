---
title : Object Storage - Utiliser Object Storage avec Pure Storage Flashblade
excerpt : Configurez Pure Storage Flashblade pour collaborer avec OVHcloud Object Storage
mise à jour : 2025-07-02
---

## Objectif

Ce guide a pour but de vous aider à configurer et à utiliser OVHcloud Object Storage comme cible de réplication pour Pure Storage « [Flashblade unified storage platform](https://www.purestorage.com/fr/products/unstructured-data-storage/flashblade-s.html){.external} ».

Il explique comment configurer, gérer et répliquer facilement des objets compatibles Pure Storage FlashBlade S3 vers OVHcloud Object Storage.

## Prérequis

- Un conteneur/bucket OVHcloud Object Storage.
- Un utilisateur avec les droits d'accès requis sur le bucket.
- Vos identifiants Object Storage (access_key et secret_access_key).

Consultez notre guide [Getting started with Object Storage](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage).

## Instructions

### Créer une connexion cible compatible S3

1. Connectez-vous à l'interface utilisateur graphique de Pure Storage FlashBlade.

2. Rendez-vous dans la section `Stockage`{.action} puis `Array`{.action}.

3. Cliquez sur le bouton « + » à côté de `S3 Target Connections` pour créer un stockage d'objets cloud *Target Connections*.

4. Nommez la connexion, par exemple avec OVHCLOUD_OBJECT_STORAGE et ajoutez les points de terminaison OVHcloud Object Storage associés dans le champ `Address`.

![page de connexion](images/01.Connections.png){.thumbnail}

La liste de tous les points de terminaison OVHcloud Object Storage se trouve [ici](/pages/storage_and_backup/object_storage/s3_location).

### Ajouter des informations d'identification pour le stockage d'objets dans le Cloud à distance

5. Rendez-vous dans la section `Protection`{.action} puis cliquez sur `Liens de réplica d'objet`{.action}.

6. Cliquez sur le bouton « + » pour ajouter des informations d'identification et de connexion distantes pour la réplication d'objets.

7. Sélectionnez `OVHCLOUD_OBJECT_STORAGE`{.action} pour la baie distante.

8. Ajoutez le nom de votre connexion, par exemple « OVHcloud_credentials », et ajoutez vos clés d'accès et secrètes depuis l'espace client.

9. Confirmez en cliquant sur `Créer`{.action} et vos identifiants à distance seront créés.

![creds page](images/02.Creds.png){.thumbnail}

### Créez un bucket qui sera répliqué sur l’Object Storage OVHcloud

10. Si ce n'est pas déjà fait, rendez-vous dans la section `Stockage`{.action} puis `Stockage d'objets`{.action} et enfin `Comptes`{.action} pour créer le compte.

11. Configurez les différents paramètres suivants : « nom du compte », « limite de quota » et « limite de quota par défaut du compartiment » pour créer le compte.

12. Cliquez sur la section `Compartiments`{.action} et sélectionnez le nom du compte.

13. Entrez un nom de compartiment « OVHcloud-source-2025 » et cliquez sur `Créer`{.action}.

### Configurer la réplication de compartiments vers l’Object Storage OVHcloud

14. Accédez à `Protection`{.action} > `Réplication d'objet`{.action} et `Lien de réplication de compartiment`{.action}.

15. Cliquez sur le bouton « + » pour créer un lien de réplica de compartiment.

16. Sélectionnez le regroupement que vous venez de créer.

17. Sélectionnez `OVHCLOUD_OBJECT_STORAGE`{.action} pour la baie distante.

18. Ajoutez le nom de votre compartiment Object Storage OVHcloud, « OVHcloud-dest-2025 »

19. Ajoutez vos identifiants à distance « OVHcloud_credentials ». Le lien de réplica de compartiment va être créé.

![replica page](images/03.Replica.png){.thumbnail}

20. Vous pouvez maintenant tester et valider la réplication de bucket de la plateforme Pure Storage Flashblade vers OVHcloud Object Storage.

## Aller plus loin

Rejoignez notre [communauté d'utilisateurs](/links/community).