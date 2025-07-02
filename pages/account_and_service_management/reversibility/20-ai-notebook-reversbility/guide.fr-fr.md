---
title: "Politique de réversibilité du produit Notebook Interface"
updated: 2025-07-02
---

## Objectif

Ce document est la politique de réversibilité du produit Notebook Interface couvrant l’offre commerciale d’OVHcloud AI Notebooks.

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.

## Liste des fonctionnalités

Les fonctionnalités du produit sont réparties en trois catégories :

1. Les **fonctionnalités principales** pour lesquelles nous garantissons la capacité de migration.
1. Les **implémentation OVHcloud** qui nécessitent une adaptation à un nouvel environnement de migration.
1. Les **fonctionnalités spécifiques** qui ne peuvent pas être garanties pour la migration car elles sont liées à l'environnement OVHcloud ou impliquent des développements personnalisés.

### 1 - Fonctionnalités principales

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| Import/Export de notebooks | Stockage des notebooks aux formats standards Jupyter (.ipynb) ou VS Code Notebook avec import et export sans adaptation | (.ipynb), Python, CSV, TXT | **Entrante** : téléchargement direct de fichiers .ipynb ou conversion via Jupyter/VS Code. <br>**Sortante** : export direct des notebooks .ipynb, réutilisables sur tout environnement Jupyter ou autre compatible.  |[Se servir de données dans un notebook via l'espace client](/pages/public_cloud/ai_machine_learning/notebook_guide_data_ui) |
| Support des IA standards | Pré installation d’environnements comme TensorFlow, PyTorch, Scikit-learn, MXNet, Hugging Face, etc. | Notebooks, Python scripts | **Entrante** :import de notebooks/scripts utilisant ces frameworks. <br>**Sortante** :export des notebooks/scripts, réutilisables sur toute plateforme supportant ces frameworks.  | [Tutoriel - Utiliser Tensorboard dans un notebook](/pages/public_cloud/ai_machine_learning/notebook_tuto_02_tensorboard) |
| Gestion des environnements personnalisés | --- | --- | **Entrante** : <br>**Sortante** :  | --- |

### 2 - Implémentations OVHcloud

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |


### 3 - Fonctionnalités spécifiques

| **Fonction** | **Description** | **Formats disponibles** | **Modèle de migration** | **Documentation disponible** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |
| --- | --- | --- | **Entrante** : <br>**Sortante** :  | --- |

| Anti-DDoS | L’anti-DDoS est un ensemble d’outils et de mécanismes conçus pour absorber les attaques par déni de service. Il comprend l'analyse du trafic, le « nettoyage » via un réseau spécialisé et la mitigation grâce à la technologie VAC développée par OVHcloud. | N/A | **Entrant** : le système anti-DDoS fait partie de notre infrastructure et est activé par défaut. Aucune action n'est requise. <br> **Sortant** : commande et configuration un anti-DDoS chez le nouveau fournisseur. | [OVHcloud DDoS Protection](/links/security/antiddos) |

## Liste des architectures

blabla
Le produit est décliné en deux offres de service : 
- xxxxx
- xxxxx

## Services partenaires

Les partenaires OVHcloud concernés figurent dans l'annuaire des [partenaires OVHcloud](/links/partner) sous les mots-clés « **Data center expansion and Migration** ».

OVHcloud dispose également d’un service dédié : [OVHcloud Professional Services](/links/professional-services).

## Coûts et frais


## Conservation des données après résiliation du contrat


