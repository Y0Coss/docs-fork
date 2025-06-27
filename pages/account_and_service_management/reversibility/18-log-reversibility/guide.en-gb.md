---
title: "Reversibility Policy for the Managed Log Manager product"
updated: 2025-06-27
---

**Objective**

This document describes the reversibility policy for the Managed Log Manager product covering the OVHcloud Log Data Platform offer.

This policy aims to implement the general reversibility principles and our compliance with the SWIPO IAAS Code of Conduct for cloud providers.

**List of features**

Features of the product line fall into three categories:

1. **Core features** for which we guarantee migration capacity.
1. **OVHcloud implementations** that require adaptation to a new migration environment.
1. **Specific features** that cannot be guaranteed for migration as they are related to the OVHcloud environment or involve custom developments.

**Core features**

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| Logs ingestion | Support of several logs' files format  | GELF, LTSV, RFC 5424, Beats, Cap'n Proto, etc | **Incoming**: direct send via shared entry point | [Mutualized inputs](/pages/manage_and_operate/observability/logs_data_platform/ingestion_mutualized_inputs)|
| Non-standard logs ingestion | LDP also supports non-traditional formats | All formats offered by Logstash | **Incoming**: direct send via dedicated entry point | [Dedicated input-logstash](/pages/manage_and_operate/observability/logs_data_platform/ingestion_logstash_dedicated_input) |
| Support of OpenSearch APIs | Import or Export logs through OpenSearch API  | JSON | **Incoming**: Special Index to ingest logs. <br>**Outgoing**: OpenSearch Scroll queries with pagination |[Mutualized input - OpenSearch API](/pages/manage_and_operate/observability/logs_data_platform/ingestion_opensearch_api_mutualized_input) <br> [Exposing your logs to third-party tools via the OpenSearch API](/pages/manage_and_operate/observability/logs_data_platform/integration_opensearch_api) |
| OpenSearch Dashboards | Visualization and exploration via OpenSearch Dashboards | JSON | **Incoming**/**Outgoing**: Visualizations, Dashboards and settings via both API and User Interface | [Using OpenSearch Dashboards with Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/visualization_opensearch_dashboards) |
| Cold Storage and Archives | Daily encrypted archives, long-term storage available 48h after logs reception | File containing GELF delivered as archive | **Incoming**: activation of the option and configuration of the stream. <br>**Outgoing**: download via Control Panel or OVHcloud API. | [Archiving your logs-cold storage](/pages/manage_and_operate/observability/logs_data_platform/archive_cold_storage) |

**OVHcloud Implementation**

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| Control Panel platform | User Interface in the Control Panel to create streams, dashboard, alias, index, OpenSearch dashboards or Logstash Inputs | N/A | **Incoming**: data and configurations related to the lifecycle of the service. <br> **Outgoing**: recreate configurations on another logs manager service. | [OVHcloud API](https://eu.api.ovh.com/console/?section=%2Fdbaas%2Flogs&branch=v1) |
| OpenSearch Index As a Service | Import or Export documents through OpenSearch API  | JSON | **Incoming**: specific names' conventions for indexes and aliases, index settings  and API restrictions. <br>**Outgoing**: OpenSearch Scroll queries with pagination | [OpenSearch Index as a Service](/pages/manage_and_operate/observability/logs_data_platform/opensearch_index) |
| Graylog Dashboards | Configuration of dashboards and searches saved by the client on the graylog interface | JSON | **Incoming**: use of Graylog APIs or Graylog User Interface. <br>**Outgoing**: Use of Graylog APIs. | [Greylog documentation](https://go2docs.graylog.org/4-0/home.htm) |
| Archives encryption | Systematic encryption of archives using public PGP keys provided by the client | PGP Keys | **Incoming**: PGP key registration via API or User Interface on the Control Panel. <br>**Outgoing**: Retrieving the saved keys and setting up an encryption mechanism in the target environment | [Encrypting your logs Archives](/pages/manage_and_operate/observability/logs_data_platform/archive_cold_storage_encryption) |

**Specific features**

| **Function** | **Description** | **Available formats** | **Migration model** | **Available documentation** |
| --- | --- | --- | --- | --- |
| Versioning managed by OVHcloud | Updates of OpenSearch, Graylog are under OVHcloud responsibility | N/A | **Incoming**: installation of new packages that allow the platform to be used (see RACI). <br>**Outgoing**: version management at the expense of the client. | [Accountability model](https://help.ovhcloud.com/csm/en-gb-logs-data-platform-responsibility-model?id=kb_article_view&sysparm_article=KB0050057) |
| Anti-DDoS OVHcloud | Mitigation VAC included by default | N/A | **Incoming**: automatic. <br> **Outgoing**: provide an equivalent third party solution. | [Anti-DDoS OVHcloud](https://www.ovhcloud.com/en/security/anti-ddos/) |

**List of architectures**

The components of the product are accessible from the OVHcloud interface and allow to operate streams, dashboards, dedicated inputs, indexes, aliases and OpenSearch Dashboards instances.

The product is divided into two service offers:

* A shared infrastructure: "logs-account"
* A dedicated cluster: "logs-enterprise"

**Partner services**

The OVHcloud partners concerned are listed in the [OVHcloud partners directory](/links/partner) under the "**cloud migration**" keywords.

OVHcloud also has a dedicated service: [OVHcloud Professional Services](/links/professional-services).

**Cost and fees**

Some features described in the tables above are not available free of charge, please consult the [product page](https://www.ovhcloud.com/en-gb/identity-security-operations/logs-data-platform/) to see the complete pricing

* No additional exit fees.
* Billing depends on the volume stored and the type of infrastructure mobilized (indexed/archived).
* Any assistance or turnkey export service may incur additional costs.

**Data retention after termination of the contract**

OVHcloud does not guarantee the use and availability of backups to restore customer data after termination of the service.

* Streams and OpenSearch indices are deleted immediately after service is removed.
* The cold storage archives are immediately destroyed upon termination of the service
* The customer is fully responsible for the repatriation of his data via API or [ldp-archive-mirror](https://github.com/ovh/ldp-archive-mirror) before decommissioning the service or terminating the contract.
