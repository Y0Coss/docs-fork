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

<table border="1" cellpadding="4" cellspacing="0">
  <thead>
    <tr><th>Component Name</th><th>Component</th></tr>
  </thead>
  <tbody>
    <tr><td rowspan="1">Chassis</td><td>Inspur NF5280M5</td></tr>
    <tr><td rowspan="2">Motherboard</td><td>YZMB-00882-104</td></tr>
    <tr><td>YZMB-00882-10E</td></tr>
    <tr><td rowspan="3">Processor</td><td>Intel Xeon Gold 6226R</td></tr>
    <tr><td>Intel Xeon Gold 6242R</td></tr>
    <tr><td>Intel Xeon Gold 6248R</td></tr>
    <tr><td rowspan="1">Memory</td><td>There is no memory limitation due to Nutanix Certification. Any equivalent from NF5280M5 BOM is usable.</td></tr>
    <tr><td rowspan="1">OS Drive</td><td>Intel D3-S4510 Sata SSD 480gb - ref. SSDSCKKB480G801</td></tr>
    <tr><td rowspan="3">Storage Drive (Only SAS SSD)</td><td>Samsung SAS SSD PM1643a 3.84TB ref MZILT3T8HBLS/007</td></tr>
    <tr><td>Samsung SAS SSD PM1643 3.84TB ref MZILT3T8HALS-00007</td></tr>
    <tr><td>WDS SS530 3.84TB ref WUSTR1538ASS201</td></tr>
    <tr><td rowspan="1">Storage Controller</td><td>Carte Jbod LSI 12gbps Pcie 8x 6xSFF-8643 9305-24I</td></tr>
    <tr><td rowspan="1">NIC</td><td>ConnectX-5 NIC card for OCP2.0 25GbE dual-port SFP28, PCIe3.0 x8</td></tr>
  </tbody>
</table>


### T4 - Scale-iX - Asrock SPC741D8QM3-NL-E

This 1U configuration supports Emerald Rapids CPUs and NVMe-only storage, designed for SCALE-iX clusters.

<table border="1" cellpadding="4" cellspacing="0">
  <thead>
    <tr><th>Component Name</th><th>Component</th></tr>
  </thead>
  <tbody>
    <tr><td rowspan="1">Chassis</td><td>1U 21" OVH</td></tr>
    <tr><td rowspan="1">Motherboard</td><td>Asrock SPC741D8QM3-NL-E</td></tr>
    <tr><td rowspan="3">Processor</td><td>CPU INTEL Emerald Rapids XEON6526Y</td></tr>
    <tr><td>CPU INTEL Emerald Rapids XEON6542Y</td></tr>
    <tr><td>CPU INTEL Emerald Rapids XEON6554S</td></tr>
    <tr><td rowspan="1">Memory</td><td>There is no memory limitation due to Nutanix Certification. Any equivalent from T4 SCALE BOM is usable.</td></tr>
    <tr><td rowspan="1">OS Drive</td><td>DD 2.5in SSD NVMe 960GB 64gbps PM9A3 512n Samsung ref MZQL2960HCJR-00A07</td></tr>
    <tr><td rowspan="1">OS Drive (alt.)</td><td>DD 2.5in SSD NVMe 960GB 64gbps 7450PRO 512n Micron ref MTFDKCC960TFR-1BC15ABYY</td></tr>
    <tr><td rowspan="3">Storage Drive (Only NVME)</td><td>DD 2.5in SSD NVMe 1.92TB 64gbps PM9A3 512n Samsung ref MZQL21T9HCJR-00A07</td></tr>
    <tr><td>DD 2.5in SSD NVMe 3.84TB 64gbps PM9A3 512n Samsung ref MZQL23T8HCLS-00A07</td></tr>
    <tr><td>DD 2.5in SSD NVMe 7.68TB 64gbps PM9A3 512n Samsung ref MZQL27T6HBLA-00A07</td></tr>
    <tr><td rowspan="3">Storage Drive (alt.)</td><td>DD 2.5in SSD NVMe 1.92TB 64gbps 7450PRO 512n Micron ref MTFDKCC1T9TFR-1BC15ABYY</td></tr>
    <tr><td>DD 2.5in SSD NVMe 3.84TB 64gbps 7450PRO 512n Micron ref MTFDKCC3T8TFR-1BC15ABYY</td></tr>
    <tr><td>DD 2.5in SSD NVMe 7.68TB 64gbps 7450PRO 512n Micron ref MTFDKCC7T6TFR-1BC15ABYY</td></tr>
    <tr><td rowspan="1">Storage Controller</td><td>X</td></tr>
    <tr><td rowspan="1">NIC</td><td>CARTE NVIDIA 2xSFP28 25GbE OCP 3.0 ref CX-6 LX CRYPTO - SECURE BOOT 900-9X625-0083-SB0</td></tr>
    <tr><td rowspan="2">NIC (alt.)</td><td>CARTE BROADCOM 2xSFP28 25GbE OCP 3.0 ref BCM957414N4140C</td></tr>
    <tr><td>CARTE BROADCOM 2xSFP28 25GbE PCIe 4.0 x8 ref P225P BCM957414A4142CC</td></tr>
    <tr><td rowspan="1">Power Supply</td><td>Alim AC 1U T4 850W FSP YH5851-1EBR2A0D</td></tr>
    <tr><td rowspan="1">TPM</td><td>TPM ASROCK SPI 2.0</td></tr>
  </tbody>
</table>

### T5 - HGR-HCI GEN2 - COMPAL FERA1

Latest T5 profile using the COMPAL FERA1 platform, targeting high-performance NVMe HCI workloads.

<table border="1" cellpadding="4" cellspacing="0">
  <thead>
    <tr><th>Component Name</th><th>Component</th></tr>
  </thead>
  <tbody>
    <tr><td rowspan="1">Chassis</td><td>COMPAL SR220-2</td></tr>
    <tr><td rowspan="1">Motherboard</td><td>CM LGA4677-X COMPAL IER70 FERA1-E MB</td></tr>
    <tr><td rowspan="3">Processor</td><td>Intel EMR Xeon 5515+</td></tr>
    <tr><td>Intel EMR Xeon 6526Y</td></tr>
    <tr><td>Intel EMR Xeon 6542Y</td></tr>
    <tr><td rowspan="1">Memory</td><td>There is no memory limitation due to Nutanix Certification. Any equivalent from NF5280M5 BOM is usable.</td></tr>
    <tr><td rowspan="1">OS Drive</td><td>DD 2.5in SSD NVMe 960GB 64gbps PM9A3 512n Samsung ref MZQL2960HCJR-00A07</td></tr>
    <tr><td rowspan="3">Storage Drive (Only NVME)</td><td>DD 2.5in SSD NVMe 1.92TB 64gbps PM9A3 512n Samsung ref MZQL21T9HCJR-00A07</td></tr>
    <tr><td>DD 2.5in SSD NVMe 3.84TB 64gbps PM9A3 512n Samsung ref MZQL23T8HCLS-00A07</td></tr>
    <tr><td>DD 2.5in SSD NVMe 7.68TB 64gbps PM9A3 512n Samsung ref MZQL27T6HBLA-00A07</td></tr>
    <tr><td rowspan="3">Storage Drive (alt.)</td><td>DD 2.5in SSD NVMe 1.92TB 64gbps 7450PRO 512n Micron ref MTFDKCC1T9TFR-1BC15ABYY</td></tr>
    <tr><td>DD 2.5in SSD NVMe 3.84TB 64gbps 7450PRO 512n Micron ref MTFDKCC3T8TFR-1BC15ABYY</td></tr>
    <tr><td>DD 2.5in SSD NVMe 7.68TB 64gbps 7450PRO 512n Micron ref MTFDKCC7T6TFR-1BC15ABYY</td></tr>
    <tr><td rowspan="1">Storage Controller</td><td>X</td></tr>
    <tr><td rowspan="1">NIC</td><td>CARTE NVIDIA 2xSFP28 25GbE OCP 3.0 ref CX-6 LX CRYPTO - SECURE BOOT 900-9X625-0083-SB0</td></tr>
  </tbody>
</table>

## Go further

Learn more about Nutanix hardware validation on the [Nutanix Elevate platform](https://elevate.nutanix.com).

If you need training or technical assistance to implement our solutions, please contact your Technical Account Manager or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for a custom analysis of your project.

Ask questions, give your feedback and interact directly with the team building our Hosted Private Cloud services on the dedicated [Discord](https://discord.gg/ovhcloud) channel.

Join our [community of users](/links/community).
