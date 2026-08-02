---
title: "Veeam Backup Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_backup_repos.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Veeam Backup Repositories


The storage target for an InterSystems IRIS application backup policy depends on the mode configured in the policy. In backup mode, backup files are stored in a Veeam backup repository added to the Veeam Backup & Replication infrastructure. In snapshot-only mode, storage snapshots are retained on the source storage system instead. This section describes both options and the limitations that apply to backup repositories.

Snapshot-Only Mode

In snapshot-only mode, Veeam Backup & Replication does not copy data to a backup repository. Instead, it instructs the storage system to create and retain storage snapshots of the volumes that hold the InterSystems IRIS instance data. When you configure the policy, you select the storage system as the snapshot target in the Backup repository field of the wizard. The storage system appears in the list as a dedicated entry.

For Veeam Backup & Replication to create and manage storage snapshots, the storage system must be registered in Veeam Backup & Replication with the Block storage for application protection role enabled before you create the policy. For details, see [Registering Storage System for Application Protection](iris_storage_registration.md).

Supported Backup Repositories

In backup mode, you can use the following types of repositories added to the Veeam Backup & Replication infrastructure to store InterSystems IRIS backups:

* [Windows Server](ms_server.md)
* [Linux Server](linux_server.md)
* [SMB (CIFS) Share](smb_share.md)
* [NFS Share](nfs_share.md)
* [Dell Data Domain with Data Domain Boost (DDBoost)](dell_dd.md)
* [Fujitsu ETERNUS CS800](fujitsu.md)
* [Infinidat InfiniGuard](infinidat_infiniguard.md)
* [HPE StoreOnce](deduplicating_appliance_storeonce.md)

If you plan to use HPE StoreOnce as a backup repository, the total number of stored files (data and metadata) must not exceed 3,000,000 per Catalyst store. If necessary, multiple Catalyst stores may be created on the same StoreOnce system.

* [Quantum DXi](deduplicating_appliance_quantum.md)
* [ExaGrid](deduplicating_appliance_exgrid.md)

Make sure the repository is configured as described in the [ExaGrid](deduplicating_appliance_exgrid.md) section.

* [Hardened Repository](hardened_repository.md)
* [Object Storage Repository](object_storage_repository.md)
* [Scale-Out Backup Repository](backup_repository_sobr.md)

If you plan to use a scale-out backup repository, consider the following:

* Make sure that the scale-out backup repository contains repository types supported for InterSystems IRIS backups.
* Veeam Backup & Replication can store InterSystems IRIS database backup files in the performance tier and the capacity tier of a scale-out backup repository. The archive tier is not supported for InterSystems IRIS database backups.

Object Storage Repository Limitations

Before you configure your backup infrastructure to back up to object storage, consider the following limitations:

* You cannot back up data using an application backup policy to the following storage devices:

* S3 Compatible with Data Archiving
* Amazon S3 Glacier
* AWS Snowball
* Azure Archive
* Azure Data Box

* Data in object storage repositories must be managed solely by Veeam Backup & Replication. Lifecycle rules are not supported; enabling them may result in backup and restore failures.
* For backups located in object storage repositories, synthetic full backup is not supported.
* For backups located in object storage repositories, the Defragment and compact full backup file option is not supported.
* For backups located in object storage repositories, data recovery options are not available if you access the repository using credentials with read-only access permissions.
* For Microsoft Azure Blob Storage, soft delete for blobs is not supported.

For information about backing up to object storage, see [Backup to Object Storage](iris_object_storage.md).

Page updated 2026-07-28

