---
title: Object Storage - Comment connecter mon bucket Object Storage avec d'autres ressources dans un réseau privé vRack ?
excerpt: Ce guide explique comment utiliser l'Object Storage avec des ressources dans un réseau privé.
updated: 2025-03-25
---

## Objectif

Ce guide explique comment utiliser l'Object Storage avec des ressources dans un réseau privé. 

## Prérequis

- Un [bucket Object Storage.](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage)
- un [réseau privé vRack.](/pages/public_cloud/public_cloud_network_services/getting-started-07-creating-vrack)
- Une [Gateway Public Cloud.](/pages/public_cloud/public_cloud_network_services/getting-started-02-create-private-network-gateway)
- D'autres ressources (instances Public Cloud, Managed Kubernetes, Bare Metal servers…)

## En pratique

### Context

Votre cas d'utilisation peut nécessiter une connexion sécurisée entre un réseau privé et votre bucket Object Storage. Nos services de réseaux privés vRack & Public Cloud Gateway vous aideront à répondre à vos besoins spécifiques en termes de sécurité et de performance. 

Cela vous permet également d'interconnecter les deux buckets Object Storage avec vos ressources rassemblées dans un réseau privé vRack (voir le diagramme d'architecture ci-dessous).

![vrack private network with buckets - diagram](images/object_storage_buckets_vrack_private.png){.thumbnail}

### Création d'un réseau privé vRack et d'une Gateway Public Cloud

Afin de créer et de configurer à la fois une Gateway Public Cloud et un réseau privé vRack, veuillez suivre les instructions de la [documentation sur la création d'un réseau privé avec une Gateway](/pages/public_cloud/public_cloud_network_services/getting-started-02-create-private-network-gateway). La documentation explique comment :

- Sélectionner et créer la Gateway appropriée en termes de performance et de géo-disponibilité.
- S'attacher à un réseau privé vRack existant ou nouvellement créé.

### Liste blanche des IP de la Gateway

Une fois la Gateway créée et associée à un réseau privé vRack, l'étape suivante consiste à mettre sur liste blanche un ensemble d'IP à partir de votre Object Storage. Pour ce faire, il y a plusieurs façons de procéder :

- Utilisation des politiques d'Object Storage (Politiques de bucket Object Storage) : cette fonctionnalité n'est pas encore disponible mais elle le sera bientôt.
- Nous avons mis en place un processus interne qui vous aide à établir une liste blanche d'un ensemble d'IP en fonction de la configuration de votre Gateway et de votre réseau privé vRack.

Pour ce faire, veuillez contacter notre équipe de support technique avec l'en-tête de demande spécifique « Object Storage - IP whitelisting process » avec la liste des plages d'adresses IP que vous devez mettre sur liste blanche, et notre équipe automatisera la configuration pour vous. Notre équipe automatisera la configuration pour vous. Le processus prend généralement jusqu'à 1 jour.

Après cette dernière étape, vous êtes prêt à utiliser votre Object Storage avec les ressources rassemblées dans un réseau privé vRack.

## Go further

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](/links/professional-services) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre [communauté d'utilisateurs](/links/community).
