---
title: Compatibilité avec les applications tierces
excerpt: Ce guide fournit une liste d'applications tierces testées et certifiées compatibles avec OVHcloud Object Storage.
updated: 2025-06-10
---
 
## Objectif
  
Chez OVHcloud, nous comprenons l'importance de la compatibilité et de l'interopérabilité avec les outils et logiciels tiers. 
Notre service **Object Storage compatible S3<sup>*</sup>** est conçu pour être flexible et adaptable à divers cas d'utilisation et flux de travail. Ce guide vise à fournir une vue d'ensemble de la compatibilité de notre service de stockage d'objets avec des outils et logiciels tiers populaires, vous aidant ainsi à intégrer notre service de manière transparente dans votre infrastructure existante.

## Tableau de compatibilité

Le tableau suivant fournit une vue d'ensemble de la compatibilité de notre service de stockage d'objets avec les outils, logiciels et/ou applications tiers :

### Protection de donnée
| Outil/Logiciel | Compatibilité | Notes | Guide de démarrage |
| --- | --- | --- | --- |
| **Veeam** | Compatible - Certifié | Certifié Veeam Ready, les détails peuvent être trouvés sur la [page Veeam Alliance Technical Program](https://www.veeam.com/partners/alliance-partner-technical-programs.html) | [Guide](/pages/storage_and_backup/object_storage/s3_veeam) |
| **IBM Storage Protect** | Compatible - Certifié | Officiellement pris en charge, détails sur [IBM Storage Protect Support Page](https://www.ibm.com/support/pages/ibm-spectrum-protect-object-storage-support) | Coming Soon |
| **Cohesity, Veritas NetBackup**  | Compatible - Certifié | Officiellement pris en charge, détails sur [NetBackup Support Page - Compatibility Matrix](https://www.veritas.com/support/en_US/dpp.NetBackup)  | [Guide](/pages/storage_and_backup/object_storage/s3_cohesity_netbackup) | Coming Soon |
| **Artesca, Veritas BackupExec** | Compatible - Certifié | Officiellement pris en charge, détails sur [BackupExec Support Page - Hardware and Cloud Storage Compatibility List](https://www.veritas.com/support/en_US/dpp.BackupExec) | Coming Soon |
| **HYCU R-Cloud™** | Compatible - Certifié | Officiellement pris en charge, détails sur [HYCU R-Cloud User Guide](https://docs.r-cloud.hycu.com/HYCU-R-Cloud-User-Guide.pdf) | [Guide](/pages/hosted_private_cloud/nutanix_on_ovhcloud/40-hycu-backup/) |

### Protection de données - Sauvegarde Kubernetes
| Outil/Logiciel | Compatibilité | Notes | Guide de démarrage |
| --- | --- | --- | --- |
| **Veeam Kasten** | Compatible | N/A | [Guide](/pages/storage_and_backup/object_storage/s3_veeam) |
| **Cloud Casa** | Compatible | Officiellement pris en charge, détails sur la [page produit Cloud Casa](https://cloudcasa.io/partners/ovhcloud-kubernetes-backup-and-dr/) | [Guide](/pages/public_cloud/containers_orchestration/managed_kubernetes/backup-and-restore-cluster-using-cloudcasa/) |
| **Trilio** | Compatible | Officiellement pris en charge, détails sur [Trilio Support Page](https://docs.trilio.io/kubernetes/appendix/configure-ovh-object-storage-as-a-target) | [Guide](https://help.ovhcloud.com/csm/en-public-cloud-kubernetes-backup-restore-cluster-trilio?id=kb_article_view&sysparm_article=KB0049632)  
|**Velereo** | Compatible | N/A | [Guide](/pages/public_cloud/containers_orchestration/managed_kubernetes/backup-and-restore-cluster-using-cloudcasa/) 

### Intégrations d'interface de ligne de commande
| Outil/Logiciel | Compatibilité | Notes | Guide de démarrage |
| --- | --- | --- | --- |
| **Rclone** | Compatible | Fournit une interface de ligne de commande pour gérer les objets et les buckets. Plus de détails sur [Rclone](https://rclone.org/) | [Guide](/pages/storage_and_backup/object_storage/s3_rclone) | [Guide](/pages/storage_and_backup/object_storage/s3_rclone) |
| **s3cmd** | Compatible |  Fournit une interface de ligne de commande pour télécharger, récupérer et gérer les données. Plus de détails sur [s3cmd](https://s3tools.org/s3cmd) | [Guide](/pages/storage_and_backup/object_storage/s3_s3cmd) | [Guide](/pages/storage_and_backup/object_storage/s3_s3cmd) |
| **Restic** | Compatible | Fournit un outil de sauvegarde qui vous permet de sauvegarder vos machines Linux, Windows, Mac sur des référentiels de stockage. Plus de détails sur [Restic](https://restic.net/) | Coming Soon |
| **MinIO client** | Compatible | Fournit une alternative aux commandes UNIX et prend en charge les services de stockage cloud compatibles Amazon S3. Plus de détails sur [client MinIO](https://min.io/docs/minio/linux/reference/minio-mc.html?ref=docs-redirect) | Coming Soon |

### Gestion de fichiers
| Outil/Logiciel | Compatibilité | Notes | Guide de démarrage |
| --- | --- | --- | --- |
| **Cyberduck** | Compatible | Fournit un client de transfert de fichiers open-source Windows pour plusieurs protocoles. Plus de détails sur [Cyberduck](https://docs.cyberduck.io/cyberduck/) | Coming Soon |
| **WinSCP** | Compatible | Fournit un client de transfert de fichiers open-source Windows pour plusieurs protocoles. Plus de détails sur  [WinSCP](https://winscp.net/eng/index.php) | [Guide](/pages/storage_and_backup/object_storage/s3_winscp) |

### Partage de fichiers
| Outil/Logiciel | Compatibilité | Notes | Guide de démarrage |
| --- | --- | --- | --- |
| **ownCloud** | Compatible | Plate-forme de synchronisation et de partage de fichiers open-source pour la collaboration. Plus de détails sur [ownCloud](https://owncloud.com/product) | [Guide](/pages/storage_and_backup/object_storage/s3_owncloud) |
| **NextCloud Files** | Compatible | Plate-forme de synchronisation et de partage de fichiers open-source pour la collaboration. Plus de détails sur [NextCloud](https://nextcloud.com/fr/files/) | [Guide](/pages/storage_and_backup/object_storage/s3_nextcloud) |

## Aller plus loin
 
Rejoignez notre [communauté d'utilisateurs](/links/community).

<sup>*</sup>: S3 is a trademark of Amazon Technologies, Inc. OVHcloud’s service is not sponsored by, endorsed by, or otherwise affiliated with Amazon Technologies, Inc.
