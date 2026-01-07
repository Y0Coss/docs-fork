---
title: "Gérer vos sauvegardes et vos restaurations"
excerpt: "Gérer vos sauvegardes et vos restaurations"
updated: 2026-01-07
---
 
## Objectif
  
Vous avez le produit Backup Agent et vous souhaitez comprendre comment sauvegarder et restaurer vos données sur vos serveurs Baremetal.

## Prérequis

* Avoir le produit Backup Agent.
* Avoir un serveur Baremetal avec l'agent installé dessus.

## En pratique
  
### Créer une sauvegarde pour votre serveur

Cela consiste à ajouter votre serveur dans votre Backup Agent, de télécharger l'agent et l'installer sur votre serveur.

Afin d'ajouter votre serveur, vous devez :

* Aller sur le Manager, partie Backup Agent.
    * ![Backup Agent Menu](images/01-backup-agent-menu.png){.thumbnail}
* Cliquer sur votre vspc-tenant, dans la partie Services.
    * ![Backup Agent Services](images/01-backup-agent-services.png){.thumbnail}
* Aller dans la partie "Agents"
    * ![Backup Agent Tenant Infos](images/01-backup-agent-tenant-infos.png){.thumbnail}
* Cliquer sur le bouton "Ajouter une configuration".
    * ![Backup Agent Agent](images/01-backup-agent-agent.png){.thumbnail}
* Sélectionner votre serveur et le système d'exploitation.
    * ![Backup Agent Add Server 01](images/01-backup-agent-add-server-01.png){.thumbnail}
    * ![Backup Agent Add Server 02](images/01-backup-agent-add-server-02.png){.thumbnail}

### Sauvegarde

Vous avez deux possibilités de faire des sauvegardes :

* Automatique
* Manuelle

Nous allons d'abord traiter de la sauvegarde automatique.

####  Automatique

La sauvegarde automatique est intégrée dans la politique de sauvegarde que nous appliquons sur votre Backup Agent.

Cette sauvegarde fera une sauvegarde complète de votre serveur, qui sera envoyée vers votre point de stockage distant.

> [!warning]
> 
> Celle-ci va se déclencher entre 22 heures et 6 heures, sur le fuseau horaire CET pour l'Europe, et sur le fuseau horaire EST pour le Canada et l'APAC.

> [!primary]
> 
> Vous n'avez pas de possibilité de modifier ou désactiver cette sauvegarde automatique.

Vous pourrez voir le succès de cette sauvegarde via :

* Le rapport quotidien reçu.
* Le dashboard "Backup Jobs" de la Veeam Service Provider Console.
    * ![Backup Agent VSPC Backup Jobs](images/01-backup-agent-vspc-backup-jobs.png){.thumbnail}
    * ![Backup Agent VSPC Job](images/01-backup-agent-vspc-job.png){.thumbnail}

#### Manuelle

En cas de besoin, vous pouvez déclencher une sauvegarde manuelle.

Celle-ci fera également une sauvegarde complète de votre serveur, toujours envoyée vers votre point de stockage distant.

Voici la démarche à suivre :

* Ouvrir l'application "Veeam Agent" sur son serveur Baremetal :
    * ![Backup Agent BKP Agent Search](images/01-backup-agent-bkpagent-search.png){.thumbnail}
* Appuyer sur le bouton "Backup Now" pour lancer une sauvegarde :
    * ![Backup Agent BKP Agent](images/01-backup-agent-bkpagent.png){.thumbnail}

### Restauration

En cas de besoin de restaurer des données, vous avez deux possibilités :

* Via l'assistant de restauration de fichiers.
* Via l'ISO Veeam Baremetal Recovery.

#### Assistant de restauration de fichiers

Afin d'utiliser l'assistant de restauration de fichiers, voici la démarche à suivre :

* Ouvrir l'application "Veeam Agent" sur son serveur Baremetal :
    * ![Backup Agent BKP Agent Search](images/01-backup-agent-bkpagent-search.png){.thumbnail}
* Aller dans le menu et sélectionner "Restore File" :
    * ![Backup Agent Restore Menu](images/01-backup-agent-restore-menu.png){.thumbnail}
* Sélectionner le point de restauration voulu dans l'assistant :
    * ![Backup Agent Restore Points](images/01-backup-agent-restore-restore-points.png){.thumbnail}
* Et valider :
    * ![Backup Agent Restore Point Summary](images/01-backup-agent-restore-restore-points-summary.png){.thumbnail}
* Enfin, chercher votre fichier et sélectionner une option :
    * ![Backup Agent Restore Wizard](images/01-backup-agent-restore-wizard.png){.thumbnail}
    * Restore - Overwrite : Vous permet de restaurer le fichier tout en écrasant celui présent sur le serveur actuellement.
    * Restore - Keep : Vous permet de restaurer le fichier tout en gardant celui présent sur le serveur actuellement.
    * Copy To : Vous permet de copier le fichier dans un emplacement de votre serveur.
    * Explore : Vous permet d'explorer la sauvegarde.
    * Properties : Vous permet de voir les propriétés du fichier.
* Lancer une restauration vous permettra d'avoir une dernière fenêtre qui affichera le transfert :
    * ![Backup Agent Restore Transfer](images/01-backup-agent-restore-transfer.png){.thumbnail}

### ISO Veeam Baremetal Recovery

Baremetal Recovery est une fonctionnalité proposée par Veeam sous forme d'un ISO que vous devez créer en amont, et qui vous permet de démarrer dessus afin de restaurer un système sauvegardé sur un autre serveur.

Vous pouvez suivre le guide présent à cet effet : https://help.ovhcloud.com/csm/fr-veeam-agent-bare-metal-recovery?id=kb_article_view&sysparm_article=KB0067234
Vous devrez adapter le serveur et les identifiants avec ceux que nous vous aurons fourni.

## Aller plus loin
 
Échangez avec notre [communauté d'utilisateurs](/links/community).