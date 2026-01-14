---
title: "Scale-Out Backup Repositories"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_repository_sobr.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# Scale-Out Backup Repositories

In this article

A scale-out backup repository is a repository system with horizontal scaling support for multi-tier storage of data. A scale-out backup repository consists of one or more backup repositories or object storage repositories called performance tier, and can be expanded with object storage repositories for long-term and archive storage: capacity tier and archive tier. All the storage devices and systems inside the scale-out backup repository are joined into a system, with their capacities summarized.

|  |
| --- |
| Note |
| Consider the following:   * Scale-out backup repository is included in the Veeam Universal License. When using a legacy socket-based license, Enterprise or higher edition is required. * If you configure a scale-out backup repository and then downgrade to the Standard license, you will not be able to run jobs targeted at the scale-out backup repository. However, you will be able to perform restore from the scale-out backup repository. |

This feature provides the following benefits:

* It provides a convenient way of managing the backup storage.
* A scale-out backup repository can be expanded at any moment: if the extents of your scale-out backup repository run out of space, you can add a new extent to the existing scale-out backup repository. For example, if backup data grows and the backup repository reaches the storage limit, you can add a new storage system to the scale-out backup repository. The free space on this storage system will be added to the capacity of the scale-out backup repository. As a result, you will not have to move backups to a backup repository of a larger size.
* It supports any backup target supported by Veeam: Windows or Linux servers with local or DAS storage, network shares, deduplicating storage appliances, object storage repositories. All the features of any storage device or system are preserved.
* It allows you to set up granular performance policy. For more information, see [Backup File Placement for Performance Tier](backup_repository_sobr_placement.md).
* It provides practically unlimited cloud-based storage capacity: you can instruct Veeam Backup & Replication to offload data from extents to the cloud for long-term storage. For details, see [Capacity Tier](capacity_tier.md).

A scale-out backup repository can comprise different tiers, or logical levels of storage.

* Performance tier is the level used for the fast access to the data. It consists of one or more backup repositories or object storage repositories called performance extents.

For more information, see [Performance Tier](backup_repository_sobr_extents.md).

* Capacity tier is an additional level for storing data that needs to be accessed less frequently. However, you still can restore your data directly from it. The capacity tier consists of cloud-based or on-premises object storage repositories called capacity extent.

For more information, see [Capacity Tier](capacity_tier.md).

* Archive tier is an additional level for archive storage of infrequently accessed data. Applicable data can be transported either from the performance or capacity tier. For restore from the archive tier, data must undergo preparation process.

For more information, see [Archive Tier](archive_tier.md).

You can use a scale-out backup repository with almost all types of jobs and tasks that Veeam Backup & Replication runs. For a list of unsupported scenarios, see [Limitations for Scale-Out Backup Repositories](sobr_limitations.md#jobs).

Backup files stored in the scale-out repository can be used for all types of restores, replication from backup and backup copy jobs. You can verify such backups with SureBackup jobs. The scale-out backup repository can be used as a staging backup repository for restore from tape media. Files restored from the tape media are placed to the extents according to data placement policy configured for the scale-out backup repository. For more information, see [Backup File Placement for Performance Tier](backup_repository_sobr_placement.md).

To deploy a scale-out backup repository, you must configure one or more backup repositories or object storage repositories and add them to a scale-out backup repository as extents. You can use the following types of repositories:

* [Microsoft Windows backup repositories](ms_server.md)
* [Linux backup repositories](linux_server.md)
* [SMB (CIFS) shared folders](smb_share.md)
* [NFS shared folders](nfs_share.md)
* [Deduplicating storage appliances](deduplicating_storage_appliances.md)
* [Object Storage Repositories](object_storage_repository.md)

In This Section

* [Limitations for Scale-Out Backup Repositories](sobr_limitations.md)
* [Immutability for Scale-Out Backup Repositories](immutability_sobr.md)
* [Performance Tier](backup_repository_sobr_extents.md)
* [Capacity Tier](capacity_tier.md)
* [Archive Tier](archive_tier.md)
* [Adding Scale-Out Backup Repositories](sobr_add.md)
* [Managing Scale-Out Backup Repositories](managing_sobr_data.md)

Page updated 11/10/2025

Page content applies to build 13.0.1.1071
