---
title: "Gestion des tags sur les resources"
excerpt: "Découvrez comment gérer et utiliser les tags sur vos ressources OVHcloud"
updated: 2025-09-12
---

## Objectif

Dans ce guide vous apprenderez a affecter et gérer des tags sur vos produits OVHcloud et comment les utiliser dans les politiques IAM.

## Prérequis

- Disposer d'un [compte client OVHcloud](/pages/account_and_service_management/account_information/ovhcloud-account-creation).

## En pratique

### Gérer les tags via l'espace client

Il est possible de gérer les tags de vos produits OVHcloud soit a travers l'interface général de gestion de tag, soit à travers les interfaces dédiées dans les produits.
Les tags sont des metadata sous forme de clé/valeurs ajouté aux ressources OVHcloud, pouvant être utilisé dans les politiques IAM ou la catégorisation des ressources

#### Tag Manager

Le **Tag Manager** est le menu vous permettant de gérer de manière transverse vos tags sur l'ensemble de vos produits OVHcloud.
Ce menu est accessible dans le menu `Identité, Sécurité & Opérations`{.action} et la section `Gestion des identités et des accès`{.action}

Le menu affiche l'ensemble des tags actuellement placés sur vos ressources.

![Tag Manager](images/tag-manager-01.png){.thumbnail}

Pour chaque tag, le dashboard liste le nombre de ressources sur lequel est associé ce tag ainsi que le type de tag.

Il existe 3 types de tags :

- Tag custom : Créé et managé par vous
- Tag prédéfini : Créé par OVHcloud, assigné aux ressources par vous
- Tag system : Créé et assigné automatiquement par OVHcloud à vos ressources (ne peuvent pas être supprimés)

Les tags prédéfinis non assignés et les tags systèmes ne s'affichent pas par défaut et doivent être affiché via le bouton `Filtre rapide`

En cliquant sur le tag, on accède aux détails du tag avec la liste des ressources concernées

![Tag Manager](images/tag-manager-02.png){.thumbnail}

Il en ensuite possible d'assigner ce tag à d'autre ressources via le bouton `Assigner le tag`.
La liste de l'ensemble de ressource du compte s'affiche ensuite sur laquelle il est possible de faire une sélection multiple.
Un champ de filtre est présent a droite pour faciliter la recherche dans les ressources.

A l'inverse en sélectionnant les ressources dans les détails du tag, il est possible de supprimer le tag de celles-ci via le bouton `Désassigner le tag`

#### Dashboard produits

Dans certains produits OVHcloud un menu a été ajouté pour gérer les tags directement depuis le dashboard de gestion de la ressource

![Tag Manager](images/baremetal-tag-01.png){.thumbnail}

Le menu de gestion de tags permet d'ajouter ou retirer les tags sur la ressource

![Tag Manager](images/baremetal-tag-02.png){.thumbnail}

Il est possible soit de sélectionné parmis la liste des tags prédéfinis, ou de saisir ses propres tags en tappant directement les clés et les valeurs dans les champs.

### Gérer les tags via les API

La gestion des tags est centralisée dans une unique API pour tout les produits OVHcloud :

| **Méthode** |              **Chemin**               |            **Description**             |
| :---------: | :-----------------------------------: | :------------------------------------: |
|    POST     |    /iam/resource/{resourceURN}/tag    |    Ajout d'un tag sur une ressource    |
|     DEL     | /iam/resource/{resourceURN}/tag/{key} | Suppression d'un tag sur une ressource |

Le tag doit être indiqué sous la forme :

```json
{
  "key": "environment",
  "value": "production"
}
```

### Utilisation dans les politiques IAM

Les tags peuvent être utilisé comme conditions dans les politiques IAM grâce à la condition `resource.Tag(tag_key)`

Par exemple la politique suivante permet de donner les droits sur l'ensemble des VPS qui portent le tag `Environment:Production` :

```json
{
  "conditions": {
    "conditions": [
      {
        "operator": "MATCH",
        "values": {
          "resource.Tag(Environment)": "Production"
        }
      }
    ],
    "operator": "AND"
  },
  "description": "Give access to VPS with tag Environment:Production",
  "identities": [
    "urn:v1:eu:identity:group:aa1-ovh/devs"
  ],
  "name": "vps-production",
  "permissions": {
    "allow": [
      {
        "action": "vps:apiovh:*"
      }
    ]
  },
  "resources": [
    {
      "urn": "urn:v1:eu:resource:vps:*"
    }
  ]
}
```

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).
