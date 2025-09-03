---
title: "Comment faire évoluer les ressources d'un VPS"
excerpt: "Découvrez comment faire évoluer votre RAM, votre vCPU ou votre stockage depuis votre espace client"
updated: 2025-09-03
---

<style> details>summary { color:rgb(33, 153, 232) !important; cursor: pointer; } details>summary::before { content:'\25B6'; padding-right:1ch; } details[open]>summary::before { content:'\25BC'; } </style>

**Découvrez comment ajouter des vCores, de la mémoire et du stockage à votre service VPS.** 

## Exigences

- Un [Serveur Privé Virtuel](/links/bare-metal/vps) dans votre compte OVHcloud
- Accès au [Panneau de contrôle OVHcloud](/links/manager)

## Instructions

Nos services VPS offrent flexibilité, fiabilité et performance pour une variété de besoins d'hébergement. Vous pouvez procéder à la mise à niveau de votre RAM, vCPU ou stockage dans le [Panneau de contrôle OVHcloud](/links/manager).

Connectez-vous au [Panneau de contrôle OVHcloud](/links/manager), accédez à la section `Cloud de serveurs dédiés`{.action} et sélectionnez votre serveur à partir de `Serveurs privés virtuels`{.action}.

> [!primary]
>
> Les options de mise à niveau disponibles dans votre panneau de contrôle dépendent de la gamme et du modèle de votre VPS. Les captures d'écran ci-dessous sont à titre d'illustration uniquement.



À partir de là, vous pouvez mettre à niveau vos vCores (`1`), votre mémoire (`2`) ou votre stockage (`3`).

### 1. Pour ajouter des **vCores**

Sous l'onglet **Accueil** dans le panneau **Votre configuration**, cliquez sur `Ajouter des vCores en mettant à niveau vers une gamme supérieure`.

Choisissez un nouveau modèle et cliquez sur `Suivant`{.action}.

![VPS_GS_upgradeVPS02*.png](/hc/article_attachments/38303873816339)

Choisissez vos options de mémoire et de stockage et cliquez sur `Suivant`{.action}.

![VPS_GS_upgradeVPS03.png](/hc/article_attachments/38303879253523)

Acceptez (`☑`{.action}) les **Conditions et termes** et cliquez sur `Suivant`{.action}.

![VPS_GS_upgradeVPS04.png](/hc/article_attachments/38303873819539)

Révisez vos modifications et cliquez sur `Commander`{.action}.

![VPS_GS_upgradeVPS05.png](/hc/article_attachments/38303873821331)

### 2. Pour mettre à niveau la **Mémoire**

Sous l'onglet **Accueil** dans le panneau **Votre configuration**, cliquez sur la quantité de mémoire que vous souhaitez. Les options disponibles dépendent de la gamme de VPS que vous avez actuellement.

Dans la fenêtre contextuelle, cliquez sur `Confirmer et payer`{.action} pour finaliser votre commande.

![VPS_GS_upgradeVPS06*.png](/hc/article_attachments/38303873822611)

### 3. Pour mettre à niveau le **Stockage**

Sous l'onglet **Accueil** dans le panneau **Votre configuration**, cliquez sur la quantité de stockage que vous souhaitez. Les options disponibles dépendent de la gamme de VPS que vous avez actuellement.

Dans la fenêtre contextuelle, cliquez sur `Confirmer et payer`{.action} pour finaliser votre commande.

![VPS_GS_upgradeVPS07*.png](/hc/article_attachments/38303873827091)

Consultez notre guide dédié pour les étapes suivantes : [Comment repartitionner un VPS après une mise à niveau de stockage](/hc/fr-fr/articles/360013988659).

## FAQ

/// details | Conserverai-je la même adresse IP ?

Oui, vous conserverez la même adresse IP après la mise à niveau de votre VPS.

///

/// details | Conserverai-je mes données sur le serveur ?

Oui, après une mise à niveau, vous conserverez vos données. Lorsque vous mettez à niveau votre disque, vous devrez peut-être étendre les partitions.

///

/// details | Que se passe-t-il pour la sauvegarde/snapshot ? Puis-je l'utiliser sur le nouveau VPS ?

Oui. Après les mises à niveau, vous aurez toujours accès à vos sauvegardes et snapshots.

///

/// details | Que se passe-t-il pour la licence logicielle sur l'ancien VPS ? Puis-je la déplacer automatiquement vers le nouveau VPS ?

Si vous avez une licence active, elle restera attachée au VPS. Le prix peut changer en fonction de l'accord de licence ou des exigences du fournisseur.    
Si des modifications sont apportées à la licence, elles seront expliquées avant la mise à niveau du VPS.

///

/// details | Le débit change-t-il ?

Dans certains cas, le débit peut changer, notamment lors du passage d'un VPS de niveau inférieur au niveau supérieur.

///

/// details | Cette mise à niveau serait-elle immédiate, ou aurais-je le temps d'utiliser les deux en même temps (configurer, transférer des données, etc.) ?

La mise à niveau sera effective immédiatement, en conservant toutes vos données. La mise à niveau allouera plus de ressources à votre VPS existant.

///


## Aller plus loin

[FAQ VPS](/pages/bare_metal_cloud/virtual_private_servers/vps-faq)

Rejoignez notre [communauté d'utilisateurs](/links/community).