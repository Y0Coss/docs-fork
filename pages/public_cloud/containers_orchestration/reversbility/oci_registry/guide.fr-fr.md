---
title : Politique de réversibilité du produit Managed OCI artifact Registry
updated: 2025-06-10
---

## Objectif

Ce document décrit la politique de réversibilité du produit Managed OCI artifact Registry correspondant à l'offre OVHcloud : Managed Private Registry

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.



## Liste des fonctionnalités

Les caractéristiques de la â€oeProductâ€  sont réparties en trois catégories :

- **Fonctionnalités principales** pour lesquelles nous garantissons la capacité de migration.
- ** Implémentations OVHcloud ** qui nécessitent une adaptation à un nouvel environnement de migration.
- **Fonctionnalités spécifiques** qui ne peuvent pas être garanties pour la migration car elles sont liées à l'environnement OVHcloud ou impliquent des développements personnalisés.



## Fonctionnalités principales

| Fonctionnalité                  | Description                                  | Formats       | Modèle de migration                                                                                                                                           | Documentation disponible |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| **API OCI et compatibilité** | Prise en charge native du format OCI (Open Container Initiative) pour les artefacts, les images, les graphiques Helm, les signatures Cosign, etc. | OCI, Helm, Cosign (signatures), JSON   | **Entrant** : Direct artifact push via des outils standard (docker, helm, oras, cosign, etc.) ou via l’API OCI.<br>**Sortant** : Extraction/exportation à l’aide des mêmes outils ou API vers tout registre compatible OCI/Harbor/Artifact Registry. | [API et compatibilité OCI](https://help.ovhcloud.com/csm/fr-public-cloud-private-registry-migrate-helm-charts?id=kb_article_view&sysparm_article=KB0058870)|
| **Import/Export d'artefacts**   | Upload and download of artifacts (push/pull) via Harbor/OCI CLI/API standard                                | OCI, Helm, JSON                        | **Entrant** : Import via `docker push`, `helm push`, `oras push`, etc.<br>**Sortant** : Export via `docker pull`, `helm pull`, `oras pull`, puis push vers la cible. | [Artifact Import/Export](https://help.ovhcloud.com/csm/fr-public-cloud-private-registry-migrate-helm-charts?id=kb_article_view&sysparm_article=KB0058870)|
| **Cosigner la signature** | Signature et vérification via Cosign (Sigstore), support natif à Harbor >= v2.5                                       | Cosign (signature OCI)      | **Entrant** : Importation des artefacts signés avec Cosign.<br>**Sortant** : Exportation des artefacts avec signatures, réutilisables sur tout registre Cosign/OCI compatible.                  | [ Signer les artefacts OCI avec Cosign sur le registre privé géré OVHcloud ](https://help.ovhcloud.com/csm/fr-public-cloud-private-registry-sign-artifacts-with-cosign?id=kb_article_view&sysparm_article=KB0059137)|
| **Port de réplication**            | Synchronisation automatique entre registres Harbor/OCI (push/pull ou bidirectionnelle)                                  | OCI, Helm, JSON             | **Entrant** : Configuration de la réplication depuis un registre source (Harbor/OCI).<br>**Sortant** : Réplication vers un autre registre Harbor/OCI compatible.                | [Configuration de la réplication](goharbour.io/docs/2.0.0/administration/configuration-réplication/)|
## Implémentation OVHcloud

| Fonctionnalité         | Description                                                                                                       | Formats disponibles | Modèle de migration                                                                                                                          | Documentation disponible |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| **RBAC et gestion des droits**      | Gestion des droits d'accès par projet, utilisateur, compte robot, RBAC Harbor                                               | JSON (policies), interne Harbor | **Entrante** : Adaptation manuelle des droits lors de l’import.<br>**Sortante** : Export des artefacts, puis reconfiguration des droits sur la cible.                                  |[Gestion des utilisateurs et des projets](https://help.ovhcloud.com/csm/fr-public-cloud-private-registry-management-users-projects?id=kb_article_view&sysparm_article=KB0055968)|
| **Journaux d'audit**        | Logging automatique des accès et des opérations (logs Harbor / OVHcloud)                                                    | JSON, logs internes              | **Entrante** : Non applicable à l'import.<br>**Sortante** : Export manuel des logs si nécessaire, adaptation nécessaire selon la cible.|[Access and Search Project Logs](https://goharbour.io/docs/2.3.0/working-with-projects/project-configuration/access-project-logs/)|
| **Automatisation CI/CD**            | Intégration avec les pipelines CI/CD via API Harbor/OCI, tokens robots, OIDC                                                      | JSON, YAML (pipelines)           | **Entrante** : Adaptation des pipelines pour pointer vers OVHcloud.<br>**Sortante** : Reconfiguration des pipelines vers la nouvelle cible, adaptation potentielle des tokens.         | [Harbor API](https://api.harbour.gg/docs/index.html)|
| **Analyse des vulnérabilités**       | Analyse automatique des images via scanner Harbor intégré (Trivy, Clair, etc.)                                               | JSON, rapports CSV               | **Entrante** : Non applicable à l’import.<br>**Sortante** : Exportation de rapports possible, adaptation à prévoir pour la cible en fonction de l’outil de scan utilisé.|[Clair project](https://clairproject.org/)|


## Fonctionnalités spécifiques

| Function               | Description                                                                           | Formats disponibles | Modèle de migration                                                                                   | Documentation disponible |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| **OVHcloud Manager/API**          | Interface graphique et API spécifiques à OVHcloud pour la gestion des clusters et des ressources                                 | N/A    | **Entrant** : N/A<br>**Sortant** : les scripts et l'automatisation doivent être réécrits pour le fournisseur cible ; une gestion manuelle peut être nécessaire.                            | [Spécification API OVHcloud ](https://eu.api.ovh.com/console/?section=%2FallDom&branch=v1)|
| **Infrastructure as Code** | Déploiement automatisé via les modules Terraform spécifiques à OVHcloud                           | N/A                | **Migration entrante :** Les scripts doivent être adaptés à d'autres fournisseurs. <br> **Migration sortante :** Réécriture de la configuration requise pour Terraform.                             | [Terraform](https://registry.terraform.io/providers/ovh/ovh/latest/docs)                      |



## Liste des architectures

Le service OVHcloud Managed Private Registry (basé sur Harbor) prend en charge une architecture multi-projets, multi-espaces de noms et multi-utilisateurs avec isolation logique. Il permet la réplication automatique entre les registres (Harbor/OCI), le contrôle d'accès affiné (RBAC), l'authentification OIDC, la signature et la vérification des artefacts (Cosign), l'analyse des vulnérabilités et l'intégration CI/CD via API ou des jetons de robot.
Le service est hautement disponible et peut être intégré au réseau privé vRack d’OVHcloud pour une utilisation sécurisée.



## Services Partenaires

Les partenaires OVHcloud sont répertoriés sous le mot-clé **« Migration vers le cloud »** dans l'annuaire des partenaires dédiés.

OVHcloud propose également un service dédié : [**OVHcloud Professional Services**](https://www.ovhcloud.com/fr/professional-services/).



## Coût et frais

La facturation est basée sur l'utilisation sans engagement.
Il n’y a ** pas de frais de résiliation** : la suppression du service entraîne l’arrêt immédiat de la facturation.
Tous les ** crédits OVHcloud associés sont non transférables**.

Les clients sont responsables de l'exportation de leurs artefacts avant leur suppression, car la suppression des données est irréversible.


## Rétention des données après résiliation du contrat

Après la suppression du service ou la résiliation du contrat, OVHcloud **supprime définitivement tous les artefacts, images, signatures et métadonnées** stockés dans le registre.
Les logs d'accès et l'historique sont également supprimés.
Il est donc ** essentiel d'exporter toutes les données nécessaires avant la suppression**, car la restauration n'est pas possible par la suite.
