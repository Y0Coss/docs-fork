---
title : Politique de réversibilité du produit Managed OCI artifact Registry
updated: 2025-06-10
---

## Objectif

Ce document décrit la politique de réversibilité du produit Managed OCI artifact Registry correspondant à l'offre OVHcloud : Managed Private Registry

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.

## Liste des fonctionnalités

Les caractéristiques du produit sont réparties en trois catégories :

- **Fonctionnalités principales** pour lesquelles nous garantissons la capacité de migration.
- **Implémentations OVHcloud** qui nécessitent une adaptation à un nouvel environnement de migration.
- **Fonctionnalités spécifiques** qui ne peuvent pas être garanties pour la migration car elles sont liées à l'environnement OVHcloud ou impliquent des développements personnalisés.



## Fonctionnalités principales

| Fonctionnalité| Description | Formats | Modèle de migration | Documentation disponible |
| --- | --- | --- | --- | --- |
| **API OCI et compatibilité OCI** | Support natif du format OCI (Open Container Initiative) pour artefacts, images, Helm charts, signatures Cosign, etc. | OCI, Helm, Cosign (signatures), JSON   | **Entrant** : Push direct des artefacts via outils standards (docker, helm, oras, cosign, etc.) ou API OCI.<br>**Sortant** : Pull/export des artefacts via les mêmes outils ou API vers tout autre registre compatible OCI/Harbor/Artifact Registry. | [Migrate Helm Chart from Chartmuseum to OCI](/pages/public_cloud/containers_orchestration/managed_private_registry/migrate-helm-charts-from-chartmuseum-to-oci)|
| **Import/Export d'artefacts**   | Téléversement et téléchargement d’artefacts (push/pull) via CLI/API standard Harbor/OCI | OCI, Helm, JSON  | **Entrant** :Import via docker push, helm push, oras push, etc.<br>**Sortant** : Export via docker pull, helm pull, oras pull, puis push vers la cible. | [Artifact Import/Export](/pages/public_cloud/containers_orchestration/managed_private_registry/migrate-helm-charts-from-chartmuseum-to-oci) |
| **Signature et vérification Cosign** | Signature et vérification d’artefacts via Cosign (Sigstore), support natif Harbor v2.5+ | Cosign (OCI signature) | **Entrant** : Import d’artefacts signés Cosign.<br>**Sortant** : Export des artefacts et de leurs signatures Cosign, réimport possible sur tout registre compatible Cosign/OCI. | [ Sign OCI artifacts with Cosign on OVHcloud Managed Private Registry](/pages/public_cloud/containers_orchestration/managed_private_registry/sign-artifacts-with-cosign) |
| **Replication Harbor** | Synchronisation/réplication automatique entre registres Harbor/OCI (push/pull ou bidirectionnelle) | OCI, Helm, JSON | **Entrant** : Configuration de la réplication depuis un registre source (Harbor/OCI) vers OVHcloud.<br>**Sortant** : Configuration de la réplication vers un autre registre compatible Harbor/OCI. | [Configuration de la réplication](goharbour.io/docs/2.0.0/administration/configuration-réplication/)|


## Implémentation OVHcloud

| Fonctionnalité| Description | Formats | Modèle de migration | Documentation disponible |
| --- | --- | --- | --- | --- |
| **RBAC et gestion des droits** | Gestion des droits d'accès par projet, utilisateur, compte robot, RBAC Harbor | JSON (policies), interne Harbor | **Entrant** : Adaptation manuelle des droits lors de l’import.<br>**Sortant** : Export des artefacts, puis reconfiguration des droits sur la cible. |[Gestion des utilisateurs et des projets](https://help.ovhcloud.com/csm/fr-public-cloud-private-registry-management-users-projects?id=kb_article_view&sysparm_article=KB0055968)|
| **Journaux d'audit** | Logging automatique des accès et des opérations (logs Harbor / OVHcloud) | JSON, logs internes | **Entrant** : Non applicable à l'import.<br>**Sortante** : Export manuel des logs si nécessaire, adaptation nécessaire selon la cible.|[Access and Search Project Logs](https://goharbour.io/docs/2.3.0/working-with-projects/project-configuration/access-project-logs/) |
| **Automatisation CI/CD** | Intégration avec les pipelines CI/CD via API Harbor/OCI, tokens robots, OIDC | JSON, YAML (pipelines) | **Entrant** : Adaptation des pipelines pour pointer vers OVHcloud.<br>**Sortant** : Reconfiguration des pipelines vers la nouvelle cible, adaptation potentielle des tokens.         | [Harbor API](https://api.harbour.gg/docs/index.html)|
| **Analyse des vulnérabilités** | Analyse automatique des images via scanner Harbor intégré (Trivy, Clair, etc.) | JSON, rapports CSV | **Entrant** : Non applicable à l’import.<br>**Sortant** : Export de rapports possible, adaptation à prévoir pour la cible en fonction de l’outil de scan utilisé.|[Clair project](https://clairproject.org/)|


## Fonctionnalités spécifiques

| Fonctionnalité| Description | Formats | Modèle de migration | Documentation disponible |
| --- | --- | --- | --- | --- |
| **OVHcloud Manager/API** | Interface graphique et API spécifiques à OVHcloud pour la gestion des clusters et des ressources | N/A | **Entrant** : N/A<br>**Sortant** : les scripts et l'automatisation doivent être réécrits pour le fournisseur cible ; une gestion manuelle peut être nécessaire. | [Spécification API OVHcloud ](https://eu.api.ovh.com/console/?section=%2FallDom&branch=v1)|
| **Infrastructure as Code** | Déploiement automatisé via les modules Terraform spécifiques à OVHcloud  | N/A | **Entrant :** Les scripts doivent être adaptés à d'autres fournisseurs. <br> **Sortant :** Réécriture de la configuration requise pour Terraform. | [Terraform](https://registry.terraform.io/providers/ovh/ovh/latest/docs) |



## Liste des architectures

Le service Managed Private Registry d’OVHcloud (basé sur Harbor) supporte une architecture multi-projets, multi-namespaces et multi-utilisateurs avec isolation logique. Il permet la réplication automatique entre registres (Harbor/OCI), la gestion fine des droits (RBAC), l’authentification OIDC, la signature et la vérification des artefacts (Cosign), le scanning de vulnérabilités, ainsi que l’intégration CI/CD via API ou tokens robot. Le service est hautement disponible et peut être intégré au réseau privé vRack OVHcloud pour des usages sécurisés.

## Services Partenaires

Les partenaires OVHcloud sont répertoriés sous le mot-clé **« Migration vers le cloud »** dans l'annuaire des partenaires dédiés.

OVHcloud propose également un service dédié : [**OVHcloud Professional Services**](https://www.ovhcloud.com/fr/professional-services/).



## Coût et frais

La facturation est à l’usage, sans engagement. Aucun frais de résiliation spécifique n’est appliqué : la suppression du service arrête la facturation immédiatement. Les crédits OVHcloud éventuellement associés ne sont pas transférables. Il incombe au client d’exporter ses artefacts avant suppression, car leur effacement est irréversible.


## Conservation des données après résiliation du contrat

Après suppression du service ou résiliation du contrat, OVHcloud supprime définitivement tous les artefacts, images, signatures et métadonnées stockés dans le registre. Les logs et historiques d’accès sont également supprimés. Il est donc impératif d’exporter toutes les données nécessaires avant suppression, aucune restauration n’étant possible après coup.
