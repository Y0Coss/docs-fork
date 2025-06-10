# Reversibility Policy for the â€oeManaged Orchestrationâ€  Product

## Objectif

Ce document décrit la politique de réversibilité pour la gamme de produits (Managed Orchestration).

Cette politique vise à mettre en œuvre les principes généraux de réversibilité et notre conformité avec le Code de conduite SWIPO IaaS pour les fournisseurs de cloud.



## Liste des fonctionnalités

Les caractéristiques de la â€oeProductâ€  sont réparties en trois catégories :

- **Fonctionnalités principales** pour lesquelles nous garantissons la capacité de migration.
- ** Implémentations OVHcloud ** qui nécessitent une adaptation à un nouvel environnement de migration.
- **Fonctionnalités spécifiques** qui ne peuvent pas être garanties pour la migration car elles sont liées à l'environnement OVHcloud ou impliquent des développements personnalisés.



## Fonctionnalités principales

| Fonctionnalité                  | Description                                  | Formats       | Modèle de migration                                                                                                                                           | Documentation disponible |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| **Orchestration via Kubernetes** | Gestion des clusters via l’API Kubernetes (kubectl, Helm, CI/CD, etc.), conforme CNCF.                            | YAML, JSON, OCI               | **Entrant** : Déployez des manifestes, des graphiques Helm et des images OCI via l’API Kubernetes standard.<br>**Sortant** : Exportez des manifestes, des graphiques Helm, des images ; réutilisables sur tout cluster Kubernetes compatible. | [Creating a cluster](https://help.ovhcloud.com/csm/fr-public-cloud-kubernetes-create-cluster?id=kb_article_view&sysparm_article=KB0054955)|
| **Orchestration via Rancher**   | Orchestration de conteneurs simplifiant le déploiement, la gestion et la mise à l’échelle des applications conteneurisées.                | YAML, JSON, OCI               | **Entrant** : Importation de manifestes, de graphiques Helm, d’images OCI ou de cluster via l’API et l’interface utilisateur.<br>**Sortant** : Exportation de manifestes, de graphiques, d’images via l’API ; réutilisable sur tout cluster compatible.            | [Getting Started with Managed Rancher Service](https://help.ovhcloud.com/csm/fr-public-cloud-managed-rancher-service-getting-started?id=kb_article_view&sysparm_article=KB0061903)
| **Exportation/Importation de manifeste**      | Déploiement, exportation et migration de ressources via des fichiers Kubernetes YAML/JSON standard.                        | YAML, JSON                    | **Entrant** : Importation directe des manifestes existants.<br>**Sortant** : Exporter à l'aide de `kubectl get -o yaml/json` ; utilisable sur tout cluster Kubernetes compatible. |[Deploying an application](https://help.ovhcloud.com/csm/fr-public-cloud-kubernetes-deploy-application?id=kb_article_view&sysparm_article=KB0054991)|
| **IAM**                         | Gestion des identités et des accès pour les ressources du cluster via Rancher en utilisant des fournisseurs d'identité externes.           | Active Directory, LDAP, OpenLDAP, Azure AD | **Entrant** : créez ou importez des rôles et des stratégies d’accès via l’API ou l’interface utilisateur.<br>**Sortant** : exportez des configurations via l’API ou l’interface utilisateur Rancher.                              | [Configuration de l'authentification](https://ranchermanager.docs.rancher.com/guides-pratiques/guides-nouveaux-utilisateurs/permissions-authentification-et-configuration-globale/authentication-config)|

## Implémentation OVHcloud

| Fonctionnalité         | Description                                                                                                       | Formats disponibles | Modèle de migration                                                                                                                          | Documentation disponible |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| **Liaison du fournisseur d'identité**        | Connexion entre l'identity provider et le cluster                                                        | JSON                | **Entrant** : Ajustez les fichiers de configuration au format OVH avant de les importer via CLI ou UI.<br>**Sortant** : exportez au format OVH, puis adaptez-vous à l’environnement cible.    | [Configuring the OIDC provider on an OVHcloud Managed Kubernetes cluster](https://help.ovhcloud.com/csm/en-public-cloud-kubernetes-configure-oidc-provider?id=kb_article_view&sysparm_article=KB0049671)|
| **Configuration du plan de contrôle**      | Configuration du control plane Kubernetes via API OVH                                                 | N/A                 | **Entrant** : certains paramètres du control plane configurables via l’API OVH.<br>**Sortant** : non directement exportables ; à redéfinir manuellement dans la configuration cible. | [Creating a cluster](https://help.ovhcloud.com/csm/fr-public-cloud-kubernetes-create-cluster?id=kb_article_view&sysparm_article=KB0054955)|
| **Intégration vRack**                | vRack fournit un réseau VLAN privé pour les services OVHcloud (uniquement sur le plan de données Kubernetes, pas sur le plan de contrôle) | N/A               | **Entrant** : Managed Kubernetes inclut vRack par défaut.<br>**Sortant** : documente l’architecture réseau et effectue la réplication avec le VLAN dans l’environnement cible.        | [ Using vRack Private Network ](https://help.ovhcloud.com/csm/fr-public-cloud-kubernetes-using-vrack?id=kb_article_view&sysparm_article=KB0055392)|
| **Journalisation**                          | Audit et traçabilité des actions au sein de Kubernetes. Les journaux du Rancher ne sont pas accessibles au client.                | N/A                 | **Entrant** : N/A<br>**Sortant** : La redirection des journaux nécessite l’intégration avec des outils externes conformes au LDP.                                                          |[Managed Kubernetes Service Audit Logs Forwarding](https://help.ovhcloud.com/csm/en-public-cloud-kubernetes-forwarding-audit-logs?id=kb_article_view&sysparm_article=KB0062285)|
| **Opérateurs et modules complémentaires personnalisés**       | Certains opérateurs/modules complémentaires sont déployés via OVHcloud Marketplace ou sont spécifiques à OVHcloud                        | YAML, JSON, Helm    | **Entrant** : Installer si compatible avec OVHcloud Kubernetes.<br>**Sortant** : Peut nécessiter une adaptation ou un remplacement par des équivalents standard (en particulier dans Rancher).       |[OVH Marketplace](https://marketplace.ovhcloud.com/?at_medium=sl&at_platform=google&at_campaign=AdWords&at_creation=noi_ovhmarketplace_fr_se_marketplace_defensive_acquisition_mofu()&at_variant=684417988319&at_network=search&at_term=ovh%20marketplace&gad_source=1&gad_campaignid=20716049&cgad_term=Cgad_source=1&cgad_campaignid=207166044999999999999999799999999999999999999999999999999979997999999999999999999999999997999999799999999999999997999332333 jwuvrBBhDcARIsAKRrkjdW-xorTLoCGLJT6ZIcLU6ayHPc80rpGxAAqcLnFeFggWUd2w1ycPgaAk-IEALw_wcB)|
| **Pools de nœuds**                       | Prise en charge de la création et de la gestion des pools de nœuds                                                                | N/A                 | **Entrant** : les pools de nœuds sont configurés via l’interface OVH.<br>**Sortant** : le format du pool peut être réutilisé dans des environnements cibles équivalents.                            |[Managing nodes and node pools](https://help.ovhcloud.com/csm/en-public-cloud-kubernetes-manage-nodes?id=kb_article_view&sysparm_article=KB0049898)|


## Fonctionnalités spécifiques

| Function               | Description                                                                           | Formats disponibles | Modèle de migration                                                                                   | Documentation disponible |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| **OVHcloud Manager/API**          | Interface graphique et API spécifiques à OVHcloud pour la gestion des clusters et des ressources                                 | N/A    | **Entrant** : N/A<br>**Sortant** : les scripts et l'automatisation doivent être réécrits pour le fournisseur cible ; une gestion manuelle peut être nécessaire.                            | [Spécification API OVHcloud ](https://eu.api.ovh.com/console/?section=%2FallDom&branch=v1)|
| **Mises à jour gérées (MCO / MCS)**   | Mises à jour du control plane gérées par OVHcloud                                                                         | N/A    | **Entrant** : N/A<br>**Sortant** : non portable ; géré différemment selon la stratégie de mise à jour de la plateforme cible.                                            | [Partage de responsabilitÃ© sur le service Kubernetes managé par OVHcloud](https://help.ovhcloud.com/csm/fr-public-cloud-kubernetes-sibility-model?id=kb_article_view&sysparm_article=KB0058750)|
| **Rancher OVHcloud Edition**      | Version limitée de Rancher disponible chez OVHcloud                                                              | N/A    | **Entrant** : configurez les fonctionnalités de Rancher si disponibles.<br>**Sortant** : réécriture nécessaire pour une utilisation avec des outils de Rancher complets ou d'autres outils de gestion.       |[Managed Rancher Service](https://www.ovhcloud.com/fr/public-cloud/managed-rancher-service/)|
| **Infrastructure as Code** | Déploiement automatisé via les modules Terraform spécifiques à OVHcloud                           | N/A                | **Migration entrante :** Les scripts doivent être adaptés à d'autres fournisseurs. <br> **Migration sortante :** Réécriture de la configuration requise pour Terraform.                             | [Terraform](https://registry.terraform.io/providers/ovh/ovh/latest/docs)                      |
| **Anti-DDoS** | L’anti-DDoS est un ensemble d’outils et de mécanismes conçus pour absorber les attaques par déni de service. Il comprend l'analyse du trafic, le « nettoyage » via un réseau spécialisé et la mitigation grâce à la technologie VAC développée par OVHcloud.                                                  | N/A                | **Migration entrante :** Le système anti-DDoS fait partie de notre infrastructure et est activé par défaut. Aucune action n'est requise. <br> **Migration sortante:** Commander et configurer un service anti-DDoS chez le nouveau fournisseur.             | [Protection anti-DDoS](https://www.ovh.com/fr/anti-ddos/)<br>[Technologie anti-DDoS](https://www.ovh.com/fr/anti-ddos/technologie-anti-ddos.xml)                        |



## Liste des architectures

La solution Managed Orchestration d’OVHcloud est basée sur des clusters Kubernetes gérés et multi-nœuds, offrant une haute disponibilité, une mise à l’échelle automatique, une gestion centralisée et une intégration de réseau privé (vRack). Elle comprend l’intégration avec les principaux outils de surveillance, de journalisation et de CI/CD. Les architectures prises en charge permettent la migration multi-cloud et le déploiement hybride.

Le service managé d'orchestration fonctionne dans une seule région (parmi plusieurs régions disponibles proposées par OVHcloud). Il est possible de gérer plusieurs clusters dans différentes régions (fournis par OVHcloud ou d'autres fournisseurs) à l'aide du service Rancher exécuté dans une seule région.



## Services Partenaires

Les partenaires OVHcloud sont répertoriés sous le mot-clé **« Migration vers le cloud »** dans l'annuaire des partenaires dédiés.

OVHcloud propose également un service dédié : [**OVHcloud Professional Services**](https://www.ovhcloud.com/fr/professional-services/).



## Coût et frais

La facturation suit un modèle de **paiement à l’usage**. Les frais cessent lorsque le client ne consomme plus de ressources.
Il n’y a ** pas de frais de résiliation** : la suppression du service entraîne immédiatement l’arrêt de la facturation.
Tous les ** crédits OVHcloud associés sont non transférables**.

Après résiliation, OVHcloud libère les ressources associées, ce qui signifie que les données ne peuvent pas être récupérées.
Les clients sont responsables de l'exportation de leurs configurations, manifestes et images de conteneurs **avant la résiliation**.

> **Remarque :** Lors de l'utilisation de Rancher, des frais minimaux s'appliqueront même si aucun cluster n'est orchestré.

## Rétention des données après résiliation du contrat

Une fois le service supprimé ou le contrat résilié, OVHcloud libère les ressources du cluster.
Il est donc ** impératif d'exporter au préalable toutes les données et configurations nécessaires **, aucune restauration n'étant possible par la suite.
