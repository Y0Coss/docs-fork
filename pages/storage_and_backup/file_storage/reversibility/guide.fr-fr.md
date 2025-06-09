---
title : Politique de réversibilité du stockage de fichiers
mise à jour : 2025-06-09
---

## Objectif

Ce document présente la politique de réversibilité du produit File Storage couvrant les offres OVHcloud : Enterprise File Storage et NAS-HA .

Cette politique vise à mettre en œuvre les principes de réversibilité mondiaux et les exigences du code de conduite SWIPO IaaS pour les fournisseurs de cloud.

Carte des fonctionnalités ##

Les fonctionnalités du nom du produit sont réparties en trois catégories :

- Les [fonctionnalités principales](#core-features) pour lesquelles nous garantissons la possibilité de migrer
- La [mise en œuvre d’OVHcloud](#ovhcloud-implementation), dont la migration nécessitera des adaptations à un nouvel environnement.
- [Fonctionnalités spécifiques](#specific-functionalities), dont la migration en tant que telle est impossible à garantir car elles sont liées à l'environnement OVHcloud ou à des développements spécifiques.

### Fonctionnalités principales <a name=« Fonctionnalités principales »></a>

|Fonctionnalité|Description|Formats disponibles|Modèle de migration|Documentation disponible|
|---|---|---|---|---|
| **Protocole NFSv3**               | Accès universel via NFSv3, compatible avec tous les systèmes supportant ce protocole.                            | NetApp : NFSv3<br>NAS-HA : NFSv3+v4 | **Entrant** : Montage direct sur serveurs OVH ou externes via NFSv3, copie de fichiers à l’aide d’outils standard (rsync, cp, etc.).<br>**Sortant** : Démontage du volume, copie des fichiers via NFSv3 vers n’importe quel stockage compatible. | [File Storage](https://help.ovhcloud.com/csm/fr-documentation-storage-file-storage?id=kb_browse_cat&kb_id=38e74da5a884a950f07829d7d5c75217&kb_category=4da029c4d56129901e115599f64d04a9)
| **Snapshots Manuels/Automatiques**   | Création/restauration de snapshots pour la sauvegarde ou la restauration instantanée.                                               | NFSv3                  | **Entrant** : Copier les données du snapshot à l’aide d’outils tels que rsync.<br>**Sortant** : Export les données restaurées à l’aide de rsync ou d’outils similaires. | [File Storage](https://help.ovhcloud.com/csm/fr-documentation-storage-file-storage?id=kb_browse_cat&kb_id=38e74da5a884a950f07829d7d5c75217&kb_category=4da029c4d56129901e115599f64d04a9)
| **Accès multi-serveurs**          | Montage simultané sur plusieurs serveurs (Linux/Unix/VMs).                                                   | NFSv3                  | **Entrant** : Montage sur tous les serveurs OVH concernés.<br>**Sortant** : Démontage, puis remontez sur la cible si compatible NFSv3. | [File Storage](https://help.ovhcloud.com/csm/fr-documentation-storage-file-storage?id=kb_browse_cat&kb_id=38e74da5a884a950f07829d7d5c75217&kb_category=4da029c4d56129901e115599f64d04a9)

### Implémentation OVHcloud <a name=« Implémentation OVHcloud »></a>

|Fonctionnalité|Description|Formats disponibles|Modèle de migration|Documentation disponible|
|---|---|---|---|---|
| **vRack**                        | Le vRack (baie virtuelle) est une technologie de VLAN privé qui permet l’interconnexion entre les services OVHcloud. | N/A        | **Entrant** : les services Hosted Private Cloud sont inclus par défaut dans le vRack. <br> **Sortant** : Documenter l’architecture réseau et répliquez-la à l’aide de VLAN sur l’environnement cible. | [V(x)LAN creation](https://help.ovhcloud.com/csm/fr-vmware-vlan-creation?id=kb_article_view&sysparm_article=KB0045480)<br>[File Storage vRack](https://labs.ovhcloud.com/en/enterprise-file-storage-vrack/)
| **ACL and Permission Management**| Les autorisations POSIX/ACL sont gérées au niveau du système de fichiers.                                                  | IP ACL     | **Entrant** : Adaptation manuelle des permissions lors du transfert de fichiers, IP de whitelist pour l'accès, puis le client gère les droits POSIX. <br> **Sortant** : Export des fichiers, puis reconfigurez les autorisations sur la cible en fonction de sa compatibilité POSIX. |[File Storage](https://help.ovhcloud.com/csm/fr-documentation-storage-file-storage?id=kb_browse_cat&kb_id=38e74da5a884a950f07829d7d5c75217&kb_category=4da029c4d56129901e115599f64d04a9)



### Fonctionnalités spécifiques <a name=« Fonctionnalités spécifiques »></a>

|Fonctionnalité|Description|Formats disponibles|Modèle de migration|Documentation disponible|
|---|---|---|---|---|
|**Anti-DDoS**|L’anti-DDoS est un ensemble d’équipements et de moyens mis en place pour absorber les attaques par déni de service distribuées. Il comprend une analyse du trafic, l’« aspiration » vers un réseau spécialisé et la mitigation, assurée par la technologie VAC développée par OVHcloud.|NA|**Entrant** : L’Anti-DDoS est une composante de notre infrastructure, activée par défaut. Aucune action n’est requise.<br><br>**sortant** : commandez et configurez un anti-DDoS chez le nouveau fournisseur.|[Protection anti-DDoS OVHcloud](https://www.ovh.co.uk/anti-ddos/)<br><br>[Technologie anti-DDoS](https://www.ovh.co.uk/anti-ddos/anti-ddos-technology.xml)|
| **Gestion via OVHcloud Manager** | Service managé par OVHcloud avec une interface graphique propriétaire et des API pour la gestion des volumes et des snapshots. | N/A    | **Entrant** : Non applicable. <br> **Sortant** : les scripts/API doivent être réécrits pour la cible ; une gestion manuelle peut être nécessaire. | [File Storage](https://help.ovhcloud.com/csm/fr-documentation-storage-file-storage?id=kb_browse_cat&kb_id=38e74da5a884a950f07829d7d5c75217&kb_category=4da029c4d56129901e115599f64d04a9)

Liste des architectures ###

File Storage d'OVHcloud s'appuie sur NetAppÂ® ONTAPÂ® (Enterprise File Storage) ou OpenZFS (NAS-HA) en fonction de l'offre. L’architecture est active-active, avec une redondance sur deux nœuds et une réplication locale des données pour assurer une haute disponibilité. Les volumes sont accessibles via NFSv3 ou NFSv4, selon l’offre commerciale, et peuvent être montés sur plusieurs serveurs, avec la possibilité de snapshots automatiques/manuels et d’intégration au réseau privé via vRack.

### Services partenaires

Les partenaires OVHcloud sont répertoriés sous le mot-clé **« Migration vers le cloud »** dans l'annuaire des partenaires dédiés.

OVHcloud propose également un service dédié : [**OVHcloud Professional Services**](https://www.ovhcloud.com/fr/professional-services/).

### Coût et frais

Pas de sur facturation lié à la migration des données par défaut. La facturation s’arrête dès la résiliation du service. 
Le paiement se fait en début de mois, le remboursement en cas de résiliation en cours du mois n’est pas possible. Idem pour les engagements sur 12, 24 ou 36 mois.

### Rétention des données après résiliation du contrat

Les données sont supprimées à la résiliation du service et ne peuvent pas être récupérées. Pour éviter la perte de données, une exportation doit être effectuée avant la résiliation.
