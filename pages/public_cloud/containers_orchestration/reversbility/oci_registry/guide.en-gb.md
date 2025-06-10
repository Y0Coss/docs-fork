# Reversibility Policy for the â€œOCIâ€ Product

## Objective

This document outlines the reversibility policy for the product line (OCI).

This policy aims to implement general reversibility principles and our compliance with the SWIPO IaaS Code of Conduct for cloud providers.



## List of Features

The features of the â€œProductâ€ are divided into three categories:

- **Core features** for which we guarantee migration capability.
- **OVHcloud implementations** that require adaptation to a new environment for migration.
- **Specific features** that cannot be guaranteed for migration as they are tied to the OVHcloud environment or involve custom developments.



## Core Features

| Feature                  | Description                                  | Formats       | Migration Model                                                                                                                                           | Documentation Available |
|--------------------------|----------------------------------------------|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|
| **OCI API and Compatibility** | Native support for the OCI (Open Container Initiative) format for artifacts, images, Helm charts, Cosign signatures, etc. | OCI, Helm, Cosign (signatures), JSON   | **Inbound**: Direct artifact push via standard tools (docker, helm, oras, cosign, etc.) or via OCI API.<br>**Outbound**: Pull/export using the same tools or API to any OCI/Harbor/Artifact Registry-compatible registry. | [OCI API and Compatibility](https://help.ovhcloud.com/csm/fr-public-cloud-private-registry-migrate-helm-charts?id=kb_article_view&sysparm_article=KB0058870)|
| **Artifact Import/Export**   | Upload and download of artifacts (push/pull) via standard Harbor/OCI CLI/API                                | OCI, Helm, JSON                        | **Inbound**: Import via `docker push`, `helm push`, `oras push`, etc.<br>**Outbound**: Export via `docker pull`, `helm pull`, `oras pull`, then push to the target. | [Artifact Import/Export](https://help.ovhcloud.com/csm/fr-public-cloud-private-registry-migrate-helm-charts?id=kb_article_view&sysparm_article=KB0058870)|
| **Cosign Signature** | Signature and verification via Cosign (Sigstore), support native in Harbor >= v2.5                                       | Cosign (OCI signature)      | **Inbound**: Import of artifacts signed with Cosign.<br>**Outbound**: Export of artifacts with signatures, reusable on any Cosign/OCI registry compatible.                  | [ Sign OCI artifacts with Cosign on OVHcloud Managed Private Registry ](https://help.ovhcloud.com/csm/fr-public-cloud-private-registry-sign-artifacts-with-cosign?id=kb_article_view&sysparm_article=KB0059137)|
| **Replication Harbor**            | Synchronisation automatique entre registres Harbor/OCI (push/pull ou bidirectionnelle)                                  | OCI, Helm, JSON             | **Inbound**: Configuration of replication from a source registry (Harbor/OCI).<br>**Outbound**: Replication to another compatible Harbor/OCI registry.                | [Configuring Replication](goharbor.io/docs/2.0.0/administration/configuring-replication/)|
## OVHcloud Implementation

| Feature         | Description                                                                                                       | Available Formats | Migration Model                                                                                                                          | Documentation Available |
|------------------|-------------------------------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|
| **RBAC and management of rights**      | Management of access rights by project, user, robot account, RBAC Harbor                                               | JSON (policies), interne Harbor | **Entrante** : Adaptation manuelle of rights during import.<br>**Sortante** : Export of artefacts, then reconfiguration of rights on the target.                                  |[Managing users and projects](https://help.ovhcloud.com/csm/fr-public-cloud-private-registry-managing-users-projects?id=kb_article_view&sysparm_article=KB0055968)|
| **Audit logs**        | Automatic logging of access and operations (logs Harbor/OVHcloud)                                                    | JSON, logs internes              | **Entrante** : Non applicable to import.<br>**Sortante** : Manual export of logs if needed, adaptation necessary according to the target.|[Access and Search Project Logs](https://goharbor.io/docs/2.3.0/working-with-projects/project-configuration/access-project-logs/)|
| **CI/CD Automation**            | Integration with CI/CD pipelines via Harbor/OCI API, robot tokens, OIDC                                                      | JSON, YAML (pipelines)           | **Entrante** : Adaptation of pipelines to point to OVHcloud.<br>**Sortante** : Reconfiguration of pipelines to the new target, potential adaptation of tokens.         | [Harbor API](https://api.harbor.gg/docs/index.html)|
| **Vulnerability scanning**       | Automatic image analysis via integrated Harbor scanner (Trivy, Clair, etc.)                                               | JSON, CSV reports               | **Entrante** : Non applicable to import.<br>**Sortante** : Export of reports possible, adaptation to be foreseen for the target according to the scan tool used.|[Clair project](https://clairproject.org/)|


## Specific Features

| Function               | Description                                                                           | Formats Available | Migration Model                                                                                   | Documentation Available |
|------------------------|---------------------------------------------------------------------------------------|--------------------|----------------------------------------------------------------------------------------------------|--------------------------|
| **OVHcloud Manager/API**          | OVHcloud-specific graphical interface and API for managing clusters and resources                                 | N/A    | **Incoming**: N/A<br>**Outgoing**: Scripts and automation must be rewritten for the target provider; manual management may be required.                            | [OVHcloud API specification ](https://eu.api.ovh.com/console/?section=%2FallDom&branch=v1)|
| **Infrastructure as Code** | Automated deployment via OVHcloud-specific Terraform modules                           | N/A                | **Inbound migration:** Scripts need to be adapted for other providers.  <br> **Outbound migration:** Configuration rewrite required for Terraform.                             | [Terraform](https://registry.terraform.io/providers/ovh/ovh/latest/docs)                      |



## List of Architectures

The OVHcloud Managed Private Registry service (based on Harbor) supports a multi-project, multi-namespace, and multi-user architecture with logical isolation. It enables automatic replication between registries (Harbor/OCI), fine-grained access control (RBAC), OIDC authentication, artifact signing and verification (Cosign), vulnerability scanning, and CI/CD integration via API or robot tokens.  
The service is highly available and can be integrated with the OVHcloud vRack private network for secure usage.



## Partner Services

OVHcloud partners are listed under the keyword **"Cloud Migration"** in the dedicated partner directory.

OVHcloud also offers a dedicated service: [**OVHcloud Professional Services**](https://www.ovhcloud.com/fr/professional-services/).



## Cost and Fees

Billing is usage-based with no commitment.  
There are **no termination fees**: deleting the service immediately stops billing.  
Any associated **OVHcloud credits are non-transferable**.

Clients are responsible for exporting their artifacts before deletion, as data removal is irreversible.


## Data Retention After Contract Termination

After service deletion or contract termination, OVHcloud **permanently deletes all artifacts, images, signatures, and metadata** stored in the registry.  
Access logs and history are also removed.  
It is therefore **critical to export all necessary data prior to deletion**, as restoration is not possible afterward.
