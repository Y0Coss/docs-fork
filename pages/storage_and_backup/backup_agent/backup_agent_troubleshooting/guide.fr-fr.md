---
title: "Guide de résolution de problèmes"
excerpt: "Guide de résolution de problèmes sur le produit Backup Agent"
updated: 2026-01-07
---
 
## Objectif

Vous trouvez ici une liste de potentielles problématiques que vous pouvez rencontrer sur le produit Backup Agent.

## Liste des possibles problématiques

* Mon agent n'arrive pas à se connecter à votre serveur.
    * Vous devez vous assurer d'avoir votre pare-feu qui autorise de communiquer avec notre serveur vspc-cgw1.prod01.eu-west-rbx.backup.ovhcloud.com (137.74.125.230) en Europe avec le port TCP et UDP 6180.
    * Vous devez vous assurer que vous n'avez pas de service qui pourrait avoir un conflit de port avec votre serveur.
    * Vous pouvez trouver les logs de votre agent dans le dossier: C:\ProgramData\Veeam\ ou /var/logs.
* Votre serveur n'arrive pas à installer l'agent de sauvegarde sur mon serveur.
    * L'agent supporte les distributions Windows et les kernels natifs Linux. Si vous avez apporté des modifications à votre kernel, vous devez vous assurer d'avoir les bons packages pour permettre l'installation de l'agent. Vous trouverez la liste des paramètres nécessaires ici : https://helpcenter.veeam.com/docs/agentforlinux/userguide/system_requirements.html?ver=13
* Mon agent n'arrive pas à sauvegarder, j'ai l'erreur : "Failed to perform backup. Neither blksnap nor veeamsnap module was found."
    * L'agent supporte les distributions Windows et les kernels natifs Linux. Si vous avez apporté des modifications à votre kernel, vous devez vous assurer d'avoir les bons packages pour permettre l'installation de l'agent. Vous trouverez la liste des paramètres nécessaires ici : https://helpcenter.veeam.com/docs/agentforlinux/userguide/system_requirements.html?ver=13
    * Il vous faut les headers kernel Linux dans un premier temps, et vous pouvez ensuite tenter d'installer ou reconfigurer votre package veeamsnap ou veeamblksnap ou blksnap, dépendant de votre système d'exploitation.
* Mon agent n'arrive pas à sauvegarder, j'ai l'erreur : "POSIX: Failed to create or open file [/.veeamsnapstorage/veeamsnapstore"
    * Pour sauvegarder, Veeam effectue des snapshots en plus de conserver les données qui seront écrites dans la sauvegarde, ce snapshot s'appelle le "veeamsnapstorage".
    * Afin de régler le souci, vous augmentez la taille du snapshot via le fichier /etc/veeam/veeam.ini :
> [!primary]
> 
> [blksnap]
>
> #The minimum allowable size of the difference storage in sectors
> diffStorageMinimum = 2097152
* Remplacer la valeur en bytes par le nombre de GB voulu (GB divisé par 512, pour 3GB il faut mettre 3221225472 / 512 = 6 291 456)
    * Et enfin redémarrer le service veeamservice.
* Je n'arrive pas à lancer une sauvegarde manuelle.
    * Contactez le support OVHcloud pour investiguer en nous fournissant des logs et des captures d'écrans.
* Mon utilisation du stockage ne s'est pas actualisé suite à la suppression d'un agent.
    * Nous gardons vos données durant 14 jours à la suite d'une suppression d'un agent, l'utilisation du stockage se mettra à jour suite aux 14 jours et la suppression des données.
* J'ai désinstallé mon Veeam Agent, comment le réinstaller ?
    * Contactez le support OVHcloud pour vous aider à réinstaller votre agent.
* J'ai réinstallé mon serveur, comment réinstaller Backup Agent ?
    * Vous devez supprimer votre agent dans la partie Agents de votre vspc-tenant, et ensuite télécharger et installer l'agent sur votre nouveau système d'exploitation.