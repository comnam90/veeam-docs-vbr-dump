---
title: "Backup Files"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_backup_files.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# Backup Files

In this article

For every application backup policy for MongoDB, Veeam Backup & Replication creates and stores database backup files, and a separate metadata file for each backup chain. The backup files provide a consistent and integrated way for Veeam Backup & Replication to store and manage backup data, while ensuring that the data is protected, accessible and can be quickly restored when needed.

All backup files created by the backup policy reside in a dedicated folder in the backup repository. Veeam Backup & Replication creates a set of backup files for each replica set in a backup scope.

Backup Files

Veeam Backup & Replication stores data backup files for each MongoDB replica set in a backup scope in the following formats:

* .VBK — full backup file.
* .VIB — incremental backup file.
* .VBM — backup metadata file. It contains information about the computer on which the backup was created, every restore point in the backup chain, how restore points are linked to each other and so on. The backup metadata file is required for restore operations.

The backup metadata file is updated with every backup policy session.

If you configured an application backup job to process the oplog and create log backups, Veeam Backup & Replication also stores log backup files in the following formats:

* .VLM — log backup job metadata file.
* .VLB — incremental log backup file.
* .VMM — log backup metadata file.

The backup metadata file is updated with every backup policy session.

For more information about the oplog backup, see [Oplog Backup](mongo_oplog_backup.md).

Page updated 7/31/2025

Page content applies to build 13.0.1.1071
