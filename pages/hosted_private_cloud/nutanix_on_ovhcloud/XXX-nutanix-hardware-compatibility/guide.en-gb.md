---
title: 'Nutanix hardware compatibility - OVHcloud configurations'
excerpt: 'Detailed overview of qualified hardware components for OVHcloud Nutanix platforms, including T5, T4, and GEN2 references'
updated: 2025-06-27
---

## Objective

**This guide lists the hardware components validated for OVHcloud Nutanix infrastructure.**

Each configuration includes chassis, motherboard, CPU, storage, and network elements, grouped by platform reference.

## Requirements

- Access to OVHcloud Nutanix technical specifications
- Basic understanding of hardware compatibility layers
- Familiarity with T5, T4, and GEN2 profiles used in OVHcloud data centers

The following software versions are currently validated by OVHcloud for Nutanix environments:

| Product/Feature | Version | Comment |
|-----------------|---------|---------|
| AOS             | 7.X     | **LTS (Long-Term Support)** — Once validated by OVHcloud |
| AHV             | 10.X    | Latest available version for the AOS installed by OVHcloud |
| PrismCentral    | 2024.X  | Latest compatible version tested and validated by OVHcloud |

## Instructions

### T5 - HGR-HCI - Inspur NF5280M5

This configuration is based on the Inspur NF5280M5 chassis, widely used in OVHcloud HCI environments.

| Component Name | Component |
|----------------|-----------|
| Chassis | Inspur NF5280M5 |
| Motherboard | YZMB-00882-104 |
| Motherboard | YZMB-00882-10E |
| Processor | Intel Xeon Gold 6226R |
| Processor | Intel Xeon Gold 6242R |
| Processor | Intel Xeon Gold 6248R |
| Memory | There is no memory limitation due to Nutanix Certification. Any equivalent from NF5280M5 BOM is usable. |
| OS Drive | Intel D3-S4510 Sata SSD 480gb - ref. SSDSCKKB480G801 |
| Storage Drive (Only SAS SSD) | Samsung SAS SSD PM1643a 3.84TB ref MZILT3T8HBLS/007 |
| Storage Drive (Only SAS SSD) | Samsung SAS SSD PM1643 3.84TB ref MZILT3T8HALS-00007 |
| Storage Drive (Only SAS SSD) | WDS SS530 3.84TB ref WUSTR1538ASS201 |
| Storage Controller | Carte Jbod LSI 12gbps Pcie 8x 6xSFF-8643 9305-24I |
| NIC | ConnectX-5 NIC card for OCP2.0 25GbE dual-port SFP28, PCIe3.0 x8 |

### T4 - Scale-iX - Asrock SPC741D8QM3-NL-E

This 1U configuration supports Emerald Rapids CPUs and NVMe-only storage, designed for SCALE-iX clusters.

| Component Name | Component |
|----------------|-----------|
| Chassis | 1U 21" OVH |
| Motherboard | Asrock SPC741D8QM3-NL-E |
| Processor | CPU INTEL Emerald Rapids XEON6526Y |
| Processor | CPU INTEL Emerald Rapids XEON6542Y |
| Processor | CPU INTEL Emerald Rapids XEON6554S |
| Memory | There is no memory limitation due to Nutanix Certification. Any equivalent from T4 SCALE BOM is usable. |
| OS Drive | DD 2.5in SSD NVMe 960GB 64gbps PM9A3 512n Samsung ref MZQL2960HCJR-00A07 |
| OS Drive (alt.) | DD 2.5in SSD NVMe 960GB 64gbps 7450PRO 512n Micron ref MTFDKCC960TFR-1BC15ABYY |
| Storage Drive (Only NVME) | DD 2.5in SSD NVMe 1.92TB 64gbps PM9A3 512n Samsung ref MZQL21T9HCJR-00A07 |
| Storage Drive (Only NVME) | DD 2.5in SSD NVMe 3.84TB 64gbps PM9A3 512n Samsung ref MZQL23T8HCLS-00A07 |
| Storage Drive (Only NVME) | DD 2.5in SSD NVMe 7.68TB 64gbps PM9A3 512n Samsung ref MZQL27T6HBLA-00A07 |
| Storage Drive (alt.) | DD 2.5in SSD NVMe 1.92TB 64gbps 7450PRO 512n Micron ref MTFDKCC1T9TFR-1BC15ABYY |
| Storage Drive (alt.) | DD 2.5in SSD NVMe 3.84TB 64gbps 7450PRO 512n Micron ref MTFDKCC3T8TFR-1BC15ABYY |
| Storage Drive (alt.) | DD 2.5in SSD NVMe 7.68TB 64gbps 7450PRO 512n Micron ref MTFDKCC7T6TFR-1BC15ABYY |
| Storage Controller | X |
| NIC | CARTE NVIDIA 2xSFP28 25GbE OCP 3.0 ref CX-6 LX CRYPTO - SECURE BOOT 900-9X625-0083-SB0 |
| NIC (alt.) | CARTE BROADCOM 2xSFP28 25GbE OCP 3.0 ref BCM957414N4140C |
| NIC (alt.) | CARTE BROADCOM 2xSFP28 25GbE PCIe 4.0 x8 ref P225P BCM957414A4142CC |
| Power Supply | Alim AC 1U T4 850W FSP YH5851-1EBR2A0D |
| TPM | TPM ASROCK SPI 2.0 |

### T5 - HGR-HCI GEN2 - COMPAL FERA1

Latest T5 profile using the COMPAL FERA1 platform, targeting high-performance NVMe HCI workloads.

| Component Name | Component |
|----------------|-----------|
| Chassis | COMPAL SR220-2 |
| Motherboard | CM LGA4677-X COMPAL IER70 FERA1-E MB |
| Processor | Intel EMR Xeon 5515+ |
| Processor | Intel EMR Xeon 6526Y |
| Processor | Intel EMR Xeon 6542Y |
| Memory | There is no memory limitation due to Nutanix Certification. Any equivalent from NF5280M5 BOM is usable. |
| OS Drive | DD 2.5in SSD NVMe 960GB 64gbps PM9A3 512n Samsung ref MZQL2960HCJR-00A07 |
| Storage Drive (Only NVME) | DD 2.5in SSD NVMe 1.92TB 64gbps PM9A3 512n Samsung ref MZQL21T9HCJR-00A07 |
| Storage Drive (Only NVME) | DD 2.5in SSD NVMe 3.84TB 64gbps PM9A3 512n Samsung ref MZQL23T8HCLS-00A07 |
| Storage Drive (Only NVME) | DD 2.5in SSD NVMe 7.68TB 64gbps PM9A3 512n Samsung ref MZQL27T6HBLA-00A07 |
| Storage Drive (alt.) | DD 2.5in SSD NVMe 1.92TB 64gbps 7450PRO 512n Micron ref MTFDKCC1T9TFR-1BC15ABYY |
| Storage Drive (alt.) | DD 2.5in SSD NVMe 3.84TB 64gbps 7450PRO 512n Micron ref MTFDKCC3T8TFR-1BC15ABYY |
| Storage Drive (alt.) | DD 2.5in SSD NVMe 7.68TB 64gbps 7450PRO 512n Micron ref MTFDKCC7T6TFR-1BC15ABYY |
| Storage Controller | X |
| NIC | CARTE NVIDIA 2xSFP28 25GbE OCP 3.0 ref CX-6 LX CRYPTO - SECURE BOOT 900-9X625-0083-SB0 |

## Go further

Learn more about Nutanix hardware validation on the [Nutanix Elevate platform](https://elevate.nutanix.com).

If you need training or technical assistance to implement our solutions, please contact your Technical Account Manager or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for a custom analysis of your project.

Ask questions, give your feedback and interact directly with the team building our Hosted Private Cloud services on the dedicated [Discord](https://discord.gg/ovhcloud) channel.

Join our [community of users](/links/community).
