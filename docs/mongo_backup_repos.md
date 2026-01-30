---
title: "Veeam Backup Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_backup_repos.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Veeam Backup Repositories


You can store MongoDB backup files in repositories added to the Veeam Backup & Replication infrastructure. In this section, you can find the list of supported backup repositories and limitations for MongoDB backups.

Supported Backup Repositories

You can use the following types of repositories added to the Veeam Backup & Replication infrastructure to store MongoDB backups:

* [Windows Server](ms_server.md)
* [Linux Server](linux_server.md)
* [SMB (CIFS) Share](smb_share.md)

* [NFS Share](nfs_share.md)

* [Dell Data Domain with Data Domain Boost (DDBoost)](dell_dd.md)

* [Fujitsu ETERNUS CS800](fujitsu.md)
* [Infinidat InfiniGuard](infinidat_infiniguard.md)

* [HPE StoreOnce](deduplicating_appliance_storeonce.md)

If you plan to use HPE StoreOnce as a backup repository for MongoDB backups, the total number of stored files (data and metadata) must not exceed 3,000,000 per Catalyst store. If necessary, multiple Catalyst stores may be created on the same StoreOnce system.

* [Quantum DXi](deduplicating_appliance_quantum.md)
* [ExaGrid](deduplicating_appliance_exgrid.md)

Make sure the repository is configured as described in the [ExaGrid](deduplicating_appliance_exgrid.md) section.

* [Hardened Repository](hardened_repository.md)

* [Object Storage Repository](object_storage_repository.md)

* [Scale-Out Backup Repository](backup_repository_sobr.md)

If you plan to use the scale-out backup repository, consider the following:

* Make sure that the scale-out backup repository contains repositories supported by Veeam Backup & Replication.
* If you plan to store MongoDB backups on scale-out backup repositories, Veeam Backup & Replication can store MongoDB backup files in the performance tier and capacity tier. The archive tier are not supported for MongoDB backups.

Object Storage Repository Limitations

Before you configure your backup infrastructure to back up to the object storage, consider the following limitations:

* You cannot back up data using an application backup policy to the following storage devices:

* S3 Compatible with Data Archiving
* Amazon S3 Glacier
* AWS Snowball
* Azure Archive
* Azure Data Box

* Data in object storage repositories must be managed solely by Veeam Backup & Replication, including retention and data management. Lifecycle rules are not supported, and their enabling may result in backup and restore failures.

* For backups located in object storage repositories, synthetic full backup is not supported.

* For backups located in object storage repositories, the Defragment and compact full backup file option is not supported.
* For backups located in object storage repositories, data recovery options are not available if you access the object storage repository using credentials with the read-only access permissions.

* For Microsoft Azure Blob storage, MongoDB Backup does not support soft delete for blobs.


