---
title: "Reversibility Policy for the xxxxx product"
updated: 2025-06-27
---

**Objective**

This document describes the reversibility policy for the xxxx product covering the OVHcloud xxxx offer.

This policy aims to implement the general reversibility principles and our compliance with the SWIPO IAAS Code of Conduct for cloud providers.

**List of features**

Features of the product line fall into three categories:

1. **Core features** for which we guarantee migration capacity.
1. **OVHcloud implementations** that require adaptation to a new migration environment.
1. **Specific features** that cannot be guaranteed for migration as they are related to the OVHcloud environment or involve custom developments.

**Core features**

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| OCI container deployment and management | AI models deployment or workloads via standard Docker/OCI images, orchestrated on a native Kubernetes cluster or compatible API | OCI, Docker, YAML, JSON | **Inbound** : direct import of OCI/Docker images via API, CLI (Docker, Kubectl, Helm, etc.), or via CI/CD pipeline. <br>**Outbound** : export of OCI/Docker images, YAML/JSON manifests and configurations which can be used on any Kubernetes cluster or OCI platform. | [Build & use a custom Docker image](/pages/public_cloud/ai_machine_learning/deploy_tuto_12_build_custom_image) |
| Standard API usage | Manage workloads, services, configurations and monitoring via the Kubernetes API (kubectl, Helm, etc.) | YAML, JSON, OCI | **Inbound**: direct deployment of manifests, charts, AI models via standard API. <br>**Outbound**: export of manifests, charts and configurations via kubectl that can be used on any compatible Kubernetes cluster. | [Build & use a custom Docker image](/pages/public_cloud/ai_machine_learning/deploy_tuto_12_build_custom_image) |
| OCI/Docker Image Registry | Using public/private registries for container images and AI models | OCI, Docker | **Inbound**: pull/extract images from any compatible registry. <br>**Outbound**: push/export images to any other compatible registry. | [Portfolio of AI apps and models](/pages/public_cloud/ai_machine_learning/deploy_guide_05_app_portfolio) |
| Using API, CLI and Infrastructure as Code | Deployment, management and automation via OVHcloud API, CLI or Infrastructure as Code (Terraform) | YAML, JSON, HCL | **Inbound**: configurations, scripts and templates. <br>**Outbound**: Export scripts, templates and configurations that are reusable on other target environments   | [Features, Capabilities and Limits](/pages/public_cloud/ai_machine_learning/deploy_guide_01_capabilities) |



**OVHcloud Implementations**

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |
| --- | --- | --- | **Inbound** :  <br> **Oubound** :   | []() |


**Specific features**

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| Anti-DDoS protection| Anti-DDoS is a set of tools and mechanisms designed to absorb denial of service attacks. It includes traffic analysis, "clean-up" via a specialized network, and mitigation using VAC technology developed by OVHcloud. | N/A | **Inbound**: The anti-DDoS system is part of our infrastructure and is enabled by default. No action is required <br> **Outbound**: Order and configure an anti-DDoS solution from the new provider | [Anti-DDoS OVHcloud](https://www.ovhcloud.com/en/security/anti-ddos/) |

**List of architectures**
xxxx

The product is divided into two service offers:

* xxxx
* xxx

**Partner services**

The OVHcloud partners concerned are listed in the [OVHcloud partners directory](/links/partner) under the "**Data center expansion and Migration**" keywords.

OVHcloud also has a dedicated service: [OVHcloud Professional Services](/links/professional-services).

**Cost and fees**

**Data retention after contract termination **


