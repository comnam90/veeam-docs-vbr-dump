---
title: "Performance Tier"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_repository_sobr_extents.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Performance Tier

In this article

Performance tier of a scale-out backup repository is the level used for fast access to the data.

The performance tier of a scale-out backup repository can comprise one or more performance extents. A performance extent is a backup repository or an object storage repository added to the scale-out backup repository. The list of the performance extents is displayed at the [Add Performance Extents](sobr_add_extents.md) step of the New Scale-out Backup Repository wizard. You can use the performance tier with almost all types of jobs and tasks that Veeam Backup & Replication runs. For a list of unsupported scenarios, see [Limitations for Performance Tier](performance_tier_limitations.md).

After you add a backup repository or an object storage repository to the scale-out backup repository, they no longer exist as individual backup repositories.

When a backup repository or an object storage repository is added as a performance extent, some of its original settings are kept, and some are not. The following settings are kept, or inherited:

* Number of tasks that can be performed simultaneously.
* Read and write data rate limit.
* Data decompression settings.
* Block alignment settings.
* Connection mode (using gateway server or direct).
* Object storage consumption (for object storage repositories).

The following settings are not inherited:

* Rotated drive settings. Rotated drive settings are ignored and cannot be configured at the level of the scale-out backup repository.
* Per-machine backup file settings. Per-machine settings can be configured at the level of the scale-out backup repository.

Supported Types of Repositories

You can use the following types of repositories as performance extents:

* [Microsoft Windows backup repositories](ms_server.md)
* [Linux backup repositories](linux_server.md)
* [SMB (CIFS) shared folders](smb_share.md)
* [NFS shared folders](nfs_share.md)
* [Deduplicating storage appliances](deduplicating_storage_appliances.md)
* [Object Storage Repositories](object_storage_repository.md)

In This Section

* [Limitations for Performance Tier](performance_tier_limitations.md)
* [Extent Structure of Performance Tier with Object Storage Repositories](performance_tier_structure.md)
* [Backup File Placement for Performance Tier](backup_repository_sobr_placement.md)
* [Immutability for Performance Tier](immutability_performance_tier.md)
* [Transferring Backups to Performance Tier](data_transfer_to_performance_tier.md)
* [Removing Performance Extents from Scale-Out Repositories](sobr_remove_extent.md)

Page updated 9/2/2025

Page content applies to build 13.0.1.1071
