---
title: "Direct Backup to Object Storage Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/direct_backup_to_object_storage_limitations.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# Direct Backup to Object Storage Considerations and Limitations


This section contains the general limitations for direct backup to object storage:

* The periodic compact of a full backup option is not available. For more information, see the following sections related to specific platforms:

* VMware vSphere — [Maintenance Settings](backup_job_advanced_maintenance_vm.md#compactfullbackup).
* Microsoft Hyper-V — [Maintenance Settings](backup_job_advanced_maintenance_hv.md#compactfullbackup).

* By default, Veeam Backup & Replication uses the [forever forward incremental method](incremental_forever_backup.md) to back up directly to object storage repositories. If you want to create a new full backup, enable the [long-term retention policy (GFS)](gfs_retention_policy.md). In this case, Veeam Backup & Replication will create [synthetic full backups](synthetic_full_backup.md) and, therefore, will produce a [forward incremental backup chain](forward_incremental_backup.md).

|  |
| --- |
| Note |
| To produce an independent full backup, you can also run the active full backup manually or specify a periodic schedule for it. Note that this method will significantly increase object storage space consumption. |

* In direct object storage repositories, Veeam Backup & Replication stores backup chain in the per-machine backup with separate metadata files format. For more information, see [Backup Chain Formats](per_vm_backup_files.md).
* You cannot back up directly to Amazon S3 Glacier Storage, S3 compatible with Data Archiving and Azure Archive Storage object storage repositories. These types of object storage repositories can only be used as archive extents of the scale-out backup repository. For more information, see [Archive Tier](archive_tier.md).
* You cannot use direct backup to object storage to keep backups of applications running on Kubernetes persistent volumes created by Veeam Kasten Plug-In for Veeam Backup & Replication.
* [For VeeamZIP] You cannot move VeeamZIP backups to direct object storage repositories or when they are added as a performance tier of a scale-out backup repository.  However, you can still move VeeamZIP backups to an object storage repository used as capacity tier.

Unix-Based Veeam Agent Computers Limitations

Consider the following limitations:

* Veeam Agent for Unix supports only Amazon S3, as well as these types of S3 compatible storage: MinIO, IBM Cloud and Wasabi Cloud.
* [For Oracle Solaris 10 1/13] To enable Veeam Agent connection to S3 compatible storage repositories, you must install the necessary CA certificates. For more information on installing the certificates, see [this Veeam KB article](https://veeam.com/kb4735).
* Veeam Agent for Unix only supports backup repositories that are configured to have [direct connection](object_storage_repository.md#direct) to object storage.


