---
title: 'Assigner un tag à un serveur Bare Metal'
excerpt: 'Créez et modifiez des tags pour chaque serveur depuis votre espace client'
updated: 2025-06-27
---

## Objectif

Créez des tags à assigner à vos services, afin de les organiser, et leur appliquer des stratégies avec la granularité souhaitée.

**Ce guide détaille comment attribuer et supprimer des tags pour des serveurs individuels, depuis l'espace client OVHcloud.**

## Introduction

Les tags sont des étiquettes que vous pouvez attribuer à vos ressources, et qui vous permettent de les organiser et les gérer plus efficacement. Chaque tag est constitué de deux parties: la clé, qui représente un attribut ou une catégorie, et la valeur, qui est l'information associée à cette clé.

Vous pouvez, par exemple, catégoriser vos ressources par site, service, ou encore niveau de sécurité. Une telle utilisation des tags peut notamment faciliter la recherche, l'organisation de vos ressources, la gestion des coûts associés, ou encore l'application de stratégies avec la granularité souhaitée.

## Prérequis
- Un [serveur dédié](/links/bare-metal/bare-metal) dans votre compte OVHcloud
- Accès à l’[espace client OVHcloud](/links/manager)

### Attribution d’un tag à un serveur depuis l’espace client

Pour commencer à utiliser des tags, connectez-vous à [OVHcloud Control Panel](/links/manager){.external} et choisissez la section `Bare Metal Cloud`{.action}. Cliquez sur `Serveurs Dédiés`{.action} et sélectionnez votre serveur dans la liste.

![General informations](images/general_information.png){.thumbnail}

Dans l'onglet `General informations`{.action} (1), cliquez sur le bouton `Ajouter un tag`{.action} (2) dans la zone **Tags**. Cliquez ensuite sur `Assigner un tag`{.action} (2).

![Add a tag](images/add_a_tag.png){.thumbnail}

![Empty tag list](images/Tag_list_empty.png){.thumbnail}

Ouvrez le menu déroulant sous `Clé`{.action} et sélectionnez le tag que vous souhaitez appliquer au serveur.

Ensuite, ouvrez de la même manière le menu déroulant sous `Valeur`{.action} et sélectionnez la valeur appropriée.

Si vous souhaitez utiliser une clé ou une valeur qui n'est pas encore créée, tapez-la, puis cliquez sur `Ajouter texte`{.action}, où « texte » est remplacé par le texte que vous avez entré.

![Assign a tag](images/assign_tag.png){.thumbnail}

![Assign a tag - populated](images/assign_tag_populated.png){.thumbnail}

Enfin, cliquez sur le bouton `Assigner`{.action} dans la partie inférieure droite de la fenêtre.
Vous visualisez alors la liste des tags appliqués au serveur choisi.

![Tag list with example](images/tag_list_with_example.png){.thumbnail}

### Suppression d'un tag sur serveur

Dans la liste des tags attribués, cliquez sur le bouton `...`{.action}, à droite du tag que vous souhaitez supprimer.
Cliquez ensuite sur `Désassigner`{.action}.

![Tag list unassign](images/tag_list_unassign.png){.thumbnail}

Une fenêtre de confirmation s'affiche. Cliquez sur le bouton `Confirmer`{.action} pour désassigner le tag.

![Unassign tag](images/unassign_tag){.thumbnail}

## Aller plus loin

Rejoignez notre [communauté d'utilisateurs](/links/community).