---
title : Comment lancer un diagnostic OVHcloud Connect depuis votre espace client
excerpt: Découvrez comment obtenir un rapport de l'état de vos services OVHcloud Connect
mise à jour : 10/04/2025
---

## Objectif

Avec OVHcloud Connect, vous pouvez relier votre réseau d'entreprise à votre réseau privé OVHcloud vRack, sans créer de tunnel VPN à travers Internet. Vous bénéficiez ainsi d’une connexion plus rapide et plus stable, avec une bande passante garantie.

**Ce guide vous explique comment obtenir un rapport de l'état de vos services OVHcloud Connect depuis votre espace client.**


## Prérequis

- une [solution OVHcloud Connect](https://www.ovhcloud.com/fr/network-security/ovhcloud-connect/) avec une configuration POP valide

## Liste des diagnostics disponibles

### Mode L3

- **Par défaut** : Extrait les états de session BGP et toutes les informations associées
- **Routes** : Récupère la table de routage apprise par OVHcloud via BGP
- **Advertised-Routes** : Récupère la table de routage annoncée par OVHcloud via BGP

### Mode L2 

- **Adresse MAC** : Extrait la liste des adresses MAC des périphériques réseau et du vRack

## Instructions

### Mode L3

Dans votre espace client OVHcloud, dans la section Réseau, vous pouvez retrouver la liste de vos services OVHcloud Connect.

![OCC Control Panel](images/OCC_cpanel.png){.thumbnail}

Ouvrez le service pour lequel vous souhaitez obtenir un diagnostic :

![Service OCC](images/OCC_service_BGP.png){.thumbnail}

En bas du panneau « Configuration POP », vous trouverez un segment nommé « Diagnostic POP » et un bouton de sélection **(...)**. Cliquez dessus, puis sélectionnez « Test BGP Peering » :

![Bouton de test du service OCC](images/OCC_service_test_button_BGP.png){.thumbnail}

Une fenêtre s'ouvrira. Sélectionnez le type de diagnostic que vous souhaitez utiliser, puis cliquez sur « Lancer le diagnostic » :

![OCC Diagnostics Choice](images/OCC_diag_choice.png){.thumbnail}

Vous pouvez maintenant accéder à la liste de vos diagnostics en ouvrant l'onglet « Diagnostics ».

![OCC Diagnostics Tab](images/OCC_diag_tab_BGP.png){.thumbnail}

Chaque diagnostic est référencé à l'aide d'un ID et d'un horodatage.
Vous pouvez lire le contenu des diagnostics en cliquant sur le bouton de sélection **(...)** situé à droite de chacun d'entre eux. Vous pouvez sélectionner « Voir le résultat » pour ouvrir une fenêtre avec le contenu du diagnostic souhaité, ou « Télécharger le résultat » pour obtenir un fichier *.txt* avec le même contenu.

![OCC Diagnostic view button](images/OCC_diag_view_button.png){.thumbnail}

### Mode L2

Dans votre espace client OVHcloud, dans la section Réseau, vous pouvez retrouver la liste de vos services OVHcloud Connect.

![OCC Control Panel](images/OCC_cpanel.png){.thumbnail}

Ouvrez le service pour lequel vous souhaitez obtenir un diagnostic :

![Service OCC](images/OCC_service_MAC.png){.thumbnail}

En bas du panneau « Configuration POP », vous trouverez un segment nommé « POP Diagnostic » et un bouton de sélection **(...)**. Cliquez dessus, puis sélectionnez « Voir la liste de mes adresses MAC » :

![OCC Service Test Button](images/OCC_service_test_button_MAC.png){.thumbnail}

Vous pouvez maintenant accéder à la liste de vos diagnostics en ouvrant l'onglet « Diagnostics ».

![OCC Diagnostics Tab](images/OCC_diag_tab_MAC.png){.thumbnail}

Chaque diagnostic est référencé à l'aide d'un ID et d'un horodatage.
Vous pouvez lire le contenu des diagnostics en cliquant sur le bouton de sélection **(...)** situé à droite de chacun d'entre eux. Vous pouvez sélectionner « Voir le résultat » pour ouvrir une fenêtre avec le contenu du diagnostic souhaité, ou « Télécharger le résultat » pour obtenir un fichier *.txt* avec le même contenu.

![OCC Diagnostic view button](images/OCC_diag_view_button.png){.thumbnail}

## Limites

- **Durée de rétention des diagnostics** : vous ne pouvez visualiser que les diagnostics initiés **au cours des sept derniers jours.** Nous vous recommandons de les télécharger et de les archiver correctement, au cas où vous auriez besoin d'un accès ultérieur.

- **Nombre maximum de diagnostics** : sur une période de 24 heures, vous pouvez lancer un maximum de 10 diagnostics par type de diagnostic et par service. Par exemple, si vous avez deux services OVHcloud Connect configurés sur votre espace client OVHcloud, tous deux configurés en mode Layer 3, vous pouvez théoriquement lancer 10 de chaque type de diagnostic par service, pour un total de 60.
<br> Cette limite a été fixée afin de limiter la quantité de ressources utilisées par l’infrastructure OVHcloud, les diagnostics étant lancés en temps réel.

## Aller plus loin

Si vous avez besoin de formation ou d'assistance technique pour mettre en œuvre nos solutions, contactez votre représentant commercial ou cliquez sur [ce lien](https://www.ovhcloud.com/fr/professional-services/) pour obtenir un devis et demandez à nos experts Professional Services de vous aider sur votre cas d'utilisation spécifique de votre projet.

Échangez avec notre communauté d’utilisateurs sur <https://community.ovh.com/>.
