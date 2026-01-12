---
title: Local Zone Compute - Fonctionnalités, capacités et limites
excerpt: Découvrez les fonctionnalités, les capacités et les limites actuelles des instances Local Zones
updated: 2026-01-12
---

## Objectif

Les instances Local Zones sont une extension des [régions](/links/public-cloud/regions-pci) qui rapprochent les services OVHcloud de lieux spécifiques, offrant une latence réduite et des performances améliorées pour les applications.
Les instances Local Zones sont stratégiquement placées à proximité des zones à forte demande des utilisateurs. Leur objectif principal est de minimiser le temps nécessaire au transfert des données entre l'utilisateur et le cloud, afin de rendre les services plus rapides et plus réactifs et de répondre aux exigences de Data residency.

Retrouvez plus d’informations sur notre [page dédiée aux instances Local Zone](/links/public-cloud/local-zones).

**Découvrez les fonctionnalités ainsi que les capacités actuelles et à venir des instances Local Zones.**

## Fonctionnalités disponibles

| Services Public Cloud | Produit                    | Disponibilité Local Zone | Limitations |
| --------------------- | -------------------------- | ------------------------ | ----------- |
| Compute               | Instances                  | Oui | La suspension (mise en attente) n'est pas prise en charge dans les zones locales |
|                       | Metal instances            | Non | |
|                       | GPU                        | Non | |
|                       | Instance backup            | Non | |
|                       | Distant backup             | Non | |
|                       | Image Linux                | Non | |
|                       | Images Windows             | Non | |
|                       | Workflow                   | Non | |
|                       | Téléchargez votre propre image | Oui | Taille d'image limitée à 25 Go maximum |
| Network               | Load Balancer              | Non | |
|                       | Gateway                    | Non | |
|                       | Floating IP                | Non | |
|                       | Private Network with vRack | Non | Les zones locales ne sont pas compatibles avec vRack. Les réseaux privés sont limités à la même zone locale uniquement. Le protocole DHCP est pris en charge sur les réseaux privés locaux. |
| Storage               | Object Storage             | Oui | 1. Politiques utilisateur non prises en charge. Toutes les clés d'accès d'un projet peuvent accéder à tous les compartiments de toutes les zones locales. </br> 2. Seule la classe de stockage Standard est prise en charge. </br> 3. Fonctionnalités S3 non prises en charge : balises S3, conservation légale, SSE-OMK, réplication S3, journalisation des accès au serveur. |
|                       | Block Storage              | Oui | Pas de prise en charge du chiffrement. Les volumes classiques ne peuvent pas être multi-connectés. Les volumes classiques sont limités à 250 IOPS (contre 500 IOPS dans les régions 3AZ). Taille maximale de 4 To (contre 12 To). |
|                       | File Storage               | Non | |
| Container             | Managed Kubernetes Service | Non | |
|                       | Managed Rancher Service    | Non | |
|                       | Managed Private Registry   | Non | |
| DBaas                 | DBaas                      | Non | |
|                       | Analytics                  | Non | |
| AI                    | AI                         | Non | |

## Capacités et limitations

Toutes les fonctionnalités d'instance qui ne sont pas répertoriées ici seront disponibles dans les prochains mois. Notre objectif est de prendre en charge l'ensemble des fonctionnalités déjà supportées dans les régions globales.

### Serveur SMTP

Les instances en Local Zone ne peuvent pas contacter de serveurs SMTP.

## Aller plus loin

- [Object Storage - Spécifications pour Local Zones](/pages/storage_and_backup/object_storage/s3_local_zones_limitations)

N’hésitez pas à nous faire part de vos questions, retours et suggestions pour améliorer le service :

- Sur le [serveur Discord OVHcloud](https://discord.gg/ovhcloud)
