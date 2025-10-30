---
title: 'Déroulement d’un RMA'
excerpt: 'Découvrez les étapes de restitution d’un téléphone fourni par OVHcloud'
updated: 2025-10-30
---

<style>
details>summary {
    color:rgb(33, 153, 232) !important;
    cursor: pointer;
}
details>summary::before {
    content:'\25B6';
    padding-right:1ch;
}
details[open]>summary::before {
    content:'\25BC';
}
</style>

## Objectif

Lorsque vous changez de téléphone, vous restituez votre ancien matériel. Que notre support échange votre équipement ou que vous ayez résilié votre ligne, un RMA (pour *Return Merchandise Agreement* ou « autorisation de retour d'un équipement ») est généré. Ce RMA permet de tracer et valider l'arrivée de l'équipement dans nos locaux et de restituer la caution liée au matériel.

**Découvrez les étapes d'un RMA.**

## Prérequis

- Disposer d'un téléphone VoIP fourni sous caution par OVHcloud.
- Être connecté à l'[espace client OVHcloud](/links/manager), partie `Télécom`{.action}.

## En pratique

> [!primary]
>
> Pour plus d'informations sur l'échange de téléphones fournis par OVHcloud, consultez notre guide « [Gérer le téléphone Plug & Phone d’une ligne SIP](/pages/web_cloud/phone_and_fax/voip/commander_associer_ou_changer_un_telephone) ».

Ce guide décrit 2 exemples de RMA (échange de téléphone et résiliation) afin d'en comprendre le fonctionnement.
D'autres typologies de RMA existent, leur déroulement étant similaire (envoi d'un e-mail puis rappel et enfin clôture du RMA).

### Réception du premier e-mail et envoi du colis

Lorsque votre RMA est créé, vous recevez un premier e-mail :

/// details |  E-mail pour un échange de téléphone

> 
> Objet: [OVH-TELECOM] Bon de retour pour votre matériel : #MODEL# #IDENT# 
>
>
> Bonjour,
>
> Vous avez demandé, en date du #DATE#, un matériel de remplacement à celui correspondant au modèle #MODEL# (Réference : #REFERENCE#).
> Voici le bon de retour, au format PDF, pour le renvoi de ce matériel : #Lien vers le PDF du RMA#
> Veuillez imprimer ce bon svp, puis joindre la partie basse à votre colis, tandis que la partie haute devra être collée dessus, à l'extérieur.
> Merci de bien vérifier que votre colis contienne tous les éléments d'origine. Vous disposez de 15 jours pour nous renvoyer ce matériel. 
> Après ce délai, vous pourrez être facturé de la caution et/ou des frais de pénalités.
> Votre numéro de retour (RMA) est : #RMA# Il vous sera demandé en cas d'échange avec notre support concernant ce dossier. 
> Adresse de retour : OVH SAS 155 avenue Georges Hannart 59170 CROIX.
>

///

/// details | E-mail pour une résiliation

> 
> Objet: [OVH-TELECOM] Bon de retour pour votre matériel : #MODEL# #IDENT# 
>
> 
> Bonjour,
>
> En date du #DATE#, un bon de renvoi du matériel, fourni par OVHcloud, a été créé.
> Modèle : #MODEL# Réference/Mac : #REFERENCE#
> Cette demande de retour a pu être générée, non sur votre demande, dans les cas suivants :
>
> - Résiliation d'un abonnement
> - Suspension prolongée d'un abonnement
> - Impayé d'un abonnement*
>
> Voici le bon de retour, au format PDF, pour le renvoi de ce matériel : #Lien vers le PDF du RMA#
> Veuillez imprimer ce bon svp, puis joindre la partie basse à votre colis, tandis que la partie haute devra être collée dessus, à l'extérieur.
> Merci de bien vérifier que votre colis contienne tous les éléments d'origine.
> Vous disposez de 15 jours pour nous renvoyer ce matériel. Après ce délai, vous pourrez être facturé de la caution et/ou des frais de pénalités.
> Votre numéro de retour (RMA) est : #RMA# Il vous sera demandé en cas d'échange avec notre support concernant ce dossier.
> Adresse de retour : 155 avenue Georges Hannart 59170 CROIX.
> 
> *Cette demande de retour sera automatiquement annulée en cas de régularisation de votre situation dans les délais. 
> A défaut, votre abonnement sera définitivement supprimé et les frais éventuels restants appliqués.
>

///

Lorsque vous recevez cet e-mail, le lien du PDF est disponible dans le corps de l' e-mail. Il se présente sous cette forme :

![deroulement-rma](images/rma2020.png){.thumbnail}

> [!success]
>
> 1. Connectez-vous à votre [espace client OVHcloud](/links/manager) et cliquez sur `Télécom`{.action}.
> 1. Cliquez sur `VoIP & Fax`{.action} puis sur le groupe de facturation contenant votre ligne SIP.
> 1. Cliquez sur l'onglet `Services`{.action} puis sur la ligne SIP concernée (vous pouvez rechercher le numéro dans le champ prévu à cet effet).
> 1. Cliquez alors sur l'onglet `Assistance`{.action} puis sur `Suivi RMA`{.action}.
>
> Les informations relatives au RMA sont alors visibles, ainsi qu'un bouton pour `Télécharger le bon de retour`{.action}.
>
> **L’impression du bon de retour doit être effectuée de façon claire et lisible afin que les code-barres puissent être scannés lors de la réception.**

Une partie du bon est impérativement à joindre dans le colis et l'autre volet est à coller sur le colis pour l'affranchissement.

Le volet à joindre dans le colis contient une checklist des éléments à renvoyer. **N'oubliez aucun élément pour récupérer la totalité de la caution**.<br>
Si vous disposez de plusieurs téléphones similaires, vérifiez que l'adresse MAC (une adresse unique par téléphone) du téléphone correspond bien à celle écrite dans l'e-mail reçu ou dans la référence du bon RMA avant la mention « 3BHE » (RMAxxxx**MAC**3BHE).

Si vous devez restituer plusieurs téléphones, vous pouvez les regrouper dans un seul colis. Dans ce cas, **glissez bien l'ensemble des bons de retour dans le colis** (un bon de retour par téléphone) et collez la partie haute d'un des bons de retour sur le colis pour l'affranchissement.

> [!primary]
>
> Le colis doit être envoyé depuis un bureau de Poste.

Conservez le récépissé de dépôt du colis tant que vous n'avez pas eu confirmation de la bonne réception de celui-ci dans nos locaux.

> [!warning]
>
> Nous vous prions de bien vouloir retirer du matériel et de son emballage tout effet personnel, information ou élément qui n’aurait aucun lien avec le matériel retourné.
> 
> Dans le cas contraire, OVHcloud tentera de prendre contact avec le client par courriel pour restituer les biens n’appartenant pas à OVHcloud. A compter de l’envoi de ce courriel et sans retour de la part du client dans un délai de 30 jours calendaires, OVHcloud procédera à la destruction dudit matériel.
>

### Les rappels

Au bout de 10 et de 15 jours, si nous n'avons pas reçu votre colis avec le bon RMA, nous vous envoyons un rappel par e-mail sous cette forme :

/// details | E-mail de rappel

> 
> Objet: [OVH-TELECOM] Non réception de votre matériel : #MODEL# #IDENT#
>
>
> Bonjour,
>
> Sauf erreur de notre part, nous n'avons toujours pas reçu le matériel lié au retour ouvert en date du #DATE# :
> Modèle : #MODEL# 
> Réference : #REFERENCE#
> Voici le bon de retour, au format PDF, pour le renvoi de ce matériel : #Lien vers le PDF du RMA#
> Veuillez imprimer ce bon svp, puis joindre la partie basse à votre colis, tandis que la partie haute devra être collée dessus, à l'extérieur.
> Merci de bien vérifier que votre colis contienne tous les éléments d'origine.
> Sans restitution de votre matériel dans les 3 jours, nous devrons procéder à la fermeture de ce dossier.
> Adresse de retour : OVH SAS 155 avenue Georges Hannart 59170 CROIX.
>

///

### La clôture

#### Le matériel est reçu

Lorsque nous avons reçu votre équipement, vous recevez cet e-mail :

/// details | E-mail d'accusé de réception

> 
> Objet: [OVH-TELECOM] Réception du retour de votre matériel : #MODEL# #IDENT#
> 
> 
> Bonjour,
>
> Nous avons réceptionné le matériel lié au RMA #RMA# correspondant à la référence #MODEL#, et nous vous en remercions.
> Tout est en ordre et la totalité de votre caution vous sera restituée dans les jours qui suivent. 
> Elle sera créditée sur votre compte OVH, accessible à partir de votre espace Client Télécom > Facturation > Mon Compte OVH.
> Vous pouvez à tout moment procéder à un transfert vers votre compte bancaire depuis votre espace client.
>

///

Si une caution est restituée, elle sera disponible sous forme d'avoir sur votre compte prépayé OVHcloud et servira ainsi à régler vos prochaines factures de manière automatique.<br>
Si vous le souhaitez, vous pouvez en demander le remboursement sur votre compte bancaire via les étapes suivantes, **sous réserve d'avoir [enregistré un compte bancaire SEPA dans votre compte OVHcloud et de l'avoir défini en moyen de paiement par défaut](/pages/account_and_service_management/managing_billing_payments_and_services/manage-payment-methods) au préalable** :

1. Connectez-vous à votre [espace client OVHcloud](/links/manager) et cliquez sur `Télécom`{.action}.
1. Cliquez sur `VoIP & Fax`{.action} puis sur le groupe de facturation souhaité.
1. Cliquez sur l'onglet `Facturation`{.action} puis sur `Virement vers un compte bancaire`{.action}.
1. Dans le tableau, cliquez sur les `...`{.action} à droite de la ligne correspondant à la caution restituée, puis sur `Demander un remboursement`{.action}.
1. Cliquez sur `Valider la demande`{.action}.

Le montant du remboursement apparaîtra au crédit du compte bancaire SEPA défini dans votre espace client OVHcloud sous 48 heures.

> [!primary]
> Si le montant de l'avoir n'apparaît pas sur le solde du compte prépayé OVHcloud ou est incomplet, cela signifie que la totalité ou une partie de ce montant a été utilisée automatiquement pour le règlement de vos factures.

#### Le matériel n'est pas reçu

Passé le délai de clôture du RMA, la caution n'est pas restituable. La caution étant Hors Taxes, la TVA correspondant au matériel non restitué est facturée.

Vous recevez alors l'e-mail suivant :

/// details | E-mail de fermeture du RMA

> 
> Objet: [OVH-TELECOM] Fermeture du dossier retour : #RMA# #IDENT#
>
> Bonjour,
>
> Sauf erreur de notre part, nous n'avons pas reçu le matériel lié au retour ouvert en date du #DATE# : 
> Modèle : #MODEL# 
> Réference/Mac : #REFERENCE#
> Le bon de retour, pour le renvoi de ce matériel, était le suivant : #Lien vers le PDF du RMA#.
> Nous sommes donc dans l'obligation de fermer votre ticket.
>

///

### Erreur d'envoi d'un téléphone 

Si vous renvoyez à OVHcloud un téléphone autre que celui concerné par le RMA, il est malgré tout indispensable de nous retourner le matériel réclamé sur le bon RMA. En effet, le délai de renvoi court toujours et le matériel correspondant au RMA doit nous être restitué. 

Nous vous conseillons de contacter le support, via un [ticket d'assistance depuis le centre d'aide](https://help.ovhcloud.com/csm?id=csm_get_help), pour indiquer votre erreur d'envoi afin qu'une solution soit étudiée concernant le matériel renvoyé par erreur.

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).
