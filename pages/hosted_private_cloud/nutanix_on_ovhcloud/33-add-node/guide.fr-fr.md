---
title: "Ajouter ou retirer un nœud dans un cluster Nutanix (Scale In/Out)"
excerpt: "Ajustez dynamiquement votre cluster Nutanix hébergé sur OVHcloud en ajoutant ou retirant des nœuds via le Control Panel."
hidden: true
updated: 2025-05-22
---

<style>
 pre {
     font-size: 14px !important;
 }
 pre.bgwhite {
   background-color: #fff !important;
   color: #000 !important;
   font-family: monospace !important;
   padding: 5px !important;
   margin-bottom: 5px !important;
 }
 pre.bgwhite code {
   background-color: #fff !important;
   border: solid 0px transparent !important;
   font-family: monospace !important;
   font-size: 0.90em !important;
   color: #000 !important;
 }
 .small {
     font-size: 0.90em !important;
 }
</style>

## Objectif

Les clusters Nutanix sur OVHcloud sont évolutifs. Vous pouvez désormais **ajouter (scale out)** ou **retirer (scale in)** des nœuds directement depuis le Control Panel OVHcloud.

> [!warning]
> OVHcloud vous met à disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous appartient donc de ce fait d’en assurer le bon fonctionnement.
>
> Ce guide a pour but de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à l'équipe [Professional Services OVHcloud](https://www.ovhcloud.com/fr/professional-services/) ou à un [prestataire spécialisé](https://partner.ovhcloud.com/fr/directory/) si vous éprouvez des difficultés ou des doutes concernant l’administration, l’utilisation ou la mise en place d’un service sur un serveur.

## Prérequis

- Un cluster Nutanix hébergé dans votre compte OVHcloud
- Un accès au [Control Panel OVHcloud](/links/manager)
- Un accès à l’interface Prism Central
- Un accès à l’[API OVHcloud](https://api.ovh.com/)

## Informations techniques

- Votre cluster doit comporter entre **3 et 15 nœuds**
- Tous les nouveaux nœuds doivent utiliser la **même version d’AOS** que le cluster existant

## En pratique

### Scale Out (ajouter un nœud)

#### Ajouter un nœud

1. Depuis le [Control Panel OVHcloud](/links/manager), accédez à votre cluster Nutanix via les menus `Hosted Private Cloud`{.action} et `Nutanix`{.action}.

![Vue d'ensemble du cluster](images/adding-nodes-01.png){.thumbnail}

2. Dans l’onglet **General information**, la section **Number of nodes** est visible. Cliquez sur `Manage my nodes`{.action}.

![Nombre de nœuds](images/manage-nodes.png){.thumbnail}

3. Dans l’onglet **Nodes**, sélectionnez `Add nodes`{.action}.

![Ajouter des nœuds](images/adding-nodes-03.png){.thumbnail}

5. Vérifiez la configuration et le tarif dans la fenêtre contextuelle, puis cliquez sur `Order`{.action} pour lancer l’ajout.

![Fenêtre commande](images/adding-nodes-04.png){.thumbnail}

Une fois le nœud livré, son statut s’affiche dans l’onglet **General information**.

La zone **Number of nodes** indiquera qu’un nouveau nœud est prêt à être installé.

![Nouveau nœud à installer](images/adding-nodes-05.png){.thumbnail}

#### Installer un système d’exploitation (OS)

> [!tabs]
> OVHcloud Control Panel
>> 1. Si vous cliquez à nouveau sur `Manage my nodes`{.action}, vous verrez la liste des nœuds. Pour tout nœud avec le statut **OS not installed**, cliquez sur le bouton *more options* `...`{.action} et sélectionnez `Install`{.action}.
>>
>> ![Statut du nœud](images/install-os-01.png){.thumbnail}
>>
>> 2. Saisissez les paramètres de configuration du nœud. Veillez à installer la même version d'AOS que votre cluster.
>>
>> Cliquez sur `Install`{.action}.
>>
>> ![Formulaire installation](images/install-os-02.png){.thumbnail}
>>
>> 3. Une bannière de confirmation apparaîtra.
>>
>> ![Confirmation](images/install-os-03.png){.thumbnail}
>
> OVHcloud API
>> Pour installer le nœud via l’[API OVHcloud](https://api.ovh.com/){.external}, utilisez l’appel suivant :
>>
>> > [!api]
>> > @api {v1} PUT /nutanix/{serviceName}/nodes/{server}/deploy

Une fois le nœud installé, vous pouvez vous connecter à Prism Central ou Prism Element pour l’intégrer au cluster.

Consultez la documentation suivante :

- [Étendre un cluster via Prism Central](https://portal.nutanix.com/page/documents/details?targetId=Prism-Central-Guide-vpc_2024_3_1:mul-node-add-pc-t.html)

- [Étendre un cluster](https://portal.nutanix.com/page/documents/details?targetId=Web-Console-Guide-Prism-v7_0:wc-cluster-expand-wc-t.html)

### Scale In (retirer un nœud)

#### Éteindre (power down) un nœud

1. Depuis le [Control Panel OVHcloud](/links/manager), accédez à votre cluster Nutanix via les menus `Hosted Private Cloud`{.action} et `Nutanix`{.action}.

![Vue d'ensemble du cluster](images/control-panel.png){.thumbnail}

2. Dans l’onglet **General information**, vous pouvez voir le nombre de nœuds. Cliquez sur `Manage my nodes`{.action}.

![Manage my nodes](images/manage-nodes.png){.thumbnail}

3. Deux options s’offrent à vous :

> [!tabs]
> OVHcloud Control Panel
>> Pour le nœud à retirer, cliquez sur le bouton *more options* `...`{.action} puis sélectionnez `Power down`{.action}.
>> ![Éteindre un nœud](images/powerdown-nodes-01.png){.thumbnail}
>>
>> Une fenêtre d’avertissement s’ouvrira. Saisissez le terme demandé et cliquez sur `Power down`{.action}.
>>
>> > [!info]
>> > **NOTE :** L’arrêt d’un nœud Nutanix peut avoir un impact sur votre cluster. Consultez les [prérequis sur le portail Nutanix](https://portal.nutanix.com/page/documents/list?type=software) avant de poursuivre.
>>
>> ![Alerte arrêt](images/powerdown-nodes-02.png){.thumbnail}
>>
>> Une bannière de confirmation apparaîtra.
>> ![Confirmation arrêt](images/powerdown-nodes-03.png){.thumbnail}
>>
> OVHcloud API
>> Vous pouvez également arrêter un nœud via l’[API OVHcloud](https://api.ovh.com/){.external}.
>> Récupérer le Boot ID :
>> Saisissez *power* comme valeur pour **bootType**.
>>
>> > [!api]
>> > @api {v1} GET /dedicated/server/{serviceName}/boot
>>
>> Définir le Boot ID :
>> > [!api]
>> > @api {v1} PUT /dedicated/server/{serviceName}
>>
>> Éteindre le nœud :
>> > [!api]
>> > @api {v1} POST /dedicated/server/{serviceName}/reboot

#### Désinstaller le nœud

> [!tabs]
> OVHcloud Control Panel
>> Une fois le nœud éteint, cliquez sur le bouton *more options* `...`{.action} puis sélectionnez `Uninstall`{.action}.
>> ![Bouton désinstaller](images/remove-nodes-01.png){.thumbnail}
>>
>> Une fenêtre d’avertissement apparaîtra. Saisissez le terme requis et cliquez sur `Uninstall`{.action}.
>>
>> > [!info]
>> > **NOTE :** La désinstallation d’un nœud Nutanix peut avoir un impact sur votre cluster. Consultez les [prérequis sur le portail Nutanix](https://portal.nutanix.com/page/documents/list?type=software) avant de poursuivre.
>>
>> ![Alerte désinstallation](images/remove-nodes-02.png){.thumbnail}
>>
>> Une bannière de confirmation apparaîtra.

>> ![Confirmation désinstallation](images/remove-nodes-03.png){.thumbnail}
>>
> OVHcloud API
>> Pour désinstaller un nœud via l’[API OVHcloud](https://api.ovh.com/){.external}, utilisez l’appel suivant :
>> > [!api]
>> > @api {v1} POST /nutanix/{serviceName}/node/{server}/terminate

#### Supprimer le nœud

Une fois le nœud désinstallé, cliquez sur le bouton *more options* `...`{.action} puis sélectionnez `Terminate`{.action}.

![Supprimer le nœud](images/remove-nodes-04.png){.thumbnail}

Une fenêtre d’avertissement apparaîtra. Saisissez le terme requis puis cliquez sur `Confirm`{.action}.

> [!info]
> **NOTE :** Le service suspendu restera visible dans la liste des nœuds pendant environ une semaine avant suppression définitive. Vous pouvez l’annuler pendant ce délai.

## Aller plus loin

Pour aller plus loin, vous pouvez consulter :

[Nutanix Hyperconvergence](/pages/hosted_private_cloud/nutanix_on_ovhcloud/03-nutanix-hci)

[Guide d’ajout de nœud Nutanix](https://portal.nutanix.com/page/documents/details?targetId=Web-Console-Guide-Prism-v7_0:wc-cluster-expand-wc-t.html)

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en œuvre de nos solutions, contactez votre Technical Account Manager ou demandez une analyse personnalisée de votre projet à nos experts de l’équipe [Professional Services](/links/professional-services).

Posez des questions, donnez votre avis et interagissez directement avec l’équipe qui construit nos services Hosted Private Cloud sur le canal [Discord](https://discord.gg/ovhcloud) dédié.

Échangez avec notre [communauté d'utilisateurs](/links/community).