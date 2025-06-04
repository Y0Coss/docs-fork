---
title: Third-party applications compatibility
excerpt: This guide provides a list of tested, certified third-party applications compatible with OVHcloud Object Storage
updated: 2025-06-10
---
 
## Objective
  
At OVHcloud, we understand the importance of compatibility and interoperability with third-party tools and software. Our **S3<sup>*</sup>-compatible Object Storage** service is designed to be flexible and adaptable to various use cases and workflows. This guide aims to provide an overview of the compatibility of our Object Storage service with popular third-party tools and software, helping you to integrate our service seamlessly into your existing infrastructure.

## Compatibility Table

The following table provides an overview of the compatibility of our OVHcloud Object Storage service with third-party tools, software and/or applications:

### Data Protection
| Tool/Software | Compatibility | Notes | Getting Started |
| --- | --- | --- | --- |
| **Veeam** | Compatible | Veeam Ready certified, details can be found on [Veeam Alliance Technical Program page](https://www.veeam.com/partners/alliance-partner-technical-programs.html) | [Guide](/pages/storage_and_backup/object_storage/s3_veeam) |
| **IBM Storage Protect** | Compatible | Supports S3 API, provides a Python library for interacting with Object Storage | 
| **Cohesity, Veritas NetBackup**  | Compatible | Officially supported, details can be found on [NetBackup Support Page - Compatibility Matrix](https://www.veritas.com/support/en_US/dpp.NetBackup)  |
| **Artesca, Veritas BackupExec** | Compatible | TO ADD | 
| **HYCU** | Compatible | TO ADD | 

### Data Protection - Kubernetes Backup
| Tool/Software | Compatibility | Notes | Getting Started |
| --- | --- | --- | --- |
| **Veeam Kasten** | Compatible | TO ADD | [Guide](/pages/storage_and_backup/object_storage/s3_veeam) |
| **Cloud Casa** | Compatible | TO ADD | [Guide](/pages/public_cloud/containers_orchestration/managed_kubernetes/backup-and-restore-cluster-using-cloudcasa/) |

### Command-Line Interface Integrations
| Tool/Software | Compatibility | Notes | Link |
| --- | --- | --- | --- |
| **Rclone** | Compatible | Provides a command-line interface for managing objects and buckets | 
| **s3cmd** | Compatible | Supports S3 API, provides a command-line interface for managing objects and buckets |

### File management 
| Tool/Software | Compatibility | Notes | Link |
| --- | --- | --- | --- |
| **WinSCP** | Compatible | TO ADD | 
| **To ADD** | Compatible | TO ADD |

### Data Analytics 
| Tool/Software | Compatibility | Notes | Link |
| --- | --- | --- | --- |
| **Splunk** | Compatible | TO ADD | 
| **Atempo Miria** | Compatible | TO ADD |

### File Sharing 
| Tool/Software | Compatibility | Notes | Link |
| --- | --- | --- | --- |
| **ownCloud** | Compatible | Supports S3 API, can be used as a web-based interface for managing objects and buckets | 
| **Nextcloud** | Compatible | Supports S3 API, can be used as a web-based interface for managing objects and buckets |
 
## Go further
 
Join our [community of users](/links/community).

<sup>*</sup>: S3 is a trademark of Amazon Technologies, Inc. OVHcloud’s service is not sponsored by, endorsed by, or otherwise affiliated with Amazon Technologies, Inc.
