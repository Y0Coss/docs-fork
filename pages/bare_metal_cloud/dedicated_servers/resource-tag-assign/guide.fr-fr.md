---
title: 'Assigner un tag à un serveur Bare Metal'
excerpt: 'Créez et modifiez des tags pour chaque serveur depuis l'espace client'
updated: 2025-02-07
---

## Objectif

Créez des tags à assigner à vos services, afin de les organiser, et leur appliquer des stratégies avec la granularité souhaitée.

**Ce guide détaille comment attribuer et supprimer des tags pour des serveurs individuels, depuis l'espace client OVHcloud.**

## Introduction

Les tags sont des étiquettes que vous pouvez attribuer à vos ressources, et qui vous permettent de les organiser et les gérer plus efficacement. Chaque tag est constitué de deux parties: la clé, qui représente un attribut ou une catégorie, et la valeur, qui est l'information associée à cette clé.

Vous pouvez, par exemple, catégoriser vos ressources par site, service, ou encore niveau de sécurité. Une telle utilisation des tags peut faciliter la recherche, l'organisation de vos ressources, la gestion des coûts associés, ou l'application de stratégies avec la granularité souhaitée, notamment.

## Prérequis
- Un [serveur dédié](/links/bare-metal/bare-metal) dans votre compte OVHcloud
- Accès à l’[espace client OVHcloud](/links/manager)

### Attribution d’un tag à un serveur depuis l’espace client

Pour commencer à utiliser des tags, connectez-vous à [OVHcloud Control Panel](/links/manager){.external} et choisissez la section `Bare Metal Cloud`{.action}. Cliquez sur `Serveurs Dédiés`{.action} et sélectionnez votre serveur dans la liste.

![General informations](images/general_information2025.png){.thumbnail}

[//] : # (Les liens vers les images de ce guide doivent être remplis avec les captures d'écran appropriées du prototype FIGMA, ou directement depuis l'espace client OVHcloud si disponible)

Dans l'onglet `General informations`{.action} (1), cliquez sur le bouton `Add tags`{.action} (2) dans la zone **Balises**. Cliquez ensuite sur `Assign tag`{.action} (2).

![Empty tag list](images/Tag_list_empty2025.png){.thumbnail}

Ouvrez le menu déroulant sous `Tag key`{.action} et sélectionnez le tag que vous souhaitez appliquer au serveur.
Ensuite, ouvrez de la même manière le menu déroulant sous `Tag value`{.action} et sélectionnez la valeur appropriée.
Si vous souhaitez utiliser une balise ou une valeur qui n'est pas encore créée, tapez-la, puis cliquez sur `Tag your-value`{.action}, où « your-value » est remplacé par le texte que vous avez entré.

![Assign tag](images/assign_tag2025.png){.thumbnail}
![Assign tag populated](images/assign_tag_populated2025.png){.thumbnail}

Enfin, cliquez sur le bouton `Assigner`{.action} dans la partie inférieure droite de la fenêtre.
Vous visualisez alors la liste des tags appliqués au serveur choisi.

![Tag list with examples](images/liste_de_balises_avec_exemple2025.png){.thumbnail}

### Suppression d'un tag sur serveur

Dans la liste des tags attribués, cliquez sur le bouton `..`{.action}, à droite du tag que vous souhaitez supprimer.
Cliquez ensuite sur `Unassign tag`{.action}.

![Tag list unassign](images/tag_list_unassign2025.png){.thumbnail}

Une fenêtre de confirmation s'affiche. Cliquez sur le bouton `Confirm`{.action} pour annuler l'assignation de la balise.

![Unassign tag](images/unassign_tag2025){.thumbnail}

## Aller plus loin

[Comment utiliser le gestionnaire de tags](/pages/bare_metal_cloud/dedicated_servers/resource-tag-manager)

Rejoignez notre [communauté d'utilisateurs](/links/community).