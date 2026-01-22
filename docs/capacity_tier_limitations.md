---
title: "Limitations for Capacity Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/capacity_tier_limitations.html"
last_updated: "1/21/2026"
product_version: "13.0.1.1071"
---

# Limitations for Capacity Tier


General Limitations

Consider the following limitations for the capacity tier:

* If you want to add object storage repositories of another provider as capacity extents, you must switch the object storage of the former extent [to the sealed mode](sobr_seal.md). For example, if you used Amazon S3 object storage as capacity extents and you want to add Microsoft Azure Blob as a new extent, you must first seal the Amazon S3 object storage.

* If you want to use S3-compatible repositories by different providers as capacity extents, one of these repositories must be in the sealed mode. For example, if you want to use both Wasabi Cloud object storage and IBM Cloud object storage within the same capacity tier, Wasabi Cloud object storage must be in [sealed mode](sobr_seal.md).

* You cannot add more than one instance of Azure Databox or Snowball Edge AWS object storage repository as a capacity extent.
* You cannot add the object storage repository that contains imported backups as a capacity extent. For more information, see [Importing Object Storage Backups](osr_import_backups.md).
* You cannot copy transaction log backups to the capacity tier.
* You cannot use the capacity tier as a target for file backup jobs and object storage backup jobs.
* Before you start using the capacity tier, make sure to check the pricing plans of your cloud storage provider to avoid additional costs for offloading and downloading backup data.

* Within a scale-out backup repository, the mount server of a performance extent will act as a gateway server of the capacity extent if all of the following is true:

1. You use SMB share/NFS share/deduplicating storage appliances as performance extents of your scale-out backup repository.
2. You have chosen Automatic selection for the gateway server at the [Specify Shared Folder Settings](repository_server.md) step of the New backup repository wizard.
3. For the object storage that you use as the capacity extent, you have not selected to connect to object storage using a gateway server at the Account step of the New Object Repository wizard.

* Downloading or restoring data from capacity tier does not reuse the existing blocks present on performance tier if performance tier consists of object storage repositories.

* Full restore points downloaded from capacity tier to XFS performance extents do not use Fast Clone.

* If you use immutability and have several extents in your capacity tier, you must enable it for all active extents within this tier. If you want to use a mixed immutability configuration (with some extents immutable and some mutable), you must switch either all mutable or all immutable extents to the [sealed mode](sobr_seal.md).

* You cannot use the same object storage repository as a performance extent and as a capacity extent.

* You cannot simultaneously store [capacity tier](capacity_tier.md) and [unstructured data](unstructured_data_backup.md) backups in the same object storage repository. You must either add this object storage repository as the capacity extent or use it as the backup repository for the unstructured backup job.

* If you use the [forever forward incremental backup](incremental_forever_backup.md) method to create your backups, Veeam Backup & Replication does not create inactive backup chains and will not offload data to the capacity tier. To create inactive backup chains and enable offloading to the capacity tier, you must configure the [long-term retention policy (GFS)](gfs_retention_policy.md).
* In this case, Veeam Backup & Replication will create [synthetic full backups](synthetic_full_backup.md) and, therefore, will produce a [forward incremental backup chain](forward_incremental_backup.md).
* You must enable the capacity tier encryption for Veeam Data Cloud Vault if you want to use it as a capacity extent.
* If you add [S3 compatible repositories with multiple buckets](object_storage_repository.md#childbuckets) as capacity extents, Veeam Backup & Replication will ignore this setup and store backups in the master bucket.
* The immutability period that is based on the backup job retention is not supported for the capacity tier. If you add an object storage repository with this configuration as the capacity extent, Veeam Backup & Replication will switch it to the immutability-dependent retention.

* [For backup copy jobs] If your backup copy job targets a scale-out backup repository that has a capacity tier configured with the move policy, and this capacity tier contains backups in the [deprecated format](per_vm_backup_files.md#pervmdeprecated) (backups created before Veeam Backup & Replication version 12), you need to [upgrade these backups](backup_change_type.md#separate_meta_upgrade) before you upgrade to Veeam Backup & Replication version 13.

|  |
| --- |
| Note |
| We do not recommend you to [detach](detach_backup.md) the backups; otherwise,  Veeam Backup & Replication may fail and it will require creating an active full backup. |

Limitations for Veeam Solutions

For more information on limitations for a specific Veeam solution that utilizes capacity tier functionality, see the following sections of the necessary guide:

* [Veeam Plug-In for SAP HANA](sap_repos.md#cap) — to check limitations for an SAP-certified backup and recovery solution that allows you to back up and restore SAP HANA databases.
* [Veeam Plug-In for Oracle RMAN](repos_rman.md#cap) — to check limitations for an Oracle-certified backup and recovery solution that allows you to back up and restore Oracle databases.
* [Veeam Plug-In for SAP on Oracle](sap_orcl_repos.md#cap) — to check limitations for an SAP-certified backup and recovery solution that allows you to back up and restore Oracle databases to which an SAP application is connected.
* [Veeam Plug-In for Microsoft SQL Server](repos_mssql.md#cap) — to check limitations for a backup and recovery solution that allows you to back up and restore Microsoft SQL Server databases.
* [Veeam Plug-In for IBM Db2](db2_backup_repos.md#cap) — to check limitations for a backup and recovery solution that allows you to back up and restore IBM Db2 databases.


