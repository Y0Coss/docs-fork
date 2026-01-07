---
title: "Comment configurer votre première sauvegarde"
excerpt: "Comment configurer votre première sauvegarde sur votre serveur Bare Metal avec le produit Backup Agent"
updated: 2026-01-07
---
 
## Objectif
  
Vous venez de commander votre offre Backup Agent pour votre serveur Bare Metal, et vous souhaitez mettre en place vos premières sauvegardes.
  
## Prérequis

* Avoir commandé Backup Agent via la commande de votre serveur Baremetal ou via le menu "Backup Agent" dans votre Manager.
* Avoir démarré et configuré un système d'exploitation sur votre serveur Baremetal.

## En pratique

Afin de pouvoir configurer votre première sauvegarde, vous devez installer l'agent sur votre serveur Baremetal.


Le fonctionnement est le suivant :

![Backup Agent Functional Diagram](images/01-backup-agent-diagram.png){.thumbnail}

Une fois l'agent installé, celui-ci recevra la politique de sauvegarde et permettra d'opérer les sauvegardes.

Pour installer votre agent sur votre serveur Baremetal, voici la démarche à suivre :

### Windows

* Vous rendre sur votre Manager, dans la partie Backup Agent.
    * ![Backup Agent Menu](images/01-backup-agent-step15.png){.thumbnail}
* Cliquer sur votre vspc-tenant, dans la partie Services.
    * ![Backup Agent Services](images/01-backup-agent-services.png){.thumbnail}
* Aller dans la partie "Agents"
    * ![Backup Agent Tenant Infos](images/01-backup-agent-tenant-infos.png){.thumbnail}
* Cliquer sur le bouton "Télécharger" en haut du tableau de vos Agents.
    * ![Backup Agent Agents](images/01-backup-agent-agent.png){.thumbnail}
* Sélectionner votre système d'exploitation et choisissez soit de télécharger le fichier d'installation ou d'utiliser une des commandes proposées pour le récupérer.
    * ![Backup Agent Step 13](images/01-backup-agent-step13.png){.thumbnail}
* Une fois le fichier d'installation sur votre Baremetal, vous pouvez l'exécuter et suivre la procédure du logiciel :
    * ![Backup Agent Step 01](images/01-backup-agent-step01.png){.thumbnail}
    * ![Backup Agent Step 02](images/01-backup-agent-step02.png){.thumbnail}
    * ![Backup Agent Step 03](images/01-backup-agent-step03.png){.thumbnail}
    * ![Backup Agent Step 04](images/01-backup-agent-step04.png){.thumbnail}
    * ![Backup Agent Step 05](images/01-backup-agent-step05.png){.thumbnail}

Une fois installé, vous pourrez voir votre agent se connecter à notre infrastructure afin de redescendre votre politique de sauvegarde :
    * ![Backup Agent Step 06](images/01-backup-agent-step06.png){.thumbnail}
    * ![Backup Agent Step 07](images/01-backup-agent-step07.png){.thumbnail}

Enfin, une fois redescendu, vous pourrez voir votre agent de sauvegarde configuré et présent sur votre serveur Baremetal :
    * ![Backup Agent Step 08](images/01-backup-agent-step08.png){.thumbnail}
    * ![Backup Agent Step 09](images/01-backup-agent-step09.png){.thumbnail}

Par défaut vos sauvegardes sont déclenchées entre 22 heures et 6 heures du matin, mais vous pouvez lancer des sauvegardes manuellement en cliquant sur le bouton "Backup Now".

### Linux

* Vous rendre sur votre Manager, dans la partie Backup Agent.
    * ![Backup Agent Menu](images/01-backup-agent-step15.png){.thumbnail}
* Cliquer sur votre vspc-tenant, dans la partie Services.
    * ![Backup Agent Services](images/01-backup-agent-services.png){.thumbnail}
* Aller dans la partie "Agents"
    * ![Backup Agent Tenant Infos](images/01-backup-agent-tenant-infos.png){.thumbnail}
* Cliquer sur le bouton "Télécharger" en haut du tableau de vos Agents.
    * ![Backup Agent Agents](images/01-backup-agent-agent.png){.thumbnail}
* Sélectionner votre système d'exploitation et choisissez soit de télécharger le fichier d'installation ou d'utiliser une des commandes proposées pour le récupérer.
    * ![Backup Agent Step 14](images/01-backup-agent-step14.png){.thumbnail}
* Une fois le fichier d'installation sur votre Baremetal, en vous étant dans le dossier le contenant vous pouvez l'exécuter de la manière suivante :

```bash
sudo ./LinuxAgentPackages.<NOMDEVOTRECOMPANY>.sh
```

Une fois l'installation complétée, vous pourrez vérifier son installation avec cette commande :

```bash
sudo veeamconsoleconfig -s

Management agent
    Connection state       : Connected
    Cloud gateway          : <OVHDOMAIN>:6180
    Connection account     : <UTILISATEUR>
Backup agent
    Status                 : Not installed
```

# Aller plus loin
 
Échangez avec notre [communauté d'utilisateurs](/links/community).