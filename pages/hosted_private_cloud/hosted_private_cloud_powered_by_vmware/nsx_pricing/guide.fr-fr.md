---
title: Tarification et gestion des NSX Edges OVHcloud
excerpt: Guide sur les options de tarification, configurations et personnalisation des NSX Edges pour VMware sur OVHcloud.
updated: 2025-01-02
---
# Informations concernant le mode de tarification et les configurations des NSX Edges

## Objectif
Cette documentation a pour but d'expliquer les options de tarification, les configurations disponibles et les possibilités de personnalisation des NSX Edges dans un environnement VMware sur OVHcloud. Elle fournit également les étapes pour gérer ces configurations à travers l'interface OVHcloud.

---

## Prérequis
- **Accès à l’interface Manager OVHcloud** pour gérer vos NSX Edges.
- **Utilisation de VMware NSX 4.1.1** pour accéder aux options de personnalisation.
- Connaissance de base des concepts VMware et des fonctionnalités des NSX Edges.

---

## Principe général
### Configuration par défaut
Lors de la création d’un environnement VMware, OVHcloud fournit automatiquement :
- **2 NSX Edges Medium** :
  - 4 vCPU.
  - 8 Go RAM.
- Cette configuration par défaut répond à la majorité des besoins standards en connectivité et en sécurité réseau.

### Personnalisation
Vous pouvez adapter votre infrastructure en fonction de vos besoins spécifiques :
1. **Taille des NSX Edges** :
   - Medium : 4 vCPU, 8 Go RAM.
   - Large : 8 vCPU, 32 Go RAM.
   - XL : 16 vCPU, 64 Go RAM.
2. **Nombre de NSX Edges** :
   - Minimum : 2 (configuration par défaut).
   - Maximum : Jusqu’à **10 NSX Edges par cluster**.

### Limitations
- **1 cluster NSX Edge par vDC**.
- **10 NSX Edges maximum par cluster** (limitation Broadcom/VMware).
- Les versions NSX 4.0.1 ne supportent pas :
  - La commande de nouveaux vDC sous NSX 4.1.1.
  - La modification ou l’ajout de NSX Edges.

> _[Insérer une capture d'écran montrant une configuration par défaut dans l'interface Manager]_

---

## En pratique
### Étapes pour personnaliser les NSX Edges
1. **Commander de nouveaux NSX Edges** :
   - Connectez-vous à l’interface Manager OVHcloud.
   - Naviguez vers la section **NSX Edges** de votre environnement VMware.
   - Cliquez sur « Ajouter un Edge » et sélectionnez la taille souhaitée.

   > _[Insérer une capture d'écran du processus de commande dans l'interface Manager]_

2. **Modifier la taille des NSX Edges existants** :
   - Accédez à la liste des NSX Edges dans le Manager.
   - Sélectionnez l’Edge à modifier.
   - Choisissez une nouvelle taille (Medium, Large ou XL) et appliquez les modifications.

   > _[Insérer une capture d'écran de la modification de taille dans l'interface Manager]_

3. **Supprimer des NSX Edges inutilisés** :
   - Identifiez l’Edge à supprimer dans l’interface Manager.
   - Cliquez sur « Supprimer » et confirmez l’action.

   > _[Insérer une capture d'écran illustrant la suppression d’un NSX Edge]_

### Tarification
- **Medium** : 200 €/mois pour 2 NSX Edges.
- **Large** : 400 €/mois pour 2 NSX Edges.
- **XL** : 800 €/mois pour 2 NSX Edges.
- Chaque NSX Edge supplémentaire est facturé selon la taille choisie.

   > _[Insérer un tableau récapitulatif des prix par taille dans l'interface Manager]_

---

## Aller plus loin
Pour des informations détaillées ou pour résoudre des problèmes techniques, vous pouvez consulter les ressources suivantes :
- **[Documentation technique VMware NSX](https://www.vmware.com/products/nsx.html)** pour explorer les fonctionnalités avancées des NSX Edges.
- En cas de besoin, contactez le support OVHcloud via votre espace client.
