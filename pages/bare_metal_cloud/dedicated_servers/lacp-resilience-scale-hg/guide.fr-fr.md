---
title: Amélioration de la résilience réseau sur les serveurs Baremetal
excerpt: Découvrez la nouvelle architecture d’agrégation réseau visant à renforcer la résilience des interfaces publiques et privées de vos serveurs Baremetal OVHcloud.
updated: 2025-09-19
---

>[!primary]
> Ce document concerne un déploiement prévu le **31 octobre 2025**, qui changera la manière dont fonctionne l'aggrégation de liens (LACP) au sein des infrastructures OVHcloud.
> Les clients OVHcloud concernés par ces changements recevront également une communication par mail.
>

## Objectif

Ce guide présente la nouvelle architecture d’agrégation réseau mise en place sur les serveurs Baremetal OVHcloud.  
Cette évolution a pour but de renforcer la tolérance aux pannes et d’améliorer la continuité de service pour vos environnements critiques.  

## Prérequis

- Posséder un [serveur dédié](/links/bare-metal/bare-metal);
- Avoir configuré l’agrégation de liens (LACP) sur vos interfaces publiques ou privées (hors OLA).  

## En pratique

### Ce qui change

Jusqu’à présent, l’agrégation (LACP) des interfaces réseau était réalisée sur des ports appartenant à la **même carte réseau (NIC)**.  
Cette configuration assurait déjà une redondance en cas de défaillance d’un switch ToR, mais ne couvrait pas le risque de panne d’une carte réseau.  

Désormais :  
- Les agrégations logiques seront réparties sur **deux cartes réseau distinctes** (sans modification physique du câblage).  
- Les agrégations existantes ne sont pas modifiées. 

![Resilience comparison before/after](images/resilience_comparison.png){.thumbnail}

Si vous n’utilisez pas l’agrégation de liens LACP sur votre serveur, **aucune action n’est requise** et **aucun changement ne sera visible pour vos services**.  

### Comment effectuer le changement sur vos serveurs

Lors d’une reconfiguration des agrégations, la nouvelle règle sera appliquée automatiquement. 
Pour activer la nouvelle règle, vous pouvez également effectuer un passage en mode **OLA**, puis un retour en mode par défaut.
Une fois la nouvelle règle activée, il ne sera plus possible de revenir à l’ancienne configuration.  
Les serveurs livrés après la date de déploiement bénéficieront directement de cette nouvelle règle.

**Attention :** Afin que les modifications soient effectives, vous devez **reconfigurer les adresses MAC déclarées** dans votre système d’exploitation.  

**En cas de configuration incorrecte dans l’OS, la résilience pourrait ne pas être effective.**

### Bénéfices

Sous réserve d’une configuration correcte côté OS, cette évolution permet :  
- **Disponibilité renforcée** : meilleure tolérance aux pannes matérielles (cartes réseau, switches, connectique).  
- **Connectivité ininterrompue** : vos services restent accessibles même en cas de défaillance d’une carte réseau.  
- **Évolution transparente** : aucune modification requise pour les agrégations existantes, hors cas spécifiques mentionnés ci-dessus.  


## Aller plus loin

Rejoignez notre [communauté d'utilisateurs](/links/community).