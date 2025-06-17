---
title: 'Lecture et filtrage des logs NSX-T'
excerpt: 'Apprenez à accéder aux journaux du pare-feu NSX-T, à les comprendre et à les filtrer sur votre environnement Hosted Private Cloud'
updated: 2025-06-12
---

## Objectif

**Ce guide explique comment extraire et analyser les informations clés des logs NSX-T** pour dépanner le trafic bloqué ou surveiller l'activité du pare-feu sur votre Hosted Private Cloud.

## Prérequis

- Accès à l'interface vSphere
- Accès à [l'espace client OVHcloud](/links/manager) (NSX-T doit être activé) ou à votre système Syslog/outils d’agrégation de logs
- Connaissance de base du firewall NSX-T et du trafic réseau

## Instructions

### Étape 1 : identifier les champs de logs utiles

Lors de l'inspection des journaux, concentrez-vous sur les éléments suivants :

| Field                  | Description                                                      |
|-----------------------------------------------------------------------------------------------------|
| Timestamp              | Heure à laquelle l'événement est survenu                                     |
| Action                 | Indique si le trafic a été autorisé ou abandonné (par exemple, ALLOW / DROP)      |
| ID règle                | ID de la règle NSX-T correspondant au trafic                    |
| IP source              | Adresse IP d'origine                                                |
| IP de destination         | Adresse IP cible                                                |
| Protocol               | Protocole utilisé (TCP, UDP, ICMP, etc.)                             |
| Port source/de destination| Ports impliqués dans la connexion                                 |

> **Conseil :** Ces champs sont suffisants pour identifier les problèmes de connectivité les plus courants.

### Étape 2 : accéder aux logs

#### Option 1 : Depuis l’espace client OVHcloud

1. Connectez-vous à [l'espace client OVHcloud](/links/manager), puis accédez à NSX-T
2. Dans le menu de gauche, accédez à la section `Sécurité`{.action}
3. Sous **Pare-feu distribué**, cliquez sur l'onglet `Surveiller`{.action}
4. Ouvrez la vue `Logs`{.action} pour explorer les entrées en temps réel ou télécharger les journaux historiques

#### Option 2 : depuis un serveur Syslog

Si NSX-T est configuré pour transférer les journaux en externe :

1. Connectez-vous à votre plateforme Syslog ou d'agrégation de logs
2. Filtrer les entrées à l'aide de champs tels que « DROP », « ruleId », « src », « dst », « proto » ou « dport »

Exemple de ligne de journal :

DROP ruleId=101 src=192.168.1.10 dst=10.0.0.5 proto=TCP dport=443

### Étape 3 : Filtrer et analyser les logs

En fonction de votre chaîne d'outils :

- Utiliser `Log Insight`{.action} pour créer des filtres et des tableaux de bord
- Dans des outils comme Graylog, ELK ou Splunk, créez des requêtes pour vous concentrer sur le trafic abandonné ou sur des ID de règle spécifiques
- À partir des exportations CLI, filtrez à l'aide de :

« bash
grep « DROP » nsx-logs.log | awk '{print $2, $5, $7}'
«

## Aller plus loin

- [Documentation officielle de VMware NSX-T](https://docs.vmware.com/fr/VMware-NSX-T-Data-Center/index.html)
- [How to Configure Syslog in NSX-T](https://kb.vmware.com/s/article/74656)

Rejoignez notre [communauté d'utilisateurs](/links/community).