---
title: "Compatibilité matérielle Nutanix - Configurations OVHcloud"
excerpt: "Vue d'ensemble des composants matériels validés pour les plateformes Nutanix chez OVHcloud : références T5, T4 et GEN2"
updated: 2025-06-27
---

## Objectif

**Découvrez les composants matériels validés pour les infrastructures Nutanix chez OVHcloud.**
Chaque configuration regroupe les éléments clés : châssis, carte mère, processeur, stockage et réseau, selon le profil matériel utilisé.

## Prérequis

- Accès aux spécifications techniques Nutanix d’OVHcloud
- Connaissances de base sur les couches de compatibilité matérielle
- Connaissance des profils T5, T4 et GEN2 utilisés dans les datacentres OVHcloud

## Prérequis

- Accès aux spécifications techniques Nutanix d’OVHcloud  
- Connaissances de base sur les couches de compatibilité matérielle  
- Connaissance des profils T5, T4 et GEN2 utilisés dans les datacentres OVHcloud

Les versions logicielles suivantes sont actuellement validées par OVHcloud pour les environnements Nutanix :

| Produit/Fonctionnalité | Version | Commentaire |
|------------------------|---------|-------------|
| AOS                    | 7.X     | **LTS (Long-Term Support)** — Une fois validée par OVHcloud |
| AHV                    | 10.X    | Dernière version disponible pour l’AOS installé par OVHcloud |
| PrismCentral           | 2024.X  | Dernière version compatible testée et validée par OVHcloud |

## En pratique

### T5 - HGR-HCI - Inspur NF5280M5

Cette configuration repose sur le châssis Inspur NF5280M5, largement utilisé dans les clusters HCI d’OVHcloud.

<table border="1" cellpadding="4" cellspacing="0">
  <thead>
    <tr><th>Component Name</th><th>Component</th></tr>
  </thead>
  <tbody>
    <tr><td rowspan="1">Châssis</td><td>Inspur NF5280M5</td></tr>
    <tr><td rowspan="2">Carte mère</td><td>YZMB-00882-104</td></tr>
    <tr><td>YZMB-00882-10E</td></tr>
    <tr><td rowspan="3">Processeur</td><td>Intel Xeon Gold 6226R</td></tr>
    <tr><td>Intel Xeon Gold 6242R</td></tr>
    <tr><td>Intel Xeon Gold 6248R</td></tr>
    <tr><td rowspan="1">Mémoire</td><td>Aucun bridage lié à la certification Nutanix. Toute référence présente dans le BOM NF5280M5 est utilisable.</td></tr>
    <tr><td rowspan="1">Disque OS</td><td>Intel D3-S4510 Sata SSD 480 Go - ref. SSDSCKKB480G801</td></tr>
    <tr><td rowspan="3">Disque (SAS uniquement)</td><td>Samsung SAS SSD PM1643a 3.84 To - ref. MZILT3T8HBLS/007</td></tr>
    <tr><td>Samsung SAS SSD PM1643 3.84 To - ref. MZILT3T8HALS-00007</td></tr>
    <tr><td>WDS SS530 3.84 To - ref. WUSTR1538ASS201</td></tr>
    <tr><td rowspan="1">Contrôleur de stockage</td><td>Carte Jbod LSI 12 Gbps PCIe 8x 6xSFF-8643 9305-24I</td></tr>
    <tr><td rowspan="1">Carte réseau</td><td>ConnectX-5 OCP2.0 25GbE dual-port SFP28, PCIe 3.0 x8</td></tr>
  </tbody>
</table>


### T4 - Scale-iX - Asrock SPC741D8QM3-NL-E

Cette configuration 1U est conçue pour les clusters SCALE-iX. Elle prend en charge les processeurs Emerald Rapids et un stockage 100 % NVMe.

<table border="1" cellpadding="4" cellspacing="0">
  <thead>
    <tr><th>Component Name</th><th>Component</th></tr>
  </thead>
  <tbody>
    <tr><td rowspan="1">Châssis</td><td>1U 21" OVH</td></tr>
    <tr><td rowspan="1">Carte mère</td><td>Asrock SPC741D8QM3-NL-E</td></tr>
    <tr><td rowspan="3">Processeur</td><td>Intel Emerald Rapids Xeon 6526Y</td></tr>
    <tr><td>Intel Emerald Rapids Xeon 6542Y</td></tr>
    <tr><td>Intel Emerald Rapids Xeon 6554S</td></tr>
    <tr><td rowspan="1">Mémoire</td><td>Aucun bridage lié à la certification Nutanix. Toute référence présente dans le BOM SCALE T4 est utilisable.</td></tr>
    <tr><td rowspan="1">Disque OS</td><td>Samsung PM9A3 NVMe 960 Go - ref. MZQL2960HCJR-00A07</td></tr>
    <tr><td rowspan="1">Disque OS (alt.)</td><td>Micron 7450PRO NVMe 960 Go - ref. MTFDKCC960TFR-1BC15ABYY</td></tr>
    <tr><td rowspan="3">Disque NVMe</td><td>Samsung PM9A3 NVMe 1.92 To - ref. MZQL21T9HCJR-00A07</td></tr>
    <tr><td>Samsung PM9A3 NVMe 3.84 To - ref. MZQL23T8HCLS-00A07</td></tr>
    <tr><td>Samsung PM9A3 NVMe 7.68 To - ref. MZQL27T6HBLA-00A07</td></tr>
    <tr><td rowspan="3">Disque NVMe (alt.)</td><td>Micron 7450PRO NVMe 1.92 To - ref. MTFDKCC1T9TFR-1BC15ABYY</td></tr>
    <tr><td>Micron 7450PRO NVMe 3.84 To - ref. MTFDKCC3T8TFR-1BC15ABYY</td></tr>
    <tr><td>Micron 7450PRO NVMe 7.68 To - ref. MTFDKCC7T6TFR-1BC15ABYY</td></tr>
    <tr><td rowspan="1">Contrôleur de stockage</td><td>X</td></tr>
    <tr><td rowspan="1">Carte réseau</td><td>NVIDIA CX-6 LX CRYPTO 2xSFP28 25GbE OCP 3.0 - ref. 900-9X625-0083-SB0</td></tr>
    <tr><td rowspan="2">Carte réseau (alt.)</td><td>Broadcom 2xSFP28 25GbE OCP 3.0 - ref. BCM957414N4140C</td></tr>
    <tr><td>Broadcom PCIe 4.0 x8 - ref. BCM957414A4142CC</td></tr>
    <tr><td rowspan="1">Alimentation</td><td>FSP 850W AC 1U - ref. YH5851-1EBR2A0D</td></tr>
    <tr><td rowspan="1">TPM</td><td>TPM ASROCK SPI 2.0</td></tr>
  </tbody>
</table>

### T5 - HGR-HCI GEN2 - COMPAL FERA1

Ce profil T5 GEN2 intègre la plateforme COMPAL FERA1. Il cible les environnements HCI à hautes performances reposant sur des disques NVMe.

<table border="1" cellpadding="4" cellspacing="0">
  <thead>
    <tr><th>Component Name</th><th>Component</th></tr>
  </thead>
  <tbody>
    <tr><td rowspan="1">Châssis</td><td>COMPAL SR220-2</td></tr>
    <tr><td rowspan="1">Carte mère</td><td>COMPAL IER70 FERA1-E - CM LGA4677-X</td></tr>
    <tr><td rowspan="3">Processeur</td><td>Intel EMR Xeon 5515+</td></tr>
    <tr><td>Intel EMR Xeon 6526Y</td></tr>
    <tr><td>Intel EMR Xeon 6542Y</td></tr>
    <tr><td rowspan="1">Mémoire</td><td>Aucun bridage lié à la certification Nutanix. Toute référence présente dans le BOM NF5280M5 est utilisable.</td></tr>
    <tr><td rowspan="1">Disque OS</td><td>Samsung PM9A3 NVMe 960 Go - ref. MZQL2960HCJR-00A07</td></tr>
    <tr><td rowspan="3">Disque NVMe</td><td>Samsung PM9A3 NVMe 1.92 To - ref. MZQL21T9HCJR-00A07</td></tr>
    <tr><td>Samsung PM9A3 NVMe 3.84 To - ref. MZQL23T8HCLS-00A07</td></tr>
    <tr><td>Samsung PM9A3 NVMe 7.68 To - ref. MZQL27T6HBLA-00A07</td></tr>
    <tr><td rowspan="3">Disque NVMe (alt.)</td><td>Micron 7450PRO NVMe 1.92 To - ref. MTFDKCC1T9TFR-1BC15ABYY</td></tr>
    <tr><td>Micron 7450PRO NVMe 3.84 To - ref. MTFDKCC3T8TFR-1BC15ABYY</td></tr>
    <tr><td>Micron 7450PRO NVMe 7.68 To - ref. MTFDKCC7T6TFR-1BC15ABYY</td></tr>
    <tr><td rowspan="1">Contrôleur de stockage</td><td>X</td></tr>
    <tr><td rowspan="1">Carte réseau</td><td>NVIDIA CX-6 LX CRYPTO 2xSFP28 25GbE OCP 3.0 - ref. 900-9X625-0083-SB0</td></tr>
  </tbody>
</table>

## Aller plus loin

Retrouvez les détails des validations matérielles sur la [plateforme Nutanix Elevate](https://elevate.nutanix.com).

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en œuvre de nos solutions, contactez votre Technical Account Manager ou demandez une analyse personnalisée de votre projet à nos experts de l’équipe [Professional Services](/links/professional-services).

Posez des questions, donnez votre avis et interagissez directement avec l’équipe qui construit nos services Hosted Private Cloud sur le canal [Discord](https://discord.gg/ovhcloud) dédié.

Échangez avec notre [communauté d'utilisateurs](/links/community).