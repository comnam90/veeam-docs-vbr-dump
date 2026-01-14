---
title: "External Repositories"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/external_repository.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# External Repositories

In this article

An external repository is a read-only repository. You can use Veeam Backup & Replication to copy, import and restore backups created by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10), [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\* and [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1) from external repositories to the cloud or on-premises repositories. This way, you can migrate workloads between cloud, on-premises and virtual infrastructures.

Veeam Backup & Replication supports the following types of external repositories:

* Amazon S3 (with Standard storage class assigned)
* Azure Blob (Hot and Cool access tier)
* Google Cloud (with Standard storage class assigned)

Deployment

To start working with backups created by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10), [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\* and [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1), you must add a repository that contains backups of Amazon EC2 instances, Azure VMs or Google Cloud VMs to the Veeam Backup & Replication infrastructure as an external repository. For more information, see [Adding External Repositories](external_repositories_add.md).

Usage Scenarios

You can perform the following operations:

* [Copy backups to on-premises repositories](about_backup_copy.md).
* [Restore EC2 instances, Azure VMs and Google Cloud VMs to AWS](restore_amazon.md).
* [Restore Azure VMs, EC2 instances and Google Cloud VMs to Microsoft Azure](restore_azure.md).
* [Restore Google Cloud\* instances, EC2 instances and Azure VMs to Google Cloud](restore_google.md).
* [Restore guest OS files and folders](guest_file_recovery.md).
* [Export disks of EC2 instances, Azure VMs and Google Cloud\* VMs](disk_export.md).

* [Govern retention policies](external_repository_retention.md).
* [Perform Instant Recovery to VMware vSphere](instant_recovery.md).
* [Perform Instant Recovery to Microsoft Hyper-V](instant_recovery_to_hv.md).

\*This feature is available for Microsoft Windows-based backup servers.

|  |
| --- |
| Note |
| Consider the following:   * During the process of copying backups, or restore to Amazon EC2 or Microsoft Azure, data of EC2 instances and Azure VMs may migrate from one geographic location to another. In this case, Veeam Backup & Replication displays a warning and stores a record about data migration to job or task session details. For more information, see [Locations](locations.md#ext). * You cannot use an external repository as a target for backup or backup copy jobs. * If your Azure Blob repository is encrypted using an Azure Key Vault key, the gateway server associated with this repository must have a direct connection to the following resources: management.azure.com, management.core.windows.net, login.windows.net, and login.microsoftonline.com. HTTP/HTTPS proxies are not supported. |

In This Section

* [How External Repository Works](external_before_begin.md)
* [Adding External Repositories](external_repositories_add.md)
* [Managing External Repositories](managing_external_repositories.md)

Page updated 10/20/2025

Page content applies to build 13.0.1.1071
