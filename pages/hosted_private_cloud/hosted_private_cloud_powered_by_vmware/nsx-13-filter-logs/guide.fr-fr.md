---
title: 'Lecture et filtrage des logs NSX-T'
excerpt: 'Découvrez comment accéder aux journaux du pare-feu NSX-T et les filtrer afin de résoudre les problèmes de trafic bloqué sur votre Hosted Private Cloud.'
updated: 2025-09-08
---

## Objectif

Ce guide explique comment extraire et analyser les informations clés des journaux NSX-T pour dépanner le trafic bloqué ou surveiller l'activité du pare-feu sur votre Hosted Private Cloud.

## Prérequis

- Accès à l'interface vSphere
- Accès à l'[espace client OVHcloud](/links/manager) avec NSX-T activé, ou à votre système Syslog ou plateforme d’agrégation de logs
- Connaissances de base du pare-feu NSX-T et du trafic réseau

## Instructions

### Étape 1 : Identifier les champs de logs utiles

Lors de l'inspection des journaux, concentrez-vous sur les éléments suivants :

| Field          | Description                                                   |
|----------------|---------------------------------------------------------------|
| Timestamp      | Heure à laquelle l'événement est survenu                       |
| Action         | Indique si le trafic a été autorisé ou bloqué (ALLOW ou DROP) |
| Rule ID        | Identifiant de la règle NSX-T correspondant au trafic         |
| Source IP      | Adresse IP d'origine                                          |
| Destination IP | Adresse IP cible                                              |
| Protocol       | Protocole utilisé, tel que TCP, UDP ou ICMP                   |

> [!primary]
> Ces champs sont généralement suffisants pour identifier les problèmes de connectivité les plus courants.

*Facultatif : les ports source et de destination peuvent aider à identifier les problèmes spécifiques aux applications.*

### Étape 2 : Accéder aux logs

Les journaux NSX-T sont accessibles soit directement depuis l’espace client OVHcloud, soit via un serveur Syslog externe si la redirection est activée.

#### Option 1 : Depuis l’espace client

1. Connectez-vous à l’[espace client OVHcloud](/links/manager), puis accédez à NSX-T.
2. Dans le menu de gauche, allez dans la section `Sécurité`{.action}.
3. Sous **Pare-feu distribué**, cliquez sur l’onglet `Surveiller`{.action}.
4. Ouvrez l’onglet `Logs`{.action} pour explorer les entrées en temps réel ou télécharger les journaux historiques.

#### Option 2 : Depuis un serveur Syslog

Si NSX-T est configuré pour transférer les journaux vers l’extérieur :

1. Connectez-vous à votre plateforme Syslog ou à votre agrégateur de logs.
2. Filtrez les entrées à l’aide de champs tels que `DROP`, `ruleId`, `src`, `dst`, `proto` ou `dport`.

Exemples de lignes de journal :

```bash
ALLOW ruleId=202 src=10.0.0.15 dst=192.168.2.20 proto=UDP dport=53
DROP  ruleId=101 src=192.168.1.10 dst=10.0.0.5   proto=TCP dport=443
```

### Étape 3 : Filtrer et analyser les logs

En fonction de votre outil :

- Avec `Log Insight`{.action}, créez des filtres et des tableaux de bord.

- Avec Graylog, ELK ou Splunk, utilisez des requêtes pour cibler le trafic bloqué ou certains Rule ID.

- Depuis un export CLI, filtrez avec :

```bash
grep "DROP" nsx-logs.log | awk '{print $1, $3, $5, $7}'
```
### Avancé : Améliorer la lisibilité dans Graylog

Pour rendre les journaux de pare-feu NSX-T plus faciles à lire et plus proches de la simplicité du format NSX-V, vous pouvez configurer des extracteurs et des tableaux de bord dans Graylog :

1. **Créer un flux d’entrée dédié**

Configurez un flux Graylog pour capturer uniquement les journaux de pare-feu NSX-T (`facility=local6` et `comp="nsx-edge"`) afin de les isoler des autres messages système.

2. **Normaliser les horodatages et les hôtes**

Utilisez des extracteurs Graylog pour nettoyer le format brut des journaux syslog, en conservant uniquement l’horodatage de l’événement (par ex. : `2024-03-18T06:29:50.837Z`) et le nom d’hôte source (par ex. : `edge27-857b.rbx1a.pcc.ovh.net`).

3. **Analyser l’action du pare-feu et l’ID de règle**

Appliquez un extracteur Grok ou regex pour découper des entrées comme `INET TERM PASS 2025 OUT TCP` en champs structurés :

    - `Action = PASS / DROP`
    - `Rule ID = 2025`
    - `Direction = OUT`
    - `Protocol = TCP`

4. **Extraire les champs source et destination** 

Analysez les adresses IP et ports (par ex. : `10.216.242.234/61790 -> 10.216.240.19/3128`) en champs Graylog structurés :

    - `src_ip`, `src_port`
    - `dst_ip`, `dst_port`

5. **Supprimer les métadonnées inutiles**

Retirez les attributs verbeux tels que `[nsx@6876 comp="nsx-edge" ...]` qui n’apportent aucune valeur pour le dépannage. Cela permet d’alléger les journaux et de les rendre plus lisibles.

6. **Créer une vue/console simplifiée des journaux**

Créez un tableau de bord Graylog affichant uniquement les champs essentiels (Date, Action, Rule ID, Source, Destination, Protocol).

    Cela reproduit la clarté des journaux NSX-V et accélère le dépannage.

## Aller plus loin

- [Documentation officielle de VMware NSX-T](https://docs.vmware.com/fr/VMware-NSX-T-Data-Center/index.html)
- [How to Configure Syslog in NSX-T](https://kb.vmware.com/s/article/74656)

Si vous rencontrez des difficultés avec le réseau au sein de VCD on OVHcloud, consultez le guide « [VMware Cloud Director on OVHcloud - Network Concepts](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vcd_network_concepts) ».

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou [cliquez ici](/links/professional-services) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Posez des questions, donnez votre avis et interagissez directement avec l’équipe qui construit nos services Hosted Private Cloud sur [Discord](https://discord.gg/ovhcloud).