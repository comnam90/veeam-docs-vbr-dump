---
title: "Archive Tier"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/archive_tier.html"
last_updated: "11/21/2025"
product_version: "13.0.1.1071"
---

# Archive Tier

In this article

Archive tier is an additional tier of storage that can be attached to a scale-out backup repository. You can transfer data to the archive tier directly from the performance tier or from the capacity tier. To transfer data to the archive tier, the [archiving job session](archiving_job.md) runs periodically. Archived data in the archive tier is cheaper than in the performance and capacity tier. However, restoring data from the archive tier is longer and more expensive compared to the capacity tier. Data must be prepared for restore from the archive tier.

This feature is most useful in the following cases:

* You have a lot of rarely (no more than once a quarter) accessed data that has to be stored in an archive.
* You want to save costs and space on storing archived data.

Supported Types of Object Storage Repositories

The archive tier consists of object storage repository added as a single archive extent. You can add one of the following cloud-based object storage repositories with "cold" data storage:

* Amazon S3 Glacier.
* S3 compatible object storage with data archiving.
* Microsoft Azure Archive Storage.

Before you configure an object storage repository as the archive extent, you must add it to Veeam Backup & Replication backup infrastructure. For more information, see [Adding Amazon S3 Glacier Storage](osr_amazon_glacier_adding.md), [Adding S3 Compatible with Data Archiving](compatible_glacier_add.md) and [Adding Azure Archive Storage](osr_adding_blob_storage_archive_tier.md). You can add the archive extent to your scale-out backup repository and configure its settings on the [Add Archive Tier](new_archive_tier.md) step of the New Scale-out Backup Repository wizard.

Direct Data Transfer to Archive Tier

Veeam Backup & Replication supports direct data transfer to the archive tier in case your scale-out backup repository has the following configuration:

* The performance tier consists of direct attached storage ([Microsoft Windows Server](ms_server.md), [Linux Server](linux_server.md), [Hardened Repository](hardened_repository.md)) and the archive tier consists of all [supported types of object storage repositories](#supportedobjs).
* The performance tier consists of network attached storage ([SMB (CIFS) Share](smb_share.md), [NFS Share)](nfs_share.md) and the archive tier consists of all [supported types of object storage repositories](#supportedobjs).
* The performance tier or the capacity tier consists of object storage repositories and the archive tier consists of all [supported types of object storage repositories](#supportedobjs).

|  |
| --- |
| Important |
| Veeam Backup & Replication does not support direct data transfer from the performance or capacity tier that consists of Google Cloud object storage to the archive tier. |

Supported Types of Backup Files

The following types of backup files are supported for archive storage:

* Backup files with GFS flags.
* VeeamZIP backup files.
* Exported backup files.
* Orphaned backups with GFS flags.
* Backups created by Veeam Plug-In for Nutanix AHV.

* Backups created by Veeam Backup for Oracle Linux Virtualization Manager and Red Hat Virtualization.
* Backups exported by Kasten policies.

In This Section

* [Limitations for Archive Tier](limitations_archive_tier.md)
* [Archiving Job](archiving_job.md)
* [Archive Extent Structure](archive_extent_structure.md)
* [Immutability for Archive Tier](immutability_archive_tier.md)
* [Encryption for Archive Tier](encryption_for_archive_tier.md)
* [Managing Archive Tier](managing_archive_tier.md)
* [Restore from Archive Tier](restore_archive_tier.md)

Page updated 11/21/2025

Page content applies to build 13.0.1.1071
