title: "Reversibility Policy for the Data Unified product"
updated: 2025-07-31

**Objective**

This document describes the reversibility policy for the Managed Data Visualization product covering the OVHcloud Managed Grafana offer.

This policy aims to implement the general reversibility principles and our compliance with the SWIPO IAAS Code of Conduct for cloud providers.


## List of features

The features of the product line fall into three categories:

1. **Core features** for which we guarantee migration capacity.
1. **OVHcloud implementations** that require adaptation to a new migration environment.
1. **Specific features** that cannot be guaranteed for migration as they are related to the OVHcloud environment or involve custom developments.

### 1 - Core features

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| Data Catalog | Integration of more than 60 connectors to centralize data sources | CSV, JSON, XML, Parquet, Avro, JDBC, Kafka, REST, FTP, etc. | **Inbound**: configuration of standard connectors via web interface.<br> **Outbound**: export metadata and data via API.| [Data Catalog documentation](https://docs.dataplatform.ovh.net/#/en/product/data-catalog/index) |
| Lakehouse Manager | Unified storage based on Apache, Iceberg and Trino | Parquet, ORC, Avro, Iceberg | **Inbound**: manual configuration via a web interface   <br> **Outbound**: export via Trino, Spark, or API. | [Lakehouse Manager documentation](https://docs.dataplatform.ovh.net/#/en/product/lakehouse-manager/index) |
| Data Processing Engine | ETL/ELT pipeline orchestration with Spark and Python. | Python, PySpark | **Inbound**: manual configuration via web interface or git repository connection. <br> **Outbound**: export workflows via Git or API. | [Data processing engine documentation](https://docs.dataplatform.ovh.net/#/en/product/dpe/index) |
| Analytics Manager | Create dashboards with no-code or SQL (Trino) editor. | SQL, JSON | **Inbound**: manual configuration via the web interface. <br> **Outbound**: export requests/visualizations via API. | [Analytics Manager documentation](https://docs.dataplatform.ovh.net/#/en/product/am/index) |
| Applications Services | Web application deployment and APIs (Node.js, Python, Docker). | --- | **Inbound**: manual configuration via web interface or via git repository. <br> **Outbound**: export via Git or API | [Applications services documentation](https://docs.dataplatform.ovh.net/#/en/product/app-manager/index) |

### 2 - OVHcloud implementations

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Inbound**: <br> **Outbound** : | --- |
| Data Processing Engine | Orchestration de pipelines ETL/ELT avec Spark et Python. | Format spÃ©cifique Ã  la plateforme OVH, pas de standard | Entrante : DonnÃ©es importÃ©es depuis data catalog avec configuration manuelle ou automatique des jobsSortante : Pas dâ€™export possible | Data processing engine |
| Gestion des identitÃ©s et des accÃ¨s | Gestion des comptes et accÃ¨s utilisateurs sur la data platform | N/A | EntranteÂ : configuration via lâ€™interface WebSortanteÂ : export des comptes utilisateurs au format CSV | DATAP IAM |
| Control Center | Gestion centralisÃ©e des performances et workflows. | N/A | Entrante : N/A (Pas de donnÃ©es importÃ©es)Sortante : Non exportable actuellement (Logs et infos de monitoring de la plateforme) | Control center |

  
### 3 - Specific features

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| --- | --- | --- | **Inbound**: <br> **Outbound** : | --- |
| API OVHcloud | Automatisation via API propriÃ©taires. | JSON | Entrante : CrÃ©ation du serviceSortante : Pas dâ€™export de donnÃ©e | API OVH |
| Monitoring intÃ©grÃ© | Outils de surveillance OVHcloud intÃ©grÃ©s. | N/A | Entrante : N/A (Pas de donnÃ©es importÃ©es)Sortante : Non exportable actuellement (Logs et infos de monitoring de la plateforme) | Control center |

## List of architectures



## Partner Services

The OVHcloud partners concerned are listed in the [OVHcloud partners directory](/links/partner) under the "**Data center expansion and migration**" keywords.

OVHcloud also has a dedicated service: [OVHcloud Professional Services](/links/professional-services).

## Costs and fees

