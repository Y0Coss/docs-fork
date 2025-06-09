---
title : Politique de réversibilité de Cold Storage
mise à jour : 2025-06-09
---

## Objectif

Ce document décrit la politique de réversibilité du produit Cold Storage couvrant l'offre Cold Archive d’OVHcloud.

Cette politique vise à mettre en œuvre les principes de réversibilité mondiaux et les exigences du code de conduite SWIPO IaaS pour les fournisseurs de cloud.

Carte des fonctionnalités ##

Les fonctionnalités du nom du produit sont réparties en trois catégories :

- Les [fonctionnalités principales](#core-features) pour lesquelles nous garantissons la possibilité de migrer
- La [mise en œuvre d’OVHcloud](#ovhcloud-implementation), dont la migration nécessitera des adaptations à un nouvel environnement.
- [Fonctionnalités spécifiques](#specific-functionalities), dont la migration en tant que telle est impossible à garantir car elles sont liées à l'environnement OVHcloud ou à des développements spécifiques.

### Fonctionnalités principales <a name=« core-features »></a>

|Fonctionnalité|Description|Formats disponibles|Modèle de migration|Documentation disponible|
|---|---|---|---|---|
| **Compatibilité standard des API S3**| Accès et gestion via API compatible S3 (RESTful, outils CLI AWS, SDK, etc.).                              | S3 (REST, JSON, objets)                                                                     | Entrant : chargement direct dans un bucket Object Storage via l’API, la CLI ou le SDK S3. <br> Sortant : récupération/exportation directe via l’API, la CLI ou le SDK S3 vers tout autre fournisseur compatible S3. | [Cold Archive](https://www.ovhcloud.com/fr/cold-archive/) |
| **Import/Export d'objets en bloc**    | Migration de données par lots à l'aide de commandes S3 (`aws s3 cp/sync`, etc.).                                              | S3 (objets, dossiers)                                                                         | Entrant : Copie de données d'une autre solution S3 vers le bucket Object Storage OVHcloud. <br> Sortant : Exportation en masse via les mêmes outils vers une autre plateforme S3 ou compatible. | [Cold Archive](https://www.ovhcloud.com/fr/cold-archive/) |
| **Chiffrement Côté Serveur**       | Chiffrement natif au niveau du compartiment AES-256, compatible S3 SSE.                                               | S3 (SSE-S3, SSE-C)                                                                            | Entrant : téléchargement de données chiffrées ou non, géré de manière transparente. <br> Sortant : exporter sans modification ; chiffrement maintenu ou retraité par la cible. |[Cold Archive](https://www.ovhcloud.com/fr/cold-archive/) |
| **Rétention à long terme**          | Données stockées sur des bandes magnétiques, avec une durée de vie de plus de 10 ans.                                                 | S3 (objets)                                                                                  | Entrant : Importer sans adaptation. <br> Sortant : Export d’objets via API S3 ; Reprise sur n’importe quel stockage compatible. |[Cold Archive](https://www.ovhcloud.com/fr/cold-archive/) |

### Implémentation OVHcloud <a name=« ovhcloud-implementation »></a>

|Fonctionnalité|Description|Formats disponibles|Modèle de migration|Documentation disponible|
|---|---|---|---|---|
| **Archivage complet par compartiments**        | L'archivage s'applique à l'ensemble du compartiment (pas d'archivage au niveau objet).                                           | S3 (compartiment)           | Entrant : nécessite le regroupement d'objets à archiver dans un bucket dédié. <br> Sortant : exporte les objets du bucket, puis les importe dans la cible (une adaptation peut être nécessaire si la cible ne prend pas en charge l’archivage au niveau du bucket). | [Cold Archive](https://www.ovhcloud.com/fr/cold-archive/) |
| **Restauration différée (â€oeUnfreezeâ€)** | Les données doivent être « dégelées » avant d'être téléchargées (plusieurs heures de latence).                                           | S3 (objets)          | Entrant : Non applicable. <br> Sortant : l'utilisateur doit lancer une demande de restauration (« unfreeze »), puis télécharger les objets dans une fenêtre de 24 heures ; adaptation nécessaire si la cible ne dispose pas de ce mécanisme. | [Cold Archive](https://www.ovhcloud.com/fr/cold-archive/) |
| **Immuabilité des données**            | Capacité à rendre les données immuables pour une période définie ou indéfinie (WORM).                                     | S3 (Object Lock)      | Entrant : la source doit prendre en charge l'immuabilité des données S3. <br> Sortant : exportation possible, mais la cible doit prendre en charge le verrouillage S3 ou nécessiter un ajustement manuel des stratégies d'immuabilité. | [Cold Archive](https://www.ovhcloud.com/fr/cold-archive/) |



### Fonctionnalités spécifiques <a name=« specific-functions »></a>

|Fonctionnalité|Description|Formats disponibles|Modèle de migration|Documentation disponible|
|---|---|---|---|---|
|**Anti-DDoS**|L’anti-DDoS est un ensemble d’équipements et de moyens mis en place pour absorber les attaques par déni de service distribuées. Il comprend une analyse du trafic, l’« aspiration » vers un réseau spécialisé et la mitigation, assurée par la technologie VAC développée par OVHcloud.|S/O|**Migration entrante** : L’Anti-DDoS est une composante de notre infrastructure, activée par défaut. Aucune action n’est requise.<br><br>**Migration sortante** : commandez et configurez un anti-DDoS chez le nouveau fournisseur.|[Protection anti-DDoS OVHcloud](https://www.ovh.co.uk/anti-ddos/)<br><br>[Technologie anti-DDoS](https://www.ovh.co.uk/anti-ddos/anti-ddos-technology.xml)|
| **Architecture OVHcloud 4-Datacenter** | Répartition sur 4 datacenters en France grâce à l’erasure coding 8+4.                                       | N/A    | Entrant : Non applicable. <br> Sortant : non transférable, dépend de l’architecture cible.              | [Cold Archive](https://www.ovhcloud.com/fr/cold-archive/) |
| **Gestion via OVHcloud Manager/API** | Interface graphique et API propriétaires OVHcloud pour la gestion des archives.                                   | N/A    | Entrant : Non applicable. <br> Sortant : les scripts/API doivent être réécrits pour la cible ; une gestion manuelle peut être nécessaire. | [Cold Archive](https://www.ovhcloud.com/fr/cold-archive/) |

Liste des architectures ###

Le stockage à froid d’OVHcloud (CDSTO) est basé sur une architecture géo-distribuée dans quatre datacenters physiquement séparés (distants de plusieurs kilomètres), utilisant la technologie de bande magnétique d’IBM. Les données sont stockées à l’aide d’un code d’effacement 8+4, ce qui garantit une résilience et une tolérance extrêmes à la perte d’un site entier.

### Services partenaires

Les partenaires OVHcloud sont répertoriés sous le mot-clé **« Migration vers le cloud »** dans l'annuaire des partenaires dédiés.

OVHcloud propose également un service dédié : [**OVHcloud Professional Services**](https://www.ovhcloud.com/fr/professional-services/).

### Coût et frais

Pas de frais de résiliation : il n'y a pas de frais supplémentaires par défaut pour la migration des données. La facturation s'arrête dès la résiliation du service. Cependant, une modification tarifaire intervient lors de la restauration des données, sur la base de la tarification actuelle du support de stockage vers lequel les données ont été transférées.

### Rétention des données après résiliation du contrat

OVHcloud ne conserve aucune donnée après la résiliation du service. Les snapshots sont supprimés de manière irréversible. Une exportation manuelle doit être réalisée au préalable pour conserver les données.
Pour récupérer ses données, le client doit les désarchiver, puis les récupérer dans le bucket où elles ont été restaurées.
Remarque : le processus de désarchivage peut prendre jusqu'à 48 heures.
